# F016 — Linha Direta com DEAMs

**Categoria:** Prevention
**Fase:** Fase 4
**Funciona sem rede de usuarios:** Sim (depende de parceria institucional, nao de usuarios)

---

## Objetivo

Conectar mulheres diretamente com a Delegacia da Mulher (DEAM) mais proxima — com informacoes atualizadas, sem precisar buscar numero de telefone e com opcao de relato pre-estruturado para agilizar o atendimento.

---

## O problema

A DEAM existe, mas a barreira de acesso e alta:
- Numero de telefone desatualizado na internet
- Horario de funcionamento incerto
- Mulher nao sabe o que dizer ou como iniciar o relato
- Vergonha ou medo de ser julgada ao ligar

Esta feature reduz essa barreira ao maximo.

---

## Funcionalidades

### Localizador de DEAM
- DEAM mais proxima com:
  - Distancia e como chegar
  - Horario de funcionamento real (atualizado semanalmente)
  - Telefone verificado
  - Se tem plantao 24h
  - Se tem atendimento presencial sem agendamento
  - Avaliacao anonima de usuarias que ja usaram

### Ligue agora
- Botao de chamada direta para a DEAM
- Fallback automatico para o 190 se DEAM nao atender em X segundos (configuravel)
- Fallback para Central de Atendimento a Mulher (180)

### Relato pre-estruturado
- Antes de ligar, usuaria pode preencher formulario rapido:
  - Tipo de violencia
  - Frequencia / ultima ocorrencia
  - Se ha ameaca atual
  - Se ha filhos envolvidos
- Formulario e exibido durante a chamada como roteiro para a usuaria
- Nao e enviado para a DEAM — e apenas um guia para a propria mulher

### Agendamento de BO online (integracao futura)
- Para estados com portal de BO digital (SP, MG)
- Link direto para o portal oficial
- Instrucoes passo a passo adaptadas ao estado

---

## Banco de dados de DEAMs

### Fonte dos dados
- Cadastro Nacional de Delegacias da Mulher (SENASP/MJSP)
- Atualizacao automatica mensal via API oficial (quando disponivel)
- Curadoria manual para dados incompletos ou desatualizados

### Campos mantidos por DEAM
- Nome oficial
- Endereco completo + coordenadas GPS
- Telefone(s) — principal e alternativo
- Horario de atendimento (por dia da semana)
- Se faz BO presencial sem agendamento
- Se tem plantao 24h
- Se tem psicóloga ou assistente social

### Mecanismo de atualizacao comunitaria
- Usuaria que ligou pode confirmar ou atualizar informacoes
- Flag "informacao possivelmente desatualizada" se ultimo verificador > 90 dias
- Time interno verifica flags em ate 5 dias uteis

---

## Para regioes sem DEAM

Em municipios sem DEAM:
1. Delegacia comum mais proxima (com nota de que nao e especializada)
2. CRAM (Centro de Referencia de Atendimento a Mulher)
3. Central 180 (nacional, 24h, sigilosa)
4. Ministerio Publico local (onde ha Promotoria da Mulher)

---

## Privacidade

- O app nao registra que a usuaria usou o localizador de DEAM
- Numero da DEAM nunca aparece no historico de chamadas do proprio app
- Chamadas sao feitas pelo discador nativo do sistema operacional

---

## Parceria necessaria

- **SENASP / MJSP:** acesso ao cadastro nacional e API de atualizacao
- **Secretarias Estaduais de Seguranca:** validacao de dados por estado
- **OAB:** lista de advogados pro bono por regiao para encaminhamento pos-relato

---

## Metricas de impacto

- Numero de DEAMs contatadas via app
- % de numeros verificados nos ultimos 30 dias
- NPS da experiencia de quem usou o recurso
- Tempo medio ate atendimento (pesquisa pos-uso, opcional)
