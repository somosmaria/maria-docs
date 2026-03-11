# F005 — Registro de Evidencias

**Categoria:** Core
**Fase:** MVP (Fase 1)
**Funciona sem rede de usuarios:** Sim

---

## Objetivo

Registrar automaticamente evidencias de situacoes de risco — com validade juridica — que possam ser usadas em denuncias, boletins de ocorrencia ou processos legais.

---

## Tipos de evidencia registrados

### Audio
- Gravacao automatica ao acionar emergencia ou modo silencioso
- Armazenado localmente com criptografia AES-256
- Metadata: timestamp, duracao, localizacao GPS no inicio da gravacao
- Qualidade: 16kHz mono (suficiente para voz, baixo consumo de armazenamento)

### Localizacao
- Coordenadas GPS com precisao + endereco reverso
- Registrado: no acionamento, a cada 30 segundos durante alerta, no encerramento
- Exportavel como historico de trajeto com timestamps

### Foto/Video (manual)
- Usuaria pode capturar foto ou video diretamente pelo app
- Arquivos recebem hash SHA-256 no momento da captura
- Metadata inclui: hora, coordenadas, versao do app

### Log de eventos
- Registro cronologico de todos os acionamentos
- Inclui: tipo de evento, horario, localizacao, modo de ativacao
- Nao editavel pela usuaria (integridade garantida)

---

## Armazenamento e seguranca

### Local
- Todos os arquivos ficam no dispositivo, criptografados
- Acesso apenas com autenticacao (PIN ou biometria)
- Nao aparece na galeria de fotos do dispositivo

### Backup (opt-in)
- Usuaria pode ativar backup criptografado em nuvem
- Provedores suportados: Google Drive, iCloud (E2E criptografado antes do upload)
- Chave de criptografia fica apenas com a usuaria — nem a plataforma pode acessar

### Protecao contra delecao forcada
- Evidencias nao podem ser deletadas pelo app em modo normal
- Delecao requer: PIN + confirmacao + periodo de graca de 24h
- Durante periodo de graca, evidencias ainda existem em backup

---

## Validade juridica

Para que evidencias digitais tenham peso em processo:

- **Timestamp com NTP verificado** — horario sincronizado com servidor de tempo oficial
- **Hash SHA-256** de cada arquivo gerado no momento da captura
- **Log imutavel** de todos os eventos
- **Exportacao em formato padrao** com relatorio de integridade

### Exportacao para uso legal
A usuaria pode gerar um relatorio PDF contendo:
- Lista de evidencias com hashes e timestamps
- Mapa de localizacoes registradas
- Historico de eventos
- Instrucoes sobre como apresentar a delegacia

---

## Diario de Incidentes (preview da F014)

O Registro de Evidencias e a fundacao para o Diario de Incidentes (Fase 4), que adiciona:
- Campo de texto para descricao do ocorrido
- Classificacao do tipo de violencia
- Vinculacao com registros anteriores do mesmo agressor
- Linha do tempo de um relacionamento abusivo
