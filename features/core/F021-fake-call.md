# F021 — Chamada Falsa

**Categoria:** Core
**Fase:** Fase 1 (MVP)
**Prioridade:** Alta — feature simples, impacto imediato, zero dependencia de rede
**Funciona sem rede de usuarios:** Sim (100% local)

---

## Objetivo

Simular uma ligacao entrando no celular para que a usuaria possa sair de uma situacao
constrangedora, perigosa ou desconfortavel sem precisar explicar ou confrontar.

---

## O problema

Situacoes cotidianas onde a mulher precisa de uma saida rapida:
- Esta em um encontro e sente que algo esta errado
- Esta sendo assediada e nao quer confronto
- Precisa sair de uma situacao com o parceiro sem causar explosao
- Esta presa em uma conversa com desconhecido que a deixa desconfortavel
- Quer encerrar uma situacao sem ter que dar explicacao

A chamada falsa e a saida socialmente aceita que nao exige coragem de confronto.

---

## Como funciona

### Ativacao imediata
- Widget na tela de bloqueio: "Receber chamada em 30 segundos"
- Toque unico — sem abrir o app, sem desbloquear o celular
- 30 segundos depois: celular toca normalmente, como uma chamada real

### Ativacao agendada
- "Ligar para mim em X minutos" — configuravel: 1, 2, 5, 10, 15 min
- Util quando ela sabe com antecedencia que vai precisar de uma saida

### Personalizacao
- Nome do contato ficticio: qualquer nome que ela queira (padrao: "Mae")
- Foto: foto real de contato do celular ou foto padrao
- Ringtone: o padrao do celular (parece real)
- Duracao da chamada "atendida": livre — ela encerra quando quiser

---

## A simulacao da chamada

```
[Tela de chamada entrando]
Mae
celular

[Atender]   [Rejeitar]
```

Ao "atender":
```
[Em chamada — Mae]
00:12

[Mudo]   [Alto falante]   [Encerrar]
```

O app nao reproduz voz — a usuaria faz o monologo ("Oi mae... ah e? Ja vou, espera").
Simples e eficaz.

### Versao com audio (avancada)
- Audio pre-gravado de uma "voz de mae" ou "voz de amiga" (gravado pela propria usuaria)
- Reproduz em loop enquanto chamada esta "ativa"
- Permite que a usuaria coloque no viva-voz para reforcar a ilusao

---

## Integracao com Modo Camuflado

No Modo Camuflado (app disfarçado de calculadora):
- Sequencia especifica de digitos dispara chamada falsa imediata
- Ex: digitar "1111=" — celular toca em 30 segundos
- Nenhuma notificacao visivel de que o Rede Mulher foi acionado

---

## Casos de uso

| Situacao | Como usar |
|----------|-----------|
| Encontro que ficou estranho | Widget na tela de bloqueio antes do encontro |
| Assedio em transporte publico | Ativacao imediata pelo widget |
| Situacao tensa em casa | Sequencia no Modo Camuflado |
| Reuniao de trabalho desconfortavel | Agendada com antecedencia |
| Volta para casa sozinha a noite | Agendada para X minutos |

---

## Por que funciona

A chamada falsa funciona porque:
1. Interrompe o padrao da situacao sem confronto direto
2. Da uma desculpa socialmente aceita sem que a mulher precise mentir "conscientemente"
3. Permite saida rapida mesmo quando ela esta sob pressao psicologica
4. Nao exige que ela esteja em modo de "emergencia" — funciona para desconforto leve tambem

---

## Metricas de uso

- Feature com potencial de ser a mais usada do app no cotidiano
- Cada uso e uma oportunidade de retencao e lembranca do app
- Nao requer conexao, nao requer configuracao previa — zero fricao
