# F007 — Verificacao de Motorista

**Categoria:** Movement
**Fase:** Fase 2
**Funciona sem rede de usuarios:** Sim

---

## Objetivo

Permitir que uma mulher compartilhe rapidamente os dados do carro e do motorista com seus contatos de confianca antes de entrar em um veiculo por aplicativo ou carona.

---

## O problema

Crimes envolvendo motoristas de aplicativo sao frequentes. A maior vulnerabilidade e o momento entre entrar no carro e o contato perder o rastro.

O compartilhamento manual de dados (foto do carro, placa, nome do motorista) e lento, incomodo e muitas vezes esquecido.

---

## Fluxo de uso

### Entrada rapida de dados

1. Usuaria abre "Verificar Motorista" no app
2. Digita placa do veiculo ou escaneia com a camera
3. App preenche automaticamente (se integracao com base de veiculos existir) ou usuaria preenche:
   - Placa
   - Modelo e cor do carro
   - Nome do motorista (campo opcional)
4. Toca em "Compartilhar com meu Circulo"

### O que e enviado para os contatos

```
[REDE MULHER]
[Nome] entrou em um veiculo.

Veiculo: Honda Civic Preto - ABC-1234
Motorista: Carlos Silva
Horario: 23:14
Localizacao de embarque: R. da Aurora, 142 - Recife

Rastrear trajeto: [link]
Se ela nao confirmar chegada ate 23:45, entre em contato.
```

### Acompanhamento

- Modo Me Acompanhe e ativado automaticamente
- Contatos acompanham o trajeto em tempo real
- Confirmacao de chegada ao destino

---

## Integracao com apps de transporte

**MVP (sem integracao):** entrada manual de dados

**Fase futura (com parceria):**
- Integracao via API com Uber e 99 para importar dados automaticamente
- Ou: leitura de screenshot/notificacao do app de transporte via acessibilidade

---

## Verificacao cruzada (feature futura)

- Base de dados de motoristas com historico de incidentes reportados pela comunidade
- Integrada com relatorios do Procon e delegacias (requer parceria)
- Alerta se placa ou motorista tiver historico de ocorrencias

---

## Privacidade

- Dados do motorista nao sao armazenados no servidor — apenas compartilhados momentaneamente com o Circulo
- Nenhum dado de terceiros (motorista) fica na base da plataforma sem consentimento
