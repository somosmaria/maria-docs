# Tela Home — O Cockpit de Proteção

> A tela mais importante do app. O centro de controle. O que a usuária vê quando abre o Maria.

---

## Objetivo da tela

Em menos de 1 segundo, a usuária deve saber:
1. **Estou protegida?** → status de rede visível
2. **Tem Guardiãs perto?** → contador e radar
3. **O que faço agora?** → ação principal clara

---

## Layout — Estado: Rede Inativa (solo)

```
┌─────────────────────────────────────────┐
│  Boa noite, Ana          ● Online  🔔   │  14sp, text-secondary
├─────────────────────────────────────────┤
│                                         │
│         ┌─────────────────────┐         │
│         │                     │         │
│         │    ○ ─ ─ ─ ─ ─ ─   │         │  Radar: círculo externo
│         │       ○ ─ ─ ─       │         │  tracejado em violet/20
│         │           ★         │         │  ★ = posição da usuária
│         │                     │         │  Nenhum ponto = sem Guardiãs
│         └─────────────────────┘         │
│                                         │
│    Nenhuma Guardiã próxima agora.       │  text-tertiary, 14sp
│    Convide amigas para sua área →       │  link em violet-300
│                                         │
├─────────────────────────────────────────┤
│                                         │
│  ┌─────────────────────────────────┐   │
│  │  ▶  ESTOU SAINDO                │   │  Botão primário
│  └─────────────────────────────────┘   │  bg: violet-600, h: 60dp
│                                         │
│  ┌──────────────┐  ┌──────────────┐   │
│  │  📍 Me Acomp │  │  ⏱ Check-in │   │  Ações rápidas
│  └──────────────┘  └──────────────┘   │  bg: bg-surface, h: 56dp
│                                         │
│          [SOS]                          │  FAB vermelho, 64dp
│  🏠 Home  👁 Monit.  🔒 Prot.  👤 Eu  │  Bottom bar, 72dp
└─────────────────────────────────────────┘
```

---

## Layout — Estado: Rede Ativa (Guardiã ativada)

```
┌─────────────────────────────────────────┐
│  ● Protegida                       🔔   │  Verde, 14sp, negrito
├─────────────────────────────────────────┤
│                                         │
│         ┌─────────────────────┐         │
│         │  ●       ●          │         │  Radar animado
│         │     ○ ─ ─ ─ ─      │         │  Pontos roxos pulsando
│         │  ●     ★     ●      │         │  = Guardiãs ativas
│         │     ○ ─ ─ ─ ─      │         │  Linhas tracejadas
│         │          ●          │         │  conectam sutilmente
│         └─────────────────────┘         │
│                                         │
│    ● 7 Guardiãs protegendo você        │  Verde, 16sp, semibold
│    Raio de 500m · São Paulo             │  text-tertiary, 13sp
│                                         │
├─────────────────────────────────────────┤
│                                         │
│  ┌─────────────────────────────────┐   │
│  │  ■  CHEGUEI (encerrar)          │   │  Botão: bg-surface
│  └─────────────────────────────────┘   │  border: violet-600/40
│                                         │
│  ┌──────────────┐  ┌──────────────┐   │
│  │  📍 Rota     │  │  ⏱ 23 min   │   │  Me Acomp ativo / ETA
│  └──────────────┘  └──────────────┘   │  (estado ativo dos cards)
│                                         │
│          [SOS]                          │  Glow verde no FAB (inativo)
│  🏠 Home  👁 Monit.  🔒 Prot.  👤 Eu  │  Muda para vermelho se SOS
└─────────────────────────────────────────┘
```

---

## Componente: Radar de Guardiãs

O radar é o elemento visual central do app. Não é um mapa real — é uma representação abstrata e anônima da rede.

### Visual

- **Fundo**: `bg-base` (#0f060f)
- **Círculos concêntricos**: 2-3 anéis tracejados em `violet-600/15` a `violet-600/30`
- **Ponto central (★)**: `violet-100`, 10dp, pulsante suave
- **Pontos de Guardiãs (●)**: `violet-300`, 6dp, com glow `violet-600/30`
- **Animação dos pontos**: flutuam levemente (±3dp, 3-5s, ease in/out), nunca teleportam

### Estados do radar

| Estado | Visual |
|--------|--------|
| Solo (sem Guardiãs) | Apenas os anéis, sem pontos, cor violet-600/10 |
| Rede ativa (< 3 Guardiãs) | 1-3 pontos, anéis em violet-600/20 |
| Rede forte (3-10 Guardiãs) | Múltiplos pontos, anéis em violet-600/35, glow central |
| Alerta na rede | Um ponto pisca vermelho, radar pulsa |

### O que NÃO mostrar

- Localização exata das Guardiãs (apenas posição relativa aproximada)
- Identidade ou qualquer dado pessoal
- Quantidade exata acima de 10 ("10+" é suficiente e mais seguro)

---

## Componente: Botão "Estou Saindo"

O principal CTA do app. Ativa a usuária na rede de Guardiãs.

```
┌─────────────────────────────────────────┐
│  ▶  ESTOU SAINDO                        │
└─────────────────────────────────────────┘
```

- **Largura**: full-width (margem 20dp de cada lado)
- **Altura**: 60dp
- **Fundo**: gradiente linear `violet-600` → `violet-500`
- **Texto**: "ESTOU SAINDO", 16sp, DM Sans 700, branco, letter-spacing 0.05em
- **Ícone**: `Play` (Lucide), 18dp, à esquerda do texto
- **Hold delay**: 0.5s de segurar para ativar (evita toque acidental)
- **Feedback no hold**: borda ilumina progressivamente enquanto segura
- **Quando ativo**: muda para "■ CHEGUEI (encerrar)" com fundo `bg-surface` e border `violet-600`

---

## Componente: Cards de Ação Rápida

Dois cards lado a lado abaixo do botão principal.

```
┌──────────────┐  ┌──────────────┐
│ 📍           │  │ ⏱            │
│ Me Acompanhe │  │ Check-in ETA │
│              │  │ Configurar → │
└──────────────┘  └──────────────┘
```

- **Fundo**: `bg-surface` + border `rgba(255,255,255,0.06)`
- **Altura**: 80dp
- **Estado inativo**: ícone em `violet-300`, texto em `text-secondary`
- **Estado ativo** (feature em uso): borda em `violet-600/40`, fundo `violet-600/08`
- **Toque**: abre bottom sheet de configuração rápida

---

## Fluxo de ativação "Estou Saindo"

```
[Usuária segura o botão 0.5s]
       ↓
[Borda ilumina — feedback visual de "segurar"]
       ↓
[Soltar]
       ↓
[Vibração suave]
       ↓
[Radar anima — pontos de Guardiãs aparecem]
       ↓
[Contador atualiza: "X Guardiãs próximas"]
       ↓
[Status muda para "● Protegida"]
```

Se não há Guardiãs próximas:
```
[Toast discreto]: "Modo solo ativo. Seus recursos individuais funcionam."
```

---

## Header da tela Home

```
┌─────────────────────────────────────────┐
│  Boa noite, Ana          ● Online  🔔   │
└─────────────────────────────────────────┘
```

- **Saudação**: "Boa tarde/noite/manhã, [primeiro nome]" — humaniza sem expor
- **Status (● Online)**: sempre visível, muda conforme estado:
  - `● Online` (verde) — app funcionando, internet disponível
  - `● SMS` (âmbar) — sem internet, fallback ativo
  - `● Offline` (vermelho) — sem conexão de nenhum tipo
- **Ícone de notificação**: dot indicator discreta quando há alertas novos

---

## Considerações de segurança na Home

- Se o agressor pegar o telefone desbloqueado, o que ele vê?
  - Em modo normal: status "Online", radar sem pontos (se solo), botão "Estou Saindo" — ambíguo o suficiente
  - Em modo Guardiã ativo: radar com pontos — pode ser qualquer "app de GPS"
  - A Home NÃO deve ter nada que diga explicitamente "app de segurança contra agressores"
- O nome "Maria" e os textos foram cuidadosamente escolhidos para não trair o contexto
