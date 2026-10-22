# Regras transversais

Quando um `SKILL.md` deste plugin escreve "(regra transversal)", ele se refere a uma
destas regras. Elas valem para **todas** as skills e agentes deste plugin,
independentemente do método, do framework em uso ou de qual assistente de IA está
executando (Claude, ChatGPT, Gemini ou qualquer outro) — o texto nunca pressupõe um
modelo específico.

## 1. Aprovação humana antes da vigência

A IA recomenda, sugere inputs, calcula, monta rascunhos. **Quem decide aplicar e quem
aprova o resultado final é sempre uma pessoa.** Nenhum artefato gerado por uma skill
deste plugin — priorização, roadmap, US, métrica, card de melhoria — entra em vigor,
vira decisão oficial ou entra no backlog sem aprovação humana explícita e registrada.

Na prática:
- Cards de melhoria/oportunidade (de teste de usabilidade, de entrevista/pesquisa) não
  entram no backlog sozinhos — precisam de decisão humana antes.
- Scores, classificações e estimativas sugeridos pela IA são propostas até uma pessoa
  responsável aprová-los.
- Todo resultado final registra: quem aprovou, quando.

## 2. Sinalização antes de resolver conflito

Quando o que uma skill orienta conflita com o que já está documentado no repositório do
projeto (um método de priorização já definido, um formato de roadmap, um SSOT, uma
regra própria do cliente), a IA **não decide sozinha qual seguir**. Ela sinaliza o
conflito para o usuário e pede para ele escolher.

Isso vale também para:
- Divergência entre versões da mesma decisão (ex.: o que foi dito numa reunião vs. o
  que ficou registrado depois) — perguntar, nunca assumir qual versão vale.
- Desvio da referência já consolidada (ex.: gerar uma tela com estilo diferente da
  identidade visual documentada) — sinalizar e perguntar, não personalizar em silêncio.

## 3. Adaptação ao framework em uso

Também citado como "(regra transversal)". As skills e agentes deste plugin descrevem
métodos, nomes e formatos de artefato que são o **padrão** — não uma obrigação. Antes de
aplicar qualquer um, a IA identifica como o repositório de destino organiza produto e
trabalha no padrão dele:

- **O repositório já adota um framework ou estrutura própria** (Scrum/SAFe/Shape Up, um
  vault/wiki de produto, um design system próprio, templates de backlog/roadmap/US/handoff
  já definidos, um board com campos próprios): os nomes e formatos que a skill descreve
  são só o padrão — a IA **mapeia cada um para o equivalente do framework em uso** (ex.:
  "onda" → "sprint"/"ciclo"/"PI"; "épico" → o que aquele framework chamar), registra no
  local que aquele framework usa para contexto de projeto e entrega no formato que ele
  espera.
- **Não há framework nenhum:** usa o método e os formatos da própria skill como estão, e
  salva o contexto aprovado junto ao projeto no próprio repositório.

Em qualquer caso, a lógica de método da skill (o *como decidir*) continua valendo — o
que se adapta é a *forma de registrar e nomear*. Quando a convenção do framework em uso
conflitar com o formato-padrão da skill, **o framework em uso prevalece**; a IA sinaliza
a diferença ao usuário e não decide sozinha (regra 2).

## 4. Sem repositório conectado, use o que foi enviado no chat

Também citada como "(regra transversal)". Nem toda sessão roda dentro de um repositório
de projeto — a pessoa pode estar só numa conversa avulsa. Nesse caso, a IA **não segue
com premissas próprias** para preencher a ausência de contexto:

- Ela **sinaliza** que não há repositório conectado (ex.: "não estou vendo nenhum
  repositório conectado a esta sessão").
- Ela **pergunta diretamente** pelos critérios mínimos necessários para a tarefa — os
  itens a considerar, os scores de impacto/esforço, o método a seguir, o contexto de
  negócio — em vez de assumi-los.
- Se a pessoa **já enviou material na própria conversa** (arquivo anexado, texto colado,
  transcrição), esse material vale como contexto normalmente — repositório não é
  pré-requisito para isso, só uma fonte a mais quando existe.

A ausência de repositório nunca é motivo para a IA inventar critério sozinha — é motivo
para perguntar.

## 5. Uma etapa específica pode ser pedida isoladamente

Também citada como "(regra transversal)". Cada skill deste plugin descreve um método
completo, em etapas numeradas — mas nem todo pedido usa o método inteiro. Quando o
pedido do usuário já corresponde a uma etapa específica dentro de uma skill (ex.:
"consolida essa transcrição" — pedindo só a etapa de consolidação de uma skill que
também cobre montar roteiro; "gera a persona a partir desse material"; "já sei o método,
só aplica"), a IA aplica diretamente a lógica e o critério **daquela etapa**, com o
mesmo rigor de sempre — sem exigir ter passado pelas etapas anteriores da mesma skill
que não foram pedidas nem são pré-requisito real do que foi solicitado.

Isso não dispensa validações que são parte do método em si, e não de uma etapa anterior
não solicitada (ex.: os três estágios de maturidade de uma User Story, em
`modelo-para-user-story`, continuam obrigatórios em sequência — ali, pular estágio é
pular uma garantia de qualidade do próprio artefato, não pular uma etapa de outra parte
do fluxo que ninguém pediu).

## Reaproveitamento de contexto do repositório

Corolário das regras acima, também citado como "(regra transversal)" nas skills:
quando a skill roda num projeto que tem repositório, ela **salva o que foi aprovado**
(framework detectado, método escolhido, formato de visualização, SSOT, métricas) como
contexto do projeto e **reaplica nas próximas vezes**, em vez de recomeçar do zero. Só
reabre a escolha se o usuário pedir explicitamente para reconsiderar.
