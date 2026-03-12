# Roadmap — Maria

---

## Principio de priorizacao

Cada fase so comeca quando a fase anterior estiver estavel em producao.
Features que dependem de rede (usuarios na mesma area) ficam para depois das features individuais.

**Legenda de prioridade:** 🔴 Alta  🟡 Media  🟢 Baixa

---

## Fase 1 — MVP Individual (Mes 1 a 4)

**Meta:** entregar valor para a primeira usuaria, sem depender de rede.
**Principio:** cada feature deve funcionar com zero outros usuarios.

| # | Feature | Prioridade | Doc |
|---|---------|-----------|-----|
| F001 | Botao de Emergencia | 🔴 | `features/core/F001-emergency-button.md` |
| F002 | Modo Protecao Silenciosa | 🔴 | `features/core/F002-silent-protection.md` |
| F003 | Modo Camuflado | 🔴 | `features/core/F003-camouflage-mode.md` |
| F004 | Circulo de Confianca | 🔴 | `features/core/F004-trust-circle.md` |
| F005 | Registro de Evidencias | 🔴 | `features/core/F005-evidence-recording.md` |
| F020 | Detector de Stalkerware | 🔴 | `features/core/F020-stalkerware-detector.md` |
| F021 | Chamada Falsa | 🔴 | `features/core/F021-fake-call.md` |
| F029 | Monitoramento de Chegada (ETA) | 🔴 | `features/movement/F029-eta-monitoring.md` |
| F030 | Protocolo Pós-Agressão | 🔴 | `features/prevention/F030-post-assault-protocol.md` |

### Criterios de saida da Fase 1
- App funcionando offline para alertas SMS fallback
- Modo Camuflado testado em iOS e Android
- Evidencias com criptografia E2E e hash verificavel
- Detector de stalkerware com base atualizada (Coalition Against Stalkerware)
- ETA: alerta SMS disparado corretamente em testes com prazo expirado
- Protocolo Pós-Agressão: validado por profissionais de saúde e juristas
- 100 usuarias beta com retencao > 40% em 30 dias

---

## Fase 2 — Deslocamento e Documentacao (Mes 5 a 8)

**Meta:** proteger mulheres em mobilidade e preparar saida segura de situacoes de violencia.

| # | Feature | Prioridade | Doc |
|---|---------|-----------|-----|
| F006 | Modo Me Acompanhe | 🔴 | `features/movement/F006-accompany-me.md` |
| F007 | Verificacao de Motorista | 🔴 | `features/movement/F007-ride-verification.md` |
| F008 | Check-in por Inatividade | 🔴 | `features/movement/F008-inactivity-checkin.md` |
| F009 | Modo Viagem | 🟡 | `features/movement/F009-travel-mode.md` |
| F023 | Cofre de Documentos | 🔴 | `features/prevention/F023-document-vault.md` |
| F026 | Modo Gravacao Continua | 🔴 | `features/core/F026-continuous-recording.md` |
| F031 | Modo Balada | 🔴 | `features/movement/F031-nightout-mode.md` |

### Criterios de saida da Fase 2
- Me Acompanhe com fallback SMS quando sem internet
- Check-in testado com janelas de 5, 15 e 30 min
- GPS em background: consumo < 5% por hora
- Cofre de Documentos com backup E2E funcionando
- Gravacao continua com upload automatico a cada 60s verificado
- Modo Balada: grupo de saída e check-in de bebida testados

---

## Fase 3 — Rede Comunitaria (Mes 9 a 14)

**Meta:** ativar camada de apoio entre usuarios e no espaco publico.

**Pre-requisito:** densidade minima de 500 usuarias ativas por cidade piloto.

| # | Feature | Prioridade | Doc |
|---|---------|-----------|-----|
| F010 | Rede de Apoio Local | 🔴 | `features/community/F010-local-network.md` |
| F011 | Mapa de Seguranca | 🔴 | `features/community/F011-safety-map.md` |
| F012 | Pontos Seguros | 🔴 | `features/community/F012-safe-points.md` |
| F013 | Relatos da Comunidade | 🟡 | `features/community/F013-community-reports.md` |
| F022 | Chat de Apoio com Voluntarias | 🟡 | `features/prevention/F022-support-chat.md` |
| F025 | Testemunha Voluntaria | 🟡 | `features/community/F025-witness-report.md` |
| F027 | Alerta para Vizinhos | 🟡 | `features/community/F027-neighbor-alert.md` |
| F028 | Rede de Guardias | 🔴 | `features/core/F028-guardian-network.md` |

### Criterios de saida da Fase 3
- 50 Pontos Seguros ativos na cidade piloto
- Chat com ao menos 20 voluntarias treinadas, fila < 5 min no horario de pico
- Rede local testada — rate limiting e moderacao validados
- Alerta de vizinhos funcionando com densidade minima de 50 usuarios/km²

---

## Fase 4 — Prevencao e Saida (Mes 15 a 20)

**Meta:** apoiar mulheres em situacao de violencia domestica continuada a documentar e sair.

| # | Feature | Prioridade | Doc |
|---|---------|-----------|-----|
| F014 | Diario de Incidentes | 🔴 | `features/prevention/F014-incident-diary.md` |
| F015 | Plano de Fuga | 🔴 | `features/prevention/F015-escape-plan.md` |
| F016 | Linha Direta com DEAMs | 🔴 | `features/prevention/F016-deam-direct-line.md` |
| F024 | Independencia Financeira | 🟡 | `features/prevention/F024-financial-independence.md` |

### Criterios de saida da Fase 4
- Parceria com ao menos 3 DEAMs para validacao de dados e fluxo
- Diario exportavel em formato aceito como prova juridica
- Mapeamento de abrigos atualizado e verificado por estado

---

## Fase 5 — Integracao Institucional (Mes 21+)

**Meta:** integrar com sistemas publicos — cadastro de agressores, monitoramento judicial.

**Pre-requisito:** produto com base de usuarios estabelecida e credibilidade institucional.

| # | Feature | Prioridade | Doc |
|---|---------|-----------|-----|
| F017 | Monitoramento de Medida Protetiva | 🔴 | `features/institutional/F017-protective-order-monitor.md` |
| F018 | Alertas Judiciais | 🟡 | `features/institutional/F018-judicial-alerts.md` |
| F019 | Consulta ao Cadastro de Agressores (CNPVD) | 🔴 | `features/institutional/F019-aggressor-registry.md` |

### Dependencias
- Parceria CNJ (CNPVD + SEEU)
- Acordo com operadoras de tornozeleira
- Aprovacao de framework legal de privacidade (LGPD + autorizacao judicial)
- Homologacao por tribunais estaduais parceiros

---

## Resumo de features por fase

| Fase | Features | Total |
|------|---------|-------|
| Fase 1 — MVP Individual | F001-F005, F020, F021, F029, F030 | 9 |
| Fase 2 — Deslocamento e Documentacao | F006-F009, F023, F026, F031 | 7 |
| Fase 3 — Rede Comunitaria | F010-F013, F022, F025, F027, F028 | 8 |
| Fase 4 — Prevencao e Saida | F014-F016, F024 | 4 |
| Fase 5 — Integracao Institucional | F017-F019 | 3 |
| **Total** | | **31** |

---

## O que nunca entra no roadmap

- Substituir policia ou servicos de emergencia oficiais
- Prometer seguranca absoluta
- Coletar dados de localizacao sem consentimento explicito e granular
- Monetizacao por publicidade (conflito direto com privacidade da usuaria)
- Lista de agressores gerada por usuarios (risco de difamacao e retaliacao)
- Features de rede antes do produto ter massa critica na cidade
