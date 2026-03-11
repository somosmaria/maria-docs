# F026 — Modo Gravacao Continua

**Categoria:** Core
**Fase:** Fase 2
**Prioridade:** Alta — extensao natural do F005, alta demanda em violencia domestica
**Funciona sem rede de usuarios:** Sim (grava localmente; upload quando tiver conexao)

---

## Objetivo

Gravar audio continuamente em background e fazer upload automatico para armazenamento
seguro a cada 60 segundos — garantindo que o conteudo esteja preservado mesmo que o
dispositivo seja destruido, confiscado ou formatado pelo agressor.

---

## Por que 60 segundos

O intervalo de upload e critico:
- Muito rapido (ex: 5s): consumo excessivo de bateria e dados
- Muito lento (ex: 5min): agressor pode destruir o dispositivo antes do upload
- 60 segundos: equilibrio entre cobertura e consumo; mesmo se o dispositivo for destruido,
  o maximo perdido e o ultimo minuto

---

## Casos de uso

### Ameaca em andamento
Mulher percebe que a situacao vai escalar. Ativa o modo com um gesto discreto.
Mesmo que o celular seja tirado dela, o audio dos proximos minutos ja esta no servidor.

### Prova de violencia psicologica
Ameacas, humilhacoes, xingamentos — frequentemente sem testemunhas. Gravacao continua
pode capturar o padrao de comportamento ao longo do tempo.

### Cobertura de situacao de risco
Ao chegar em local de risco (reuniao forcada com o agressor, entrega de filhos), ativa
o modo antes de entrar.

---

## Ativacao

### Manual
- Botao discreto no app (nao na tela principal — requer acesso consciente)
- Gesto de ativacao: personalizado pela usuaria

### Via Modo Camuflado
- Sequencia de digitos especifica na "calculadora"
- Nenhuma indicacao visual de que esta gravando

### Automatica (opt-in)
- Quando o botao de emergencia e acionado (F001)
- Quando o Modo Silencioso e ativado (F002)

---

## Indicadores visuais

Por padrao: nenhum indicador visivel — icone de gravacao seria perigoso.

Opcao configuravel: LED piscando (so quando ela escolhe saber).

---

## Onde os audios ficam

### Armazenamento local
- Segmentos de 60s gravados localmente enquanto o upload nao acontece
- Maximo de 10 minutos de buffer local (10 segmentos)
- Segmentos mais antigos deletados automaticamente quando buffer cheio

### Upload automatico
- Cada segmento e criptografado no dispositivo antes do upload
- Upload via dados moveis ou Wi-Fi
- Se sem conexao: armazena localmente ate ter conexao
- Servidor armazena: arquivo criptografado + hash SHA-256 + timestamp NTP verificado

### Acesso
- So a usuaria pode descriptografar (zero-knowledge)
- Acessivel pelo Diario de Incidentes (F014) ou como arquivo avulso

---

## Consumo de recursos

| Recurso | Estimativa |
|---------|-----------|
| Bateria | ~8% por hora |
| Dados moveis | ~3 MB por hora (audio comprimido) |
| Armazenamento local | ~18 MB buffer de 10 min |

---

## Validade juridica

### Gravacao sem consentimento no Brasil

**Ponto critico:** a legislacao brasileira (CP Art. 151, §1) nao criminaliza a auto-gravacao —
gravar uma conversa da qual voce **participa** e legal, mesmo sem avisar a outra parte.

Gravacoes como prova em processo:
- STF ja aceitou gravacoes ambientais feitas pela vitima como prova (HC 91.867)
- Hash SHA-256 e timestamp NTP verificam que o arquivo nao foi editado
- Relatorio de integridade do arquivo gerado pelo app

O app inclui orientacoes sobre como apresentar a gravacao como prova juridica.

---

## Protecao contra abuso da feature

- Nao e possivel gravar terceiros sem que ela propria esteja presente
- Gravacao automatica so ativada via emergencia, nunca por terceiros
- Logs de ativacao armazenados localmente (quando, por quanto tempo)

---

## Limitacoes

- Qualidade do audio depende do microfone e da posicao do celular
- Ambiente com muito ruido pode comprometer o conteudo
- iOS tem restricoes tecnicas para gravacao de audio em background sem audio ativo — exige
  workaround (audio de frequencia inaudivel em loop para manter sessao de audio ativa)
- Bateria e dado: usuaria deve estar ciente do consumo antes de ativar por longo periodo
