# F031 — Modo Balada

**Categoria:** Movement
**Fase:** Fase 2
**Prioridade:** 🔴 Alta — risco específico e alto, público jovem, alta frequência de uso
**Funciona sem rede de usuarios:** Parcialmente (features individuais funcionam; rede de guardias amplia proteção)

---

## Objetivo

Proteção específica para saídas noturnas — bares, festas, shows, baladas — onde os
riscos são diferentes do deslocamento comum: bebida, transporte de volta, ambientes
barulhentos que dificultam pedir socorro.

---

## Por que merece um modo próprio

Saída noturna tem um perfil de risco distinto:

| Risco | Presente na balada? | Coberto por outros modos? |
|-------|-------------------|--------------------------|
| Desconhecidos próximos em ambiente fechado | Sim | Não |
| Bebida alcoólica reduzindo percepção de risco | Sim | Não |
| Adulteração de bebida (boa noite cinderela) | Sim | Não |
| Transporte de volta com estranhos | Sim | Parcialmente (F007) |
| Ambiente barulhento que impede ligar | Sim | Parcialmente (F002) |
| Separação do grupo de amigas | Sim | Não |
| Retorno tarde da noite sozinha | Sim | F006, F029 |

---

## Ativação

```
[MODO BALADA]

Onde você vai: [Nome do local ou endereço]
Com quem:      [Selecionar contatos do Círculo]
Volta prevista: [02:00 ▼]

[Ativar Modo Balada]
```

---

## Funcionalidades do modo

### 1. Grupo de saída compartilhado

Quando ativado com amigas que também têm o app:
```
Seu grupo esta noite:
● Carol — no local ✓
● Bruna — a caminho
● Lara — no local ✓

[Onde está o grupo]
```

- Cada uma vê as outras no mapa (consentimento bilateral — todas devem aceitar)
- Se uma sair do local sem avisar: notificação discreta para o grupo
- "Saindo com alguém" — botão para informar que está indo embora com uma pessoa (nome/desc opcional)

### 2. Check-in de bebida

Registro voluntário e discreto:
```
[+1 drink]
```
- Contador pessoal e privado — só ela vê
- Após X drinks: lembrete discreto "Você quer que eu fique de olho em você?"
- Não é julgamento — é ferramenta que ela controla

### 3. Alerta de adulteração de bebida

Orientação preventiva integrada ao modo:
- Sintomas para ficar atenta (tontura súbita, visão turva, desorientação fora do esperado)
- Botão rápido "Não estou me sentindo bem" — aciona Círculo com localização imediata
- Sem precisar digitar nada — um toque

### 4. Verificação de transporte de volta

Antes de entrar em qualquer carro:
```
[INDO EMBORA]

Como você está voltando?

[Uber/99 — compartilhar dados]
[Carro de amigo — registrar placa]
[A pé — ativar Me Acompanhe]
[Motorista particular — registrar dados]
```

Integrado com F007 (Verificação de Motorista) e F006 (Me Acompanhe).

### 5. Botão de socorro silencioso para ambiente barulhento

Em balada, não dá para ligar. Gritar não adianta. O app oferece:
- Shake do celular 3x = aciona Círculo com localização
- Segurar botão de volume por 3s = aciona emergência silenciosa
- Flash da câmera pisca (sinal visual para quem estiver perto)

### 6. Monitoramento de chegada automático

Ao ativar o Modo Balada com hora de volta:
- F029 (ETA) ativado automaticamente para o horário definido
- Se não chegou em casa no prazo: Círculo recebe alerta com última localização conhecida
- Sem precisar configurar separadamente

---

## Tela simplificada para quando estiver bebendo

Interface adaptativa: quando o check-in de bebida registra X drinks, a interface muda:
- Botões maiores
- Menos opções
- Foco nas ações críticas: "Estou bem", "Preciso de ajuda", "Quero ir embora"

---

## Encerramento do modo

```
Você chegou bem em casa?

[Cheguei ✓]

Boa noite. Você e suas amigas ficaram
seguras essa noite.
```

Ao confirmar:
- Localização deletada do servidor
- Grupo de saída encerrado
- Dados de check-in de bebida apagados (permanecem apenas localmente se ela quiser)

---

## Modo para quem sai sozinha

Nem sempre há grupo. Para saída solo:
- Contato de confiança recebe "Ana está saindo para [local] e deve voltar até [hora]"
- Check-in automático na hora de volta (F029)
- Rede de Guardias ativada na área do local

---

## Alerta sobre boa noite cinderela (GHB/Rohypnol)

### O que o app ensina (conteúdo preventivo)
- Nunca deixar bebida sem supervisão
- Sintomas de adulteração: gosto amargo repentino, tontura rápida, confusão
- O que fazer se suspeitar: não beber mais, avisar alguém de confiança, sair do local
- GHB é eliminado do organismo em 4-8h — exame deve ser feito o mais rápido possível

### Botão de emergência específico
```
[Suspeito que adulteraram minha bebida]
```
- Aciona Círculo imediatamente com localização
- Exibe instrução: "Peça para alguém de confiança te acompanhar até o hospital agora"
- Registra timestamp para o exame toxicológico
- Conecta com F030 (Protocolo Pós-Agressão) se necessário

---

## Integração com Pontos Seguros (F012)

Mapa do Modo Balada exibe:
- Pontos Seguros abertos naquele horário próximos ao local
- Farmácias 24h
- Hospitais e UPAs

Se ela precisar sair do local rapidamente, sabe para onde ir.

---

## Privacidade

- Dados de localização durante a saída: compartilhados apenas com o grupo definido por ela
- Check-in de bebida: armazenado apenas localmente, nunca no servidor
- Histórico de locais visitados: nunca armazenado no servidor
- Ao encerrar o modo: todos os dados do servidor são deletados

---

## Por que Fase 2 e não Fase 1

- O módulo de grupo requer que outras usuárias também tenham o app (massa mínima)
- Features individuais do modo (ETA, socorro silencioso, verificação de carro) podem ir no MVP
- Fase 1 entrega o modo em versão solo; Fase 2 adiciona o componente de grupo
