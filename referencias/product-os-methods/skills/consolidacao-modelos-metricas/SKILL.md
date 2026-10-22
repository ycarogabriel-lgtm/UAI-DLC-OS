---
name: consolidacao-modelos-metricas
description: "Definir ou consolidar métricas de produto: separa KPI de OKR e amarra cada métrica a um objetivo de produto."
---

# Consolidação de Modelos de Métricas

> As menções a "(regra transversal)" abaixo remetem às regras transversais deste plugin, em `${CLAUDE_SKILL_DIR}/../../docs/REGRAS_TRANSVERSAIS.md` (o arquivo `docs/REGRAS_TRANSVERSAIS.md` na raiz do plugin, não no repositório em que você está trabalhando). Leia esse arquivo antes de aplicar a skill. Fora do Claude Code, as regras precisam ser fornecidas junto com esta skill.

## O princípio inegociável

KPI e OKR não são a mesma coisa e não podem ser tratados como intercambiáveis. Toda métrica proposta precisa estar amarrada a um objetivo de produto — uma métrica solta, sem ligação clara com nenhum objetivo, não entra na consolidação.

## Como conduzir

**0. Verifique o repositório e o framework em uso antes de propor.**
- **Framework em uso (verifique primeiro).** Identifique como o repositório de destino organiza produto e trabalhe no padrão dele (regra transversal — ver `${CLAUDE_SKILL_DIR}/../../docs/REGRAS_TRANSVERSAIS.md`, "Adaptação ao framework em uso"):
  - *O repositório já adota um framework ou estrutura própria* (Scrum/SAFe/Shape Up, ou um modelo próprio de OKR/KPI, North Star, HEART, AARRR, um board de métricas): a distinção KPI × OKR e a amarração a objetivo continuam obrigatórias, mas registre no modelo e nos campos que o framework já usa (ex.: o modelo de OKR/KPI ou o board de métricas que o framework já adota).
  - *Nenhum*: use os formatos desta skill como estão.
  A lógica desta skill — KPI ≠ OKR, toda métrica amarrada a um objetivo, governança V.E.R.A. quando for ROI — continua valendo; o que se adapta é onde e como registrar. Se a convenção do framework conflitar com o formato-padrão daqui, o framework em uso prevalece — sinalize a diferença, não decida sozinha.
- Se o repositório já tiver métricas/OKRs definidos para o produto, reaproveite como contexto em vez de propor do zero — só reabra se o usuário pedir para reconsiderar (regra transversal).
- Se houver conflito entre o que esta skill orienta e o que já está documentado no repositório, sinalize e pergunte — nunca decida sozinha (regra transversal).

**1. Pergunte sempre: KPI ou OKR?**
Antes de registrar qualquer métrica proposta, pergunte se ela é um KPI (acompanhamento contínuo, estável) ou parte de um OKR (meta temporária, com prazo). Não misture os dois tipos na mesma lista sem essa distinção clara.

**2. Aplique as regras de cada tipo.**

*KPI*
- Métrica operacional estável, usada para acompanhamento contínuo.
- Todo KPI acompanhado precisa ter uma ação associada prevista para quando o número fugir do esperado — KPI sem ação associada é sinal de alerta, aponte isso ao usuário em vez de deixar passar.

*OKR*
- Objetivo estratégico com resultados-chave mensuráveis, muda com mais frequência que KPI (normalmente por ciclo/trimestre).
- Todo OKR precisa ter prazo definido — OKR sem prazo é erro comum, não aceite sem esse dado.
- Um KPI pode virar componente de um resultado-chave de um OKR — mas isso deve ficar explícito na consolidação, não implícito.

**2.1 Quando o KPI for de valor de negócio/ROI, aplique o framework V.E.R.A. e sua governança.**
A lógica abaixo está descrita por completo aqui — não depende de nenhuma skill externa instalada, para esta skill funcionar sozinha em qualquer ambiente. **Se o ambiente já tiver uma skill dedicada de apuração de valor/ROI**, prefira usá-la para a mecânica do KPI (versão de referência, mais completa e mantida à parte); na ausência dela, aplique a lógica descrita a seguir diretamente. Use sempre que o KPI proposto for sobre comprovar valor/ROI de uma feature ou entrega (não todo KPI operacional precisa disso — só quando o objetivo é justificar valor para diretoria/sponsors/cliente):

*Princípios de governança do modelo (nunca deixar de aplicar):*
- Rastreabilidade: todo valor reportado precisa ter fonte de dado e memória de cálculo documentada — nunca só o número final.
- Fundamento: o racional é validado com as áreas de negócio envolvidas (Finanças, Operações, Logística, Digital, Fiscal etc.), não só assumido pela IA.
- Periodicidade: apuração é recorrente (mensal), com consolidação para relatos executivos — não é um exercício único.
- Dono do dado: todo KPI precisa de um responsável nomeado (pessoa, não área genérica) pela apuração, evidência e validação — sem owner nomeado, o KPI não está pronto para o Value Case.
- Transparência de maturidade e não duplicidade: os dois já cobertos abaixo.

*Papéis e cadência (contexto de quem participa, se o usuário pedir para desenhar a governança em si — não é tarefa mecânica da IA, é organizacional):* Comitê de Valor/Value Board (mensal ou trimestral — sponsor executivo, liderança CS/CX, Finanças) → Value Office (mensal — CS, analista de governança) → Value Owner por iniciativa (contínuo — líder da iniciativa/PO, com apoio de CS) → Finanças/Controladoria (por ciclo de apuração — FP&A).

- Classifique o KPI em um pilar — **Value** (valor financeiro novo), **Efficiency** (custo/esforço reduzido), **Risk** (risco/perda evitada) ou **Acceleration** (velocidade de captura de resultado) — sempre com justificativa explícita, nunca em silêncio.
- Nomeie no padrão fixo: [verbo de mudança] + [o que muda] + [unidade] + [recorte, se necessário]. Nunca aceite o nome da funcionalidade como nome do KPI.
- Rode o checklist de elegibilidade (5 perguntas) antes de qualquer KPI virar linha do Value Case: é atribuível a esta iniciativa isoladamente? tem causa única e rastreável? o nome é métrica, não pergunta? tem unidade explícita? tem fonte auditável nomeada? 5 de 5 sim → KPI válido; falhou em 1–2 → é "ganho genérico" (ex.: EBITDA, Receita Total, Margem Consolidada, NPS geral da empresa) — reporte só no resumo executivo, nunca como KPI de iniciativa, e sugira o KPI específico equivalente; falhou em 3+ → ainda é ideia, aponte o que falta.
- Antes de aprovar o KPI no Value Case (segundo checklist, depois do de elegibilidade): baseline preenchido (não só a meta); fonte de dados nomeada (sistema/relatório específico, nunca "a definir"); owner de negócio nomeado (pessoa, não área); pilar único atribuído; sem sobreposição — o mesmo real de valor não pode aparecer em outro KPI da mesma frente/iniciativa.
- Aplique a fórmula do pilar (Value, Efficiency, Risk Benefit ou Acceleration) preenchendo com os números que o usuário já deu e marcando `[a definir]` no resto.
- Status do KPI é sempre **Estimado** por padrão (baseado em premissas/projeções); sobe para **Validado** quando a área de negócio/Finanças confirma a estimativa (mas ainda sem dado real); sobe para **Auditado/Apurado** só com dado real coletado — e só KPIs com status Auditado/Apurado entram no ROI comprovado à diretoria.
- Regras de governança que não podem ser violadas: cada real de valor pertence a uma única iniciativa e um único pilar predominante (sem dupla contagem); quando um ganho impacta mais de um pilar, o secundário vira nota qualitativa, nunca soma dobrada; Acceleration é sempre valor direcional, nunca somado ao ROI financeiro hard dos demais pilares; casos com premissas não validadas ficam "Estimado" e não entram no ROI comprovado.
- Fórmula de ROI, quando o usuário pedir o fechamento consolidado: Benefício total = Value + Efficiency + Risk + Acceleration; ROI = (Benefício total − Custo) / Custo, onde Custo = CAPEX de implantação + OPEX de recorrência. A IA pode montar essa conta, mas os valores de CAPEX/OPEX vêm do usuário/Financeiro — nunca estimados sozinhos.
- Quando o pedido for uma visão consolidada de várias iniciativas (tipo relatório para EBR/QBR), organize por pilar (com drill-down por iniciativa dentro de cada pilar) ou por projeto (lista única) — conforme o que o usuário quiser ver primeiro.
- Pontos que são sempre decisão humana, nunca automática: classificar um benefício como hard/soft/risk-adjusted; os três cenários Conservador/Base/Agressivo; Payback e NPV/VPL em projetos plurianuais; qual pilar fica como primário quando a descrição toca dois pilares com peso semelhante.
- Fora do escopo desta skill (ficam com skills próprias, se existirem no ambiente): hierarquia Objetivo → KR → KPI (framework de OKR completo) e modelagem de eventos de analytics (GA4/Firebase).

**3. Amarre toda métrica a um objetivo de produto.**
Se a métrica proposta não tiver ligação clara com nenhum objetivo de produto, não a inclua na consolidação sem antes perguntar a qual objetivo ela serve.

**4. Registre e mantenha como contexto para o resto do processo.**
- A consolidação de métricas alimenta o loop de atualização periódica do roadmap (skill `construcao-alinhamento-roadmap`). Quando uma métrica indicar que o roadmap deveria mudar, aponte isso explicitamente para o usuário — não decida sozinha se o roadmap muda ou não.
- Salve a consolidação como contexto do repositório, para reaproveitar/atualizar nas próximas vezes (regra transversal), em vez de reconstruir do zero a cada consulta.

## Formato da saída

```
## Framework/estrutura em uso
[Framework/estrutura detectada no repositório, ou nenhum — e em que modelo/campos as métricas abaixo foram registradas]

## Conflito com o repositório (se houver)
[O que já está documentado e onde diverge do que esta skill orienta]

## Métricas já existentes reaproveitadas (se houver)
[Quais vieram do repositório, sem precisar perguntar de novo]

## Métricas propostas

### [Nome da métrica] — KPI ou OKR
[Tipo; prazo (se OKR); objetivo de produto ao qual está amarrada; ação associada prevista (se KPI). Se for KPI de valor/ROI: pilar V.E.R.A. + justificativa, resultado do checklist de 5 perguntas de elegibilidade, resultado do checklist de aprovação (baseline/fonte/owner/pilar único/sem sobreposição), fórmula aplicada, status Estimado/Validado/Auditado]

## ROI consolidado (se solicitado)
[Benefício total = V+E+R+A; Custo = CAPEX+OPEX (fornecidos pelo usuário/Financeiro); ROI resultante]

## Pontos de atenção
[Ex.: OKR sem prazo definido; KPI sem ação associada; métrica sem objetivo de produto claro]

## Sinal para o roadmap (se houver)
[Se alguma métrica sugerir uma mudança no roadmap vigente — sinalizado, não decidido aqui]
```

## Cuidados

- Não imponha o formato de registro desta skill quando o repositório usa outro modelo de métricas — registre no dele; a distinção KPI × OKR, a amarração a objetivo e a governança V.E.R.A. permanecem, a forma se adapta.
- Não trate KPI e OKR como a mesma coisa.
- Não aceite OKR sem prazo definido.
- Não aceite KPI sem ação associada prevista para quando o número fugir do esperado.
- Não inclua métrica sem ligação clara com um objetivo de produto.
- Não decida sozinha um conflito entre esta skill e o repositório.
- Não proponha métricas do zero se já existirem salvas no repositório — reaproveite, e só reabra se o usuário pedir para reconsiderar.
- Não trate um "ganho genérico" (EBITDA, Receita Total, NPS geral) como KPI de iniciativa — ele falha no checklist de elegibilidade, reporte só como contexto.
- Não some o valor de Acceleration ao ROI financeiro hard dos outros pilares — é sempre valor direcional, à parte.
- Não deixe um KPI de valor/ROI entrar no ROI comprovado à diretoria sem status Auditado/Apurado.
- Não classifique sozinha hard/soft/risk-adjusted benefit, cenários Conservador/Base/Agressivo, ou o pilar primário quando houver empate — sinalize e pergunte.
- Não aprove um KPI no Value Case sem owner de negócio nomeado (pessoa, não área) e sem fonte de dados nomeada.
- Não deixe o mesmo real de valor aparecer em mais de um KPI da mesma frente/iniciativa.
- Não estime CAPEX/OPEX sozinha para fechar um ROI consolidado — esses valores vêm do usuário/Financeiro.
