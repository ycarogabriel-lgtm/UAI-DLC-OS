# product-os-methods — métodos de produto para qualquer IA

Métodos de produto (discovery, refinamento, priorização, roadmap, métricas, protótipo,
handoff, testes) e uma equipe de 11 especialistas de produto, escritos para funcionar com
**qualquer assistente de IA** — não só Claude. Empacotados como plugin do Claude Code para
quem usa essa ferramenta, mas o conteúdo em si não pressupõe nenhum modelo específico.
**Feito para rodar junto ao repositório e ao framework que você já usa** — não instala
estrutura de pastas, não pede que você adote nenhuma metodologia.

## Use com qualquer IA, não só Claude Code

O texto de cada método (`SKILL.md`) e de cada especialista (`agents/*.md`) — tudo abaixo
da segunda linha `---` — fala sempre em "a IA", nunca assume Claude, ChatGPT, Gemini ou
qualquer outro modelo por nome. Os únicos trechos específicos do Claude Code são o cabeçalho
(`name`/`description` entre `---`), que serve só para o Claude Code decidir quando
acionar automaticamente aquele método ou especialista, e a variável
`${CLAUDE_SKILL_DIR}` no caminho das regras transversais, que o Claude Code troca pela
pasta da skill — fora dele, ignore o cabeçalho e use o arquivo `docs/REGRAS_TRANSVERSAIS.md`
deste repositório.

**Fora do Claude Code, para usar com outra IA:**
1. Abra o arquivo do método/especialista que quer usar (ex.:
   `skills/priorizacao-de-backlog/SKILL.md`).
2. Copie o conteúdo a partir da segunda linha `---` (pule o cabeçalho — é metadado de
   acionamento do Claude Code, não faz parte da instrução).
3. Cole como instrução de sistema / instrução customizada / mensagem inicial no
   assistente que você usa:
   - **ChatGPT** — em "Instruções personalizadas" ou nas instruções de um Projeto/GPT.
   - **Gemini** — nas instruções de um Gem.
   - **Copilot, Cursor, Windsurf** — num arquivo de regras do projeto (ex.:
     `.cursor/rules`, `AGENTS.md`).
   - **Qualquer outro chat** — cole no início da conversa, antes de pedir a tarefa.
4. **Cole também o conteúdo de [`docs/REGRAS_TRANSVERSAIS.md`](docs/REGRAS_TRANSVERSAIS.md).**
   Todas as skills remetem a essas regras ("(regra transversal)") — sem elas, a skill
   perde a aprovação humana, a sinalização de conflito e a adaptação ao framework.
5. Repita para cada método/especialista que quiser combinar — várias ferramentas aceitam
   múltiplos blocos de instrução.

Nenhuma edição no texto é necessária: ele já é neutro quanto a qual IA está executando.

## O que faz este pacote ser agnóstico ao repositório e ao framework

Cada skill começa detectando **como o seu repositório organiza produto** e trabalha no
padrão dele:

- **Você já usa um framework ou estrutura própria** (Scrum, SAFe, Shape Up, um board com
  campos próprios, um vault/wiki de produto, um design system próprio, templates de
  história/roadmap/handoff já definidos): a skill trata os nomes e formatos dela como
  *padrão*, não como obrigação — mapeia cada um para o equivalente do seu framework
  (ex.: "onda" → "sprint"/"ciclo"/"PI") e registra no formato que você já usa.
- **Você não usa framework nenhum**: a skill usa os próprios métodos e formatos como
  estão e salva o contexto aprovado junto ao projeto no seu repositório.
- **Não há repositório conectado à sessão** (uma conversa avulsa, sem projeto aberto): a
  skill sinaliza isso e pergunta diretamente pelos critérios mínimos, em vez de presumir
  — e considera normalmente qualquer material que você já tenha enviado na conversa
  (arquivo, texto colado, transcrição) como contexto.

Em todos os casos, **a lógica de método continua valendo — o que se adapta é a forma de
registrar e nomear.** Quando a convenção do seu framework conflita com o formato-padrão
da skill, o seu framework prevalece e a skill sinaliza a diferença em vez de decidir
sozinha. Detalhe em [`docs/REGRAS_TRANSVERSAIS.md`](docs/REGRAS_TRANSVERSAIS.md).

## Instalação — se você usa Claude Code

```
/plugin marketplace add brunaaguilar/product-os-methods-plugin
/plugin install product-os-methods@product-os-methods
```

_O repositório é privado: a instalação só funciona para quem tem acesso a ele e está
autenticado no git (o Claude Code usa as credenciais git da máquina para clonar)._

Se você usa outra IA, não há "instalação" — veja "Use com qualquer IA" acima.

## O que vem no plugin

### Agentes (`agents/`)

| Agente | Para quê |
|---|---|
| `product-lead` | Estratégia, discovery, roadmap, priorização — resolver o problema certo |
| `product-owner` | Priorização, refinamento, divisão de escopo, planejamento de entrega — decidir o que construir na ordem certa |
| `business-analyst` | Regras de negócio, épicos, funcionalidades, critérios de aceite rastreáveis |
| `product-designer` | Jornada, fluxos, arquitetura da informação, protótipo — experiência antes da tela |
| `ux-researcher` | Entrevistas, testes de usabilidade, síntese de evidência — decisão antes de opinião |
| `solution-architect` | Arquitetura sustentável, trade-offs, integrações, dívida técnica consciente |
| `tech-lead` | Planejamento técnico, qualidade de código, evolução do time |
| `qa-engineer` | Estratégia de testes, riscos, cenários de exceção — qualidade contínua |
| `workshop-specialist` | Facilitação de sessões colaborativas, decisões documentadas |
| `presentation-specialist` | Narrativa, comunicação executiva, apresentações orientadas à decisão |
| `ai-product-specialist` | Identificar onde IA amplia os demais especialistas, sem substituir julgamento humano |

### Skills de método (`skills/`)

| Skill | Cobre |
|---|---|
| `refinamento-de-negocio` | Decisão de negócio rastreável, fonte única da verdade, critérios de aceite Given-When-Then |
| `priorizacao-de-backlog` | Impacto×Esforço, MoSCoW, RGT, RICE, WSJF — método aprovado por pessoa |
| `modelo-para-user-story` | Template de US completo, DoR, DoD, INVEST |
| `construcao-alinhamento-roadmap` | Backlog priorizado → roadmap por ondas, com capacidade do time |
| `consolidacao-modelos-metricas` | KPI vs OKR, cada métrica amarrada a um objetivo de produto |
| `identidade-visual` | Reunir/documentar tokens, componentes, acessibilidade antes de prototipar |
| `prototipacao` | Fluxograma macro → protótipo navegável → análise heurística |
| `handoff-tecnico-e-especificacao` | Entrega do protótipo validado ao time técnico |
| `teste-de-usabilidade` | Planejar/conduzir/consolidar teste com usuário real |
| `entrevista-e-pesquisa` | Entrevista qualitativa, síntese de discovery e personas, com evidência rastreável |
| `visualizacao-de-dados` | Storytelling com dados (Cole Nussbaumer Knaflic) — tipo de gráfico pela pergunta, corte de saturação, atenção direcionada, em qualquer gráfico, tabela ou dashboard |

Os métodos se encadeiam (refinamento → US → priorização → roadmap → identidade visual →
protótipo → handoff → teste), mas **o fluxo é cíclico e adaptável, não um pipeline
rígido** — cada skill funciona sozinha e detecta o que já existe no repositório antes de
agir. Quando uma skill cita outra (`priorizacao-de-backlog`, etc.) e essa outra não
estiver instalada, trate a citação como uma etapa manual.

## Duas regras de conteúdo

1. **Nenhum conteúdo de cliente.** As skills carregam método, não dados de projeto de
   ninguém.
2. **Nada para "instalar".** Este plugin não cria estrutura de pastas nem impõe
   metodologia — ele se encaixa no que o seu repositório já tem.

## Escopo

Este pacote está completo nos dois pilares: **11 especialistas** (`agents/`) e **11
métodos** (`skills/`). Os especialistas seguem o formato validado em `product-owner.md`
— missão, princípios, modelos mentais, fluxo de trabalho (com referência por nome às
skills de método aplicáveis, quando existirem), limites de atuação e critério de
sucesso.
