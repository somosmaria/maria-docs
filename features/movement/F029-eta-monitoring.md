# F029 — Monitoramento de Chegada (ETA)

**Categoria:** Movement
**Fase:** Fase 1 (MVP)
**Prioridade:** 🔴 Alta — simples, alto impacto, zero dependência de rede
**Funciona sem rede de usuarios:** Sim

---

## Objetivo

A mulher define um destino e um prazo. Se ela não confirmar chegada no tempo combinado,
o app manda mensagem automática para o contato de confiança — sem ela precisar fazer nada.

---

## A diferença para o F006 e F008

| Feature | O que monitora | Dispara quando |
|---------|---------------|----------------|
| F006 Me Acompanhe | Rota em tempo real | Desvio de rota |
| F008 Check-in Inatividade | Movimento do corpo | Para de se mover |
| **F029 ETA** | **Chegada ao destino** | **Não chegou no prazo** |

F029 é o mais silencioso dos três — roda completamente em background sem interação.
Ela só age se algo der errado.

---

## Fluxo principal

### Configuração (30 segundos)
```
Vou para:  [Casa da minha mãe        ]
Devo chegar em: [20 minutos  ▼]
Avisar: [Mãe — (81) 99999-0000  ▼]

[Iniciar monitoramento]
```

### Durante o trajeto
- App roda em background — ela não precisa olhar para ele
- GPS verifica periodicamente se está dentro do raio do destino
- Sem interação necessária

### Chegada detectada automaticamente
```
Você chegou! Tudo bem?

[Sim, cheguei bem ✓]   [Não estou bem]
```

Se não tocar em nada em 2 minutos após chegar: confirma automaticamente.
Mensagem enviada para o contato: "Ana chegou bem. 21h47."

### Prazo expirado sem chegada
```
[REDE MULHER — ETA EXPIRADO]
Ana definiu que chegaria às 22h.
Já são 22h08 e ela não chegou ao destino.

Última localização conhecida:
Av. Agamenon Magalhães, altura do 3200, Recife
Há 8 minutos.

[Ver no mapa]   [Ligar para Ana]   [Ligar 190]
```

---

## Configurações de prazo

### Prazo manual
- Qualquer valor: 5, 10, 15, 20, 30, 45, 60 minutos
- Estimativa automática baseada em GPS (distância atual ao destino)

### Margem de tolerância
- Padrão: 5 minutos de tolerância após o prazo
- Configurável: 2 a 15 minutos
- Evita falsos alarmes por trânsito ou pequenos atrasos

### Extensão de prazo
Se ela está atrasada mas bem:
- Notificação discreta: "Seu prazo expira em 5 minutos. Tudo bem?"
- Um toque para adicionar +10 minutos sem precisar reconfigurar tudo
- Máximo de 2 extensões antes de confirmar manualmente

---

## Destinos salvos

- App aprende destinos frequentes (casa, trabalho, academia)
- Sugestão automática: "Voltando para casa? Monitorar chegada em 25 min?"
- Destinos salvos protegidos por PIN — agressor não vê para onde ela costuma ir

---

## Mensagem automática para o contato

### Formato da mensagem (SMS ou WhatsApp)
```
[Rede Mulher] Ana deveria ter chegado em casa às 22h.
São 22h09 e o app não confirmou chegada.

Última localização conhecida (22h01):
maps.google.com/?q=-8.0522,-34.9286

Por favor, tente contato ou acione o 190.
```

### Canais de envio (em ordem)
1. Push notification para o app do contato (se ele tiver o Rede Mulher)
2. WhatsApp (via API)
3. SMS (fallback garantido — não depende de internet)

---

## Modo discreto — sem notificação visível

Para quando o agressor pode ver a tela:
- Monitoramento ativo sem banner, sem som, sem vibração
- Apenas ícone minúsculo na barra de status (configurável para ocultar)
- Se ele pegar o celular: app parece desligado

---

## Ativação rápida pelo Modo Camuflado

Na "calculadora" disfarçada:
- Digitar destino como cálculo: `2205=` (22h05 como prazo) + número do destino salvo
- App ativa monitoramento sem abrir a interface real

---

## Integração com a Rede de Guardias (F028)

Quando ETA expira e contato não consegue agir:
- Opção de escalar para a Rede de Guardias na área do último GPS conhecido
- Guardias próximas recebem alerta da localização aproximada
- Ela não precisa ter ativado "Estou saindo" previamente — emergência sobrepõe

---

## Privacidade do destino

- Destino nunca armazenado no servidor — apenas no dispositivo
- Coordenadas GPS enviadas ao servidor apenas quando o prazo expira
- Após confirmação de chegada: dados do trajeto deletados imediatamente
- Contato recebe localização apenas em caso de não chegada
