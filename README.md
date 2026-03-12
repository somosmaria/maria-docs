# Maria

> Uma guardia protege a outra. Juntas, formam um escudo.

---

## A ideia central

Quando uma mulher sai de casa e ativa o app, ela entra automaticamente em uma rede de
proteção com outras mulheres que também estão fora — na mesma rua, no mesmo bairro.

Elas não se conhecem. Não precisam. O compromisso é com a rede.

Se algo acontece com uma, as outras já estão conectadas e prontas. Não é um botão de
pânico isolado. É um escudo coletivo, formado por mulheres que escolheram proteger e
ser protegidas.

**Isso é o que diferencia o Maria de qualquer outro app de segurança.**

---

## O problema

Mulheres no Brasil enfrentam violência de forma sistêmica:

- **4 mulheres assassinadas por dia** — recorde histórico de 1.470 feminicídios em 2025 (Ministério da Justiça)
- **68% dos feminicídios** cometidos por parceiros ou ex-parceiros
- **Medidas protetivas** existem, mas a execução depende de estrutura policial insuficiente
- O tempo entre pedir socorro e a ajuda chegar pode ser fatal

Apps existentes falham porque:
- Dependem de contatos que a mulher já conhece
- São reativos — só funcionam quando o perigo já chegou
- São facilmente identificados e deletados por agressores
- Não criam rede — cada mulher é uma ilha

---

## A solução — três camadas

### Camada 1 — Eu mesma
Features que funcionam sozinhas, sem rede, para qualquer mulher desde o primeiro dia.
- Botão de emergência com fallback SMS
- Modo Proteção Silenciosa (gestos discretos)
- Modo Camuflado (app disfarçado)
- Detector de Stalkerware
- Chamada Falsa
- Gravação Contínua com upload automático
- Cofre de Documentos criptografado

### Camada 2 — Meu círculo
Features que conectam a mulher com pessoas que ela já conhece e confia.
- Círculo de Confiança (até 5 contatos)
- Registro de Evidências (legal, E2E)
- Modo Me Acompanhe
- Check-in por Inatividade
- Modo Viagem

### Camada 3 — A rede de guardias
**A camada central.** Features que conectam mulheres entre si — sem se conhecerem —
formando um escudo coletivo e ativo.
- [**F028 Rede de Guardias**](docs/features/core/F028-guardian-network.md) — "Estou saindo": entra na rede de guardias ativas na area
- Pontos Seguros — estabelecimentos parceiros treinados
- Mapa de Segurança — inteligência coletiva sobre o espaço urbano
- Alerta para Vizinhos — grito silencioso que atravessa paredes
- Rede de Apoio Local — alertas anônimos entre mulheres próximas
- Testemunha Voluntária — denunciar o que você viu

---

## Como funciona na prática

```
Ana sai de casa às 22h para voltar do trabalho.

Abre o app → toca "Estou saindo"

App: "3 Guardias ativas perto de você agora."

Ana caminha. O app roda em background.
Nenhuma das 3 guardias sabe quem é Ana.
Ana não sabe quem são elas.
Mas todas sabem que estão se protegendo.

Ana chega em casa → toca "Cheguei"

App: "Você protegeu 3 mulheres hoje.
      3 mulheres te protegeram hoje."
```

---

## O que é uma Guardia

Uma guardia não é uma vítima esperando socorro. É uma mulher que:
- **Escolheu ativamente** estar disponível para proteger outras
- **Fez um pledge** com a rede — não com indivíduos
- **Oferece e recebe** proteção de forma recíproca
- **Age** quando uma guardia próxima aciona emergência (liga para o 190, vai ao local, faz barulho)

Ser guardia é uma identidade, não só uma função.

---

## Estrutura do repositório

```
maria-docs/
  product/
    vision.md           # Visão, missão, valores
    personas.md         # Perfis de usuário
    challenges.md       # Desafios e mitigações
    partnerships.md     # Parcerias por fase
  features/
    core/               # F001-F005, F020, F021, F026, F028
    movement/           # F006-F009, F029, F031
    community/          # F010-F013, F025, F027
    prevention/         # F014-F016, F022-F024, F030
    institutional/      # F017-F019
  technical/
    architecture.md
    privacy-security.md
  ROADMAP.md
```

---

## Roadmap resumido

| Fase | Meta | Features centrais |
|------|------|------------------|
| Fase 1 — MVP | Valor para a primeira usuária, sem rede | F001-F005, F020, F021, F028 (modo solo) |
| Fase 2 — Movimento | Proteção em deslocamento | F006-F009, F023, F026 |
| Fase 3 — Rede | Escudo coletivo ativo | F028 (rede completa), F010-F013, F027 |
| Fase 4 — Prevenção | Saída segura de situação abusiva | F014-F016, F022-F024 |
| Fase 5 — Institucional | Integração com sistema público | F017-F019 |

---

## Por que começar pelas features individuais

A Rede de Guardias só é poderosa com densidade de usuárias. Antes de ter essa densidade,
as features individuais (Camada 1) entregam valor real para cada mulher — e cada uma que
entra fortalece a rede para todas as outras.

O crescimento da rede é consequência da utilidade individual, não pré-requisito.
