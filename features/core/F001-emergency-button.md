# F001 — Botao de Emergencia

**Categoria:** Core
**Fase:** MVP (Fase 1)
**Funciona sem rede de usuarios:** Sim

---

## Objetivo

Permitir que uma mulher acione ajuda imediata de forma rapida e simples, em qualquer situacao de risco.

---

## Comportamento

### Ativacao
- Botao central e visivel na tela principal
- Ativacao por toque longo (2 segundos) para evitar acionamento acidental
- Contador regressivo de 3 segundos com opcao de cancelar antes de disparar

### O que acontece ao acionar

1. **Alerta para o Circulo de Confianca** — SMS + notificacao push com localizacao atual
2. **Localizacao em tempo real** — contatos recebem atualizacoes de GPS a cada 30 segundos
3. **Gravacao automatica de audio** — inicia em background, armazenada localmente com criptografia
4. **Notificacao para rede local** — se existir densidade suficiente de usuarios na regiao (Fase 3)
5. **Acionamento de autoridades** — opcao para ligar 190 ou 180 com um toque adicional

### Fallback sem internet
- Envio de SMS para contatos do Circulo de Confianca com coordenadas GPS
- SMS nao depende de dados moveis

---

## Mensagem enviada para contatos

```
[REDE MULHER - ALERTA]
[Nome da usuaria] ativou o botao de emergencia.
Localizacao: https://maps.google.com/?q=-8.063,-34.871
Horario: 22:47 - 11/03/2026

Acoes rapidas:
- Ligar para ela
- Ver localizacao em tempo real: [link]
- Ligar 190
```

---

## Desativacao
- Botao de "Estou bem" na tela principal
- Confirmacao com PIN ou biometria para evitar desativacao forcada pelo agressor
- Desativacao nao apaga as evidencias ja registradas

---

## Seguranca e privacidade
- Localizacao compartilhada apenas com o Circulo de Confianca, nao com desconhecidos
- Audio gravado localmente; nao enviado automaticamente (apenas sob controle da usuaria)
- Log do acionamento registrado com timestamp e hash para validade juridica

---

## Metricas de sucesso
- Tempo medio de acionamento < 3 segundos
- Taxa de entrega de SMS em modo fallback > 95%
- Zero acionamentos acidentais reportados apos 30 dias de uso
