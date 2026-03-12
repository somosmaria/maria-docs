# F019 — Consulta ao Cadastro de Agressores

**Categoria:** Institutional
**Fase:** Fase 5 (integração institucional — requer parceria CNJ e aprovação de framework legal)
**Funciona sem rede de usuarios:** Sim

---

## Objetivo

Permitir que mulheres consultem se uma pessoa tem registro no Cadastro Nacional de Pessoas
Envolvidas em Violencia Domestica (CNPVD) — de forma segura, privada e sem expor a
identidade de quem consulta.

---

## Base legal

### Lei 14.149/2021 — CNPVD
Cria o Cadastro Nacional de Pessoas Envolvidas em Violencia Domestica e Familiar contra
a Mulher. Mantido pelo CNJ. Dados incluem pessoas com:
- Condenacao transitada em julgado por violencia domestica (Lei Maria da Penha)
- Medida protetiva ativa registrada no sistema
- Reincidencia em crimes de violencia domestica

**A plataforma nao gera nem armazena esse dado** — apenas consulta a API publica do CNJ
e exibe o resultado. Responsabilidade legal pelo conteudo e do CNJ.

### Cadastros estaduais complementares
- **SP:** Cadastro de Agressores do TJSP (via portal de transparencia)
- **RJ:** Registro Estadual de Violencia Domestica (SESP-RJ)
- **MG:** Sistema de Acompanhamento de Medidas Protetivas (SEJUSP-MG)
- **PE:** Modulo do IITB (em implantacao)

---

## Como funciona para a usuaria

### Consulta por nome
```
[CONSULTAR CADASTRO DE AGRESSORES]

Nome completo: ___________________
Estado (opcional): _______________

[Consultar]

A busca e anonima — seu nome nao e registrado.
```

### Resultado positivo
```
[RESULTADO DA CONSULTA]

Encontrado no Cadastro Nacional (CNPVD / CNJ)

Esta pessoa possui registro de envolvimento em
violencia domestica no banco de dados oficial do
Conselho Nacional de Justica.

Numero de registros: 1
Ultimo registro: 2023

[O que isso significa]   [Meus direitos]   [Falar com a DEAM]

Fonte: CNJ — CNPVD (Lei 14.149/2021)
Data da consulta: hoje
```

### Resultado negativo
```
[RESULTADO DA CONSULTA]

Nenhum registro encontrado no Cadastro Nacional.

Ausencia de registro nao significa ausencia de
historico de violencia — muitos casos nao chegam
ao sistema judicial.

[Entenda os limites desta consulta]
```

---

## Privacidade de quem consulta

- A consulta nao requer login — pode ser feita anonimamente
- IP de consulta nao e armazenado nos servidores da plataforma
- A consulta ao CNJ e feita via proxy anonimizador — o CNJ nao sabe quem consultou
- Nenhum historico de consultas armazenado, nem localmente

**Por que isso e critico:** uma mulher consultando o nome do proprio companheiro nao pode
deixar rastro que ele possa encontrar.

---

## Limitacoes comunicadas ativamente

O app exibe estas limitacoes em toda tela de resultado:

1. **Subnotificacao:** a maioria dos casos de violencia domestica nunca chega ao Judiciario
2. **Atraso de dados:** o CNPVD depende de alimentacao pelos tribunais — pode ter lag de semanas
3. **Colisao de nomes:** nomes comuns podem gerar falsos positivos — o dado e indicativo, nao definitivo
4. **Escopo:** so cobre violencia domestica registrada — nao inclui outros crimes
5. **Sem foto ou CPF:** a busca por nome pode trazer homonimos

---

## Busca por CPF (versao avancada)

Tecnicamente mais precisa — elimina problema de homonimos.

**Desafio:** pedir CPF expoe a mulher (ela precisa saber o CPF do parceiro, o que pode gerar
suspeita) e aumenta o risco se ele encontrar o historico de busca no celular.

**Solucao:**
- Campo de CPF optional — so exibido se a usuaria escolher "Busca avancada"
- CPF nunca armazenado — descartado apos a consulta
- Resultado nao menciona o CPF — apenas confirma/nega registro

---

## Integracao tecnica

### API do CNJ
- CNPVD ainda nao tem API publica documentada (2024) — status: em desenvolvimento
- Caminho de acesso: Programa Justica 4.0 do CNJ (parceria necessaria)
- Alternativa temporaria: consulta ao portal de transparencia do CNJ via scraping autorizado

### Fallback sem API
Enquanto API nao esta disponivel:
- Link direto para o portal de consulta do CNPVD (externo)
- Instrucoes passo a passo para a usuaria fazer a consulta ela mesma
- Link para portais estaduais onde existem

---

## Expansao futura

### Integracao com Sinal Vermelho
O programa Sinal Vermelho (CNJ + MMFDH) ja tem mecanismo de identificacao de
situacao de violencia em farmacias e estabelecimentos. Integracao possivel para
cruzar dados e alertas.

### Alerta proativo
Se a usuaria adicionou um contato ao Circulo de Confianca e esse contato tem registro
no CNPVD — alerta discreto para ela (opt-in, configuravel).

---

## Parceria necessaria

- **CNJ** — acesso a API do CNPVD (ou autorizacao para scraping)
- **Tribunais Estaduais** — acesso a cadastros estaduais complementares
- **MMFDH** — articulacao politica para acesso prioritario
- **Juridico da plataforma** — validar modelo de responsabilidade pelo dado exibido

---

## O que esta feature nao e

- Nao e uma lista gerada por usuarios — dado 100% oficial e governamental
- Nao permite que usuarios adicionem, editem ou removam registros
- Nao expoe dados pessoais alem do que o CNJ ja torna publico
- Nao substitui boletim de ocorrencia ou medida protetiva
- Nao garante que ausencia de registro significa pessoa segura
