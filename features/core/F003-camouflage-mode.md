# F003 — Modo Camuflado

**Categoria:** Core
**Fase:** MVP (Fase 1)
**Funciona sem rede de usuarios:** Sim

---

## Objetivo

Proteger mulheres em relacionamentos controladores onde o parceiro examina o celular regularmente. O app nao pode parecer um app de seguranca.

---

## Como funciona

O aplicativo pode operar em dois modos:

### Modo Disfarce (aparencia padrao)
Quando instalado, o app aparece na tela inicial como uma das seguintes opcoes (escolha da usuaria):
- Calculadora
- Bloco de Notas
- Conversor de Moedas
- Previsao do Tempo

O icone, nome e interface de abertura sao identicos a um app comum.

**Exemplo — Calculadora:**
- Abre com interface funcional de calculadora
- Realiza calculos reais normalmente
- Para um observador externo, e uma calculadora

### Desbloqueio do app real
Para acessar o app de seguranca, a usuaria:
- Digita um codigo secreto na calculadora (ex: `1985=` → um numero seguido de `=`)
- A tela transiciona silenciosamente para o app real
- O codigo e definido pela propria usuaria no onboarding

---

## Requisitos tecnicos

### Android
- Publicado como app de calculadora no Google Play
- Icone e nome alterados
- Intent filters configurados para parecer calculadora

### iOS
- App Store tem politicas mais rigorosas contra "apps enganosos"
- Estrategia: publicar como "calculadora + ferramentas de seguranca" com descricao generica
- Ou: usar atalho de acessibilidade para desbloquear sem mudar icone
- Ou: versao iOS sem modo camuflado completo, apenas com icone neutro

---

## Nome do app na loja

Opcoes que nao revelam o proposito:
- "Calc Pro — Tools"
- "Nota Segura"
- "Vault & Notes"

A descricao da loja menciona "ferramentas de organizacao pessoal" sem citar seguranca feminina explicitamente.

---

## O que fica visivel vs. oculto

| Elemento | Visivel para o parceiro | Protegido |
|----------|------------------------|-----------|
| Icone do app | Calculadora | Sim |
| Nome na lista de apps | "Calc Pro" | Sim |
| Notificacoes push | Silenciadas automaticamente | Sim |
| Historico de uso do app | Aparece como calculadora | Sim |
| Dados internos (alertas, evidencias) | Nunca | Sim |
| Contatos do Circulo | Nunca expostos pelo app | Sim |

---

## Situacao de exame do telefone

Se o parceiro pegar o telefone e abrir o app:
1. Ve interface de calculadora funcional
2. Nenhuma notificacao de seguranca visivel
3. Historico do app mostra apenas uso como calculadora
4. Sem dados comprometedores acessiveis

---

## Limitacoes conhecidas

- Parceiro tecnicamente sofisticado pode encontrar o app real via gerenciador de arquivos ou configuracoes avancadas
- Uso de VPN ou monitoramento de rede pode revelar que o app se comunica com servidores externos
- Mitigacao: comunicacao via HTTPS padrao, indistinguivel de qualquer outro app de produtividade
