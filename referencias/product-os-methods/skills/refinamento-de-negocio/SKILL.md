---
name: refinamento-de-negocio
description: "Refinar decisão ou regra de negócio: esclarecer decisão, resolver conflito entre reuniões e definir critérios de aceite, com fonte única da verdade e pergunta em vez de suposição."
---

# Refinamento de Negócio

> As menções a "(regra transversal)" abaixo remetem às regras transversais deste plugin, em `${CLAUDE_SKILL_DIR}/../../docs/REGRAS_TRANSVERSAIS.md` (o arquivo `docs/REGRAS_TRANSVERSAIS.md` na raiz do plugin, não no repositório em que você está trabalhando). Leia esse arquivo antes de aplicar a skill. Fora do Claude Code, as regras precisam ser fornecidas junto com esta skill.

## O princípio inegociável

Quando há divergência de informação ou decisão pouco clara, a IA questiona — nunca assume qual versão vale. Toda decisão de negócio precisa ficar rastreável: quem decidiu, quando, e onde isso está registrado.

## Como conduzir

**0. Verifique o repositório, o framework em uso e o backlog priorizado antes de refinar.**
- **Framework em uso (verifique primeiro).** Identifique como o repositório de destino organiza produto e trabalhe no padrão dele (regra transversal — ver `${CLAUDE_SKILL_DIR}/../../docs/REGRAS_TRANSVERSAIS.md`, "Adaptação ao framework em uso"):
  - *O repositório já adota um framework ou estrutura própria* (Scrum/SAFe/Shape Up, ou um processo próprio de refinamento/decisão): os formatos desta skill são só o padrão — mapeie para o equivalente do framework (ex.: o formato de critério de aceite e o SSOT que o framework já define) e registre nele.
  - *Nenhum*: use o método e os formatos desta skill como estão.
  A lógica de refinamento desta skill continua valendo; o que se adapta é como registrar e nomear. Se a convenção do framework conflitar com o formato-padrão daqui, o framework em uso prevalece — sinalize a diferença, não decida sozinha.
- O backlog priorizado (product backlog building) é insumo direto — refine itens a partir do contexto de negócio já organizado no backlog, não do zero.
- Se o repositório já tiver um arquivo/fonte definida como single source of truth (SSOT) para decisões de negócio, use-o como referência. Se esta skill conflitar com o que já está documentado no repositório, sinalize e pergunte — nunca decida sozinha (regra transversal).

**1. Identifique e trate divergência antes de refinar.**
- Se houver mais de uma versão da mesma decisão (ex.: decisão falada em reunião que não ficou clara na conclusão, ou iniciativas divergentes/conflitantes), não escolha uma versão sozinha — pergunte explicitamente.
- Exemplos de como perguntar: "Fulano decidiu X em 10/09 — deseja mesmo seguir com essa alteração?"; "Isso diverge do que foi decidido antes — deseja prosseguir mesmo assim?"

**2. Estabeleça o fluxo decisório e o SSOT.**
- Se houver mais de um PM/PD ou handoff no meio do processo, confirme com o usuário como fica o processo decisório e qual arquivo é considerado a fonte única da verdade — não assuma isso sozinha.
- Uma vez definido, salve essa referência (qual arquivo é o SSOT) como contexto do repositório, para reaplicar nas próximas vezes — só reabra se o usuário pedir para reconsiderar (regra transversal).

**3. Escreva critérios de aceite no formato Given-When-Then.**
- Linguagem objetiva e testável. Evite termos vagos como "de forma eficaz" ou "de forma completa".
- 3 a 5 critérios de aceite específicos e mensuráveis por item, cobrindo tanto o caminho esperado quanto os casos de borda relevantes.

**4. Registre a decisão.**
- Toda decisão de negócio final registra: o que foi decidido, quem decidiu, quando, e onde está documentado (o SSOT).
- Esse registro alimenta a skill `modelo-para-user-story` — a US nasce do refinamento já resolvido, não de uma divergência em aberto.

## Formato da saída

```
## Framework/estrutura em uso
[Framework/estrutura detectada no repositório, ou nenhum — e como o registro abaixo foi mapeado para ele]

## Conflito com o repositório (se houver)
[O que já está documentado e onde diverge do que esta skill orienta]

## Divergência identificada (se houver)
[Versões conflitantes encontradas + pergunta feita ao usuário + resposta obtida]

## SSOT confirmado
[Qual arquivo/fonte é a fonte única da verdade para este item, e desde quando]

## Critérios de aceite (Given-When-Then)
1. Given [contexto] When [ação] Then [resultado esperado]
[3 a 5 critérios, cobrindo caminho esperado + casos de borda relevantes]

## Decisão registrada
[O que foi decidido; quem decidiu; quando; onde está documentado]
```

## Cuidados

- Não imponha os formatos desta skill quando o repositório usa outro framework — mapeie para o equivalente e registre no padrão dele; a lógica de refinamento permanece, a forma se adapta.
- Não escolha sozinha entre versões divergentes de uma decisão — sempre pergunte antes de seguir.
- Não assuma qual arquivo é o SSOT sem confirmar com o usuário.
- Não aceite critério de aceite vago ("de forma eficaz/completa") — exija linguagem testável.
- Não decida sozinha um conflito entre esta skill e o repositório.
- Não refine um item sem o contexto do backlog priorizado já organizado.
