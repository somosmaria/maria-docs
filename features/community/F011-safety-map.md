# F011 — Mapa de Seguranca

**Categoria:** Community
**Fase:** Fase 3
**Funciona sem rede de usuarios:** Parcialmente (dados publicos existem independente de usuarios)

---

## Objetivo

Oferecer um mapa que ajude mulheres a tomar decisoes de rota e localizacao com base em informacoes de seguranca relevantes.

---

## Camadas do mapa

### Camada 1 — Dados publicos (disponivel desde o lancamento)
- Delegacias da Mulher (DEAMs) — localizacao, horario de funcionamento, telefone
- UPAs e hospitais proximos
- Postos policiais
- Iluminacao publica (dados de prefeituras quando disponivel via API)

### Camada 2 — Pontos Seguros parceiros (Fase 3)
- Estabelecimentos parceiros treinados (farmácias, bares, postos de gasolina)
- Identificados com icone especial no mapa
- Informacoes: horario, servico disponivel, contato

### Camada 3 — Dados da comunidade (requer densidade de usuarios)
- Areas marcadas como "senti medo aqui" pela comunidade de usuarios
- Areas marcadas como "me sinto segura aqui"
- Heatmap de incidentes reportados anonimamente

### Camada 4 — Historico de ocorrencias (requer parceria com SSP)
- Dados de ocorrencias policiais por bairro (quando disponibilizados pela SSP)
- Atualizados mensalmente
- Filtros: tipo de ocorrencia, periodo, horario

---

## Funcionalidades do mapa

### Rota mais segura
- Usuaria define origem e destino
- App sugere rota com melhor iluminacao e menor historico de incidentes
- Alternativa a rota mais rapida do Google Maps

### Modo noturno
- Realca iluminacao publica e pontos seguros
- Esconde rotas com baixa iluminacao

### Alerta de area
- Notificacao quando usuaria entra em area com historico elevado de incidentes
- Configuravel (pode desativar)

---

## Contribuicao da comunidade

As usuarios podem:
- Marcar um ponto no mapa com: "Senti medo aqui", "Fui assediada aqui", "Area bem iluminada"
- Confirmacoes de outros usuarios aumentam o peso do dado
- Dados anonimos — sem vinculacao ao perfil da usuario

---

## Privacidade dos dados contribuidos

- Nenhum relato e vinculado a um usuario especifico publicamente
- Dados sao agregados antes de aparecer no mapa
- Relatos individuais ficam apenas no banco da plataforma, nunca publicos

---

## Parceria para dados de iluminacao

Prefeituras de algumas cidades disponibilizam dados de iluminacao publica em formato aberto (ex: Recife, Sao Paulo). Onde nao disponivel, a plataforma pode usar:
- Dados do OpenStreetMap
- Contribuicao da propria comunidade de usuarios
