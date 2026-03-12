# Usabilidade — Design para Cenários de Estresse

---

## O problema central de usabilidade

A usuária típica do Maria não está numa situação confortável quando mais precisa do app.
Ela pode estar:
- Com medo, coração acelerado, mãos tremendo
- Em ambiente monitorado pelo agressor
- Com bateria baixa, sem internet
- No escuro, correndo, em veículo
- Impossibilitada de olhar para a tela

**O design precisa funcionar para essa usuária, nesse momento.**
Design bonito que falha sob estresse não é design — é decoração.

---

## Princípios de stress design

### 1. Zero aprendizado na hora H

A usuária treina o app em momentos tranquilos. Na emergência, o músculo já sabe.
- Fluxo de emergência: **sempre o mesmo**, nunca muda
- Sem menus contextuais que variam conforme o estado
- Onboarding inclui simulação de uso sob pressão

### 2. Tap targets generosos

| Elemento | Tamanho mínimo | Justificativa |
|----------|---------------|---------------|
| Botão de emergência | 64×64dp | Dedo tremendo, precisão mínima |
| Ações críticas | 56×56dp | Polegar com pressão variável |
| Botões normais | 48×48dp | Padrão Material/HIG |
| Links e ações secundárias | 44×44dp | Mínimo absoluto |

**Nunca** colocar dois botões críticos adjacentes sem pelo menos 12dp de espaço.

### 3. Confirmação inteligente — nem demais, nem de menos

| Ação | Confirmação |
|------|-------------|
| Emergência | Segurar 1.5s + contagem regressiva de 3s (cancelável) |
| Ativar Modo Guardiã | Toque único + feedback háptico (sem confirmação) |
| Deletar evidência | Confirmação explícita com texto descritivo |
| Sair da rede | Toque em "Cheguei!" — sem confirmação (ela já decidiu) |
| Deletar conta | 3 passos com confirmação em cada |

**Regra:** confirmação apenas quando o erro é irreversível e grave. Nunca para ações que a usuária vai querer desfazer rápido.

### 4. Feedback inequívoco

Para cada ação crítica, a usuária recebe confirmação em 3 canais simultaneamente:

```
Emergência acionada:
  Visual:  Tela pisca vermelho → tela de emergência ativa
  Háptico: Vibração dupla forte
  Sonoro:  Beep curto (se som ligado)

Modo Guardiã ativado:
  Visual:  Radar começa a animar, contador de Guardiãs aparece
  Háptico: Vibração suave única
  Sonoro:  Silencioso (discrição)
```

### 5. Status sempre honesto

O app **nunca mente** sobre seu estado. Melhor frustrar do que criar falsa segurança.

```
✓  "7 Guardiãs próximas — proteção ativa"
✓  "Nenhuma Guardiã próxima agora"
✓  "Sem internet — alertas via SMS"
✓  "Bateria baixa — modo econômico ativo"

✗  Nunca: spinner infinito sem explicação
✗  Nunca: "Conectando..." sem timeout visível
✗  Nunca: silêncio após ação crítica
```

---

## Uso com uma mão

### Zona de alcance do polegar

Em smartphones modernos (>6"), a zona de alcance fácil do polegar cobre apenas o terço inferior da tela.

```
┌──────────────────┐
│  Zona difícil    │  ← Configurações, informação secundária
│                  │
├──────────────────┤
│  Zona média      │  ← Conteúdo principal, status
│                  │
├──────────────────┤
│  Zona fácil      │  ← Ações críticas, navegação ← AQUI
│  ████████████    │
└──────────────────┘
```

### Regras de posicionamento

- **Zona fácil (fundo da tela):** botão de emergência, bottom bar, botão "Estou Saindo"
- **Zona média:** radar de rede, status, informação que ela lê mas não toca
- **Zona difícil:** configurações, filtros, ações raramente usadas

### Alcance do polegar — regra prática

> Qualquer ação que a usuária pode precisar executar sem olhar para a tela deve estar no terço inferior da tela.

---

## Acessibilidade

### Requisitos mínimos (não negociáveis)

| Requisito | Padrão | Meta Maria |
|-----------|--------|------------|
| Contraste de texto | WCAG AA (4.5:1) | WCAG AAA (7:1) em texto crítico |
| Tamanho mínimo de fonte | 12sp | 14sp |
| Suporte a Dynamic Type (iOS) | Opcional | Obrigatório |
| Suporte a Large Text (Android) | Opcional | Obrigatório |
| VoiceOver/TalkBack | Parcial | Completo em fluxos críticos |

### Contraste no dark theme

O dark theme do Maria foi otimizado para alto contraste:
- Texto primário `#ffffff` sobre `#0f060f` → **contraste 20:1**
- Texto secundário `rgba(255,255,255,0.65)` → **contraste ~8:1**
- Labels de seção `#e8b4f8` → **contraste ~6:1**
- Texto desabilitado `rgba(255,255,255,0.20)` → contraste baixo intencional (indica inativo)

### Suporte a tamanhos de tela

- **Mínimo suportado:** 360×640dp (Android Go, smartphones de entrada)
- **Otimizado:** 390×844dp (iPhone 14 padrão)
- **Adaptado:** 430×932dp (iPhone 14 Plus, Android XL)
- **Tablet:** layout 2 colunas — Cockpit + Mapa lado a lado

---

## Performance percebida

A usuária julga a velocidade pelo que sente, não pelo que mede.

### Tempos máximos

| Ação | Tempo máximo | Se exceder |
|------|-------------|------------|
| Abrir app (cold start) | 2 segundos | Splash com radar animado |
| Acionar emergência | 0.5s para feedback visual | Nunca — é crítico |
| Ativar modo Guardiã | 1 segundo | Loading state no botão |
| Abrir cofre (biometria) | 1 segundo | Loading state |
| Carregar mapa | 2 segundos | Esqueleto animado + cache |

### Skeleton loading

Nunca mostrar tela em branco. Sempre usar skeleton animado com as dimensões exatas do conteúdo que vai aparecer. Isso reduz ansiedade percebida e evita layout shift.

### Otimismo na UI (Optimistic UI)

Para ações que quase sempre funcionam:
- Atualizar UI imediatamente, sincronizar em background
- Se falhar: desfazer silenciosamente + toast de erro

Para ações críticas:
- Nunca otimismo — confirmar no servidor antes de atualizar UI

---

## Cenários extremos de design

### Cenário 1: Bateria < 5%

- App entra em modo econômico automaticamente
- Desativa atualizações do mapa, radar em background
- Mantém: emergência, modo Guardiã, SMS fallback
- Banner discreto: "Bateria crítica — recursos essenciais preservados"

### Cenário 2: Sem internet

- Banner topo: "Sem internet — SMS ativo"
- Botão de emergência muda ícone para "📶 SMS"
- Features que precisam de rede: indicador de "offline" no lugar do conteúdo
- Gravação local continua — upload automático quando voltar

### Cenário 3: Dispositivo apreendido

- Sequência de botões (configurável) apaga dados sensíveis em < 3s
- Sem diálogo de confirmação — velocidade é tudo
- Ícone do app muda para o app-disfarce
- Histórico de navegação interna limpo automaticamente

### Cenário 4: Uso no escuro

- Brightness não reduzida automaticamente (pode trair a usuária)
- Todos os elementos têm contraste suficiente em luminosidade mínima da tela
- Botão de emergência tem borda iluminada (glow) visível mesmo em luminosidade zero

---

## Anti-padrões — o que nunca fazer

| Anti-padrão | Por quê evitar | Alternativa |
|-------------|---------------|-------------|
| Modal de confirmação para emergência | Adiciona toque sob estresse | Hold gesture com contagem regressiva |
| Notificação com texto revelador | Agressor pode ver | Preview genérico |
| Onboarding obrigatório antes da emergência | Bloqueia acesso imediato | Emergência disponível antes de completar setup |
| Swipe para deletar evidência | Gesto acidental | Botão com confirmação dupla |
| Sons alto em silêncio | Trair a usuária | Sempre respeitar modo silencioso do dispositivo |
| Animações longas (> 400ms) | Impaciente sob estresse | Animações ≤ 250ms em ações funcionais |
| Bottom sheet em cima de bottom sheet | Desorientação | Máximo 1 nível de sheet |
| Texto em caps lock extenso | Difícil de ler | Caps lock apenas em labels curtos |
| Funcionalidades escondidas em long press | Usuária não descobre | Tudo acessível via navegação explícita |
