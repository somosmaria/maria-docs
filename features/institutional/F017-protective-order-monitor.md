# F017 — Monitoramento de Medida Protetiva

**Categoria:** Institutional
**Fase:** Fase 5 (requer parceria governamental)
**Funciona sem rede de usuarios:** Sim (depende de integracao institucional, nao de usuarios)

---

## Objetivo

Alertar mulheres com medidas protetivas ativas quando o agressor monitorado eletronicamente se aproxima de locais de risco ou da propria vitima.

---

## O gap que esta feature resolve

A medida protetiva define uma distancia minima. O agressor com tornozeleira e monitorado. Mas a vitima **nao tem acesso a esse monitoramento em tempo real** — ela so descobre a violacao quando ja e tarde.

Esta feature fecha esse gap: a vitima recebe alerta proativo antes que o agressor chegue.

---

## Arquitetura da integracao

```
Tornozeleira eletronica (GPS)
        |
Sistema de monitoramento (SEEU/CNJ ou operadora)
        |
        | API segura com autorizacao judicial
        |
Plataforma Rede Mulher (backend)
        |
        | Push notification / SMS
        |
App da vitima
```

---

## Dados recebidos do sistema de monitoramento

- Posicao GPS do agressor (anonimizado — sem dados pessoais do agressor para a vitima)
- Status da tornozeleira (ativa, bateria baixa, sinal perdido)
- Alertas de violacao ja emitidos pelo sistema oficial

---

## Zonas de protecao configuradas pela vitima

A vitima define zonas de exclusao:
- Residencia
- Local de trabalho
- Escola dos filhos
- Residencia de familiares
- Outros locais relevantes

Cada zona tem:
- Raio de alerta configuravel (ex: 500m, 1km, 2km)
- Nivel de alerta: aviso / alerta / emergencia

---

## Niveis de alerta

| Distancia do agressor | Acao do app |
|----------------------|-------------|
| Dentro da zona de exclusao oficial | Alerta critico + acionar 190 automaticamente (opt-in) |
| Aproximando da zona (80% do raio) | Alerta de aviso + notificacao para Circulo |
| Na vizinhanca (raio expandido) | Notificacao informativa |

---

## Alerta recebido pela vitima

```
[REDE MULHER - ALERTA DE PROXIMIDADE]
A pessoa com medida restritiva esta a aproximadamente 400 metros.

Considere se deslocar para um local seguro.

[Ver mapa]   [Ligar 190]   [Avisar meu Circulo]
```

---

## Requisitos legais e de privacidade

Para implementar esta feature:

- **Autorizacao judicial** — o juiz responsavel pela medida protetiva autoriza o compartilhamento com a plataforma
- **Consentimento da vitima** — opt-in explicito, com explicacao clara do que sera monitorado
- **Dados do agressor nao expostos** — a vitima ve apenas distancia e direcao, nao nome/foto/localizacao exata do agressor
- **LGPD** — tratamento de dados sensiveis de acordo com Art. 11 da LGPD (protecao a vida)
- **Auditoria** — todos os acessos ao dado de monitoramento registrados e auditaveis

---

## Parceiros necessarios para implementacao

### Caminho 1 — Via CNJ
- Programa Justica 4.0 do CNJ tem editais para legaltech
- Integracao via SEEU (Sistema Eletronico de Execucao Unificado)
- Prazo estimado: 18-24 meses para aprovacao e homologacao

### Caminho 2 — Via operadoras de tornozeleira
- Empresas: Spacecom, Buddi, Synapse
- Acordo comercial direto, mais rapido
- Requer aval do Tribunal ou SEAP do estado

### Caminho 3 — Via Secretaria de Seguranca Publica
- Parceria estadual (comecar por PE ou SP que tem estrutura mais madura)
- Acesso ao sistema de monitoramento estadual

---

## Por que esta feature e Fase 5

Nao por complexidade tecnica — mas porque:
1. Requer aprovacao institucional e juridica que leva tempo
2. Depende de parceria com orgaos governamentais que tem processos longos
3. A plataforma precisa ter credibilidade e base de usuarios antes de ser levada a serio por orgaos publicos
4. O MVP e as Fases 2-4 constroem essa credibilidade

---

## Impacto potencial

Em 2023, o Brasil tinha mais de 26.000 pessoas monitoradas eletronicamente com medidas protetivas em favor de mulheres. Se 30% dessas mulheres usarem esta feature, sao mais de 7.800 vidas com protecao proativa em tempo real.
