# F018 — Alertas Judiciais

**Categoria:** Institutional
**Fase:** Fase 5 (requer parceria governamental)
**Funciona sem rede de usuarios:** Sim (depende de integracao institucional)

---

## Objetivo

Manter a mulher informada proativamente sobre o andamento do processo legal — audiencias, renovacoes de medida protetiva, decisoes judiciais — sem que ela precise acompanhar portais juridicos complexos.

---

## O problema

O processo legal de violencia domestica e longo, burocrático e opaco para a vitima:
- Audiencias marcadas sem notificacao adequada
- Medidas protetivas vencem e precisam ser renovadas — muitas mulheres perdem o prazo
- Decisoes judiciais publicadas em diarios oficiais de dificil acesso
- A mulher fica dependente do advogado ou defensor para saber o que aconteceu

Esta feature coloca a mulher no controle do proprio processo.

---

## Tipos de alertas

### Prazo de vencimento de medida protetiva
```
[REDE MULHER - MEDIDA PROTETIVA]
Sua medida protetiva vence em 15 dias (10/04/2026).

Para renovar, voce precisa comparecer a DEAM ou protocolar pedido
na Defensoria Publica.

[Onde renovar]   [Ligar para a DEAM]
```

### Audiencia agendada
```
[REDE MULHER - AUDIENCIA]
Audiencia marcada para 25/03/2026 as 14h
Vara de Violencia Domestica — Forum do Recife

[Adicionar ao calendario]   [Instrucoes de preparo]
```

### Decisao judicial proferida
```
[REDE MULHER - DECISAO JUDICIAL]
Uma decisao foi proferida no seu processo.
Consulte seu advogado ou a Defensoria Publica para mais detalhes.
```

### Alerta de descumprimento de medida
```
[REDE MULHER - ATENCAO]
O sistema registrou uma possivelmente violacao da medida protetiva.
Voce pode registrar um boletim de ocorrencia.

[Como agir agora]   [Ligue 190]
```

---

## Integracao tecnica

### Fonte dos dados
- **SEEU (Sistema Eletronico de Execucao Unificado)** — CNJ
- **Portais dos Tribunais de Justica estaduais** (TJPE, TJSP, TJMG como piloto)
- **Sistema de Informacoes de Medidas Protetivas (SIM)** — onde disponivel

### Autorizacao
- Consentimento explicito da usuaria para vincular o CPF ao processo
- Autorizacao judicial para acesso ao processo especifico
- Dados de terceiros (agressor, testemunhas) nunca expostos para a usuaria

### Mecanismo de monitoramento
- Webhook registrado no sistema do tribunal (se API disponivel)
- Fallback: polling diario com scraping autorizado (onde sem API)
- Notificacao push ou SMS para alertas criticos (audiencias < 48h)

---

## Conteudo de apoio contextual

Para cada tipo de alerta, o app oferece contexto educativo:

- **Renovacao de medida:** passo a passo para pedir renovacao, documentos necessarios
- **Audiencia:** o que esperar, como se preparar, direito a acompanhante
- **Decisao:** glossario de termos juridicos comuns em linguagem simples
- **Descumprimento:** como provar, o que e crime, penas aplicaveis

---

## Parceiros necessarios

- **CNJ:** acesso ao SEEU e API de notificacoes
- **Tribunais Estaduais:** habilitacao nos portais de processo eletronico
- **Defensoria Publica:** conteudo de apoio juridico e encaminhamento
- **OAB:** lista de advogados especializados por regiao para encaminhamento

---

## Por que esta feature e Fase 5

- Requer integracao com sistemas judiciarios que tem processo de habilitacao lento
- Necessita de autorizacao judicial processo-a-processo ou via framework legal especifico
- Depende de credibilidade previa da plataforma junto ao poder judiciario
- Tecnicamente simples — politicamente e burocraticamente complexo

---

## Impacto potencial

Em 2023, o Brasil registrou mais de 400.000 medidas protetivas concedidas. Estima-se que 20-30% vencem sem renovacao por falta de informacao da vitima. Se esta feature previne apenas 10% dessas perdas, sao 40.000 mulheres com protecao legal que seria reestabelecida.
