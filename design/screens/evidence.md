# Tela de Evidências — Registro e Cofre

> Provas que nunca são perdidas. Mesmo se o celular for destruído.

---

## Contexto de uso

Esta seção serve mulheres que:
- Estão acumulando provas antes de denunciar
- Acabaram de sofrer uma agressão e precisam registrar
- Querem garantir que áudios e fotos não sejam deletados pelo agressor

O design deve ser **rápido para registrar** e **seguro para guardar**.

---

## Arquitetura da seção Evidências

Dentro de **🔒 Proteger → Evidências**:

```
Evidências
├── Gravação Rápida (mic + câmera)
├── Cofre de Arquivos
│   ├── Áudios
│   ├── Fotos e Vídeos
│   ├── Documentos
│   └── Diário de Incidentes
└── Exportar para uso jurídico
```

---

## Tela: Gravação Rápida

O acesso mais importante: registrar agora, rápido, sem precisar abrir o cofre.

```
┌─────────────────────────────────────────┐
│  ← Registrar Evidência                  │
├─────────────────────────────────────────┤
│                                         │
│  ┌──────────────────────────────────┐  │
│  │                                  │  │
│  │  🎙                              │  │
│  │                                  │  │  Área de gravação de áudio
│  │  Toque para iniciar gravação     │  │  Grande, ocupa 40% da tela
│  │                                  │  │
│  └──────────────────────────────────┘  │
│                                         │
│  ┌────────────┐   ┌───────────────┐   │
│  │  📷 Foto   │   │  🎥 Vídeo    │   │  Grid 2 colunas
│  └────────────┘   └───────────────┘   │
│                                         │
│  ┌──────────────────────────────────┐  │
│  │  📄 Importar arquivo             │  │
│  └──────────────────────────────────┘  │
│                                         │
│  ─────────────────────────────────────  │
│                                         │
│  ⚡ Gravação automática em curso       │  Se Gravação Contínua ativa
│     Último upload: 2 min atrás         │
│                                         │
└─────────────────────────────────────────┘
```

---

## Fluxo: Gravação de Áudio

```
[Toque no botão de microfone]
       ↓
[Biometria / PIN] (primeiro uso, depois a cada sessão)
       ↓
[Gravação inicia]

┌─────────────────────────────────────────┐
│  ← Gravando...                          │
├─────────────────────────────────────────┤
│                                         │
│         🔴  ●                           │
│                                         │
│         00:00:47                        │  Contador de tempo
│                                         │
│  ████████████░░░░░░░░░░░░░░░░░░░░░░░   │  Waveform em tempo real
│                                         │
│  📤 Upload automático em 13 seg...     │  Feedback de segurança
│                                         │
│  ┌────────────┐   ┌───────────────┐   │
│  │  ⏸ Pausar │   │  ■ Encerrar  │   │
│  └────────────┘   └───────────────┘   │
│                                         │
└─────────────────────────────────────────┘
```

### Segurança durante a gravação

- Upload parcial a cada 60 segundos para servidor criptografado
- Se o app for fechado/destruído: arquivo parcial já está salvo
- Waveform discreto — visual de "gravação" mas sem texto "GRAVANDO" em destaque

---

## Cofre de Documentos

```
┌─────────────────────────────────────────┐
│  ← Cofre                    [+ Adicionar]│
├─────────────────────────────────────────┤
│                                         │
│  🎙 Áudios (3)                         │
│  ┌──────────────────────────────────┐  │
│  │ 🎙 Audio_22h47_12mar.m4a        │  │
│  │    2min 34s · 12/03 22:47       │  │  ← Timestamp
│  │    ✓ Sincronizado               │  │  ← Status de upload
│  ├──────────────────────────────────┤  │
│  │ 🎙 Audio_15h30_08mar.m4a        │  │
│  │    45s · 08/03 15:30            │  │
│  │    ✓ Sincronizado               │  │
│  └──────────────────────────────────┘  │
│                                         │
│  📷 Fotos (7)                          │
│  ┌──────────────────────────────────┐  │
│  │  [thumb] [thumb] [thumb] [+4]   │  │  Grid de miniaturas
│  └──────────────────────────────────┘  │
│                                         │
│  📄 Documentos (2)                     │
│  ┌──────────────────────────────────┐  │
│  │ 📄 RG_scan.pdf                  │  │
│  │ 📄 Medida_Protetiva.pdf         │  │
│  └──────────────────────────────────┘  │
│                                         │
│  ─────────────────────────────────────  │
│                                         │
│  🔒 Criptografado com sua biometria    │  Footer de segurança
│     Ninguém mais tem acesso            │
└─────────────────────────────────────────┘
```

### Regras de visual do cofre

- **Sem thumbnails reais de fotos** na lista — só ícone genérico + nome do arquivo
  (para que uma olhada rápida no celular não revele imagens de lesões)
- Thumbnails só aparecem dentro do próprio cofre, com biometria já confirmada
- Nomes de arquivo gerados automaticamente (nunca "foto_hematoma.jpg")

---

## Exportação para uso jurídico

```
┌─────────────────────────────────────────┐
│  ← Exportar Evidências                  │
├─────────────────────────────────────────┤
│                                         │
│  Selecione o que exportar:              │
│                                         │
│  ☑ Áudios (3 arquivos)                 │
│  ☑ Fotos (7 arquivos)                  │
│  ☐ Documentos (2 arquivos)             │
│  ☑ Diário de incidentes                │
│                                         │
│  ─────────────────────────────────────  │
│                                         │
│  Destino:                               │
│  ● Salvar no dispositivo               │
│  ○ Enviar por e-mail                   │
│  ○ Compartilhar com advogado(a)        │
│                                         │
│  ─────────────────────────────────────  │
│                                         │
│  O pacote exportado inclui:            │
│  · Hash SHA-256 de cada arquivo        │
│  · Timestamp verificado (NTP)          │
│  · Relatório em PDF formato jurídico   │
│                                         │
│  ┌─────────────────────────────────┐   │
│  │  Exportar pacote de evidências  │   │
│  └─────────────────────────────────┘   │
│                                         │
└─────────────────────────────────────────┘
```

**Importante no design:** explicar claramente o que o hash SHA-256 significa, sem jargão:
> "Cada arquivo tem uma 'impressão digital' matemática que prova que não foi alterado."
