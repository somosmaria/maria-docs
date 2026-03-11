# F008 — Check-in por Inatividade

**Categoria:** Movement
**Fase:** Fase 2
**Funciona sem rede de usuarios:** Sim

---

## Objetivo

Detectar automaticamente quando a usuaria para de se mover ou nao responde a um prompt — e acionar o Circulo de Confianca sem que ela precise fazer nada.

---

## O problema

Em muitas situacoes de risco, a mulher nao consegue acionar o botao de emergencia:
- Bateu na cabeca e perdeu a consciencia
- Esta presa em algum lugar
- O agressor tomou o celular
- Foi submetida a alguma substancia

O check-in por inatividade e o "dead man's switch" do app — funciona quando a usuaria nao consegue agir.

---

## Como funciona

### Modo automatico (durante Me Acompanhe)
1. Enquanto o Modo Me Acompanhe esta ativo, o app monitora movimento e resposta
2. Se a usuaria para de se mover por um periodo configuravel (ex: 15 minutos), o app envia prompt discreto
3. Se nao responder em 2 minutos: aciona Circulo de Confianca com ultima localizacao conhecida
4. Se responder: check-in registrado, monitoramento continua

### Modo manual (check-in agendado)
1. Usuaria programa check-in: "Lembra de mim em 1 hora"
2. No horario definido: notificacao silenciosa com um toque para confirmar
3. Sem resposta em 5 minutos: alerta para o Circulo

### Personalizacao do prompt
- Som: silencioso / vibrar / toque discreto
- Texto do prompt: customizavel (default: "Tudo bem?")
- Janela de resposta: 1 a 10 minutos
- Acao apos timeout: avisar Circulo / avisar Circulo + ligar 190 (opt-in)

---

## Algoritmo de deteccao de inatividade

```
1. GPS amostragem a cada 30 segundos (baixo consumo)
2. Se deslocamento < 20 metros em X minutos → inatividade detectada
3. Excepcao: se acelerometro indica que o usuario esta dormindo (movimento
   de respiracao normal) → suspende check-in
4. Se bateria < 5%: envia ultima localizacao para o Circulo automaticamente
```

---

## Notificacao para o Circulo

```
[REDE MULHER - CHECK-IN NAO RESPONDIDO]
Ana nao respondeu ao check-in ha 7 minutos.
Ultima localizacao: Rua Conselheiro Rosa e Silva, 200, Recife
Ha 7 minutos.

[Ver no mapa]   [Tentar ligar]   [Acionar 190]
```

---

## Configuracoes de privacidade

- Circulo so recebe localizacao quando o check-in nao for respondido
- Localizacao deletada do servidor apos confirmacao de seguranca pela usuaria
- Historico de check-ins armazenado localmente (nao no servidor)

---

## Otimizacao de bateria

- GPS em modo de baixa potencia quando sem movimento detectado
- Amostragem aumenta apenas quando inatividade e suspeita
- Meta: < 3% de consumo de bateria por hora de monitoramento
- Em bateria critica (< 10%): modo de emergencia com GPS burst (amostra, desliga, repete)
