# F014 — Relatos da Comunidade

**Categoria:** Community
**Fase:** Fase 3
**Funciona sem rede de usuarios:** Nao (requer massa critica de contribuicoes)

---

## Objetivo

Permitir que usuarias compartilhem relatos anonimos de situacoes de assedio, violencia ou inseguranca em locais publicos — criando inteligencia coletiva sobre onde e quando mulheres se sentem em risco.

---

## O problema

Assedio em espaco publico raramente e registrado. A mulher nao sabe se o que aconteceu com ela e um padrao naquele local, se outras mulheres vivenciaram o mesmo, ou se o ponto de onibus onde ela espera todo dia tem historico de ocorrencias. Esse conhecimento coletivo existe — mas nunca foi agregado de forma acessivel.

---

## Tipos de relato

### Relato rapido (30 segundos)
- **O que aconteceu:** selecao de categorias
  - Assedio verbal / cantada de rua
  - Assedio fisico / toque sem consentimento
  - Perseguicao
  - Exibicionismo
  - Tentativa de sequestro / abordagem forcada
  - Furto / roubo
  - Sentiu medo / area insegura
  - Tentativa de agressao

- **Quando:** agora / hoje / esta semana (sem hora exata obrigatorio)
- **Onde:** GPS automatico (pode ajustar manualmente)
- **Periodo do dia:** manha / tarde / noite / madrugada

### Relato detalhado (opcional)
- Descricao em texto livre
- Foto do local (sem faces, sem dados pessoais)
- Referencia ao perfil do agressor (descricao generica — roupa, altura — nunca nome ou foto)

---

## Privacidade por design

- Nenhum relato e vinculado ao perfil publico da usuaria
- Texto livre e processado para remover dados pessoais antes de armazenamento (NLP)
- Coordenadas GPS sao imprecisadas em +/- 50 metros para anonimizacao
- Relatos individuais sao invisíveis — so o agregado aparece no mapa
- Usuaria pode deletar seus relatos a qualquer momento

---

## Moderacao e abuso

### Deteccao automatica
- Relato com coordenadas de area residencial privada e suspenso para revisao
- Pico anomalo de relatos no mesmo ponto em menos de 1 hora dispara revisao manual
- Relatos de contas criadas ha menos de 48h tem peso reduzido no agregado

### Moderacao humana
- Time de moderacao voluntaria (parceria com organizacoes parceiras)
- Relatos sinalizados por 3+ usuarias sao removidos automaticamente e enviados para revisao
- Nenhum moderador tem acesso a identidade de quem relatou

---

## Como os dados aparecem no mapa

### Heatmap
- Intensidade de cor baseada em numero de relatos nos ultimos 90 dias
- Mais recentes tem peso maior (decaimento temporal)
- Separado por periodo do dia (manha, tarde, noite)

### Pinos de categoria
- Icones por tipo de ocorrencia mais frequente naquele cluster
- Ao tocar: "X relatos de assedio verbal nesta area nos ultimos 3 meses"
- Nunca mostra relato individual — sempre agregado

### Alerta de area
- Ao entrar em area com historico elevado de ocorrencias:
  - Notificacao discreta: "Esta area tem relatos frequentes de assedio a noite"
  - Sugestao de rota alternativa se houver

---

## Funcionalidades sociais (anonimas)

### "Nao estou sozinha"
Ao ver um cluster de relatos: botao "Isso tambem aconteceu comigo aqui" — adiciona confirmacao sem novo relato.

### Compartilhamento externo
- Usuaria pode exportar link do mapa de uma area especifica para compartilhar em redes sociais
- Link mostra apenas dado agregado, sem qualquer informacao individual

---

## Dado como evidencia coletiva

### Relatorio por cidade/bairro
Periodicamente, a plataforma publica relatorios anonimizados e agregados com:
- Areas com maior concentracao de relatos por tipo
- Comparativo temporal (melhora ou piora)
- Dados desagregados por periodo do dia e dia da semana

### Uso por poder publico e imprensa
- API publica com dados agregados (sem microdados) para prefeituras e pesquisadores
- Dashboard para secretarias de seguranca publica parceiras
- Relatorios sob demanda para jornalismo de dados

---

## Metricas de saude do feature

- Taxa de engajamento: % de usuarias ativas que fizeram ao menos 1 relato
- Qualidade dos relatos: % sem necessidade de moderacao
- Cobertura geografica: % de bairros com ao menos 5 relatos
- Impacto: prefeituras/orgaos que citaram os dados em acoes publicas

---

## Limitacoes e transparencia

O app comunica ativamente ao usuario:
- Os dados sao auto-relatados — nao sao dados policiais oficiais
- A ausencia de relatos nao significa que o local e seguro
- O objetivo e complementar informacao oficial, nao substitui-la
- Dados devem ser usados como mais um indicador, nao como unica fonte de decisao
