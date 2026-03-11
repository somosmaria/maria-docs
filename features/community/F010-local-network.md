# F010 — Rede de Apoio Local

**Categoria:** Community
**Fase:** Fase 3
**Funciona sem rede de usuarios:** Nao — depende de densidade de usuarios na regiao

---

## Objetivo

Criar uma rede de mulheres proximas geograficamente que possam se apoiar mutuamente em situacoes de risco, mesmo sem se conhecerem pessoalmente.

---

## Como funciona

Quando uma usuaria aciona o botao de emergencia ou modo silencioso, mulheres cadastradas na plataforma e que estejam dentro de um raio configuravel recebem um alerta anonimo.

### Alerta recebido por mulheres proximas

```
[REDE MULHER]
Uma mulher proximo a voce (aprox. 150 metros) ativou um alerta de emergencia.

Voce pode ajudar:
[ Ligar 190 ]   [ Ver localizacao ]   [ Estou indo ]   [ Nao posso agora ]
```

### Acoes disponiveis para quem recebe o alerta

- **Ligar 190** — atalho direto para policia com localizacao copiada
- **Ver localizacao** — ver no mapa onde a pessoa esta (localizacao anonima — sem nome)
- **Estou indo** — sinaliza que vai ate o local (a pessoa em perigo recebe aviso)
- **Nao posso agora** — dispensa o alerta sem penalizacao

---

## Anonimato

- Quem emite o alerta: **identificada apenas pela localizacao**, sem nome ou foto para a rede local
- Quem responde: anonima para a pessoa em perigo (apenas "uma mulher da rede esta a caminho")
- Dados pessoais nunca expostos para desconhecidos

---

## Raio de alerta

- Padrao: 300 metros
- Configuravel pela usuaria: 100m, 300m, 500m, 1km
- Em areas de baixa densidade: raio expandido automaticamente ate encontrar usuarios

---

## Limite de alertas por periodo

- Maximo de 3 alertas por hora para uma mesma regiao
- Evita sobrecarga e fadiga de alertas na rede
- Alertas criticos (botao de emergencia) ignoram o limite

---

## Problema do cold-start

Esta feature nao funciona sem usuarios na mesma regiao. Estrategia de lancamento:

1. Lancar em cidades piloto com campanha focada em bairros especificos
2. Parcerias com universidades, ONGs, grupos de mulheres para criar densidade inicial
3. So expandir para nova cidade quando atingir 500 usuarios ativos

---

## Prevencao de abuso

- Usuarios falsos ou mal-intencionados: verificacao de perfil obrigatoria
- Sistema de reputacao: usuarios com comportamento adequado recebem mais visibilidade
- Relatorio de comportamento suspeito disponivel
- Moderacao ativa nos primeiros 6 meses de cada cidade

---

## Metricas de saude da rede

- Tempo medio de primeira resposta em alertas com >= 1 usuario proximo
- Taxa de resposta a alertas por regiao
- Densidade de usuarios ativos por bairro (mapa interno de cobertura)
