# Tela de Emergência — Fluxo SOS

> O fluxo mais crítico do app. Zero margem para erro. Zero tolerância para lentidão.

---

## Princípios específicos deste fluxo

1. **Acionamento em 1 gesto** — segurar FAB 1.5s, nunca mais
2. **Cancelamento sempre possível** — mas com fricção (evitar cancelamento acidental sob pressão)
3. **Confirmação visual, sonora e háptica** — a usuária precisa ter certeza que foi
4. **Funcionamento offline** — SMS fallback, não depende de internet
5. **Discrição** — pode ser acionado sem olhar para a tela

---

## Formas de acionamento

| Método | Como | Onde funciona |
|--------|------|---------------|
| FAB (tela) | Segurar 1.5s | App aberto em qualquer tela |
| Gesto hardware | Vol+ + Vol- por 2s | Tela bloqueada, app em background |
| Modo silencioso | Sequência discreta configurada | App aberto |
| Shake | Agitar o celular 3x | App aberto (ativável nas config.) |

---

## Fluxo completo

```
ETAPA 1 — Acionamento
─────────────────────
[Usuária segura FAB vermelho]
  → 0.0s: Vibração suave começa
  → 0.5s: FAB expande, borda ilumina
  → 1.0s: Vibração forte
  → 1.5s: ACIONADO

           ↓

ETAPA 2 — Janela de cancelamento (3 segundos)
─────────────────────────────────────────────

┌─────────────────────────────────────────┐
│                                         │
│                                         │
│         🚨                              │
│                                         │
│    Enviando SOS em                      │
│         3                               │  ← Contagem regressiva
│                                         │     animada, grande (80sp)
│                                         │
│  ┌─────────────────────────────────┐   │
│  │  CANCELAR                       │   │  ← Botão grande, bg-elevated
│  └─────────────────────────────────┘   │     texto branco, borda vermelha
│                                         │
└─────────────────────────────────────────┘

  → Tela: fundo vermelho escuro (#1a0408)
  → Vibração pulsa a cada segundo
  → Se gesto hardware: sem tela — executa direto após 3s

           ↓ (se não cancelar)

ETAPA 3 — SOS Ativo
────────────────────

┌─────────────────────────────────────────┐
│  🚨 SOS ATIVO                           │  Header vermelho
├─────────────────────────────────────────┤
│                                         │
│  Alertando seu Círculo de Confiança...  │
│                                         │
│  ✓ Maria (mãe)           enviado        │  Lista de contatos
│  ✓ Camila (amiga)        enviado        │  com status de entrega
│  ◷ João (irmão)          enviando...    │
│                                         │
│  ────────────────────────────────────   │
│                                         │
│  ✓ 3 Guardiãs alertadas na área        │  Se rede ativa
│    (250m, 380m, 490m)                   │  Distâncias aproximadas
│                                         │
├─────────────────────────────────────────┤
│                                         │
│  ┌─────────────────────────────────┐   │
│  │  📍 Compartilhar localização    │   │  Ação adicional (opt-in)
│  └─────────────────────────────────┘   │
│                                         │
│  ┌─────────────────────────────────┐   │
│  │  📞 Ligar 190                   │   │  Acesso direto à polícia
│  └─────────────────────────────────┘   │
│                                         │
│  ┌─────────────────────────────────┐   │
│  │  🎙 Gravar áudio                │   │  Ativa gravação contínua
│  └─────────────────────────────────┘   │
│                                         │
│  ─────────────────────────────────────  │
│  Estou segura — encerrar SOS           │  Link discreto no fundo
└─────────────────────────────────────────┘
```

---

## Visual da tela SOS Ativo

- **Fundo**: `#160408` (vermelho muito escuro — diferente do preto normal, mas não gritante)
- **Header**: barra vermelha `#e53e5a` com "🚨 SOS ATIVO"
- **Pulsação**: glow vermelho suave no fundo, anima a cada 2s
- **Lista de contatos**: cada item tem ícone de status (check, spinner, X) em tempo real

### O que NÃO fazer na tela SOS

- ❌ Não colocar animações longas ou chamaativas — a usuária precisa de informação, não espetáculo
- ❌ Não exibir mapa visível na tela principal — pode revelar localização se alguém vê a tela
- ❌ Não exibir nome completo dos contatos se tela pode ser vista
- ❌ Não usar som padrão de sirene — discreto é mais seguro

---

## Modo silencioso — acionamento sem tela

Quando acionado via gesto de hardware (Vol+ + Vol-):

```
[Gesto detectado]
  → Sem alteração visual
  → Vibração discreta (1x curto)
  → SOS enviado via SMS para todos os contatos do Círculo
  → Localização incluída na mensagem
  → Gravação de áudio inicia em background
  → Tela permanece no que estava (app ou lock screen)
```

A usuária nunca vê a janela de cancelamento neste modo — é intencional.
Acionamento silencioso = situação em que ela não pode nem olhar pro celular.

---

## Mensagem SMS de emergência

```
[MARIA - EMERGÊNCIA]
Ana precisa de ajuda.
Localização atual: maps.google.com/...
Acionado às 22:47

Responda 1 para confirmar recebimento.
Este é um alerta automático do app Maria.
```

- Enviado para todos os contatos do Círculo simultaneamente
- SMS (não WhatsApp) — funciona sem internet
- Link de localização em tempo real (válido por 2h)
- Texto curto e direto — lido em segundos

---

## Encerrar o SOS

Encerrar o SOS tem fricção intencional — não deve ser fácil nem acidental.

```
[Usuária toca "Estou segura — encerrar SOS"]
       ↓
[Bottom sheet]:
"Você está segura?"

  ┌─────────────────────────────────────┐
  │  Sim, estou em segurança            │  ← Fundo verde
  └─────────────────────────────────────┘
  ┌─────────────────────────────────────┐
  │  Preciso de mais ajuda              │  ← Fundo vermelho
  └─────────────────────────────────────┘
  ┌─────────────────────────────────────┐
  │  Cancelar (voltar)                  │  ← Neutro
  └─────────────────────────────────────┘
```

Ao confirmar encerramento:
- Notificação automática para todos os contatos do Círculo: "Ana confirmou que está em segurança."
- Gravação de áudio encerrada e enviada para armazenamento seguro
- App retorna para tela Home

---

## Fallback por camadas

```
Internet disponível → Alertas via push + localização em tempo real
        ↓ (sem internet)
SMS via GSM → Alertas via texto + link de localização estática
        ↓ (sem sinal)
Registro local → Evento gravado localmente, enviado quando sinal voltar
```

A usuária sempre vê qual canal está sendo usado:
```
  ✓ Enviando via internet
  ⚡ Sem internet — usando SMS
  ⚠ Sem sinal — registrando localmente
```
