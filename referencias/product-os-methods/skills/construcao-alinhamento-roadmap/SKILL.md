---
name: construcao-alinhamento-roadmap
description: "Montar, atualizar ou revisar roadmap: traduz o backlog priorizado em ondas/épicos no tempo e sinaliza quando backlog e roadmap divergem."
---

# Construção e Alinhamento de Roadmap

> As menções a "(regra transversal)" abaixo remetem às regras transversais deste plugin, em `${CLAUDE_SKILL_DIR}/../../docs/REGRAS_TRANSVERSAIS.md` (o arquivo `docs/REGRAS_TRANSVERSAIS.md` na raiz do plugin, não no repositório em que você está trabalhando). Leia esse arquivo antes de aplicar a skill. Fora do Claude Code, as regras precisam ser fornecidas junto com esta skill.

## O princípio inegociável

Existe sempre **uma única versão vigente do roadmap** — a fonte única da verdade do projeto. Toda atualização substitui a anterior; nenhuma versão paralela ou desatualizada deve continuar circulando como se fosse a atual.

## Como conduzir

**0. Verifique pré-requisitos, o repositório e o framework em uso antes de começar.**
- **Framework em uso (verifique primeiro).** Identifique como o repositório de destino organiza produto e trabalhe no padrão dele (regra transversal — ver `${CLAUDE_SKILL_DIR}/../../docs/REGRAS_TRANSVERSAIS.md`, "Adaptação ao framework em uso"):
  - *O repositório já adota um framework ou estrutura própria* (Scrum/SAFe/Shape Up, ou uma cadência/estrutura de roadmap própria): "onda" é só o nome-padrão daqui — mapeie para o que o framework usa (ex.: onda → sprint, ciclo ou PI; épico → o termo do framework) e entregue o roadmap no formato dele. A conta de capacidade (passo 1.1) usa o modelo de dimensionamento do framework (horas, story points/velocity, etc.).
  - *Nenhum*: use os formatos desta skill como estão.
  A lógica desta skill — SSOT único, capacidade antes de alocar, item ligado a objetivo estratégico — continua valendo; o que se adapta são os nomes e o formato de visualização. Se a convenção do framework conflitar com o formato-padrão daqui, o framework em uso prevalece — sinalize a diferença, não decida sozinha.
- Priorização é pré-requisito: se o backlog ainda não foi priorizado, direcione o usuário para a skill `priorizacao-de-backlog` primeiro — não construa roadmap sobre backlog não priorizado.
- Se o repositório do projeto já definir um formato ou cadência de roadmap diferente do que esta skill orienta, sinalize o conflito e peça para o usuário escolher — nunca decida sozinha (regra transversal).

**1. Ofereça o formato de visualização — escolha do usuário, sem cadência padrão.**
- Opções: Gantt, diário, semanal, mensal.
- Alternativa mais leve para públicos que não precisam de datas exatas: roadmap now/next/later.
- Quando houver repositório, salve o formato escolhido como contexto do projeto e reaplique nas próximas vezes — só reabra a escolha se o usuário pedir para reconsiderar (regra transversal).

**1.1 Considere a capacidade do time antes de alocar itens nas ondas — isto não é opcional.**
Sem capacidade real, a alocação por onda vira palpite e o roadmap promete algo que a equipe não entrega. Antes de decidir em qual onda cada item priorizado cai:
- Confirme a capacidade disponível por onda (quantas pessoas dedicadas, com que % de dedicação, e a duração da onda) — se o repositório já tiver essa informação, reaproveite em vez de perguntar de novo (mesma lógica de reaproveitar a planilha de esforço na skill `priorizacao-de-backlog`).
- Em projetos dimensionados por hora: 100% de dedicação de uma pessoa equivale a 40h semanais (jornada cheia); dedicação parcial escala proporcionalmente (50% = 20h/semana, 25% = 10h/semana). A capacidade da onda é a soma dessas horas de todas as pessoas dedicadas ao longo da duração da onda (em semanas).
- Esse método de conversão em horas vale para projetos dimensionados por hora. Se o projeto usa outro modelo de dimensionamento (ex.: velocity em story points por sprint), não force a conversão em horas — confirme com o usuário qual modelo o projeto usa antes de calcular a capacidade.
- Use a estimativa de esforço já coletada na priorização (via planilha de esforço, quando existir) para calcular quantos itens priorizados cabem em cada onda dentro da capacidade disponível — não distribua os itens só pela ordem de prioridade, ignorando se cabem ou não.
- Quando o item já tiver sido refinado em história de usuário (skill `modelo-para-user-story`), ele só entra na conta de capacidade da onda depois de passar na Definition of Ready daquela skill — uma história ainda sem DoR é candidata, não item confirmado da onda.
- No formato Gantt/ondas, isso decide a posição exata do épico. No formato mais leve now/next/later, a capacidade ainda entra, mas num grão mais grosso — o suficiente para saber se algo cabe em "agora" ou não, sem precisar da conta exata de horas.
- Se a capacidade não foi informada, pergunte antes de alocar — não assuma uma distribuição só para preencher o roadmap.

**2. Estruture a visão por "ondas".**
- Visão por meses. Cada épico tem uma barra de progresso indicando onde começa e onde termina — um épico não precisa terminar dentro da mesma onda em que começou.
- Ao expandir/clicar na barra do épico, mostre o detalhe das features daquele épico, se houver.

**2.1 Diretriz visual de referência — clareza no gráfico, granularidade no clique.**
Diretriz para qualquer geração visual desta skill (Gantt ou visão por ondas), que resolve "épico atravessa mais de uma onda" sem virar bagunça visual:
- Grid simples: linhas = módulos/frentes do produto; colunas = ondas, com nome e período no cabeçalho de cada uma.
- A barra do épico é um intervalo (onda início → onda fim) com largura por coluna, não proporcional a horas — a estimativa de esforço entra só para decidir a posição/capacidade internamente, nunca aparece como número cru na leitura executiva.
- Quando o épico atravessa mais de uma onda, sinalize isso visualmente na própria barra (ex.: gradiente ou textura diferenciando a parte "plena" da parte que continua) e explique no texto (ex.: "Onda 2 → Onda 3").
- Épicos do mesmo módulo que se sobrepõem no tempo vão em raias (lanes) separadas dentro da mesma linha, em vez de se sobrepor visualmente.
- Uma legenda simples explica os elementos (cor por módulo, indicador de iniciativa em andamento, indicador de "atravessa onda").
- Ao clicar na barra, abra um painel de detalhe (lateral, não precisa travar a tela) com: nome do épico + módulo/frente, período (onda início → onda fim), badges relevantes (RGT, bloqueio técnico, iniciativa em andamento), descrição do épico — ou um aviso explícito de "sem descrição registrada" em vez de deixar em branco — e a lista de funcionalidades/features do épico. **Quando o épico atravessa mais de uma onda, agrupe as features por onda no detalhe** (um bloco por onda, com o rótulo e o período daquela onda), em vez de listar tudo junto.

**3. Conecte cada item ao objetivo estratégico por trás dele.**
- Todo item do roadmap deve deixar claro não só "o quê" e "quando", mas "por quê" — a que objetivo estratégico ele serve. Um item sem essa conexão clara é um sinal de alerta, não só um detalhe de preenchimento.

**4. Atualize de forma proativa — esse é o gatilho, não uma cadência fixa de tempo.**
Sempre que identificar itens já priorizados que ainda não estão refletidos no roadmap vigente, pergunte ao usuário se eles devem ser incorporados. Não espere ser perguntada, mas também não incorpore sozinha sem confirmar.

**5. Mantenha a versão única (SSOT).**
Toda atualização substitui a versão anterior como roadmap vigente. Se encontrar indício de uma versão desatualizada ainda em uso em paralelo (compartilhada, impressa, ou salva em outro lugar), avise o usuário em vez de simplesmente ignorar.

## Formato da saída

```
## Framework/estrutura em uso
[Framework/estrutura detectada no repositório, ou nenhum — e para quais termos "onda"/"épico" e o formato de roadmap foram mapeados]

## Conflito com o repositório (se houver)
[O que o repositório já define e onde diverge do que esta skill orienta]

## Formato de visualização
[Escolhido pelo usuário ou reaplicado do repositório — e qual]

## Capacidade considerada
[Pessoas dedicadas, % de dedicação e duração da onda — de onde veio (repositório ou informado agora) e quantos itens priorizados couberam em cada onda como resultado]

## Roadmap por ondas
[Onda/mês → épicos, com barra de progresso e objetivo estratégico de cada um; ao clicar/expandir um épico, mostrar o detalhe granular — descrição, badges relevantes e features, agrupadas por onda quando o épico atravessa mais de uma]

## Itens priorizados fora do roadmap vigente
[Se houver: quais, perguntando se devem ser incorporados agora]

## Versão vigente
[Confirmação de que esta versão substitui a anterior como única fonte da verdade]
```

## Cuidados

- Não imponha o vocabulário ("onda", "épico") nem o formato de roadmap desta skill quando o repositório usa outro framework — mapeie para o dele; a lógica (SSOT, capacidade, objetivo estratégico) permanece, a forma se adapta.
- Não construa roadmap sem o backlog já priorizado — direcione para a skill `priorizacao-de-backlog` primeiro.
- Não decida sozinha um conflito entre esta skill e o repositório.
- Não crie uma nova versão do roadmap sem aposentar explicitamente a anterior.
- Não incorpore um item novo ao roadmap sem perguntar antes — mesmo quando parecer óbvio que deveria entrar.
- Não repita a escolha de formato de visualização do zero se ela já estiver salva no repositório — só reabra se o usuário pedir.
- Não exiba estimativa em horas crua na leitura executiva — ela serve só para decidir posição/capacidade internamente.
- Não deixe descrição de épico em branco quando não houver — diga explicitamente que não há descrição registrada.
- Ao clicar num épico que atravessa mais de uma onda, não liste as features todas juntas — agrupe por onda.
- Não aloque itens em ondas sem considerar a capacidade real do time — isso não é opcional, mesmo no formato mais leve now/next/later.
