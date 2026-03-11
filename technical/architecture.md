# Arquitetura Tecnica

---

## Stack recomendada

### App Mobile
- **Flutter** — unico codebase para Android e iOS
- **Riverpod** — gerenciamento de estado
- **Dio** — HTTP client
- **flutter_secure_storage** — armazenamento de tokens e dados sensiveis
- **geolocator** — GPS em background
- **background_fetch** — tarefas em background (check-in, monitoramento)
- **flutter_local_notifications** — notificacoes locais silenciosas

### Backend
- **Python / FastAPI** — API REST
- **PostgreSQL** — banco principal
- **Redis** — cache e filas de alertas em tempo real
- **WebSockets** — rastreamento em tempo real (Me Acompanhe, rede local)
- **Celery + Redis** — tarefas assincronas (envio de SMS, processamento de alertas)

### Infraestrutura
- **AWS ou GCP** — cloud principal
- **Twilio** — envio de SMS (fallback critico)
- **Firebase Cloud Messaging** — push notifications
- **Cloudflare** — CDN, DDoS protection, WAF

---

## Principios de arquitetura

### Offline-first para features criticas
- Botao de emergencia funciona sem internet (SMS via radio GSM)
- Modo Silencioso funciona sem internet
- Evidencias gravadas localmente antes de sincronizar

### Privacidade por design
- Localizacao da usuaria nunca armazenada no servidor alem do necessario
- Dados de rastreamento deletados automaticamente apos fim do evento
- Backup de evidencias criptografado E2E — plataforma nao tem acesso

### Alta disponibilidade para alertas
- SLA de 99.9% para endpoints de emergencia
- Redundancia de envio: push + SMS simultaneamente
- Circuit breaker para fallback automatico

---

## Modelo de dados (resumo)

```
User
  - id
  - phone_hash (nunca phone em claro)
  - created_at

TrustCircleContact
  - user_id
  - contact_phone_hash
  - contact_type (primary/emergency/tracking)
  - has_app (bool)

EmergencyEvent
  - id
  - user_id (referencia, nao dados pessoais)
  - type (panic/silent/inactivity)
  - activated_at
  - resolved_at
  - locations (array de pontos GPS)

EvidenceFile
  - id
  - user_id
  - type (audio/photo/video/log)
  - sha256_hash
  - ntp_timestamp
  - encrypted_at_rest (bool)
  - storage_key (path criptografado)
```

---

## Seguranca de dados

### Dados em transito
- HTTPS obrigatorio em todas as comunicacoes
- Certificate pinning no app para prevenir MITM

### Dados em repouso
- Evidencias: AES-256, chave derivada de biometria/PIN da usuaria
- Banco de dados: criptografia em nivel de coluna para dados sensiveis
- Nenhum dado de identificacao pessoal em logs de servidor

### Autenticacao
- Login por telefone + OTP (sem email/senha como primario)
- JWT com rotacao de refresh token
- Biometria como segundo fator para acoes criticas

### Anonimizacao
- Telefones armazenados apenas como hash SHA-256
- Localizacoes na rede local usam coordenadas aproximadas (+-100m) para nao revelar posicao exata
- Relatos no mapa agregados antes de publicacao

---

## Monitoramento e observabilidade

- Alertas de downtime em endpoints criticos (< 1 minuto para detectar)
- Metricas de entrega de SMS e push por regiao
- Alertas de anomalia: pico de acionamentos (pode indicar evento de massa)
- Nenhum dado de usuario em logs de producao — apenas IDs anonimos
