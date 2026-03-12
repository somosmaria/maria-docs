# Navegação e Arquitetura de Informação — Maria

---

## Princípio fundamental de navegação

> "A usuária nunca deve precisar navegar para estar protegida."

O estado de proteção (ativa/inativa) e o botão de emergência estão **sempre acessíveis**, independente de onde a usuária estiver no app. A navegação serve para configurar e monitorar — não para acionar proteção.

---

## Arquitetura de informação

```
Maria
│
├── [SEMPRE VISÍVEL] Botão de Emergência (FAB ou gesto)
├── [SEMPRE VISÍVEL] Status de proteção (header/barra)
│
├── 🏠 Home — Cockpit de Proteção
│   ├── Botão "Estou Saindo" (ativação da rede)
│   ├── Status da rede (Guardiãs próximas)
│   ├── Radar de proximidade animado
│   └── Ações rápidas (Me Acompanhe, Check-in ETA)
│
├── 👁️ Monitorar — Mapa e Rastreamento
│   ├── Mapa de segurança (DEAMs, Pontos Seguros)
│   ├── Modo Me Acompanhe (trajeto em tempo real)
│   ├── Check-in por Inatividade
│   └── Verificação de Motorista
│
├── 🔒 Proteger — Ferramentas Individuais
│   ├── Círculo de Confiança (contatos)
│   ├── Gravação Contínua
│   ├── Cofre de Documentos
│   ├── Diário de Incidentes
│   └── Plano de Fuga
│
└── ⚙️ Eu — Perfil e Configurações
    ├── Modo Camuflado (ativar/configurar)
    ├── Detector de Stalkerware
    ├── Configurações de privacidade
    └── Recursos de apoio (DEAMs, jurídico)
```

---

## Navegação principal: Bottom Tab Bar

4 abas. Nunca 5. Nunca hambúrguer menu.

```
┌─────────────────────────────────────────┐
│                                         │
│              [CONTEÚDO]                 │
│                                         │
│  ●────────────────────────────────────  │
│  🏠 Home   👁 Monitorar  🔒 Proteger  👤 Eu  │
└─────────────────────────────────────────┘
```

### Regras da bottom bar

- **Ícone + label** sempre (nunca só ícone — o contexto de estresse exige clareza)
- Aba ativa: ícone filled + label em `--violet-100` + indicador dot em `--violet-600`
- Abas inativas: ícone outline + label em `--text-tertiary`
- Altura da barra: **72dp** (garantia de tap target + safe area do iOS/Android)
- Sem badges de notificação numéricas — usa dot indicator discreta

---

## Botão de Emergência — sempre presente

O botão de emergência não pertence à navegação normal. Ele existe em duas formas:

### Forma 1 — FAB Persistente (telas Home e Monitorar)
```
┌─────────────────────────────────────────┐
│                                         │
│                                         │
│                                  [SOS]  │  ← FAB vermelho, canto inferior direito
│  🏠 Home   👁 Monit.  🔒 Prot.  👤 Eu  │
└─────────────────────────────────────────┘
```

- Posição: canto inferior direito, **acima** da bottom bar
- Tamanho: **64×64dp** (maior que qualquer outro elemento interativo)
- Cor: `--status-danger` com glow vermelho pulsante em modo ativo
- Ação: segurar 1.5s para acionar (evita acionamento acidental) — com feedback háptico progressivo
- Alternativa: botão de volume (hardware) configurável

### Forma 2 — Gesto silencioso
- Apertar volume+ e volume- simultaneamente por 2 segundos
- Funciona com tela bloqueada, app em background, modo camuflado
- Não exibe nenhuma confirmação visual (silencioso por design)

---

## Tela Home — o Cockpit

A tela mais importante do app. Deve transmitir em menos de 1 segundo:
1. **Estou protegida ou não?** (status imediato)
2. **Quantas Guardiãs perto de mim?** (força da rede)
3. **O que posso fazer agora?** (ações disponíveis)

```
┌─────────────────────────────────────────┐
│  Maria              ● Online  [🔔]     │  ← Header: status + notif
├─────────────────────────────────────────┤
│                                         │
│         ┌───────────────────┐           │
│         │   RADAR DE REDE   │           │  ← Visualização animada
│         │   ● ●   ◉   ● ●  │           │     círculos concêntricos
│         │      ★ VOCÊ       │           │     pontos = Guardiãs
│         │   ●     ●   ●    │           │
│         └───────────────────┘           │
│                                         │
│         7 Guardiãs próximas             │  ← Status da rede
│         Raio de 500m · São Paulo        │
│                                         │
├─────────────────────────────────────────┤
│                                         │
│  ┌─────────────────────────────────┐   │
│  │  ▶  ESTOU SAINDO                │   │  ← CTA primário (botão grande)
│  └─────────────────────────────────┘   │
│                                         │
│  ┌────────────┐   ┌────────────────┐   │
│  │ Me Acomp.  │   │  Check-in ETA  │   │  ← Ações rápidas (2 col)
│  └────────────┘   └────────────────┘   │
│                                         │
│  🏠 Home   👁 Monit.  🔒 Prot.  👤 Eu  │
└─────────────────────────────────────────┘
```

**Estado: sem rede ativa (modo solo)**
```
         Nenhuma Guardiã próxima agora.
         Seus recursos individuais funcionam.
         Convide amigas para fortalecer sua área. →
```

---

## Padrões de navegação interna

### Bottom Sheet (preferido para ações secundárias)

Usado para:
- Confirmação de emergência (bottom sheet com contagem regressiva)
- Detalhes de Ponto Seguro no mapa
- Configuração rápida de Check-in ETA
- Opções de compartilhamento de evidência

Nunca usado para:
- Fluxos com mais de 3 steps (usar tela dedicada)
- Conteúdo de leitura longa

### Full Screen Modal (fluxos críticos)

Usado para:
- Registro de evidência (gravar/foto)
- Ativação de emergência (com contagem + opção cancelar)
- Onboarding e configuração inicial
- Cofre de documentos (requer biometria)

### Push Navigation (telas de detalhe)

Usado para:
- Detalhe de feature em "Proteger"
- Configurações específicas
- Histórico de eventos

---

## Gestos e interações

| Gesto | Ação |
|-------|------|
| Segurar FAB 1.5s | Ativar emergência |
| Segurar botão "Estou Saindo" 0.5s | Ativar modo Guardiã |
| Swipe up na barra de status | Detalhes do status de proteção |
| Shake do dispositivo | Chamada falsa (configurável) |
| Volume+ + Volume- | SOS silencioso (hardware) |
| Triple tap no ícone do app | Abrir em modo camuflado |

---

## Estados do app

O app tem 4 estados visuais distintos que a usuária reconhece instantaneamente pela cor da interface:

| Estado | Cor dominante | Significado |
|--------|--------------|-------------|
| **Solo** | Violet escuro `#0f060f` | App ativo, modo individual, sem rede |
| **Rede ativa** | Violet médio `#1a0a1e` com glow verde | Guardiã na rede, protegida |
| **Emergência** | Vermelho `#e53e5a` dominante | SOS acionado |
| **Camuflado** | Cinza neutro (tema calculadora) | App disfarçado |

Essa codificação por cor permite que a usuária avalie o estado sem ler nenhum texto.

---

## Notificações

### Hierarquia de notificações

| Tipo | Canal | Vibração | Som | Preview |
|------|-------|----------|-----|---------|
| Emergência de Guardiã próxima | Crítico | Padrão forte | Sim | "Alerta da rede" (sem detalhes) |
| Check-in vencido (sua) | Alto | Padrão | Sim | "Lembrete de check-in" |
| Guardiã entrou no raio | Médio | Suave | Não | Sem preview |
| ETA de alguém no seu Círculo | Médio | Suave | Não | Sem preview |
| Novidades / dicas | Baixo | Não | Não | Sem preview |

### Regras de privacidade em notificações

- **Nunca** mostrar o nome da usuária no preview
- **Nunca** revelar que é um app de segurança no texto da notificação
- Preview padrão: "Maria" + mensagem genérica
- Em modo camuflado: notificações aparecem como do app-disfarce (ex: "Calculadora")
