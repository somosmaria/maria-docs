# Design — Maria

> "A diferença entre um app que salva e um app que falha pode ser um segundo. Ou um toque a mais."

---

## O que este app É — e o que NÃO É

| Maria É | Maria NÃO É |
|---------|------------|
| Um sistema de alerta e proteção | Uma rede social |
| Um cockpit de segurança pessoal | Um fórum ou chat |
| Uma ferramenta de ação rápida | Um app de conteúdo |
| Um monitor de estado de proteção | Um app de entretenimento |
| Um sistema discreto e invisível | Um app ostensivo |

Essa distinção define cada decisão de design. O modelo mental correto para o designer é:
**tela de controle de missão** — não feed de notícias.

---

## Princípios de design

### 1. Velocidade antes de estética
A usuária pode estar sob estresse extremo. Cada toque a mais é inaceitável.
- Ação crítica (emergência): máximo 1 toque a partir de qualquer tela
- Ação importante (ativar modo sair): máximo 2 toques
- Qualquer outra ação: máximo 3 toques

### 2. Clareza sob pressão
O cérebro sob medo perde capacidade cognitiva. O design compensa isso.
- Botões grandes (mínimo 56×56dp para ações críticas)
- Linguagem direta — sem eufemismos, sem ambiguidade
- Status sempre visível — a usuária nunca deve se perguntar "o app está funcionando?"
- Hierarquia visual brutal — o que importa é óbvio

### 3. Discrição total
O agressor não pode identificar o app. O design protege a usuária também visualmente.
- Sem ícones óbvios de "segurança" ou "alerta" na tela principal quando em modo camuflado
- Notificações sem preview revelador
- Modo camuflado: aparência de calculadora ou app utilitário
- Nenhuma tela deve trair a usuária se o agressor pegar o celular

### 4. Confiança imediata
A usuária precisa confiar que o app está funcionando antes de precisar dele.
- Status de proteção sempre visível e honesto
- Feedback imediato para toda ação
- Nunca deixar a usuária na dúvida ("o alerta foi enviado?")

### 5. Uma mão, qualquer hora
- Toda ação crítica acessível com o polegar direito ou esquerdo
- Sem gestos complexos para funções essenciais
- Funciona com tela molhada, bateria baixa, mão tremendo

---

## Arquivos deste diretório

| Arquivo | Conteúdo |
|---------|----------|
| `visual-identity.md` | Cores, tipografia, ícones, espaçamento |
| `navigation.md` | Arquitetura de informação, fluxos, menus |
| `usability.md` | Princípios de usabilidade para cenários de estresse |
| `screens/home.md` | Tela principal — o cockpit de proteção |
| `screens/emergency.md` | Fluxo de emergência |
| `screens/guardian-network.md` | Rede de Guardiãs |
| `screens/evidence.md` | Registro de evidências |
| `screens/camouflage.md` | Modo camuflado |
