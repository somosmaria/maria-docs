# F020 — Detector de Stalkerware

**Categoria:** Core
**Fase:** Fase 1 (MVP)
**Prioridade:** Alta — entrega valor imediato, sem depender de rede
**Funciona sem rede de usuarios:** Sim

---

## Objetivo

Detectar aplicativos de espionagem instalados no dispositivo — stalkerware, spyware, apps de monitoramento remoto — que o agressor pode ter instalado sem o conhecimento da usuaria.

---

## O problema

Controle digital e uma das formas mais comuns de violencia psicologica:
- Agressor instala app de rastreamento enquanto a vitima dorme ou deixa o celular
- Apps como "Find My Friends", "mSpy", "FlexiSPY" ou ate o proprio Google Family Link usados sem consentimento
- Microfone e camera ativados remotamente por apps mascarados como utilitarios
- A vitima nao sabe que esta sendo monitorada — o agressor sabe exatamente onde ela esta e com quem fala

Sem saber disso, qualquer plano de fuga ou pedido de ajuda pode ser interceptado.

---

## O que o detector verifica

### Apps de monitoramento conhecidos
- Base de dados de stalkerware conhecidos (atualizada pelo projeto Coalition Against Stalkerware)
- Apps com permissoes suspeitas: localizacao em background + acesso a SMS + microfone
- Apps instalados em modo "oculto" (sem icone na tela inicial)
- Apps com nomes genericos disfarçados ("Servico do Sistema", "Atualizacao de Seguranca")

### Permissoes suspeitas
- App com acesso a localizacao em background que nao e app de mapa/clima/mobilidade
- App com acesso a microfone que nunca e aberto pela usuario
- App com acesso a todos os SMS sem ser app de mensagens padrao
- App instalado com permissao de acessibilidade que nao e teclado ou leitor de tela

### Comportamento em background
- Processos que transmitem dados em background constantemente
- Consumo de bateria anormal de apps nao reconhecidos
- Trafego de rede de apps que nao deveriam ter acesso a internet

---

## Resultado da verificacao

### Sem ameacas detectadas
```
[VERIFICACAO CONCLUIDA]
Nenhum app suspeito encontrado.

Verifique periodicamente — apps novos podem ser
instalados sem voce perceber.

[Verificar novamente]   [O que devo observar]
```

### Ameaca detectada
```
[ATENCAO — APP SUSPEITO ENCONTRADO]

"Atualizacao do Sistema" foi instalado ha 3 dias
e tem acesso a sua localizacao, microfone e SMS
sem que voce tenha autorizado conscientemente.

Este tipo de app e usado para monitoramento.

[O que fazer agora]   [Como remover com seguranca]
```

---

## Como remover com seguranca

**Atencao critica:** remover o app pode alertar o agressor de que ele foi descoberto.
O app guia a usuaria com opcoes:

1. **Remover agora** — instrucoes passo a passo (se ela estiver em local seguro)
2. **Planejar remocao** — quando e onde fazer (quando estiver fora da vista do agressor)
3. **Nao remover ainda** — manter enquanto planeja saida (o agressor pensa que ainda tem controle)
4. **Trocar de dispositivo** — orientacoes para conseguir um numero e aparelho novo

---

## Limitacoes tecnicas

### Android
- Acesso completo a lista de apps instalados e permissoes — detector muito preciso
- Apps com permissao de administrador do dispositivo sao mais dificeis de detectar
- Factory reset pode ser necessario em casos graves

### iOS
- Sandbox do iOS impede varredura completa de outros apps
- Deteccao limitada a: perfis de configuracao instalados (MDM — Mobile Device Management)
- Verificacao de perfis: Settings > General > VPN & Device Management
- Instrucoes manuais para iOS onde varredura automatica nao e possivel

---

## Parceria com Coalition Against Stalkerware

Organizacao internacional que mantém base de dados de stalkerware conhecidos:
- Base atualizada semanalmente
- Parceria permite uso da base para lookup local (sem enviar dados do dispositivo)
- Protocolo de atualizacao: app baixa hashes dos apps maliciosos, compara localmente

---

## Privacidade da verificacao

- Verificacao 100% local — nenhuma lista de apps instalados sai do dispositivo
- Resultado nao armazenado no servidor
- Nenhum dado de identificacao enviado para parceiros

---

## Educacao preventiva

Alem da varredura, o app oferece:
- Checklist "meu celular esta seguro?" — permissoes a verificar manualmente
- "Como saber se alguem acessou meu celular" — sinais comportamentais
- "Como proteger meu celular" — PIN forte, autenticacao biometrica, apps de confianca
- Orientacoes para criancas: como falar sobre privacidade digital com filhos
