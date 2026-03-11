# F025 — Testemunha Voluntaria

**Categoria:** Community
**Fase:** Fase 3
**Prioridade:** Media
**Funciona sem rede de usuarios:** Nao (requer massa critica para ser util)

---

## Objetivo

Permitir que qualquer pessoa — homem ou mulher — registre e relate uma situacao de
violencia ou assedio que **presenciou** acontecendo com outra pessoa, mesmo sem
conhecer a vitima.

---

## A diferenca em relacao a outros relatos

| Feature | Quem relata | O que relata |
|---------|-------------|--------------|
| Diario de Incidentes (F014) | A propria vitima | O que aconteceu com ela |
| Relatos da Comunidade (F013) | A propria vitima | Onde se sentiu insegura |
| **Testemunha Voluntaria** | **Terceiro que presenciou** | **O que viu acontecer com outra pessoa** |

---

## Por que isso importa

- Muitas vitimas nao conseguem ou nao querem registrar elas mesmas
- Testemunho independente tem peso juridico diferente do relato da vitima
- Cria uma rede de "olhares atentos" no espaco publico
- Normaliza a intervencao social: "nao e da minha conta" vira "eu posso fazer algo"

---

## O que pode ser relatado

- Assedio em transporte publico (onibus, metro, trem)
- Agressao fisica em espaco publico
- Situacao de perseguicao
- Situacao suspeita (mulher claramente em estado de medo com alguem)
- Assedio em ambiente de trabalho (testemunha colega)

---

## Fluxo de relato

### Relato imediato (em tempo real)
```
Estou presenciando algo agora

[Tipo de situacao]
[Onde estou — GPS automatico]
[Descricao rapida (opcional)]

[Registrar e alertar Pontos Seguros proximos]
[Registrar apenas]
```

### Relato posterior
```
Presenciei algo

[Quando]
[Onde]
[O que aconteceu]
[Foto do local (opcional, sem faces)]
[Contato (opcional — para que autoridades possam consultar)]
```

---

## Intervencao segura — o que o app orienta

O app **nao encoraja confronto direto**. Orienta:

### O metodo dos 5 Ds (baseado em metodologia internacional)
1. **Distrair** — criar uma disturbacao que interrompe a situacao (derrubar algo, perguntar horas)
2. **Delegar** — pedir ajuda a alguem com autoridade (seguranca, motorista do onibus)
3. **Documentar** — registrar o que esta acontecendo com seguranca (sem interferir)
4. **Dirigir** — falar diretamente com a vitima, ignorando o agressor ("tudo bem?")
5. **Discutir** — relatar o incidente apos o fato (quando nao e seguro intervir na hora)

---

## Privacidade do testemunho

- Testemunha pode escolher: anonimo ou com contato opcional para autoridades
- Dados de contato (se fornecidos) ficam criptografados e so acessiveis por ordem judicial
- Relato anonimo tem validade como dado estatistico — relato com contato tem validade juridica potencial

---

## Uso das informacoes

### Dados agregados
- Alimentam o Mapa de Seguranca (F011) como camada de incidentes presenciados
- Relatorios por cidade para poder publico e imprensa

### Encaminhamento para autoridades
- Testemunha pode optar por encaminhar o relato para a DEAM da area
- App gera documento estruturado com os dados do relato
- Nao substitui BO — e um relato complementar

---

## Moderacao

- Relatos obviamente falsos ou abusivos: sistema de sinalizacao
- Relatos com localizacao em area residencial especifica: revisao antes de publicacao no mapa
- Nenhum dado do agressor e publicado (apenas dado agregado de tipo e area)

---

## Educacao para intervencao

Modulo educativo no app:
- O que fazer (e o que nao fazer) ao presenciar violencia
- Como relatar de forma util para autoridades
- Seus direitos como testemunha no Brasil
- Como apoiar uma vitima que voce conhece mas que nao pediu ajuda
