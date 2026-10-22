---
name: visualizacao-de-dados
description: "Gerar ou revisar gráfico, tabela ou dashboard com storytelling com dados (Knaflic): gráfico certo para a pergunta, sem saturação, atenção direcionada."
---

# Visualização de Dados

> As menções a "(regra transversal)" abaixo remetem às regras transversais deste plugin, em `${CLAUDE_SKILL_DIR}/../../docs/REGRAS_TRANSVERSAIS.md` (o arquivo `docs/REGRAS_TRANSVERSAIS.md` na raiz do plugin, não no repositório em que você está trabalhando). Leia esse arquivo antes de aplicar a skill. Fora do Claude Code, as regras precisam ser fornecidas junto com esta skill.

## O princípio inegociável

O tipo de gráfico, a cor, o corte de elementos e o destaque de um visual nunca são a
configuração padrão da ferramenta de geração — são decisão, tomada em função de quem vai
olhar aquele visual e do que essa pessoa precisa entender ou decidir a partir dele. Um
dashboard ou gráfico gerado sem essa decisão explícita é decoração, não comunicação com
dados. Este método é baseado no livro *Storytelling com Dados*, de Cole Nussbaumer
Knaflic — a lógica abaixo aplica as lições do livro de forma concreta e verificável, não
apenas como inspiração.

## Como conduzir

**0. Verifique o repositório, o framework em uso e a identidade visual antes de desenhar.**
- **Framework em uso.** Se o repositório já tem um padrão de dashboard, BI ou relatório
  próprio (um template de dashboard já adotado, uma ferramenta de BI com convenção
  própria de cor/layout), a lógica de decisão abaixo continua valendo — o que se adapta é
  onde e em que ferramenta o resultado é registrado (regra transversal).
- **Identidade visual.** Se o repositório já tem identidade visual documentada (skill
  `identidade-visual`, se instalada, ou qualquer paleta/tipografia já definida), use as
  cores e tipografia de lá para o destaque estratégico — não invente paleta nova.
- Se o repositório já tiver um padrão de visualização (biblioteca de gráfico, tema,
  paleta) que conflite com uma orientação abaixo, sinalize o conflito e pergunte — nunca
  decida sozinha (regra transversal).

**1. Entenda o contexto antes de abrir qualquer ferramenta de gráfico.**
Pergunte (ou responda, se já souber pelo contexto da conversa):
- **Quem** vai olhar esse visual, e que nível de familiaridade essa pessoa já tem com o
  dado?
- **O quê** essa pessoa precisa saber ou decidir depois de olhar? Se a resposta não for
  articulável em uma frase, o visual ainda não está pronto para ser desenhado.
- **Como** esse visual é consumido: em uma apresentação ao vivo (você está lá para
  explicar), em um documento/e-mail (a pessoa lê sozinha, precisa de mais contexto
  embutido), ou em um **dashboard de consulta recorrente** (sem narrador, olhado várias
  vezes, para monitorar, não para uma decisão pontual)? Esses três formatos pedem desenhos
  diferentes — trate-os diferente, não use o mesmo modelo para os três.
- Resuma o ponto principal em uma única frase (a "Grande Ideia") antes de escolher
  qualquer gráfico. Se não houver uma frase clara, o pedido ainda não tem contexto
  suficiente — pergunte antes de gerar.

**2. Escolha o tipo de visual pela pergunta que os dados respondem, nunca pelo padrão da ferramenta.**
Use esta referência para decidir — e nunca aceite o gráfico padrão sugerido pela
ferramenta sem confirmar que ele é o certo para a pergunta:

| O que você precisa mostrar | Visual indicado |
|---|---|
| Um ou dois números isolados | Texto direto (número em destaque + frase de apoio) — não force gráfico ou tabela para 1-2 números |
| Comparação entre categorias | Barras (sempre com linha de base zero) |
| Tendência ao longo do tempo | Linha (pontos em intervalos de tempo coerentes entre si) |
| Comparação entre exatamente dois pontos/períodos, por categoria | Gráfico de inclinação (slopegraph) |
| Correlação entre duas variáveis | Dispersão |
| Consulta detalhada, várias unidades de medida, público variado | Tabela (bordas discretas ou espaço em branco no lugar de borda pesada) |
| Magnitude relativa dentro de uma tabela | Mapa de calor (com legenda de intervalo) |
| Parte de um todo | Barra empilhada ou barra única com destaque — nunca pizza ou rosca |

**Proibições sem exceção, porque distorcem a leitura ou dificultam a comparação (regra do método):**
- Nunca gráfico de pizza ou de rosca — comparar ângulo/área é uma tarefa visual difícil;
  se o pedido for "parte de um todo", substitua por barra.
- Nunca 3D em gráfico de negócio — distorce proporção e dificulta leitura do valor exato.
- Nunca eixo Y duplo/secundário — força o público a decidir sozinho qual linha pertence a
  qual eixo, e convida a manipulação (mesmo sem intenção).
- Nunca gráfico de barras sem linha de base zero — o olho compara o tamanho da barra, não
  o rótulo do eixo; começar o eixo fora de zero exagera visualmente a diferença real.

**3. Elimine a saturação — todo elemento sem valor informativo é candidato ao corte.**
Antes de finalizar qualquer visual, revise contra os princípios de percepção visual da
Gestalt (o que faz o público agrupar e ler elementos automaticamente, sem precisar de
borda ou grade para isso):
- **Proximidade e espaço em branco** já agrupam colunas/linhas — não é preciso grade
  completa para isso.
- **Similaridade de cor** já indica pertencimento ao mesmo grupo — não duplique isso com
  legenda distante quando dá para rotular direto no dado.
- **Fechamento e continuidade** significam que bordas, sombreado de fundo e linhas de eixo
  completas raramente são necessários — o gráfico continua legível sem eles.
- Nunca centralize título ou texto — alinhe à esquerda (ou ao início da leitura natural),
  para criar linhas retas com o resto do visual.
- Espaço em branco é decisão, não sobra — nunca preencha espaço vazio com mais dado, ícone
  ou decoração só porque "ainda cabe algo ali".
- Eixos e legendas que não são o foco da mensagem vão em cinza, nunca competindo
  visualmente com o dado em si.

**4. Direcione a atenção com intenção — nunca por acidente.**
Tamanho, cor e posição são as ferramentas mais fortes para dizer ao público onde olhar
primeiro — e o oposto também é verdade: usados sem decisão, eles dizem a coisa errada.
- Dê o mesmo peso visual (tamanho) a itens de mesma importância; **nunca deixe um item
  dominar visualmente só porque os dados dele ficaram prontos primeiro ou vieram maiores
  por padrão** — isso já mudou decisões reais de audiência sem que fosse a intenção, e é
  exatamente o tipo de acidente de design que esta skill existe para evitar.
- Use cor com moderação e propósito: uma cor de destaque sobre uma base neutra (cinza) é
  mais eficaz que uma paleta com uma cor por categoria — cor demais anula o efeito de
  chamar atenção.
- Antes de considerar o visual pronto, aplique o teste: "para onde meus olhos vão
  primeiro?" Se a resposta não for o ponto que responde à pergunta do passo 1, ajuste
  cor/tamanho/posição até que seja.

**5. Pense como designer: dê ao público as pistas de como ler o visual.**
- Rotule os dados diretamente quando possível, em vez de forçar o público a ir e voltar
  entre o dado e uma legenda distante.
- Título e rótulos de eixo em linguagem clara para quem vai ler — não em nome de campo ou
  jargão de sistema.
- Alinhe todos os elementos (título, eixos, legendas, dado) para criar uma leitura limpa,
  de cima para baixo e da esquerda para a direita.

**6. Adapte a história ao formato — dashboard recorrente e apresentação pontual não se contam do mesmo jeito.**
- **Dashboard de consulta recorrente** (sem narrador, olhado várias vezes): não tem arco
  de começo-meio-fim de uma apresentação pontual. Em vez disso, precisa de hierarquia
  visual fixa e imediata — a métrica/KPI mais importante (a Grande Ideia do passo 1) em
  destaque visual permanente, sem depender de alguém explicar o que olhar primeiro.
- **Apresentação pontual ou relatório para decisão específica**: aqui sim construa arco
  narrativo — comece pelo contexto, desenvolva com o que os dados mostram, termine com a
  chamada para ação esperada (a Grande Ideia do passo 1 deve aparecer clara, não
  escondida no meio).
- Nos dois casos, a Grande Ideia definida no passo 1 é o que organiza a hierarquia visual
  — nunca gere o visual e só depois tente encaixar uma mensagem nele.

**7. Registre como contexto do repositório.**
Salve o tipo de visual e as decisões de design aprovadas (paleta, formato de dashboard,
convenções adotadas) como contexto do projeto, para reaproveitar nas próximas
visualizações em vez de reabrir a decisão do zero a cada gráfico pedido (regra
transversal).

## Formato da saída

```
## Framework/identidade visual em uso
[Padrão de dashboard/BI e identidade visual detectados no repositório, ou nenhum]

## Contexto
Quem: [...]
O quê (decisão/ação esperada): [...]
Como é consumido: [apresentação ao vivo / documento ou e-mail / dashboard recorrente]
Grande Ideia (uma frase): [...]

## Visual escolhido e por quê
[Tipo de gráfico/tabela escolhido, ligado à pergunta que os dados respondem — não ao padrão da ferramenta]

## Saturação eliminada
[Elementos cortados: grade, borda, legenda redundante, cor sem propósito, etc.]

## Onde a atenção foi direcionada
[O que foi destacado com cor/tamanho/posição, e por quê — resultado do teste "para onde os olhos vão primeiro"]

## Pendências
[O que falta confirmar: identidade visual, dado faltante, decisão do usuário sobre formato]
```

## Cuidados

- Nunca gere um gráfico de pizza, de rosca, em 3D, ou com eixo Y duplo/secundário —
  substitua pela alternativa da tabela do passo 2, sem perguntar se pode, a menos que o
  usuário insista depois de entender o motivo.
- Nunca aceite o gráfico padrão sugerido pela ferramenta sem confirmar que ele responde à
  pergunta do passo 1 — "sempre gerar o mesmo modelo" é sinal de que este passo está sendo
  pulado.
- Nunca gráfico de barras sem linha de base zero.
- Nunca centralize título ou texto do visual.
- Nunca deixe grade completa, borda pesada ou sombreado de fundo por padrão — corte tudo
  que não ajuda a entender o dado (Gestalt, passo 3).
- Nunca use paleta arco-íris ou uma cor por categoria sem necessidade — cor é escolha
  estratégica, não preenchimento automático.
- Nunca dimensione ou posicione um elemento só porque "os dados desse ficaram prontos
  primeiro" ou "vieram maiores por padrão" — confirme que o tamanho relativo reflete a
  importância real antes de finalizar.
- Nunca trate dashboard recorrente e apresentação pontual com o mesmo desenho — o primeiro
  precisa de hierarquia visual fixa sem narrador; o segundo precisa de arco narrativo.
- Nunca gere o visual antes de conseguir dizer, em uma frase, o que a pessoa que vai olhar
  precisa saber ou fazer depois de ver — sem essa frase (a Grande Ideia), pergunte antes
  de desenhar.
- Não invente paleta nova quando o repositório já tem identidade visual documentada —
  reaproveite (skill `identidade-visual`, se instalada).
- Não decida sozinha um conflito entre esta skill e um padrão de dashboard/BI já definido
  no repositório — sinalize e pergunte.
