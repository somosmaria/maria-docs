# Identidade Visual — Maria

---

## Filosofia de cor

O roxo/violeta foi escolhido pelo significado e pelo contexto:
- Cor historicamente associada à causa feminista e à luta contra a violência doméstica
- Evoca proteção, nobreza, força interior — sem o perigo do vermelho nem a frieza do azul
- No espectro escuro, cria profundidade e seriedade — não leveza nem entretenimento

O fundo quase preto (`#0f060f`) define o tom: este app é sério, noturno, presente.
Como um painel de controle de missão. Como uma sala de monitoramento.

---

## Sistema de cores

### Cores base

| Token | Hex | Uso |
|-------|-----|-----|
| `--bg-base` | `#0f060f` | Fundo principal de todas as telas |
| `--bg-surface` | `#1a0a1e` | Cards, painéis, drawers |
| `--bg-elevated` | `#251530` | Modais, tooltips, sobreposições |
| `--bg-input` | `#200d28` | Campos de entrada |

### Cores de marca (violeta)

| Token | Hex | Uso |
|-------|-----|-----|
| `--violet-900` | `#3d1245` | Bordas sutis, divisores |
| `--violet-700` | `#5a1d6b` | Backgrounds de ícones ativos |
| `--violet-600` | `#7c2d8e` | Cor primária — botões, elementos ativos |
| `--violet-500` | `#9b3dbf` | Hover states, gradients |
| `--violet-300` | `#c472e4` | Acentos secundários, labels |
| `--violet-100` | `#e8b4f8` | Labels de seção, textos de destaque |
| `--violet-50` | `#f5e6fe` | Raramente — texto em fundo escuro muito legível |

### Cores de estado

| Token | Hex | Uso |
|-------|-----|-----|
| `--status-safe` | `#4ade80` | Protegida, online, ativo |
| `--status-warning` | `#f59e0b` | Atenção, sem rede, prazo próximo |
| `--status-danger` | `#e53e5a` | Emergência, perigo, offline crítico |
| `--status-inactive` | `#6b7280` | Desligado, inativo, indisponível |

### Cores de texto

| Token | Hex / Opacidade | Uso |
|-------|----------------|-----|
| `--text-primary` | `#ffffff` | Títulos, labels importantes |
| `--text-secondary` | `rgba(255,255,255,0.65)` | Corpo de texto, descrições |
| `--text-tertiary` | `rgba(255,255,255,0.40)` | Metadata, timestamps, placeholders |
| `--text-disabled` | `rgba(255,255,255,0.20)` | Elementos desabilitados |

### Gradientes

```
Glow de fundo (telas principais):
radial-gradient(ellipse at 50% 0%, rgba(124,45,142,0.15) 0%, transparent 60%)

Gradiente de emergência (ativação):
linear-gradient(135deg, #e53e5a 0%, #9b1f35 100%)

Gradiente de proteção ativa (modo Estou Saindo):
linear-gradient(135deg, #7c2d8e 0%, #5a1d6b 100%)
```

---

## Tipografia

### Fontes

| Fonte | Uso | Peso |
|-------|-----|------|
| **DM Sans** | Interface — toda a app | 400, 500, 600, 700 |
| **DM Serif Display** | Momentos de impacto, números grandes, marca | Regular (400) |
| **JetBrains Mono** | Timestamps, hashes, dados técnicos | 400 |

### Escala tipográfica

| Nível | Tamanho | Peso | Uso |
|-------|---------|------|-----|
| `display` | 48–64sp | DM Serif 400 | Número de Guardiãs, stat de impacto |
| `headline-l` | 28sp | DM Sans 700 | Títulos de seção principal |
| `headline-m` | 22sp | DM Sans 700 | Títulos de card, nome de feature |
| `headline-s` | 18sp | DM Sans 600 | Subtítulos, labels de navegação |
| `body-l` | 16sp | DM Sans 400 | Texto corrido, descrições |
| `body-m` | 14sp | DM Sans 400 | Cards secundários, listas |
| `body-s` | 12sp | DM Sans 400 | Captions, metadata |
| `label` | 11sp | DM Sans 700 | Labels em maiúsculas, badges |
| `mono` | 13sp | JetBrains Mono | Hashes, timestamps, IDs |

### Regras de uso

- **Nunca menos de 14sp** em texto funcional (acessibilidade + uso em estresse)
- Line height mínimo: **1.5** para corpo de texto
- Maiúsculas apenas em labels curtos (até 3 palavras), com `letter-spacing: 0.08em`
- Itálico apenas em citações e momentos emocionais — nunca em UI funcional

---

## Iconografia

### Família de ícones: Lucide (stroke, não fill)

Lucide foi escolhido por:
- Linha única, stroke — mais leve e elegante em fundo escuro
- Consistência total com o landing page
- Open source, sem dependências externas

### Tamanhos

| Contexto | Tamanho | Stroke width |
|----------|---------|--------------|
| Barra de navegação | 24×24dp | 1.75 |
| Cards e listas | 20×20dp | 1.75 |
| Botões com ícone | 18×18dp | 2.0 |
| Badges e chips | 14×14dp | 2.0 |
| Display / hero | 32–48dp | 1.5 |

### Ícones-chave do sistema

| Ação/Estado | Ícone Lucide |
|-------------|-------------|
| Emergência | `Siren` |
| Rede de Guardiãs | `Shield` |
| Modo silencioso | `EyeOff` |
| Modo camuflado | `Calculator` |
| Localização / Me acompanhe | `MapPin` |
| Check-in | `Clock` |
| Evidência / Gravação | `Mic` |
| Cofre | `FolderLock` |
| Guardiã ativa | `ShieldCheck` |
| Status OK | `CheckCircle` |
| Sem rede | `WifiOff` |
| Alerta | `AlertTriangle` |

---

## Bordas e elevação

### Raios de borda

| Elemento | Border radius |
|----------|--------------|
| Botão primário (CTA grande) | 16dp |
| Cards | 16dp |
| Chips / badges | 8dp |
| Bottom sheet | 24dp (topo) |
| Ícone container | 12dp |
| Pílulas de status | full (999dp) |

### Bordas (sempre sutis)

```
Border padrão:    1px solid rgba(255,255,255,0.08)
Border ativo:     1px solid rgba(124,45,142,0.40)
Border perigo:    1px solid rgba(229,62,90,0.30)
Border protegido: 1px solid rgba(74,222,128,0.25)
```

### Sombras / Glows

Não usamos `box-shadow` clássico em fundo escuro — usamos **glow radial**:

```
Glow violet (card ativo):   0 0 20px rgba(124,45,142,0.25)
Glow verde (protegida):     0 0 20px rgba(74,222,128,0.20)
Glow vermelho (emergência): 0 0 24px rgba(229,62,90,0.35)
```

---

## Espaçamento

Grid base: **4dp**. Todos os espaçamentos são múltiplos de 4.

| Token | Valor | Uso |
|-------|-------|-----|
| `--space-1` | 4dp | Espaço mínimo entre elementos relacionados |
| `--space-2` | 8dp | Padding interno de chips, espaço entre ícone e label |
| `--space-3` | 12dp | Padding de campos, espaço entre linhas de lista |
| `--space-4` | 16dp | Padding de cards pequenos, margem lateral padrão |
| `--space-5` | 20dp | Espaço entre seções próximas |
| `--space-6` | 24dp | Padding de cards médios |
| `--space-8` | 32dp | Espaço entre seções |
| `--space-10` | 40dp | Padding de bottom sheet, seções principais |

### Margem lateral da tela

- **16dp** mínimo em telas pequenas (< 360dp de largura)
- **20dp** padrão
- **24dp** em telas grandes

---

## Tema único: dark

O app é **100% dark theme**. Sem modo claro. Razões:
1. **Discrição**: tela escura chama menos atenção em ambientes controlados pelo agressor
2. **Bateria OLED**: telas pretas consomem muito menos energia — crítico em emergência
3. **Consistência visual** com o landing page
4. **Redução de fadiga**: uso noturno frequente (saídas à noite)
5. **Identidade forte**: dark violet é a assinatura visual do Maria
