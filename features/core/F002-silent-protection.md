# F002 — Modo Protecao Silenciosa

**Categoria:** Core
**Fase:** MVP (Fase 1)
**Funciona sem rede de usuarios:** Sim

---

## Objetivo

Permitir que uma mulher em situacao de violencia domestica ou convivendo com um agressor peca ajuda **sem que o agressor perceba**.

---

## O problema especifico

Em situacoes de violencia domestica, abrir o telefone, desbloquear e pressionar um botao pode ser impossivel ou perigoso. O agressor esta presente, pode ver a tela, pode ouvir sons.

A ativacao precisa ser **invisivel, silenciosa e rapida**.

---

## Metodos de ativacao

### Botoes fisicos
- Pressionar o botao de volume 3 vezes seguidas
- Segurar os dois botoes de volume simultaneamente por 2 segundos

### Toque discreto
- Tocar 5 vezes seguidas em um icone escondido na tela inicial
- Tocar em uma area especifica da tela de forma sequencial (definida pela propria usuaria)

### Voz (modo hands-free)
- Frase secreta configurada pela usuaria (ex: "ligar para minha mae")
- Ativada mesmo com tela desligada, se o app tiver permissao de microfone ativo

### Via relogio (se tiver smartwatch vinculado)
- Sequencia de toque no relogio
- Independe do celular estar acessivel

---

## O que acontece apos ativacao silenciosa

1. **Sem som, sem vibracao** — nenhuma resposta visual ou auditiva no dispositivo
2. **Tela permanece como estava** — nada muda na interface visivel
3. **Em background:**
   - Alerta enviado para Circulo de Confianca (SMS + push)
   - Localizacao em tempo real compartilhada
   - Gravacao de audio iniciada
   - Registro de horario e evidencias
4. **Contatos recebem mensagem diferenciada:**

```
[REDE MULHER - ALERTA SILENCIOSO]
[Nome] ativou o modo de protecao silenciosa.
Ela pode estar em uma situacao de risco.

NAO ligue para ela agora — pode ser perigoso.
Localizacao: https://maps.google.com/?q=-8.063,-34.871

Acoes recomendadas:
- Envie uma mensagem neutra ("oi, tudo bem?")
- Se nao houver resposta em 10 min, considere acionar autoridades
- Numero do DEAM mais proximo: (81) 3184-3200
```

---

## Desativacao

- Sequencia secreta configurada pela usuaria (diferente da ativacao)
- Ou via PIN na proxima vez que o app for aberto normalmente
- Se nao desativado em X minutos (configuravel), escala para alerta total

---

## Configuracao

A usuaria define na primeira configuracao:
- Qual metodo de ativacao prefere
- Quais contatos recebem o alerta silencioso
- Mensagem personalizada para os contatos
- Tempo ate escalar para alerta total

---

## Seguranca da feature

- Nenhuma notificacao visivel no dispositivo durante o modo silencioso
- Audio gravado nao e transmitido em tempo real (apenas armazenado localmente)
- Modo silencioso funciona com tela desligada e app em background
- Compativel com modo aviao (SMS como fallback)

---

## Limitacoes conhecidas

- iOS tem restricoes maiores para processos em background; pode precisar de permissao especial de acessibilidade
- Frase-chave via voz pode ser ativada acidentalmente em conversas normais; usuaria precisa escolher frase incomum
- Requer configuracao previa — nao funciona sem onboarding completo
