# F006 — Modo Me Acompanhe

**Categoria:** Movement
**Fase:** Fase 2
**Funciona sem rede de usuarios:** Sim (contatos do Circulo nao precisam do app)

---

## Objetivo

Permitir que uma mulher compartilhe seu trajeto em tempo real com pessoas de confianca, com alertas automaticos se algo sair do planejado.

---

## Quando usar

- Voltando sozinha a noite
- Caminhando por rota desconhecida
- Usando transporte publico em horario de risco
- Qualquer deslocamento em que quer que alguem saiba onde esta

---

## Fluxo de uso

### Ativar

1. Usuaria abre o app e toca em "Me Acompanhe"
2. Define o destino (busca de endereco ou seleciona no mapa)
3. App calcula rota estimada e tempo de chegada
4. Seleciona quais contatos do Circulo serao notificados
5. Inicia o modo — contatos recebem notificacao

### Durante o trajeto

- Localizacao atualizada a cada 30 segundos
- Contatos com app acompanham no mapa em tempo real
- Contatos sem app recebem link de rastreamento por SMS

### Chegou ao destino

- App detecta chegada automaticamente (geofence no destino)
- Ou usuaria confirma manualmente
- Contatos recebem confirmacao de chegada

### Se desviar da rota

- App detecta mudanca significativa de rota
- Pergunta a usuaria: "Voce mudou de plano?" com 60 segundos para responder
- Se nao responder: alerta para contatos com nova localizacao

### Se parar em local inesperado

- App detecta parada > 5 minutos em local nao planejado
- Pergunta: "Tudo bem?" com 60 segundos para responder
- Se nao responder: alerta para contatos

---

## Check-in automatico

Em viagens longas, usuaria pode ativar check-ins periodicos:
- A cada X minutos (configuravel: 15, 30, 60 min)
- App envia notificacao: "Tudo bem?"
- Usuaria responde com um toque
- Se nao responder em 3 minutos: alerta para contatos

---

## Mensagem para contatos ao iniciar

```
[REDE MULHER]
[Nome] esta a caminho de [Destino].
Previsao de chegada: 22:15 (em ~20 min)

Acompanhe em tempo real: [link]

Se ela nao confirmar chegada ate 22:30, entre em contato.
```

---

## Configuracoes

- Frequencia de atualizacao de GPS (impacta bateria)
- Quais contatos recebem rastreamento completo vs. apenas confirmacao de chegada
- Tolerancia para desvio de rota antes de acionar alerta (padrao: 300m)
- Tempo de espera antes de disparar alerta por inatividade

---

## Bateria e performance

- Modo de GPS otimizado: atualizacao a cada 30s consume ~3% de bateria por hora
- Modo economico disponivel para viagens longas: atualizacao a cada 2 minutos
- App mostra estimativa de consumo de bateria antes de iniciar
