# Privacidade e Seguranca

Este documento define as politicas e implementacoes de privacidade e seguranca do Maria. E um documento vivo — revisado a cada release maior.

---

## Principios fundamentais

### 1. Privacidade por design (Privacy by Design)
- Minimizacao de dados: coleta apenas o estritamente necessario para cada funcao
- Dados de localizacao nunca armazenados no servidor alem do necessario
- Anonimizacao por padrao — nenhum dado pessoal exposto em logs ou analytics

### 2. Seguranca para o cenario de ameaca real
O modelo de ameaca nao e o hacker comum — e o **agressor que tem acesso fisico ao dispositivo**. Toda decisao de seguranca parte desse cenario.

### 3. Confianca zero no servidor
Para dados de evidencias (audio, fotos, videos), a plataforma age como transportador cego — nao tem acesso ao conteudo. A chave de descriptografia e exclusiva da usuaria.

---

## Modelo de ameaca

| Ameaca | Probabilidade | Impacto | Mitigacao |
|--------|--------------|---------|-----------|
| Agressor com acesso fisico ao dispositivo | Alta | Critico | Modo Camuflado, PIN secundario, delecao de emergencia |
| Agressor descobre que a vitima usa o app | Alta | Critico | App disfarçado, notificacoes silenciosas |
| Vazamento de dados do servidor | Media | Alto | Hash de telefones, dados minimos, criptografia em repouso |
| Ataque MITM (man-in-the-middle) | Baixa | Alto | Certificate pinning, HTTPS obrigatorio |
| Criacao de conta falsa por agressor | Media | Medio | Confirmacao bilateral no Circulo, sem listagem publica |
| Engenharia social (suporte falso) | Baixa | Medio | Canal de suporte verificavel, nunca pede senha |
| DDoS em endpoint de emergencia | Baixa | Critico | Cloudflare WAF, rate limiting, redundancia multi-regiao |

---

## Dados coletados e sua finalidade

### Dados da conta
| Dado | Formato armazenado | Finalidade | Retencao |
|------|-------------------|------------|----------|
| Numero de telefone | SHA-256 hash | Identificacao unica | Ate delecao da conta |
| Dispositivo ID | Hash anonimizado | Anti-fraude, notificacoes | Ate logout permanente |
| FCM/APNs token | Cifrado | Push notifications | Renovado a cada sessao |

**Nunca coletado:** nome, email, foto de perfil, CPF, data de nascimento, genero.

### Dados de localizacao
| Contexto | O que e coletado | Quando e deletado |
|----------|-----------------|-------------------|
| Me Acompanhe (F006) | Pontos GPS em tempo real | Imediatamente apos fim do evento |
| Emergencia (F001) | Trilha de localizacao do evento | 90 dias apos resolucao do evento |
| Rede Local (F010) | Coordenadas aproximadas (+/-500m) | Nunca armazenado — apenas broadcast local |
| Mapa colaborativo (F011) | Ponto imprecisado (+/-50m) | Agregado — dado individual deletado em 30 dias |

### Evidencias (F005)
- Conteudo: AES-256-GCM, chave derivada de biometria/PIN da usuaria
- Servidor armazena: arquivo criptografado + hash SHA-256 + timestamp NTP
- Servidor **nao armazena**: chave de descriptografia (zero-knowledge)
- Retencao: ate deletado pela usuaria (ou 3 anos apos inatividade)

### Diario de incidentes (F014)
- Mesmo modelo de F005: criptografia E2E, zero-knowledge
- Backup criptografado: opt-in explicito, nunca automatico por padrao

---

## Seguranca do aplicativo

### Protecao fisica do dispositivo

**Modo Camuflado (F003)**
- App disfarçado como calculadora ou app utilitario
- Modo Camuflado ativavel via PIN de 6+ digitos
- No modo ativo: sem notificacoes reveladores, sem preview em app switcher

**PIN secundario**
- Secoes sensiveis (diario, plano de fuga, evidencias) protegidas por PIN separado do desbloqueio do app
- PIN incorreto 5 vezes: dados locais apagados (configuravel)

**Delecao de emergencia**
- Sequencia especifica de botoes: apaga diario, evidencias e plano de fuga em < 3 segundos
- Confirmacao visual: apenas o icone some — nao ha dialogo de confirmacao (tempo critico)

### Comunicacao

**Certificate pinning**
- App rejeita certificados SSL de autoridades nao confiadas
- Previne ataques MITM mesmo em redes comprometidas (Wi-Fi publico, corporativo)
- Rotacao de pins com fallback: 2 pins validos simultaneamente durante atualizacoes

**Canais de comunicacao**
- HTTPS com TLS 1.3 minimo para toda comunicacao com servidor
- WebSocket com autenticacao JWT para rastreamento em tempo real (F006)
- SMS via Twilio para alertas criticos (fallback sem internet)

### Autenticacao

**Login**
- Telefone + OTP via SMS (sem email/senha)
- OTP valido por 5 minutos, uso unico
- Rate limiting: max 3 tentativas de OTP por telefone/hora

**Sessao**
- JWT com TTL curto (15 minutos) + refresh token (30 dias)
- Rotacao de refresh token a cada uso
- Logout remoto: revoga todos os tokens ativos
- Sessao invalida automaticamente se dispositivo detecta root/jailbreak

**Acoes criticas (biometria)**
- Exportar evidencias, compartilhar plano de fuga, sair do Modo Silencioso — requerem biometria ou PIN
- Nao ha bypass por "esqueci a senha" para essas acoes — perda de acesso e intencional por design

---

## Seguranca do servidor

### Armazenamento de dados

**Banco de dados (PostgreSQL)**
- Criptografia em nivel de coluna para dados sensiveis (pgcrypto)
- Campos criptografados: tokens de dispositivo, FCM tokens, coordenadas GPS arquivadas
- Nenhum dado de identificacao pessoal (PII) em logs de servidor

**Arquivos de evidencia (Object Storage — S3-compatible)**
- Bucket privado, sem acesso publico
- Arquivos criptografados pelo cliente antes do upload (server nao tem a chave)
- URLs de acesso com TTL curto (15 minutos) geradas por assinatura HMAC

**Redis (cache e filas)**
- Sem dados pessoais — apenas IDs anonimizados e estados temporarios
- TTL definido para todas as chaves
- Flushado periodicamente em producao

### Infraestrutura

**Separacao de ambientes**
- Producao, staging e desenvolvimento completamente isolados
- Dados de producao nunca replicados para staging (dados sinteticos apenas)

**Acesso a producao**
- SSH apenas via chave RSA 4096-bit, sem password
- Acesso ao banco de dados: apenas via VPN interna, nunca porta publica
- Principio do menor privilegio: cada servico tem credenciais com permissoes minimas

**Monitoramento de seguranca**
- Alertas de anomalia: pico de requisicoes de um mesmo IP/usuario
- Deteccao de enumeracao: tentativas de descobrir IDs de usuarios
- WAF (Cloudflare): bloqueio de SQLi, XSS, path traversal
- Nenhum dado de usuario em logs — apenas IDs anonimos e codigos de erro

---

## Conformidade legal

### LGPD (Lei Geral de Protecao de Dados)

**Base legal para tratamento de dados sensiveis:**
- Art. 11, II, a) — protecao da vida (dados de localizacao em emergencia)
- Art. 11, II, f) — exercicio regular de direitos em processo judicial (evidencias)
- Consentimento (Art. 7, I) — para todas as funcionalidades opcionais

**Direitos da titular:**
- Confirmacao de tratamento: respondido em ate 15 dias
- Acesso aos dados: exportacao completa disponivel no app
- Correcao: editavel pelo proprio usuario
- Delecao: conta e todos os dados deletados em ate 30 dias apos solicitacao
- Portabilidade: exportacao em formato JSON

**DPO (Data Protection Officer):**
- Designado formalmente antes do lancamento publico
- Canal de contato visivel na politica de privacidade e no app

### Marco Civil da Internet
- Registros de conexao mantidos por 12 meses (obrigacao legal)
- Registros de acesso mantidos por 6 meses
- Divulgacao apenas mediante ordem judicial

---

## Resposta a incidentes

### Classificacao de incidentes

| Severidade | Definicao | SLA de resposta |
|-----------|-----------|----------------|
| P0 - Critico | Vazamento de dados de usuarios, endpoint de emergencia offline | 15 min |
| P1 - Alto | Autenticacao comprometida, dados corrompidos | 1 hora |
| P2 - Medio | Feature nao critica offline, anomalia de seguranca | 4 horas |
| P3 - Baixo | Bug de seguranca sem exposicao imediata | 48 horas |

### Plano de resposta P0
1. Isolamento imediato do sistema afetado
2. Notificacao ao time de seguranca (PagerDuty)
3. Avaliacao de escopo em 15 minutos
4. Se dados de usuarios expostos: notificacao ANPD em ate 72 horas (obrigacao LGPD)
5. Comunicado transparente para usuarios afetados
6. Post-mortem publico em ate 7 dias

---

## Auditoria e transparencia

### Auditoria interna
- Revisao de seguranca trimestral dos endpoints criticos
- Revisao de permissoes de acesso mensalmente
- Rotacao de credenciais de servico semestralmente

### Auditoria externa
- Pentest por empresa terceirizada antes de cada launch de fase
- Relatorio de auditoria publicado (com dados sensiveis redatados) no site

### Relatorio de transparencia
- Publicado semestralmente
- Contem: numero de requisicoes judiciais recebidas, numero de dados entregues, incidentes de seguranca, metricas de conformidade LGPD
