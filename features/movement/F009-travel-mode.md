# F009 — Modo Viagem

**Categoria:** Movement
**Fase:** Fase 2
**Funciona sem rede de usuarios:** Sim

---

## Objetivo

Proteger mulheres em viagens de longa distancia — onibus interestadual, viagem de carro, deslocamento noturno — com rastreamento passivo de rota e alertas configurados para a duracao da viagem.

---

## O problema

O Me Acompanhe (F006) foi desenhado para trajetos curtos de minutos. Para uma viagem de 8 horas de onibus, a usuaria nao pode ficar com o app na tela o tempo todo. Precisa de um modo que:
- Monitore em background sem consumir bateria
- Alerte o Circulo se ela desviar da rota esperada
- Funcione mesmo com o celular em modo de baixo consumo

---

## Configuracao de uma viagem

```
Destino: Recife → Fortaleza
Medio de transporte: Onibus
Horario de partida: 22:00
Chegada estimada: 06:00
Empresa: Itapemirim (opcional)
Numero do onibus / assento: 12A (opcional)
```

O app pre-calcula a rota esperada (offline, dados baixados) e monitora se o GPS se desvia do corredor esperado.

---

## Alertas em viagem

### Alerta de desvio de rota
- Se o dispositivo sair do corredor de +/- 20km da rota calculada por mais de 15 minutos:
  - Notificacao para a usuaria: "Parece que voce saiu da rota. Esta tudo bem?"
  - Sem resposta em 5 minutos: alerta para o Circulo com localizacao atual e desvio detectado

### Alerta de parada prolongada
- Se o onibus (GPS parado) fica > 45 min sem se mover fora de uma cidade/rodoviaria:
  - Verificacao silenciosa para a usuaria
  - Sem resposta: update de localizacao para o Circulo

### Chegada no destino
- App detecta chegada no destino (raio de 5km)
- Notificacao: "Chegou em Fortaleza! Avisar seu Circulo?"
- Ao confirmar: mensagem automatica para todos os contatos: "Ana chegou bem em Fortaleza."

---

## Modo de baixo consumo em viagem longa

Durante o Modo Viagem:
- GPS amostragem a cada 5 minutos (vs. 30s no Me Acompanhe)
- Sem processamento de rota em tempo real — apenas verificacao periodica de corredor
- App pode ficar em background sem tela ativa
- Estimativa de consumo: < 8% de bateria por 8 horas de viagem

---

## Compartilhamento com o Circulo

### O que o Circulo pode ver em tempo real (opt-in)
- Posicao aproximada na rota (sem ponto exato — cidade ou trecho)
- Horario estimado de chegada atualizado

### O que o Circulo recebe apenas em alerta
- Localizacao GPS exata
- Natureza do alerta (desvio de rota / inatividade / emergencia)

---

## Integracao com transportadoras (Fase futura)

Parceria com empresas de onibus e aplicativos de passagem:
- Importacao automatica de dados da viagem ao comprar passagem
- Sem necessidade de digitar rota e horario manualmente
- **Destinos prioritarios:** Buser, FlixBus, Clickbus, Embarcou

---

## Modo offline

- Dados de rodovias principais pre-carregados no app (tiles offline)
- Rota calculada localmente sem internet
- Alertas enviados via SMS se sem dados moveis
- Suporte a areas sem cobertura de dados (estrada no interior)

---

## Privacidade

- Localizacao durante viagem: compartilhada apenas com Circulo de Confianca
- Historico de viagens armazenado localmente (nao no servidor)
- Dados de rota deletados do servidor 24h apos chegada ou cancelamento
- Nunca compartilhado com terceiros, incluindo transportadoras parceiras
