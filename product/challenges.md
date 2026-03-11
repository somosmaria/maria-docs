# Desafios e Mitigacoes

Este documento lista os principais desafios do produto e como a plataforma os enderca.

---

## 1. Cold-start — rede sem usuarios

**Problema:** Features que dependem de comunidade (rede local, mapa colaborativo) nao entregam valor para as primeiras usuarias.

**Mitigacao:**
- MVP e 100% standalone — botao de panico, Circulo de Confianca, Modo Camuflado, Me Acompanhe funcionam para o primeiro usuario com zero rede
- Features de comunidade entram somente na Fase 3, quando ha massa critica minima (10k usuarias ativas por cidade)
- Dados publicos (DEAMs, hospitais, iluminacao) alimentam o mapa desde o inicio sem depender de contribuicao da comunidade
- Parceria com organizacoes (Instituto Maria da Penha, SOS Mulher) para base inicial de usuarias verificadas

---

## 2. Confiabilidade em situacao critica

**Problema:** Em emergencia real, o app precisa funcionar mesmo sem internet, com bateria baixa, ou com dispositivo sob tensao.

**Mitigacao:**
- SMS via radio GSM como fallback quando sem dados (nao depende de internet)
- Botao de panico funciona offline por design
- Modo Silencioso nao requer conexao — ativado localmente
- Evidencias gravadas localmente antes de qualquer sincronizacao
- Interface simplificada para uso em estresse — botao grande, acao em 1 toque
- Watchdog interno: se o app for forcado a fechar, agenda SMS de alerta via sistema operacional

---

## 3. Privacidade vs. funcionalidade

**Problema:** Features de localizacao e monitoramento requerem dados sensíveis que, se vazados, colocam a usuaria em risco maior.

**Mitigacao:**
- Localizacao nunca armazenada no servidor alem do necessario (deletada apos evento)
- Telefones armazenados apenas como hash SHA-256 — sem PII em claro
- Circulo de Confianca: coordenadas compartilhadas em tempo real via canal criptografado, nao passam pelo servidor
- Modo Camuflado como camada adicional de protecao fisica do dispositivo
- Princípio de minimizacao de dados: coleta apenas o estritamente necessario para a funcao

---

## 4. Contas falsas e abuso da plataforma

**Problema:** Agressores podem criar contas para monitorar vitimas via rede local ou Circulo de Confianca, ou inserir dados falsos no mapa.

**Mitigacao:**

### Rede local (F008)
- Alertas sao totalmente anonimos e unidirecionais — quem emite nao sabe quem recebeu
- Nao ha "chat" ou canal de comunicacao — so alertas pre-definidos
- Rate limiting agressivo por dispositivo: maximo 3 alertas por hora
- Sistema de reputacao com decaimento temporal — alertas de contas novas tem peso menor
- Deteccao de anomalia: emissao de alertas fora de horario de sono identifica bots

### Mapa de seguranca (F009)
- Dados agregados antes de aparecer — minimo de N confirmacoes independentes
- Relatos individuais nunca publicos — apenas agregado aparece no mapa
- Janela de tempo: relato expira apos 30 dias sem confirmacao

### Circulo de Confianca (F004)
- Adicionar contato requer confirmacao bilateral (contato precisa aceitar)
- Nao ha listagem publica de usuarias — impossivel descobrir quem usa o app
- QR Code ou link de convite com TTL curto (24h) para adicao de contatos

---

## 5. Responsabilidade legal

**Problema:** Se o app falha em situacao de emergencia, ha risco de responsabilizacao. Se armazena evidencias de crimes, ha implicacoes legais.

**Mitigacao:**
- Termos de uso claros: plataforma e ferramenta de apoio, nao substitui servicos de emergencia
- Evidencias: plataforma nao tem acesso ao conteudo (E2E) — apenas armazena arquivo criptografado
- Parceria com juristas especializados em LGPD e violencia domestica para validar fluxos
- Politica de retencao de dados clara e auditavel
- Revisao juridica antes de qualquer integracao institucional (F012)

---

## 6. Sustentabilidade financeira

**Problema:** Monetizar um produto de seguranca para populacao vulneravel e eticamente complexo e pode limitar adocao.

**Estrategia:**
- App gratuito para todas as funcionalidades de seguranca — barreira zero para acesso
- Receita via:
  - **B2G (Business-to-Government):** licenca para prefeituras e estados como servico publico
  - **B2B (Empresas):** programa de seguranca para funcionarias (RH, ESG)
  - **Pontos Seguros parceiros:** taxa de adesao para estabelecimentos comerciais
  - **Financiamento publico:** editais BNDES, CNJ Justica 4.0, FAPESP, fundacoes internacionais
- Modelo open-source para funcionalidades core considerado para Fase 4 (ganha confianca)

---

## 7. Adocao sem momento de crise

**Problema:** Mulheres so baixam o app depois de um incidente, quando ja e tarde para configurar o Circulo de Confianca e treinar o uso.

**Mitigacao:**
- Campanha de adocao preventiva: "configure antes de precisar"
- Onboarding gamificado: progresso visivel ao configurar Circulo, ativar modo silencioso, etc.
- Parceria com escolas, universidades, empresas para workshops de configuracao em grupo
- Modulo de treinamento no app: simula situacoes para a usuaria praticar sem risco
- Funcionalidades uteis no dia a dia (Me Acompanhe, Mapa) — nao so em emergencia

---

## 8. Barreira tecnologica

**Problema:** Parte do publico-alvo tem baixo letramento digital e dispositivos de entrada com hardware limitado.

**Mitigacao:**
- Design acessivel como requisito nao-funcional desde o inicio (fonte legivel, contraste alto, botoes grandes)
- Onboarding em video curto (< 2 min) com linguagem simples
- Suporte a dispositivos Android com 2GB RAM e Android 8+
- Modo offline completo para funcionalidades criticas — sem dependencia de dados moveis
- Parceria com DEAMs e CRAMs para assistencia presencial de configuracao

---

## 9. Fragmentacao do sistema publico

**Problema:** Cada estado tem sistemas diferentes (tornozeleiras, BOs digitais, CRAMs) — integracao e complexa e cara.

**Mitigacao:**
- Fase 1-3 sao 100% independentes de integracao governamental
- Fases 4-5 entram somente apos produto estabelecido e com recursos para navegar burocracia
- Comecar por estados com infraestrutura mais madura: SP, PE, MG
- Usar APIs abertas onde existem (Recife, SP ja tem dados de iluminacao publica abertos)
- Framework de adaptadores: cada estado e um conector separado, sem acoplamento ao core

---

## 10. Manutencao do banco de recursos locais

**Problema:** DEAMs, abrigos, CRAMs mudam de endereco, horario e capacidade — dados desatualizados criam risco real.

**Mitigacao:**
- Parceria com institutos (Maria da Penha, Patrícia Galvao) para curadoria mensal
- Pipeline automatizado de atualizacao: crawl + validacao humana para dados criticos
- Usuarios podem reportar informacao desatualizada (flag no app)
- SLA interno: dados de emergencia (190, DEAM) revisados semanalmente
- Fallback: sempre mostrar numero de telefone nacional (180) quando dado local incerto
