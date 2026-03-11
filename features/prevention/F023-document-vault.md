# F023 — Cofre de Documentos

**Categoria:** Prevention
**Fase:** Fase 2
**Prioridade:** Alta — essencial para o Plano de Fuga, implementacao simples
**Funciona sem rede de usuarios:** Sim

---

## Objetivo

Armazenar copias digitais criptografadas de documentos essenciais — prontas para serem
acessadas ou compartilhadas no momento da fuga, quando documentos fisicos podem nao
estar acessiveis.

---

## O problema

Mulheres que saem de situacoes de violencia domestica frequentemente saem as pressas:
- Sem tempo de pegar documentos fisicos
- Agressor pode controlar o acesso a gavetas e armarios
- Documentos podem ter sido retidos pelo agressor intencionalmente
- Sem RG ou certidao de nascimento dos filhos, acesso a abrigos e servicos fica comprometido

Uma copia digital criptografada no celular — ou em backup externo acessivel — resolve
esse problema.

---

## Documentos suportados

### Pessoais
- RG / CNH / Passaporte
- CPF
- Carteira de Trabalho (CTPS)
- Titulo de Eleitor
- Cartao do SUS
- Comprovante de residencia

### Filhos
- Certidao de nascimento de cada filho
- Cartao de vacinacao
- Documentos escolares
- Termo de guarda (se existir)

### Financeiros
- Extrato bancario recente
- Comprovante de conta propria
- Cartao de beneficio (Bolsa Familia, BPC)
- Documento de imovel ou contrato de aluguel (comprova moradia)

### Juridicos
- Medida protetiva ativa
- BOs anteriores
- Sentencas judiciais relevantes
- Contato do advogado ou defensor publico

### Evidencias
- Fotos de lesoes (vinculadas ao Diario de Incidentes F014)
- Prints de mensagens ameacadoras
- Qualquer documento que comprove violencia patrimonial

---

## Como funciona

### Adicionar documento
1. Foto pela camera ou upload de arquivo existente
2. App categoriza automaticamente (OCR para detectar tipo de documento)
3. Criptografado imediatamente antes de qualquer armazenamento
4. Miniatura borrada na galeria do dispositivo — nao aparece no Google Fotos, iCloud

### Acessar documentos
- PIN secundario obrigatorio (separado do PIN do app)
- Biometria como alternativa
- Offline: documentos acessiveis sem internet

### No Modo Camuflado
- Cofre completamente oculto — nao existe na interface disfarçada
- Acessivel apenas via sequencia especifica no modo real do app

---

## Backup seguro

### Opcao 1 — E-mail de confianca (recomendado para fuga)
- Usuaria cadastra um e-mail de confianca (de amiga, mae, advogada)
- App envia backup criptografado para esse e-mail automaticamente
- Destinataria recebe arquivo .zip protegido por senha que so a usuaria sabe
- Util se o celular for confiscado ou destruido

### Opcao 2 — Backup na nuvem (E2E)
- Backup no Google Drive ou iCloud da propria usuaria
- Arquivo criptografado antes de sair do dispositivo
- Plataforma nao tem acesso ao conteudo

### Opcao 3 — Pendrive ou dispositivo secundario
- Exportacao local para dispositivo de confianca
- Instrucoes de como criar backup fisico discreto

---

## Compartilhamento em emergencia

Com um toque, a usuaria pode enviar pacote de documentos para:
- Contato do Circulo de Confianca
- Advogado ou Defensoria Publica
- DEAM (e-mail da delegacia)

O pacote e enviado como arquivo criptografado com senha que so ela escolhe.

---

## Validade legal das copias digitais

- Fotos de documentos tem validade legal crescente no Brasil (Lei 13.874/2019)
- Para uso em abrigos: maioria aceita foto do documento
- Para BO: delegacia pode aceitar foto — orientacoes por estado incluidas no app
- Para processo judicial: original ainda necessario para maioria dos atos formais

O app informa claramente o que cada copia pode e nao pode fazer.

---

## Seguranca contra acesso forcado

Se o agressor forcá a usuaria a abrir o app:
- **PIN de emergencia alternativo:** abre versao vazia do cofre (sem documentos)
- O cofre real so e acessivel com o PIN verdadeiro
- Funciona igual ao pin de distress: ele ve um cofre vazio, ela nao revela os documentos

---

## Privacidade

- Documentos nunca processados no servidor (criptografia acontece no dispositivo)
- OCR para categorizacao: processado localmente (modelo offline)
- Miniaturas borradas automaticamente para nao aparecer em previews de galeria
- Nenhum metadado de documento armazenado no servidor — apenas hash de verificacao de integridade
