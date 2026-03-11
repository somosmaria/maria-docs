# F012 — Pontos Seguros

**Categoria:** Community
**Fase:** Fase 2
**Funciona sem rede de usuarios:** Sim (dados de parceiros, nao de usuarios)

---

## Objetivo

Criar uma rede fisica de estabelecimentos parceiros treinados que sirvam como refugio imediato para mulheres em situacao de risco — visivel no mapa do app e ativavel com um toque.

---

## O problema

Em uma situacao de risco iminente na rua, a mulher precisa de:
- Um lugar fisico para entrar e se proteger agora
- Sem precisar explicar, justificar, ou pedir permissao
- Com pessoas que saibam o que fazer

Ligar para o 190 pode demorar. Correr para casa pode ser mais perigoso. O Ponto Seguro e a opcao intermediaria que existe fisicamente no caminho.

---

## Como funciona

### Para a usuaria

1. App exibe Pontos Seguros proximos no mapa (mesmo sem abrir o app — widget de tela bloqueada)
2. Toque no Ponto Seguro mostra: nome, distancia, horario de funcionamento, como chegar
3. Ao entrar no estabelecimento: funcionario ve o icone/codigo no app e sabe o protocolo
4. Opcao de acionar Circulo de Confianca diretamente da tela do Ponto Seguro

### Para o estabelecimento

1. Recebe o alerta via sistema interno ou app do parceiro (se disponivel)
2. Segue o protocolo de acolhimento:
   - Oferecer espaco fisico seguro (area interna, longe da entrada)
   - Nao questionar ou pressionar
   - Oferecer agua, carregador de celular se necessario
   - Perguntar: "Voce quer que eu ligue para alguem?" ou "Quer que eu chame a policia?"
3. Registra o atendimento no sistema (anonimo) para relatorio de impacto

---

## Tipos de Pontos Seguros

### Tier 1 — Alta disponibilidade (24h ou quase)
- Farmácias (Ultrafarma, Pague Menos, Drogasil, Raia)
- Postos de gasolina com loja
- Hoteis e pousadas (recepcionistas treinados)
- Hospitais e UPAs (ja equipados para atendimento de violencia)

### Tier 2 — Horario comercial
- Supermercados e mercearias
- Bancos e casas loterias
- Bibliotecas publicas
- Universidades (portaria 24h)

### Tier 3 — Especializados
- DEAMs e CRAMs (funcao primaria — mas aparecem no mapa como Ponto Seguro tambem)
- Igrejas e centros religiosos com programa de acolhimento
- OAB (assistencia juridica)
- CRAS (Centro de Referencia de Assistencia Social)

---

## Protocolo de acolhimento (resumo)

Todos os Pontos Seguros recebem treinamento baseado em 4 principios:

1. **Acreditar** — sem questionar ou minimizar o relato
2. **Acolher** — oferecer espaco, nao empurrar para a rua
3. **Nao expor** — nao chamar atenção para a pessoa, nao revelar que ela esta la
4. **Encaminhar** — ajudar a acionar os recursos necessarios (190, DEAM, Circulo)

O treinamento e online, < 2 horas, com certificado valido por 2 anos.

---

## Funcionalidades no app

### Tela de Ponto Seguro proximo
```
[PONTO SEGURO MAIS PROXIMO]

Farmácia São João — 80m
Rua das Flores, 241 — Aberto 24h

[Como chegar]   [Ligar para o local]   [Avisar meu Circulo]
```

### Widget de emergencia (tela bloqueada)
- Exibe Ponto Seguro mais proximo sem desbloquear o telefone
- Distancia em metros e nome do estabelecimento

### Filtros de busca
- Por tipo de estabelecimento
- Por horario de funcionamento
- Por distancia
- "Aberto agora"

---

## Metricas de qualidade

### Por Ponto Seguro
- Numero de acionamentos no app (anonimo)
- Avaliacao da experiencia pela usuaria (voluntario, pos-evento)
- Ultima data de treinamento da equipe

### Para o programa
- Cobertura: % de areas urbanas com Ponto Seguro em raio de 500m
- Tempo medio de chegada ao Ponto Seguro mais proximo por cidade
- NPS das usuarias que usaram o recurso

---

## Expansao geografica

### Piloto (Fase 2 — Recife/PE)
- Meta: 50 estabelecimentos na Regiao Metropolitana do Recife
- Foco: farmacias, postos de gasolina, supermercados

### Escala nacional (Fase 3)
- Parceria nacional com redes de farmacia (cobertura automatica em 1.000+ cidades)
- Protocolo de onboarding escalavel: 100% digital, sem visita presencial

### Criterio de ativacao por cidade
- Minimo 20 Pontos Seguros ativos
- Distribuicao: ao menos 1 por bairro principal
- Ao menos 1 Ponto Seguro 24h por zona da cidade

---

## O que este feature nao e

- Nao e uma delegacia — nao tem poder de prender ou autuar
- Nao e uma casa de acolhimento — nao oferece hospedagem
- Nao substitui o 190 em caso de crime em andamento
- Nao garante atendimento especializado — apenas acolhimento inicial e encaminhamento
