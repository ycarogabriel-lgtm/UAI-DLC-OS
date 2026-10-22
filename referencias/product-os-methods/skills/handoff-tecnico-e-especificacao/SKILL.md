---
name: handoff-tecnico-e-especificacao
description: "Montar handoff técnico ou especificação para dev: status do MVP, backlog por onda, pendências e, sob demanda, detalhe de tela ou componente."
---

# Handoff Técnico e Especificação

> As menções a "(regra transversal)" abaixo remetem às regras transversais deste plugin, em `${CLAUDE_SKILL_DIR}/../../docs/REGRAS_TRANSVERSAIS.md` (o arquivo `docs/REGRAS_TRANSVERSAIS.md` na raiz do plugin, não no repositório em que você está trabalhando). Leia esse arquivo antes de aplicar a skill. Fora do Claude Code, as regras precisam ser fornecidas junto com esta skill.

## O princípio inegociável

O handoff nunca inventa dado. Todo conteúdo vem do que já foi decidido a montante — backlog priorizado, roadmap por ondas, protótipo já validado, estimativa de esforço do projeto, critérios de aceite. O que ainda não foi confirmado fica registrado como pendência real, nunca preenchido com suposição — e o progresso geral é sempre calculado a partir do backlog, nunca escrito à mão.

## Como conduzir

**0. Verifique o repositório, o framework em uso e o que já foi decidido a montante antes de montar o handoff.**
- **Framework em uso (verifique primeiro).** Identifique como o repositório de destino organiza produto e trabalhe no padrão dele (regra transversal — ver `${CLAUDE_SKILL_DIR}/../../docs/REGRAS_TRANSVERSAIS.md`, "Adaptação ao framework em uso"):
  - *O repositório já adota um framework ou estrutura própria* (Scrum/SAFe/Shape Up, ou um formato de handoff, ticket ou dev-doc já adotado pelo time técnico): "onda" e a estrutura deste handoff são só o padrão — entregue no formato de handoff ou de ticket que o time técnico já usa (ex.: onda → sprint/ciclo; épico → o termo do framework).
  - *Nenhum*: use a estrutura desta skill como está.
  A lógica desta skill — nada de dado inventado, progresso calculado do backlog, pendência real registrada, tom distinto do material de cliente — continua valendo; o que se adapta são os nomes e o formato do documento. Se a convenção do framework conflitar com o formato-padrão daqui, o framework em uso prevalece — sinalize a diferença, não decida sozinha.
- Handoff consome decisões já tomadas — backlog priorizado (skill `priorizacao-de-backlog`), roadmap por ondas (skill `construcao-alinhamento-roadmap`), protótipo validado (skill `prototipacao`), estimativa de esforço do projeto, critérios de aceite (skills `refinamento-de-negocio` / `modelo-para-user-story`) — não as reabre nem as reinterpreta.
- Se esta skill conflitar com o que já está documentado no repositório, sinalize e pergunte — nunca decida sozinha (regra transversal).

**1. Reconheça o que já é gerado automaticamente hoje — não recrie do zero.**
Se o projeto já tem um fluxo automático de geração de especificação a partir dos itens do backlog e do protótipo navegável, reaproveite esse fluxo como base; quando ele já cobrir o que foi pedido, não gere um documento paralelo redundante — complemente só o que falta.

**2. Monte o handoff em nível de projeto, com o conteúdo obrigatório abaixo.**
A lógica está descrita por completo aqui — não depende de nenhuma skill externa instalada. **Se o ambiente já tiver uma skill dedicada de dashboard/handoff de projeto**, prefira usá-la para gerar/atualizar o documento (versão de referência, mantida à parte); na ausência dela, aplique a lógica a seguir diretamente:

- **Progresso geral do MVP** calculado dinamicamente a partir do backlog — nunca hardcoded ou estimado à mão. Se o backlog mudar, o progresso muda junto, sem edição manual do número.
- **Diretório de artefatos** por ferramenta de origem (ex.: Mural, Figma, SharePoint, PDF), com link de abertura para cada um.
- **Estimativa de desenvolvimento**: link para a planilha de esforço já existente — reaproveite o dado, mesma lógica de reuso da priorização/roadmap, nunca peça para reestimar aqui.
- **Backlog priorizado por onda** (reaproveitando a estrutura de ondas já definida no roadmap, não uma divisão nova), com status por épico — pronto / em revisão / bloqueado. Nunca invente um status não confirmado; se não houver confirmação, registre como pendência.
- **Pendências conhecidas**: seção que existe só enquanto houver pendência real. Quando a última for resolvida, remova a seção inteira (não só o conteúdo) — uma seção com título e lista vazia é sinal de documento desatualizado.
- **Paleta e tom deliberadamente diferentes** do material voltado ao cliente (ex.: a visão executiva do roadmap, ou o relatório de ROI/valor) — a distinção visual existe para não confundir o documento interno de handoff com o que vai para o cliente.

**3. Gere o nível de página/elemento só sob demanda do dev, com os mesmos princípios aplicados ao detalhe.**
Não é o padrão de todo handoff — gere quando o time técnico pedir mais granularidade. Cobre: especificações de dimensão, espaçamento, cor e nomenclatura de componentes (herdadas da identidade visual, nunca reinventadas aqui); documentação de todos os estados, animações e transições; anotação do "porquê" de cada decisão, não só o "o quê"; dependências técnicas explícitas.

**4. Trate a estrutura interna vigente como baseline — não como camisa de força.**
A estrutura do handoff já em uso serve de baseline confiável, mas a apresentação visual pode evoluir. Mudar o padrão visual/estrutural vigente é uma decisão deliberada a confirmar com o usuário, não uma personalização silenciosa feita "de passagem" enquanto se monta um handoff pontual.

**5. Aplique boas práticas de complemento, quando fizer sentido para o contexto.**
Manter um design system compartilhado como fonte única entre design e dev reduz retrabalho; reuniões rápidas de alinhamento 2 a 3 vezes por semana ajudam a resolver dúvidas antes que virem gargalo. São sugestões de processo, não itens obrigatórios do documento.

**6. Registre o handoff como contexto e mantenha atualizado.**
- Salve o handoff (nível de projeto e, se gerado, de elemento) como contexto do repositório, atualizando-o conforme o backlog e o protótipo evoluem — não é um documento estático gerado uma vez.
- O handoff validado alimenta a skill `teste-de-usabilidade` — não avance para teste com pendências de handoff ainda em aberto sem sinalizar isso.

## Formato da saída

```
## Framework/estrutura em uso
[Framework/estrutura detectada no repositório, ou nenhum — e em que formato de handoff/ticket o conteúdo abaixo foi entregue]

## Conflito com o repositório (se houver)
[O que já está documentado e onde diverge do que esta skill orienta]

## O que já vem do fluxo automático (backlog + protótipo)
[O que foi reaproveitado sem recriar]

## Handoff — nível de projeto

### Progresso geral do MVP
[Calculado a partir do backlog — nunca hardcoded]

### Diretório de artefatos
| Ferramenta | Artefato | Link |
|---|---|---|
| [Mural/Figma/SharePoint/PDF] | [...] | [...] |

### Estimativa de desenvolvimento
[Link para a planilha de esforço existente]

### Backlog priorizado por onda
| Onda | Épico | Status | Observação |
|---|---|---|---|
| [...] | [...] | [pronto/em revisão/bloqueado] | [...] |

### Pendências conhecidas
[Só existe se houver pendência real — remover a seção inteira quando não sobrar nenhuma]

## Handoff — nível de página/elemento (só sob demanda)
[Dimensão/espaçamento/cor, tipografia e nomenclatura (herdadas da identidade visual), estados/animações/transições, o "porquê" da decisão, dependências técnicas]

## Pendências para avançar ao teste de usabilidade
[...]
```

## Cuidados

- Não imponha a estrutura e o vocabulário deste handoff quando o time técnico usa outro formato/framework — entregue no dele; as exigências (dado não inventado, progresso do backlog, pendência real) permanecem, a forma se adapta.
- Não invente status de épico, link de planilha de esforço, ou critério de aceite não confirmado — registre como pendência real.
- Não escreva o progresso geral à mão — sempre calculado a partir do backlog.
- Não use a mesma paleta/tom do material voltado ao cliente.
- Não deixe a seção de pendências com título e lista vazia — remova a seção inteira quando resolvida.
- Não recrie do zero o que já é gerado automaticamente pelo fluxo backlog + protótipo.
- Não gere o nível de página/elemento por padrão — só sob demanda do dev.
- Não mude o padrão visual/estrutural vigente do handoff "de passagem" — trate como decisão deliberada, sinalizada ao usuário.
- Não decida sozinha um conflito entre esta skill e o repositório.
