# F004 — Circulo de Confianca

**Categoria:** Core
**Fase:** MVP (Fase 1)
**Funciona sem rede de usuarios:** Sim (contatos nao precisam ter o app)

---

## Objetivo

Criar uma rede pessoal de apoio — pessoas especificas que a usuaria confia e que recebem alertas em situacoes de risco.

---

## Conceito

O Circulo de Confianca e diferente da rede local (mulheres proximas desconhecidas). Sao pessoas escolhidas manualmente — familia, amigas, colegas — que conhecem a usuaria pessoalmente e sabem o contexto dela.

Esses contatos **nao precisam ter o app instalado**. Recebem alertas por SMS.

---

## Configuracao

### Limite de contatos
- MVP: ate 5 contatos
- Fase 2+: ate 10 contatos com roles diferenciados

### Tipos de contato
- **Contato primario** — recebe todos os alertas, tem acesso ao rastreamento em tempo real
- **Contato de emergencia** — recebe apenas alertas criticos (botao de emergencia, modo silencioso)
- **Contato de monitoramento** — acompanha trajetos no Modo Me Acompanhe

### Convidar contato
1. Usuaria adiciona nome e telefone
2. App envia SMS de convite com link explicativo
3. Contato pode instalar o app ou permanecer como contato SMS apenas
4. Contato com app tem mais recursos (ver localizacao em tempo real no mapa, responder alertas)

---

## O que cada contato recebe

| Evento | Contato SMS | Contato com app |
|--------|------------|-----------------|
| Botao de emergencia | SMS com localizacao | Push + rastreamento em tempo real |
| Modo silencioso | SMS com instrucoes | Push + rastreamento + instrucoes |
| Me Acompanhe iniciado | SMS de aviso | Notificacao + link de rastreamento |
| Chegou ao destino | SMS de confirmacao | Notificacao |
| Check-in sem resposta | SMS de alerta | Push de alerta critico |

---

## Painel do contato (com app instalado)

Quando um contato tem o app, ele ve:
- Status da usuaria (ok, em deslocamento, em alerta)
- Mapa com localizacao em tempo real durante alertas
- Historico de check-ins
- Botao para ligar diretamente para a usuaria
- Botao para acionar 190

---

## Privacidade do Circulo

- Contatos nao podem ver localizacao da usuaria em tempo normal (so durante alertas ou Me Acompanhe)
- Usuaria controla exatamente o que cada contato ve e em quais situacoes
- Contatos nao podem se ver entre si
- Dados do Circulo nao sao compartilhados com a rede local

---

## Configuracao de "Nao me rastreie agora"
- Usuaria pode pausar o Circulo temporariamente (ex: quer privacidade por um periodo)
- Pausa tem tempo limite configuravel
- Nao afeta o botao de emergencia — esse sempre funciona
