# F028 — Rede de Guardias

**Categoria:** Core
**Fase:** Fase 1 (modo solo — features individuais sem rede) / Fase 3 (rede coletiva ativa — requer densidade mínima)
**Prioridade:** 🔴 Alta — define a identidade do produto
**Funciona sem rede de usuarios:** Parcialmente (features individuais funcionam; escudo ativo requer outras guardias na area)

---

## A ideia central

Uma guardia nao e uma vitima esperando socorro. E uma mulher que **escolheu ativamente proteger e ser protegida** pela rede.

Quando ela sai de casa e ativa o app, ela entra em um escudo coletivo — invisivel, silencioso, mas real. Outras guardias proximas sabem que ela esta ali. Ela sabe que elas estao ali. Ninguem precisa se conhecer. O compromisso e com a rede, nao com individuos.

> "Eu protejo voce. Voce me protege. Nos nunca nos vimos. Mas se algo acontecer, eu estou aqui."

---

## O que diferencia essa feature de tudo que existe

| App comum de seguranca | Rede de Guardias |
|------------------------|-----------------|
| Voce aciona quando ja esta em perigo | Voce ativa antes de sair — protecao preventiva |
| Depende de contatos que voce conhece | Funciona com estranhas que compartilham o compromisso |
| Alerta passivo — quem recebe decide se age | Guardia fez um pledge ativo — ela ja se comprometeu a responder |
| Cada mulher e uma ilha | Cada mulher e parte de um escudo coletivo |
| Reativo | Preventivo e continuo |

---

## Fluxo principal — "Estou saindo"

### 1. Ativacao
```
[Tela inicial]

Boa noite, Ana.

[ESTOU SAINDO]

Sua rede agora:
● 4 Guardias ativas perto de voce
```

Um toque. Sem formulario. Sem configuracao. Ela esta na rede.

### 2. Conexao com a rede
O app conecta silenciosamente com outras guardias ativas na area (raio configuravel: 500m, 1km, 2km).

Nenhuma guardia ve o nome ou rosto de outra — apenas:
- Quantas guardias estao ativas na area
- Um ponto anonimo no mapa representando cada uma
- Nivel de reputacao da guardia (escudo bronze, prata, ouro)

### 3. Durante o trajeto
- Guardia continua sua vida normalmente
- App roda em background com consumo minimo
- Se alguma guardia proxima acionar emergencia: todas recebem alerta imediato

### 4. Chegada segura
```
[Cheguei!]

Voce protegeu 3 pessoas hoje.
3 pessoas te protegeram hoje.

Ate a proxima.
```

Ao confirmar chegada, ela sai da rede ativa. Localizacao deletada do servidor.

---

## Sistema de verificacao — como garantir que e uma mulher

A verificacao nao usa reconhecimento de genero por imagem — tecnologia com vies racial e que excluiria mulheres trans. Em vez disso, usa camadas complementares:

### Camada 1 — Verificacao de numero real
- Numero de telefone valido (SMS OTP)
- Rejeita numeros VoIP (Skype, Google Voice, numeros temporarios)
- Um numero = uma conta — impossivel criar multiplas contas de teste

### Camada 2 — Onboarding declarativo
```
Para entrar na Rede de Guardias, voce declara:

"Identifico-me como mulher e entendo que esta
rede e um espaco exclusivo de protecao mutua
entre mulheres."

[Concordo e quero entrar]
```
- Declaracao cria responsabilidade legal (falsa declaracao = exclusao permanente)
- Inclui mulheres trans e nao-binarias que se identificam com o espaco
- Nao cria hierarquia de "quem e mulher de verdade"

### Camada 3 — Liveness check
- "Pisca os olhos" ou movimento especifico de cabeca
- Garante que e uma pessoa real, nao um bot ou foto
- Processado localmente — nenhuma imagem enviada para o servidor
- Realizado no onboarding e periodicamente (a cada 30 dias)

### Camada 4 — Vouching da comunidade
- Para acessar o modo guardia completo: 2 guardias existentes precisam aprovar a conta
- Aprovacao via link de convite ou QR code
- Quem faz vouching tem reputacao associada — se a conta aprovada for banida, a reputacao do voucher cai
- Cria responsabilidade social distribuida

### Camada 5 — Reputacao progressiva
```
Novata (0-7 dias)
  └── Pode usar features individuais (botao emergencia, circulo, etc.)
  └── Aparece na rede como "usuario nao verificado"

Guardia (7 dias + vouching)
  └── Acesso completo ao modo "Estou saindo"
  └── Aparece no mapa como guardia ativa
  └── Pode fazer vouching de novas membras (apos 30 dias)

Guardia Senior (90 dias + historico ativo)
  └── Reputacao maxima
  └── Seu vouching tem peso duplo
  └── Acesso a funcoes de moderacao da rede local
```

---

## O escudo — visualizacao da rede

### Mapa da guardia
- Pontos anonimos representando guardias ativas na area
- Intensidade de cor: mais guardias = area mais "protegida"
- A propria guardia ve sua posicao como estrela; outras sao circulos

### Contador de protecao
```
Agora:
🛡 Voce esta protegendo 4 mulheres
🛡 4 mulheres estao te protegendo
```

### Historico de impacto (pessoal)
```
Este mes:
47 horas como guardia ativa
12 mulheres diferentes na sua rede
1 emergencia respondida na sua area
```

---

## O que acontece quando uma guardia aciona emergencia

### Para a guardia em perigo
- Botao de emergencia (F001) acionado normalmente
- Alem do Circulo de Confianca: **todas as guardias ativas no raio recebem alerta imediato**

### Para as guardias proximas
```
[ALERTA DA REDE — GUARDIA PRECISA DE AJUDA]

Uma guardia esta em emergencia a ~200 metros.
Rua das Flores, altura do numero 400.

[Ligar 190 agora]   [Estou indo verificar]   [Nao posso agir agora]
```

### O protocolo da guardia que responde
Ela nao e policial. Nao deve se colocar em risco. O app orienta:

1. **Ligar 190 primeiro** — informar localizacao aproximada
2. **Ir ao local se seguro** — duas mulheres presentes ja muda a dinamica
3. **Fazer barulho / chamar atencao** — presencar e testemunhar ja ajuda
4. **Registrar** — fotografia do local (nao da vitima) como evidencia

---

## Reciprocidade — o pacto da rede

Ser guardia e um compromisso bilateral:
- Voce **recebe** protecao da rede
- Voce **oferece** protecao para a rede

O app torna isso visivel: cada vez que ela chega segura, ve quantas guardias estavam ativas por ela. Cada vez que ela responde a um alerta, ve o impacto.

Isso cria **obrigacao moral distribuida** — muito mais poderosa do que um botao de emergencia isolado.

---

## Modo guardia em locais fixos

Alem de "estou saindo", guardia pode ativar em locais onde passa tempo:
- "Estou no parque" — ativa raio de 200m ao redor
- "Estou trabalhando ate as 22h" — ativa guardia no bairro do trabalho
- "Estou em transporte publico" — ativa guardia na linha/trajeto

Isso preenche a rede 24h — nao so em deslocamento.

---

## Cold-start — como comecar sem rede

O problema classico: a rede so e util quando ha outras guardias. Como comecar?

### Estrategia de lancamento por bairro
1. Lancar em 1 bairro piloto (ex: Boa Viagem, Recife) com campanha de onboarding presencial
2. Meta: 100 guardias ativas no bairro antes de abrir para o proximo
3. Mapa mostra claramente onde ha guardias — cria FOMO geografico ("meu bairro ainda nao tem")
4. Cada guardia recebe link de convite para trazer 3 amigas — crescimento organico

### Modo solo (sem guardias proximas)
Mesmo sem rede ativa, a guardia tem acesso a todas as features individuais (F001-F005, F020, F021).
O app exibe honestamente:
```
Nenhuma guardia ativa perto de voce agora.
Seus recursos individuais continuam funcionando.
Convide amigas para fortalecer sua area.
```

---

## Privacidade absoluta

- Guardias nunca se veem pelo nome, foto ou qualquer dado pessoal
- Localizacao exata nunca e compartilhada — apenas area aproximada e distancia
- Ao sair da rede ("Cheguei"), localizacao deletada do servidor em tempo real
- Historico de quem esteve ativa na mesma area: nunca armazenado
- Comunicacao entre guardias: apenas via alertas pre-definidos — sem chat, sem identificacao

---

## Por que isso funciona socialmente

Pesquisas sobre redes de apoio informal mostram que:
- Mulheres tem maior probabilidade de ajudar estranhas do que estranhos
- O senso de reciprocidade ("ela pode estar me protegendo agora") aumenta engajamento
- Tornar o impacto visivel ("voce protegeu X pessoas") sustenta o comportamento
- Pertencer a uma rede tem valor identitario — "sou uma guardia" e uma identidade positiva

A Rede de Guardias nao e so uma feature. E uma **identidade coletiva**.
