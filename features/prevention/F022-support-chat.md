# F022 — Chat de Apoio com Voluntarias

**Categoria:** Prevention
**Fase:** Fase 3
**Prioridade:** Media — requer infraestrutura humana antes de lancar
**Funciona sem rede de usuarios:** Nao (requer voluntarias ativas)

---

## Objetivo

Conectar mulheres em situacao de violencia ou desconforto com voluntarias treinadas para
escuta ativa e orientacao — de forma anonima, por texto, sem necessidade de ligar ou
se identificar.

---

## Por que texto e nao voz

- Mais discreto — pode ser feito com agressor no mesmo comodo
- Sem necessidade de local privado
- A mulher tem mais controle sobre o ritmo da conversa
- Historico visivel que ela pode relembrar depois
- Voluntaria pode atender multiplas conversas simultaneamente

---

## Quem sao as voluntarias

### Perfil
- Mulheres treinadas em escuta ativa e violencia domestica
- Nao sao terapeutas ou advogadas — sao ouvintes qualificadas
- Formacao: assistentes sociais, psicologas, advogadas, educadoras e mulheres com vivencia
- Treinamento obrigatorio: 20h online (teorico + simulacao de atendimentos)
- Renovacao: 8h por semestre

### Certificacao e parceria
- Parceria com Instituto Maria da Penha para formacao das voluntarias
- Certificado emitido pelo instituto
- Codigo de conduta rigoroso: sigilo, nao julgamento, nao diretividade

### Disponibilidade
- Meta: cobertura 24h com ao menos 1 voluntaria online
- Horario critico: 18h-23h (pico historico de acionamentos)
- Fila de espera visivel: "X pessoas aguardam, tempo estimado Y min"

---

## Fluxo da conversa

### Abertura (pela usuaria)
```
Ola. Aqui e um espaco seguro e sigiloso.
Estou aqui para ouvir voce.

Como voce esta se sentindo agora?

[Estou com medo]
[Preciso de orientacao]
[So quero conversar]
[Nao sei por onde comecar]
```

### Durante a conversa
- Voluntaria nao faz perguntas invasivas sobre o agressor
- Foco em como a usuaria esta se sentindo e o que ela precisa agora
- Orientacao para recursos (DEAM, abrigo, 180) quando pertinente
- Nunca pressiona para denunciar ou para sair do relacionamento

### Encerramento
```
Obrigada por confiar em mim.

Antes de encerrar, posso te mandar alguns
recursos que podem ser uteis?

[Sim, por favor]   [Nao, obrigada]

Voce pode voltar quando quiser.
```

---

## Anonimato e privacidade

### Para a usuaria
- Sem cadastro para usar o chat — anonimo por padrao
- Nenhuma informacao pessoal solicitada
- Historico de conversa armazenado apenas localmente (nao no servidor)
- Opcao de apagar historico a qualquer momento

### Para a voluntaria
- Ve apenas o que a usuaria escolhe compartilhar
- Nao ve IP, localizacao, ou qualquer dado de conta
- Codigo de usuario anonimo (ex: "Usuaria #4821") para continuidade de atendimento

### Criptografia
- Mensagens criptografadas em transito e em repouso
- Servidor nao tem acesso ao conteudo das mensagens
- Logs de moderacao: apenas metadados (horario, duracao) — sem conteudo

---

## Protocolo de crise

Se a voluntaria identifica risco imediato a vida:

1. Pergunta diretamente: "Voce esta em perigo agora?"
2. Se sim: apresenta botao de emergencia do Rede Mulher na propria tela do chat
3. Oferece ligar para o 190 junto (ela no chat, voluntaria no telefone separado)
4. Nunca encerra a conversa enquanto ha risco ativo — escalona para supervisora

---

## Moderacao e qualidade

- Supervisora online durante todos os turnos
- Voluntaria pode pedir supervisao a qualquer momento (botao interno)
- Revisao de amostragem de conversas (10%) pela supervisora — com consentimento informado
- Avaliacao pos-atendimento pela usuaria (opcional): estrelas 1-5

---

## Escalonamento humano

Quando o chat nao e suficiente:
- Central 180 (ligacao gratuita e sigilosa, 24h) — link direto
- DEAM mais proxima — link com informacoes atualizadas
- CAPS (Centro de Atencao Psicossocial) — para saude mental
- CVV (Centro de Valorizacao da Vida) — se ha risco de autolesao

---

## Por que Fase 3 e nao Fase 1

- Requer recrutamento e treinamento de voluntarias antes de lancar
- Sem voluntarias suficientes, o chat offline frustra e abandona a usuaria em momento critico
- Fase 1 usa recursos externos (180, DEAM) como fallback humano
- Criterio de ativacao: ao menos 20 voluntarias treinadas cobrindo 18h-23h com fila < 5 min
