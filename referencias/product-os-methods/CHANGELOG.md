# Changelog

## [0.7.2] — não publicado

### Alterado
- Descrições (`description` no cabeçalho) das 11 skills encurtadas de ~5.400 para ~1.700
  caracteres no total, com o gatilho de uso no início (ex.: "Priorizar backlog: ...").
  Com muitas skills instaladas, o Claude Code reduz parte delas a só o nome na lista de
  skills disponíveis — em uma sessão com ~70 skills, 8 das 11 deste plugin apareciam sem
  descrição, o que dificulta o acionamento automático. O conteúdo de cada método (tudo
  abaixo do cabeçalho) não mudou.

## [0.7.1] — não publicado

### Corrigido
- As 11 skills citavam `docs/REGRAS_TRANSVERSAIS.md` por caminho relativo. Com o plugin
  instalado, esse caminho aponta para o repositório em que a pessoa está trabalhando, não
  para o plugin — a IA não encontrava as regras (ou lia outro arquivo com o mesmo nome).
  O caminho passou a ser `${CLAUDE_SKILL_DIR}/../../docs/REGRAS_TRANSVERSAIS.md`, que o
  Claude Code resolve para a pasta da skill dentro do plugin, e a nota de cada skill diz
  que, fora do Claude Code, as regras precisam ser fornecidas junto.
- `README.md` — comando de instalação apontava para `<owner>/product-os-methods`; agora
  usa o repositório real (`brunaaguilar/product-os-methods-plugin`) e avisa que o acesso
  exige permissão no repositório privado. O passo a passo para outras IAs passa a incluir
  colar `docs/REGRAS_TRANSVERSAIS.md`.

### Removido
- Campo `"skills": "./skills/"` do `plugin.json` — redundante, já que `skills/` é a pasta
  lida por padrão.

## [0.7.0] — não publicado

### Adicionado
- `skills/visualizacao-de-dados/SKILL.md` — 11ª skill de método, aplicando o método de
  storytelling com dados (Cole Nussbaumer Knaflic) na escolha e no desenho de qualquer
  gráfico, tabela ou dashboard: contexto e Grande Ideia antes do visual, tipo de gráfico
  escolhido pela pergunta que os dados respondem (nunca pelo padrão da ferramenta),
  proibição de pizza/rosca/3D/eixo Y duplo, corte de saturação via princípios da Gestalt,
  atenção direcionada por cor/tamanho/posição com intenção (nunca por acidente — inclui o
  caso real do livro em que um item ficou grande demais só porque seus dados ficaram
  prontos primeiro, e isso mudou a decisão da audiência), e distinção entre dashboard de
  consulta recorrente (hierarquia visual fixa, sem narrador) e apresentação pontual (arco
  narrativo começo-meio-fim). Referenciada por nome em `presentation-specialist.md` e
  `product-designer.md`. Motivada por relato de que a geração de dashboard vinha sempre
  no mesmo modelo genérico, ignorando essas boas práticas.
- `README.md`, `plugin.json`, `marketplace.json` — atualizados para citar 11 métodos
  (antes 10).

## [0.6.0] — não publicado

### Adicionado
- Os 10 especialistas restantes em `agents/`, completando a equipe de 11:
  `business-analyst`, `product-lead`, `product-designer`, `ux-researcher`, `tech-lead`,
  `solution-architect`, `qa-engineer`, `workshop-specialist`, `presentation-specialist`,
  `ai-product-specialist`. Cada um segue o formato de referência validado em
  `product-owner.md`: missão, princípios condensados, modelos mentais, fluxo de
  trabalho (com referência por nome às skills de método aplicáveis), limites de
  atuação, a cláusula de adaptação ao framework em uso, e critério de sucesso.
  Especialistas sem skill de método correspondente entre os 10 já existentes (Solution
  Architect, QA Engineer, Workshop Specialist, Presentation Specialist, AI Product
  Specialist) não têm referência cruzada forçada.
- `README.md`, `plugin.json`, `marketplace.json` — atualizados para citar os 11
  especialistas (antes só listavam `product-owner` como referência de formato).

### Corrigido
- A cláusula "Adapte-se ao framework em uso" dos 10 novos agentes citava "Product OS"
  e o caminho `02_Projetos/<projeto>/` por nome — acoplamento ao sistema interno da
  autora, inconsistente com a agnosticidade ao repositório que o resto do plugin já
  seguia (`product-owner.md` e as 10 skills nunca nomeiam um framework específico).
  Reescrita para a forma genérica já usada em `product-owner.md` (Scrum/SAFe/Shape
  Up/vault de produto, sem nomear nenhum como padrão).

## [0.5.1] — não publicado

### Adicionado
- `skills/modelo-para-user-story/SKILL.md` — passo 1 agora explicita a diferença de
  tratativa com e sem repositório para a história evolutiva: com repositório, a US é
  registrada e organizada por estágio de maturidade na estrutura do projeto; sem
  repositório, o estágio atual e o que falta para amadurecer são devolvidos direto na
  conversa. A lógica de avaliação do estágio é a mesma nos dois casos — só muda o
  destino do resultado.

## [0.5.0] — não publicado

### Adicionado
- `docs/REGRAS_TRANSVERSAIS.md` — quinta regra transversal: **uma etapa específica pode
  ser pedida isoladamente**. Quando o pedido do usuário já corresponde a uma etapa
  dentro de uma skill (ex.: consolidar material já reunido, gerar persona a partir de
  material enviado, aplicar método de priorização já escolhido), a IA aplica a lógica
  dessa etapa diretamente, sem exigir ter passado pelas etapas anteriores da mesma skill
  que não foram pedidas. Ressalva explícita: isso não afeta validações que são parte do
  método em si, como os três estágios de maturidade de `modelo-para-user-story`, que
  continuam obrigatórios em sequência.
- `skills/entrevista-e-pesquisa/SKILL.md` — passo 0 agora cita essa regra de forma
  concreta (consolidar transcrição avulsa, gerar persona a partir de material enviado).

## [0.4.0] — não publicado

### Adicionado
- `skills/entrevista-e-pesquisa/SKILL.md` — passo de **criação de persona** a partir da
  mesma consolidação de pesquisa: exige pesquisa real por trás (nunca só demografia),
  persona provisória quando o material ainda não sustenta uma versão fundamentada,
  poucas personas bem fundamentadas em vez de muitas rasas — critério padrão baseado em
  prática de mercado (Nielsen Norman Group), no mesmo padrão de citação já usado em
  `teste-de-usabilidade` e `prototipacao`. Esse critério só vale quando o usuário não
  direcionou base, método ou ferramenta próprios — nesse caso, a skill segue a direção
  dada, não o padrão.
- README — linha da tabela de skills atualizada para citar personas.

## [0.3.0] — não publicado

### Adicionado
- `docs/REGRAS_TRANSVERSAIS.md` — quarta regra transversal: **sem repositório
  conectado, use o que foi enviado no chat**. Cobre sessões avulsas (sem projeto/
  repositório aberto): a IA sinaliza a ausência de repositório, pergunta diretamente
  pelos critérios mínimos em vez de presumi-los, e considera normalmente qualquer
  material já enviado na própria conversa (arquivo, texto colado, transcrição) como
  contexto válido. Não altera as regras 1–3 nem a lógica de detecção de framework já
  existente em cada skill — é aditiva.

## [0.1.0] — não publicado

### Adicionado
- Estrutura do plugin (`.claude-plugin/plugin.json`, `marketplace.json`).
- `docs/REGRAS_TRANSVERSAIS.md` — três regras transversais: aprovação humana antes da
  vigência, sinalização antes de resolver conflito, e adaptação ao framework em uso.
- 10 skills de método: `refinamento-de-negocio`, `priorizacao-de-backlog`,
  `modelo-para-user-story`, `construcao-alinhamento-roadmap`,
  `consolidacao-modelos-metricas`, `identidade-visual`, `prototipacao`,
  `handoff-tecnico-e-especificacao`, `teste-de-usabilidade`, `entrevista-e-pesquisa`.
  Cada uma detecta o framework em uso no repositório de destino (ou a ausência dele) e
  adapta nomes e formato de registro — a lógica de método permanece.
- `agents/product-owner.md` — especialista de produto (referência de formato).

### Notas
- Este pacote é a versão agnóstica: não inclui nenhuma skill de instalação de estrutura
  de framework, nem qualquer scaffold. Serve para uso junto a um repositório e framework
  já existentes.

## [0.2.0] — não publicado

### Alterado
- README reescrito para deixar explícito que o conteúdo (métodos + especialista) é
  **agnóstico à IA que executa** — nunca pressupõe Claude, ChatGPT, Gemini ou qualquer
  outro modelo. Adicionada a seção "Use com qualquer IA, não só Claude Code", com o
  passo a passo de copiar o corpo de um `SKILL.md`/`product-owner.md` (ignorando o
  cabeçalho `name`/`description`, que é metadado específico de acionamento do Claude
  Code) para instrução de sistema/customizada de qualquer outro assistente.
- `docs/REGRAS_TRANSVERSAIS.md` e as descrições em `plugin.json`/`marketplace.json`
  passam a citar explicitamente a agnosticidade quanto à IA.
- Confirmado por auditoria: nenhum `SKILL.md` ou `agents/product-owner.md` menciona
  "Claude" no corpo da instrução (só "a IA") — a mudança foi de enquadramento/documentação,
  não de conteúdo instrucional.
