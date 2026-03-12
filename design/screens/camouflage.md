# Modo Camuflado — Design de Discrição

> O app mais seguro é o app que o agressor não sabe que existe.

---

## O problema que este modo resolve

Em relacionamentos abusivos, o controle do celular da vítima é comum:
- Agressor verifica apps instalados
- Agressor lê notificações
- Agressor procura por palavras-chave ("emergência", "fuga", "DEAM")
- Agressor deleta apps suspeitos

O Modo Camuflado transforma o Maria em um app completamente diferente — visualmente e funcionalmente — para qualquer pessoa que não saiba o código de acesso.

---

## Aparências disponíveis

A usuária escolhe uma "máscara" durante o setup:

### Opção 1 — Calculadora (padrão)

```
┌─────────────────────────────────────────┐
│                                         │
│                              0          │  Display da calculadora
│                                         │
├────────┬────────┬────────┬─────────────┤
│  AC    │  +/-   │   %    │    ÷        │
├────────┼────────┼────────┼─────────────┤
│   7    │   8    │   9    │    ×        │
├────────┼────────┼────────┼─────────────┤
│   4    │   5    │   6    │    −        │
├────────┼────────┼────────┼─────────────┤
│   1    │   2    │   3    │    +        │
├────────┴────────┼────────┼─────────────┤
│        0        │   ,    │    =        │
└─────────────────┴────────┴─────────────┘
```

- Calculadora funcional — faz cálculos reais
- Código de acesso: sequência específica (ex: `1998=`) que abre o Maria real
- Ícone do app: ícone de calculadora genérica
- Nome do app: "Calc" ou nome customizável pela usuária

### Opção 2 — Notas / Diário

App de notas simples, com texto de exemplo gerado automaticamente.

- Contém notas fictícias inocentes (lista de compras, etc.)
- Código de acesso: frase específica digitada no campo de busca
- Ícone do app: ícone de bloco de notas

### Opção 3 — App de Clima

Tela de previsão do tempo com localização real.

- Mostra clima real (usando API pública)
- Código de acesso: sequência de gestos (ex: 3 toques no ícone de sol)

---

## Fluxo de acesso — Calculadora (detalhado)

```
[Usuária abre o "app de calculadora"]
       ↓
[Vê calculadora normal — funcional]
       ↓
[Digita código de acesso: ex. 1998=]
       ↓
[Transição: calculadora "some" com fade de 300ms]
       ↓
[App Maria abre na tela Home]
```

### Código de acesso

- 4 a 8 dígitos + operador final (ex: `+`, `=`, `×`)
- Configurável pela usuária no setup
- Não há limite de tentativas (não queremos alertar o agressor)
- Entrada errada: calculadora simplesmente mostra o resultado do cálculo

---

## Visual: Notificações em modo camuflado

As notificações do app aparecem como do app-disfarce:

```
✗ NÃO fazer:
┌──────────────────────────────────────┐
│  🛡 Maria                            │
│  Ana, 3 Guardiãs próximas de você   │
└──────────────────────────────────────┘

✓ FAZER (modo camuflado ativo):
┌──────────────────────────────────────┐
│  🔢 Calc                             │
│  Lembrete configurado               │
└──────────────────────────────────────┘
```

- Nenhuma notificação do Maria aparece com conteúdo revelador
- Alertas críticos (emergência de Guardiã, SOS) vibram apenas — sem preview
- Emergência recebida enquanto em modo camuflado: apenas vibração forte (padrão duplo)

---

## Ícone do app e nome

| Configuração | Visual |
|-------------|--------|
| Padrão camuflado | Ícone de calculadora cinza + nome "Calc" |
| Personalizado | Usuária escolhe entre 8 ícones genéricos (clima, agenda, notas, etc.) |
| Nome | Customizável pela usuária (máx. 12 caracteres) |

O ícone original do Maria (escudo roxo) **nunca aparece** quando modo camuflado está ativo.

---

## Configuração do Modo Camuflado

Acessível em: **Eu → Modo Camuflado**

```
┌─────────────────────────────────────────┐
│  ← Modo Camuflado                       │
├─────────────────────────────────────────┤
│                                         │
│  Aparência do app                       │
│                                         │
│  ○ Calculadora         [preview]        │
│  ● Notas               [preview]        │  ← Selecionado
│  ○ Clima               [preview]        │
│                                         │
├─────────────────────────────────────────┤
│                                         │
│  Código de acesso                       │
│  ┌─────────────────────────────────┐   │
│  │  ••••=                          │   │
│  └─────────────────────────────────┘   │
│  [Alterar código]                       │
│                                         │
├─────────────────────────────────────────┤
│                                         │
│  Nome do app (visível na tela inicial)  │
│  ┌─────────────────────────────────┐   │
│  │  Calc                           │   │
│  └─────────────────────────────────┘   │
│                                         │
├─────────────────────────────────────────┤
│                                         │
│  ┌─────────────────────────────────┐   │
│  │  Ativar Modo Camuflado          │   │  Toggle
│  └─────────────────────────────────┘   │
│                                         │
│  ⚠ Após ativar, o app só abrirá       │
│  com seu código de acesso.             │
│  Não esqueça seu código.               │
└─────────────────────────────────────────┘
```

---

## Saída de emergência do modo camuflado

Mesmo em modo camuflado, o gesto de hardware (Vol+ + Vol-) funciona normalmente.
A usuária não precisa desativar o modo camuflado para acionar SOS.

```
[Gesto SOS via hardware]
       ↓
[SOS disparado — app continua mostrando calculadora]
       ↓
[Vibração discreta de confirmação]
       ↓
[Alertas enviados em background — sem nada na tela]
```

Esta é a feature mais crítica do modo camuflado: **o agressor vê a calculadora, a usuária acionou o SOS**.
