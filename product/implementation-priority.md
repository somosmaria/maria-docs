# Ordem de Implementação — Guardiãs

Lista completa de features na ordem exata de implementação, da mais urgente para a menos urgente.

**Princípios de ordenação:**
1. Features que protegem as outras features vêm primeiro
2. Zero dependência de rede antes de ter rede
3. Máximo impacto com mínima complexidade técnica primeiro
4. Features que habilitam outras features antes das que dependem delas
5. Parcerias institucionais (lentas) ficam para o fim

---

## FASE 1 — Base Individual

### #1 — F003 Modo Camuflado
**Por que primeiro:** se o agressor identifica e deleta o app, nada mais funciona. É a meta-feature que protege todas as outras. Sem isso, construir qualquer coisa é inútil para mulheres em situação de violência doméstica.

### #2 — F004 Círculo de Confiança
**Por que segundo:** é a espinha dorsal do produto. F001, F002, F006, F008, F029 todos dependem de contatos configurados. Sem círculo, emergências não têm para onde ir.

### #3 — F001 Botão de Emergência
**Por que terceiro:** razão central de existência do app. Depende do F004 estar configurado. SMS fallback sem internet é requisito não-negociável desta feature.

### #4 — F002 Modo Proteção Silenciosa
**Por que quarto:** estende o F001 para o cenário mais comum de violência doméstica — quando a mulher não pode usar o celular visivelmente. Gesto com botão de volume, sequência discreta.

### #5 — F030 Protocolo Pós-Agressão
**Por que quinto:** zero complexidade técnica — é conteúdo estruturado offline. Mas o impacto é imediato e direto: as primeiras 6 horas após uma agressão determinam se haverá prova para um processo. Pode ser construído em dias. Não tem sentido adiar.

### #6 — F021 Chamada Falsa
**Por que sexto:** feature mais simples do produto tecnicamente. Zero dependência de rede, zero configuração. Entrega valor imediato no cotidiano — não só em emergência. É o que faz a mulher abrir o app toda semana e manter o hábito.

### #7 — F029 Monitoramento de Chegada (ETA)
**Por que sétimo:** alto impacto, uso diário, zero dependência de rede. "Vou chegar em 20 minutos — se não chegar, avisa minha mãe." Simples, claro, salva vidas. Depende do F004.

### #8 — F020 Detector de Stalkerware
**Por que oitavo:** se o celular está comprometido com app de espionagem, nenhuma outra feature é segura — o agressor vê tudo. Precisa ser resolvido antes de construir confiança nas demais features.

### #9 — F005 Registro de Evidências
**Por que nono:** criptografia E2E, hash SHA-256, timestamp verificado — mais complexo que os anteriores. Mas crítico para o processo judicial. Depende de F004 para compartilhamento.

### #10 — F026 Gravação Contínua
**Por que décimo:** extensão direta do F005. Reutiliza a infraestrutura de criptografia e upload. Vem logo depois porque o caso de uso (upload a cada 60s antes do dispositivo ser destruído) complementa o registro de evidências.

---

## FASE 2 — Deslocamento

### #11 — F006 Modo Me Acompanhe
**Por que décimo-primeiro:** feature de movimento mais usada. Localização em tempo real para contato de confiança durante trajeto. Depende de F004.

### #12 — F008 Check-in por Inatividade
**Por que décimo-segundo:** complementa o F006. Detecta quando ela para de se mover e não responde — o "dead man's switch" do app. Pode funcionar independente do F006 também.

### #13 — F031 Modo Balada
**Por que décimo-terceiro:** integra F006, F007 e F029 em um modo específico para saída noturna. Alta frequência de uso para o público jovem. O componente individual (ETA + socorro silencioso) vai no MVP da Fase 1; o componente de grupo vem aqui.

### #14 — F023 Cofre de Documentos
**Por que décimo-quarto:** essencial para o Plano de Fuga (F015). Mas o Plano de Fuga é Fase 4 — o cofre precisa existir antes para que os documentos já estejam prontos quando ela precisar sair.

### #15 — F007 Verificação de Motorista
**Por que décimo-quinto:** caso de uso específico (entrar em carro) mas frequente. Compartilha placa e dados com o Círculo antes de entrar. Integrado ao F031.

### #16 — F009 Modo Viagem
**Por que décimo-sexto:** menos frequente que o deslocamento urbano diário. Reutiliza infraestrutura do F006 e F029. Vem por último na Fase 2 por menor frequência de uso.

---

## FASE 3 — Rede Comunitária

> Todas as features abaixo requerem densidade mínima de usuárias.
> Pré-requisito: 500 usuárias ativas na cidade piloto.

### #17 — F012 Pontos Seguros
**Por que décimo-sétimo:** primeiro da Fase 3 porque depende de parcerias físicas (farmácias, postos) — não de densidade de usuárias. Pode ser construído em paralelo com a Fase 2. Quando a rede de usuárias chegar, os pontos já estão mapeados.

### #18 — F028 Rede de Guardias
**Por que décimo-oitavo:** é a feature central do produto — mas só funciona com densidade. Vem aqui, não no início, exatamente porque precisa de base de usuárias para entregar valor. Lançar antes seria frustrar expectativa e trair a proposta.

### #19 — F011 Mapa de Segurança
**Por que décimo-nono:** camada 1 (dados públicos — DEAMs, hospitais) pode ir antes. Camadas 2-4 (dados da comunidade) dependem de usuárias ativas. Implementar por camadas.

### #20 — F027 Alerta para Vizinhos
**Por que vigésimo:** extensão da Rede de Guardias. Requer densidade ainda maior que o F028 para ser confiável. Lançar junto ou logo depois.

### #21 — F010 Rede de Apoio Local
**Por que vigésimo-primeiro:** alertas anônimos entre mulheres próximas. Parecido com F027 mas mais genérico. Vem depois porque F028 já cobre o caso crítico (emergência) de forma mais estruturada.

### #22 — F013 Relatos da Comunidade
**Por que vigésimo-segundo:** heatmap de assédio. Requer volume de relatos para ser útil — densidade maior que os anteriores. Também requer moderação ativa antes de lançar.

### #23 — F025 Testemunha Voluntária
**Por que vigésimo-terceiro:** denúncia de terceiro. Depende de comunidade ativa e moderação robusta para evitar abuso.

### #24 — F022 Chat de Apoio com Voluntárias
**Por que vigésimo-quarto:** requer recrutamento e treinamento de voluntárias antes de lançar. Sem mínimo de 20 voluntárias cobrindo horário de pico, o chat offline frustra no momento mais crítico. Infraestrutura humana vem antes da infraestrutura técnica aqui.

---

## FASE 4 — Prevenção e Saída

### #25 — F016 Linha Direta com DEAMs
**Por que vigésimo-quinto:** conteúdo + parcerias. Banco de dados de DEAMs com informações atualizadas. Mais simples que os próximos — começa com dados públicos disponíveis.

### #26 — F014 Diário de Incidentes
**Por que vigésimo-sexto:** criptografia E2E, exportação em formato jurídico, integração com F005. Complexidade técnica maior — e requer parceria com juristas para validar o formato de exportação.

### #27 — F015 Plano de Fuga
**Por que vigésimo-sétimo:** requer banco de dados de abrigos, CRAMs e assistência jurídica por estado — curadoria manual, atualização contínua. Depende do F023 (cofre de documentos) já estar pronto.

### #28 — F024 Independência Financeira
**Por que vigésimo-oitavo:** conteúdo informativo, sem complexidade técnica. Mas depende de curadoria e parcerias (SEBRAE, Caixa) para ser completo e confiável. Menor urgência que os anteriores.

---

## FASE 5 — Integração Institucional

> Todas requerem parcerias governamentais com processos longos.
> Implementação técnica é secundária — o bloqueio é burocrático.

### #29 — F019 Consulta ao Cadastro de Agressores (CNPVD)
**Por que vigésimo-nono:** dos três institucionais, é o que tem caminho mais rápido — o CNPVD já existe (Lei 14.149/2021) e o CNJ tem histórico de parcerias com legaltech via Justiça 4.0. Tecnicamente mais simples: é uma consulta a banco de dados público.

### #30 — F018 Alertas Judiciais
**Por que trigésimo:** requer acesso a portais de tribunais estaduais — múltiplos sistemas, múltiplas integrações. Começa com os estados com portais mais maduros (SP, MG, PE).

### #31 — F017 Monitoramento de Medida Protetiva (tornozeleira)
**Por que trigésimo-primeiro:** tecnicamente mais complexo, burocráticamente mais difícil. Requer autorização judicial processo-a-processo ou framework legal específico + parceria com operadoras de tornozeleira + aval de tribunais. É o mais impactante — por isso fica por último: o produto precisa ter credibilidade máxima antes de chegar aqui.

---

## Resumo por tempo estimado

| Prioridade | Feature | Fase | Tempo estimado para iniciar |
|-----------|---------|------|----------------------------|
| #1 | F003 Modo Camuflado | 1 | Semana 1 |
| #2 | F004 Círculo de Confiança | 1 | Semana 1 |
| #3 | F001 Botão de Emergência | 1 | Semana 2 |
| #4 | F002 Modo Silencioso | 1 | Semana 3 |
| #5 | F030 Protocolo Pós-Agressão | 1 | Semana 3 |
| #6 | F021 Chamada Falsa | 1 | Semana 4 |
| #7 | F029 ETA Monitoramento | 1 | Semana 5 |
| #8 | F020 Detector Stalkerware | 1 | Semana 6 |
| #9 | F005 Registro de Evidências | 1 | Semana 7 |
| #10 | F026 Gravação Contínua | 1 | Semana 9 |
| #11 | F006 Me Acompanhe | 2 | Mês 5 |
| #12 | F008 Check-in Inatividade | 2 | Mês 5 |
| #13 | F031 Modo Balada | 2 | Mês 6 |
| #14 | F023 Cofre de Documentos | 2 | Mês 6 |
| #15 | F007 Verificação Motorista | 2 | Mês 7 |
| #16 | F009 Modo Viagem | 2 | Mês 8 |
| #17 | F012 Pontos Seguros | 3 | Mês 9 |
| #18 | F028 Rede de Guardias | 3 | Mês 10 |
| #19 | F011 Mapa de Segurança | 3 | Mês 11 |
| #20 | F027 Alerta Vizinhos | 3 | Mês 12 |
| #21 | F010 Rede de Apoio Local | 3 | Mês 12 |
| #22 | F013 Relatos da Comunidade | 3 | Mês 13 |
| #23 | F025 Testemunha Voluntária | 3 | Mês 13 |
| #24 | F022 Chat de Apoio | 3 | Mês 14 |
| #25 | F016 Linha Direta DEAMs | 4 | Mês 15 |
| #26 | F014 Diário de Incidentes | 4 | Mês 16 |
| #27 | F015 Plano de Fuga | 4 | Mês 17 |
| #28 | F024 Independência Financeira | 4 | Mês 19 |
| #29 | F019 Consulta CNPVD | 5 | Mês 21 |
| #30 | F018 Alertas Judiciais | 5 | Mês 22 |
| #31 | F017 Monitoramento Tornozeleira | 5 | Mês 24+ |
