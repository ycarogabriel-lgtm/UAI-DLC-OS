---
name: entrevista-e-pesquisa
description: "Planejar, conduzir ou sintetizar entrevista/pesquisa com usuário: roteiro, consolidação com evidência rastreável, cards de oportunidade e personas baseadas em evidência."
---

# Entrevista / Pesquisa

> As menções a "(regra transversal)" abaixo remetem às regras transversais deste plugin, em `${CLAUDE_SKILL_DIR}/../../docs/REGRAS_TRANSVERSAIS.md` (o arquivo `docs/REGRAS_TRANSVERSAIS.md` na raiz do plugin, não no repositório em que você está trabalhando). Leia esse arquivo antes de aplicar a skill. Fora do Claude Code, as regras precisam ser fornecidas junto com esta skill.

## O princípio inegociável

Toda afirmação da síntese carrega a fonte de onde saiu — citação é fato, leitura é leitura, e as duas nunca se confundem. Entrevista/pesquisa explora atitude, necessidade e contexto — não é o mesmo objetivo do teste de usabilidade, que avalia desempenho de interface. E nenhum card de oportunidade nascido daqui entra no backlog sozinho — sempre precisa de decisão humana explícita antes.

## Como conduzir

**0. Verifique o repositório, o framework em uso e o objetivo antes de montar roteiro ou síntese.**
- **Framework em uso (verifique primeiro).** Identifique como o repositório de destino organiza produto e trabalhe no padrão dele (regra transversal — ver `${CLAUDE_SKILL_DIR}/../../docs/REGRAS_TRANSVERSAIS.md`, "Adaptação ao framework em uso"):
  - *O repositório já adota um framework ou estrutura própria* (um repositório de research, um template de insight ou de nota de entrevista já adotado, uma taxonomia de tags própria): registre no formato que o framework já usa — o esqueleto de roteiro e a estrutura de síntese (temas com frequência, sinais fracos, contradições, lacunas) desta skill são o conteúdo mínimo, não o formato obrigatório.
  - *Nenhum*: use os formatos desta skill como estão.
  A lógica desta skill — objetivo definido antes do roteiro, toda afirmação com fonte rastreável, card só entra no backlog com decisão humana — continua valendo; o que se adapta é o formato do registro. Se a convenção do framework conflitar com o formato-padrão daqui, o framework em uso prevalece — sinalize a diferença, não decida sozinha.
- Pergunte qual é a decisão que depende dessa entrevista/pesquisa antes de fazer qualquer coisa — "aprender sobre os usuários" não é objetivo específico o suficiente para orientar um roteiro ou uma leitura. Se o usuário não souber, ajude a formular 2 a 3 perguntas concretas e acionáveis.
- Se esta skill conflitar com o que já está documentado no repositório, sinalize e pergunte — nunca decida sozinha (regra transversal).
- **Se o pedido já é por uma etapa específica** (ex.: "consolida essa transcrição", "gera a persona a partir desse material") — aplique direto a lógica e o critério daquela etapa; não exija ter passado pelo roteiro (passo 1) ou por outra etapa anterior desta skill que não foi pedida (regra transversal).

**1. Monte o roteiro seguindo o arco de entrevista qualitativa e um esqueleto padrão.**
- Estrutura do roteiro: cabeçalho com objetivo(s) da entrevista, perfil do entrevistado, tipo de roteiro (ex.: semiestruturado) e entregáveis esperados; introdução pessoal + trecho de consentimento (LGPD, quando houver gravação); corpo dividido em blocos temáticos, cada um com objetivo declarado; encerramento com pergunta aberta final e indicação de próximos entrevistados, se houver.
- Se o repositório já tiver um esqueleto de roteiro em uso, reaproveite a estrutura, não recrie do zero. O conteúdo específico de um roteiro anterior serve de exemplo, nunca de texto fixo a copiar para outro entrevistado/contexto.
- Siga o arco da entrevista qualitativa: abertura leve → rapport → aprofundamento → cool down → encerramento. Comece com perguntas de baixo risco para relaxar o participante.
- Prefira poucas perguntas abertas bem desenhadas, com perguntas de acompanhamento previstas — sondagem exploratória do tipo "me conta mais sobre isso" ou "por que isso é importante pra você", sem induzir a resposta. Pilote o roteiro com colegas antes de aplicar com usuário real, quando possível.
- Fique atenta às limitações de dados autorreportados — memória falha, viés de desejabilidade social — e não trate relato como fato absoluto.

**2. Conduza e reúna o material de uma vez, não fonte por fonte isolada.**
- Cruze o material disponível — entrevistas, tickets de suporte, respostas de pesquisa, notas de call, planilhas — em vez de analisar cada fonte separadamente sem conexão com as demais.
- Liste o material reunido e confirme com o usuário antes de sintetizar; se algo estiver ilegível ou vazio, avise antes de começar — não sintetize fingindo ter lido o que não deu para ler.

**3. Consolide com evidência rastreável.**
A lógica está descrita por completo aqui — não depende de nenhuma skill externa instalada. **Se o ambiente já tiver uma skill dedicada de síntese de pesquisa**, prefira usá-la (versão de referência, mais completa e mantida à parte). Na ausência dela, aplique a lógica a seguir diretamente:

- Leia todo o material antes de concluir qualquer coisa — não forme a tese cedo (ex.: no terceiro arquivo) e use o resto só para confirmá-la.
- Agrupe por tema, não por arquivo/fonte — o valor está em ver o mesmo problema aparecendo em fontes que não se conhecem.
- Conte com honestidade: "apareceu em N de M fontes" é sempre melhor do que "apareceu com frequência".
- Toda citação vem com a fonte exata (arquivo, trecho ou linha) — sem fonte, a afirmação não entra na síntese, ou entra marcada explicitamente como hipótese.
- Nunca transforme sentimento relatado em número inventado — "vários usuários frustrados" não vira "60% de insatisfação" sem medição real.
- Preserve achados desconfortáveis, mesmo quando contradizem uma decisão já tomada — é justamente o propósito de consolidar pesquisa, não um efeito colateral indesejado.
- Registre também sinais fracos (o que apareceu uma vez só), contradições entre fontes, e o que o material não responde (lacunas que precisariam de nova pesquisa) — essas seções costumam ser as mais valiosas e as que mais somem em sínteses automáticas malfeitas.
- Anonimize participantes (P1, P2...) na saída.

**4. Gere cards de oportunidade — nunca direto para o backlog.**
A partir da consolidação, gere cards de possíveis oportunidades — mas, mesma lógica do teste de usabilidade, eles não entram no backlog sozinhos; precisam de decisão/direcionamento humano explícito antes (regra transversal — IA sugere, uma pessoa aprova). Se aprovados, alimentam de volta a skill `priorizacao-de-backlog`.

**5. Gere personas quando solicitado — não exige ter conduzido entrevista por esta skill.**
Persona não depende de rodar o processo completo de roteiro/entrevista (passos 1–4). Ela pode nascer de: uma consolidação feita por esta skill, **qualquer material enviado na própria conversa para análise** (uma transcrição avulsa, um documento, notas, respostas de pesquisa), ou do contexto já registrado no repositório do projeto. Ao ser pedida uma persona, verifique primeiro o que está disponível — material desta conversa e/ou contexto do projeto (regras transversais 3 e 4) — antes de assumir que falta informação.

- **Se o usuário já indicar a base, o método ou a ferramenta que quer usar** (ex.: "monta a persona só com base nessa transcrição", "usa nosso template de persona", "segue tal método") — siga a direção dele. Os critérios abaixo (prática de mercado, Nielsen Norman Group) são a recomendação **padrão para quando nada foi especificado**, nunca uma obrigação por cima do que o usuário pediu.
- Gere persona com base em evidência real do material analisado (o que está na transcrição, no documento ou no contexto do projeto) — nunca a partir de suposição pura ou só de dados demográficos (idade, cargo, cidade não bastam; o que sustenta a persona é padrão de comportamento, objetivo e necessidade observados no material).
- Se o material disponível for pouco (uma fonte só, tema não confirmado), gere uma **persona provisória** e marque explicitamente como hipótese a validar — nunca apresente como definitiva.
- Estruture cada persona com: nome e retrato breve (papel/contexto), objetivos, comportamentos observados, frustrações/necessidades e um cenário de uso — cada elemento remetendo à evidência de origem (trecho da transcrição/documento, ou tema da síntese, quando houver).
- Prefira poucas personas bem fundamentadas (tipicamente 2 a 4) a muitas personas rasas — excesso de personas dilui o foco de decisão.
- Persona é insumo de contexto para decisão, não decisão em si — não substitui os cards de oportunidade nem a priorização.

**6. Diferencie do teste de usabilidade e registre como contexto.**
- Entrevista/pesquisa explora atitude, necessidade e contexto. Teste de usabilidade avalia desempenho de um design já existente. Não confunda os dois nem misture roteiros; se a pergunta que motivou o pedido for sobre desempenho de uma tela específica, sinalize que a skill `teste-de-usabilidade` pode ser mais adequada.
- Salve o roteiro (esqueleto reaproveitável), a síntese, os cards e as personas geradas como contexto do repositório, para reaproveitar/atualizar nas próximas rodadas, quando houver repositório (regra transversal). Persona é revisitada quando novo material mudar o padrão observado — não é artefato estático feito uma vez e esquecido.

## Formato da saída

```
## Framework/estrutura em uso
[Framework/estrutura detectada no repositório, ou nenhum — e em que formato/repositório de research o roteiro e a síntese abaixo foram registrados]

## Conflito com o repositório (se houver)
[O que já está documentado e onde diverge do que esta skill orienta]

## O que você perguntou
[Objetivo/decisão que orienta a entrevista/pesquisa]

## Roteiro
**Objetivo(s):** [...]
**Perfil do entrevistado:** [...]
**Tipo:** [ex.: semiestruturado]
**Entregáveis esperados:** [...]

### Bloco temático — [nome] (objetivo: [...])
[Perguntas abertas + acompanhamento previsto]

## Material reunido
[N arquivos/fontes — entrevistas, tickets, respostas de pesquisa, notas de call, planilhas. O que estava ilegível/vazio, se houver]

## Temas

### [Nome do tema] — apareceu em [N] de [total]
[Descrição em 2 a 3 frases]

Evidência:
- "[citação literal]" — [fonte, trecho/linha]

O que isso sugere: [leitura própria, marcada como tal]

## O que apareceu uma vez só
[Sinais fracos]

## Contradições
[Onde as fontes discordam entre si]

## O que este material NÃO responde
[Lacunas — o que precisaria de nova pesquisa]

## Cards de oportunidade (pendentes de decisão humana)
- [Card] — origem: [tema/evidência]. Aprovado? [sim/não/pendente]

## Personas (quando geradas)
[Se o usuário direcionou base/método/ferramenta própria, registre aqui seguindo a direção dele. Caso contrário, gere pelo critério padrão desta skill:]

### [Nome da persona] — [provisória/fundamentada]
**Retrato:** [papel/contexto em 1 a 2 frases]
**Objetivos:** [...]
**Comportamentos observados:** [...] — origem: [tema/evidência]
**Frustrações/necessidades:** [...] — origem: [tema/evidência]
**Cenário de uso:** [...]

## Pendências
[...]
```

## Cuidados

- Não imponha o esqueleto de roteiro e a estrutura de síntese desta skill quando o repositório usa outro formato de research — registre no dele; as exigências (objetivo antes do roteiro, fonte rastreável, decisão humana no card) permanecem, a forma se adapta.
- Não monte roteiro ou síntese sem antes confirmar qual decisão depende dela.
- Não conclua um tema antes de ler todo o material reunido.
- Não inclua afirmação sem fonte rastreável — ou marque explicitamente como hipótese.
- Não transforme sentimento relatado em número inventado.
- Não omita achado desconfortável só porque contradiz uma decisão já tomada.
- Não deixe de anonimizar participantes na saída.
- Não deixe um card de oportunidade entrar no backlog sozinho — decisão humana explícita sempre antes.
- Não confunda entrevista/pesquisa com teste de usabilidade — são objetivos diferentes.
- Não decida sozinha um conflito entre esta skill e o repositório.
- Não gere persona sem evidência real por trás (material analisado ou contexto do projeto), nem a partir só de dados demográficos.
- Não exija ter conduzido entrevista por esta skill antes de gerar persona — material enviado na conversa ou contexto do projeto já bastam.
- Não imponha o critério padrão de persona (Nielsen Norman Group) quando o usuário já indicou base, método ou ferramenta próprios — a recomendação vale só na ausência de direcionamento.
- Não gere muitas personas rasas — poucas e bem fundamentadas valem mais que muitas.
