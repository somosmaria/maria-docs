# F027 — Alerta para Vizinhos

**Categoria:** Community
**Fase:** Fase 3
**Prioridade:** Media — requer densidade de usuarios para funcionar
**Funciona sem rede de usuarios:** Nao (requer outros usuarios na mesma area)

---

## Objetivo

Notificar silenciosamente usuarios do Rede Mulher em um raio de 100 metros que ha uma
situacao de emergencia no local — permitindo que vizinhos tomem acao (ligar para o 190,
ir verificar, acionar o responsavel do predio).

---

## O problema

Em violencia domestica, o vizinho frequentemente ouve mas nao sabe o que fazer:
- Ouvir gritos e nao saber se e grave o suficiente para chamar a policia
- Nao querer "se meter" em assunto de casal
- Nao ter como saber se a mulher ja pediu ajuda

A mulher, por outro lado, pode nao conseguir gritar ou ligar — mas pode apertar um botao.
O Alerta para Vizinhos e o grito silencioso que atravessa paredes.

---

## Como funciona

### Ativacao
- Integrado ao botao de emergencia (F001) como camada adicional
- Ao acionar emergencia, usuaria ve opcao: "Alertar vizinhos tambem?" (opt-in)
- Pode ser ativado separadamente sem acionar emergencia completa

### O que os vizinhos recebem
```
[REDE MULHER — ALERTA PROXIMO]

Alguem esta pedindo ajuda a ~80 metros de voce.

O que voce pode fazer:
• Ligar 190 e informar o endereco aproximado
• Ir verificar se esta tudo bem
• Acionar o sindico ou responsavel do local

[Ligar 190]   [Ja liguei]   [Nao posso ajudar agora]
```

### O que os vizinhos NAO recebem
- Endereco exato (apenas distancia aproximada)
- Nome ou qualquer identificacao da usuaria
- Foto ou qualquer dado pessoal

---

## Privacidade por design

**O alerta e completamente anonimo e unidirecional:**
- Vizinhos nao sabem quem enviou — apenas que alguem na area precisa de ajuda
- Usuaria que enviou nao sabe quem recebeu nem quem respondeu
- Nao ha canal de comunicacao entre quem alertou e quem recebeu — apenas o 190 como acao

**Por que isso e seguro:**
- Agressor nao consegue usar o feature para identificar a vitima
- Nao e possivel rastrear quem enviou o alerta — nem o agressor pode descobrir

---

## Raio de alcance configuravel

| Configuracao | Raio | Uso tipico |
|-------------|------|-----------|
| Vizinhos imediatos | 50m | Apartamentos / casas geminadas |
| Quadra | 100m | Padrao — residencias em rua |
| Bairro proximo | 200m | Areas com baixa densidade de usuarios |

Raio maior = mais usuarios alertados = maior chance de resposta, mas menor precisao.

---

## Mecanismo tecnico

### Sem servidor central para localizacao
Para garantir anonimato:
1. Usuaria envia alerta com coordenadas imprecisadas (+/- 20m) para servidor
2. Servidor calcula quais usuarios estao no raio sem expor coordenada exata de nenhum dos dois
3. Notificacao push enviada sem incluir coordenadas
4. Coordenadas descartadas do servidor imediatamente apos envio das notificacoes

### Sem conexao (Bluetooth/Wi-Fi Direct)
- Se sem internet, alerta pode ser enviado via Bluetooth Low Energy (BLE) para dispositivos proximos
- Dispositivo receptor encaminha o alerta para o servidor se tiver conexao (relay anonimo)
- Funciona como mesh local — expande cobertura em situacoes de emergencia

---

## Previsao de efetividade por densidade

| Usuarios ativos por km² | % de chance de ao menos 1 vizinho receber |
|------------------------|------------------------------------------|
| 10 | ~15% |
| 50 | ~55% |
| 100 | ~80% |
| 200+ | ~95% |

**Por que Fase 3:** abaixo de 50 usuarios/km² o feature e pouco confiavel. Lancar antes gera
expectativa falsa e pode colocar a usuaria em risco (ela conta com o alerta e ninguem recebe).

---

## Prevencao de abuso

- Rate limiting: maximo 1 alerta por usuario por hora
- Cooldown automatico: apos resolucao, 30 minutos antes de novo alerta
- Alertas falsos repetidos: conta bloqueada para esse feature (nao para o app inteiro)
- Nenhum mecanismo de "cancelar alerta" rapido — cancelamento requer confirmacao de seguranca

---

## Integracao com condominio (futuro)

Parceria com apps de condominio (Minha Portaria, Condoflex):
- Alerta pode chegar para o porteiro / sindico do predio diretamente
- Porteiro tem protocolo de verificacao e acionamento do 190
- Muda o feature de "peer-to-peer" para "peer-to-responsavel"
