# F014 — Diario de Incidentes

**Categoria:** Prevention
**Fase:** Fase 4
**Funciona sem rede de usuarios:** Sim

---

## Objetivo

Permitir que mulheres em situacao de violencia continuada registrem incidentes ao longo do tempo, construindo um historico documentado com validade juridica para eventual processo legal.

---

## Por que isso importa

Em casos de violencia domestica, o processo legal depende frequentemente de:
- Demonstrar um padrao de comportamento (nao so um episodio isolado)
- Provar que a violencia foi continuada e sistematica
- Ter registros com data, local e descricao dos eventos

Mas muitas mulheres nao registram boletim de ocorrencia no momento (medo, dependencia financeira, filhos). O diario permite acumular evidencias enquanto ela ainda nao esta pronta para denunciar — para usar quando estiver.

---

## O que pode ser registrado

### Registro de incidente
- **Data e hora** (automatica + editavel)
- **Localizacao** (GPS automatico + descricao manual)
- **Tipo de violencia:**
  - Fisica
  - Psicologica / emocional
  - Sexual
  - Patrimonial / financeira
  - Moral
  - Virtual / digital
- **Descricao livre** do ocorrido
- **Evidencias anexadas:** foto, audio, video
- **Pessoas presentes** (nomes, opcional)
- **Estado fisico:** lesoes observadas (com foto opcional)

### Linha do tempo
- Visualizacao cronologica de todos os incidentes registrados
- Padroes identificaveis: frequencia, escalada, tipo
- Filtros por tipo de violencia, periodo

---

## Seguranca do diario

- Criptografia E2E: so a usuaria acessa (nem a plataforma)
- Protegido por PIN ou biometria separado do app principal
- No modo Camuflado: aparece como "Notas Pessoais" ou totalmente oculto
- Backup criptografado automatico (opt-in)

---

## Exportacao para uso legal

A usuaria pode gerar um relatorio exportavel em PDF ou formato juridico com:
- Linha do tempo de incidentes com timestamps verificados
- Hashes das evidencias (comprovam que nao foram alteradas)
- Relatorio de integridade dos arquivos
- Instrucoes de apresentacao em delegacia ou tribunal

### Formato aceito
- PDF assinado digitalmente pela plataforma
- Compativel com as exigencias do TJPE, TJSP e maioria dos tribunais estaduais
- Pode ser enviado diretamente para advogado ou DEAM pelo app

---

## Funcionalidades de apoio

### Lembretes de registro
- Opcional: lembrete diario discreto ("Voce quer registrar algo hoje?")
- Notificacao anonima, sem texto revelador
- Configuravel para horarios em que o parceiro nao esta por perto

### Sugestao de acoes
Apos registrar um incidente, o app pode sugerir:
- "Voce sabia que pode registrar um BO online? Saiba mais."
- "Esta e a 5ª ocorrencia de violencia fisica. Aqui estao seus direitos."
- Links para DEAM, CRAM, assistencia juridica gratuita
