---
name: teste-de-usabilidade
description: "Planejar, moderar ou consolidar teste de usabilidade com usuários reais e transformar achados em melhorias de backlog, sem tratar um teste isolado como fato."
---

# Teste de Usabilidade

> As menções a "(regra transversal)" abaixo remetem às regras transversais deste plugin, em `${CLAUDE_SKILL_DIR}/../../docs/REGRAS_TRANSVERSAIS.md` (o arquivo `docs/REGRAS_TRANSVERSAIS.md` na raiz do plugin, não no repositório em que você está trabalhando). Leia esse arquivo antes de aplicar a skill. Fora do Claude Code, as regras precisam ser fornecidas junto com esta skill.

## O princípio inegociável

Nenhum teste de usabilidade roda sem que a história de usuário com todos os critérios de aceite atendidos, a especificação e o protótipo navegável já validado nos fluxos estejam prontos — teste de usabilidade mede se o que já foi decidido funciona na prática, não é o lugar para decidir escopo ainda em aberto. E nenhum achado de teste vira item de backlog sozinho — sempre passa por decisão humana explícita antes.

## Como conduzir

**0. Verifique o repositório, o framework em uso e os pré-requisitos antes de montar qualquer roteiro.**
- **Framework em uso (verifique primeiro).** Identifique como o repositório de destino organiza produto e trabalhe no padrão dele (regra transversal — ver `${CLAUDE_SKILL_DIR}/../../docs/REGRAS_TRANSVERSAIS.md`, "Adaptação ao framework em uso"):
  - *O repositório já adota um framework ou estrutura própria* (um template de plano e de relatório de teste já adotado, uma convenção de research ops própria): registre no template que o framework já usa — a estrutura de roteiro e a consolidação por ponto de atrito desta skill são o conteúdo mínimo, não o formato obrigatório.
  - *Nenhum*: use os formatos desta skill como estão.
  A lógica desta skill — pré-requisitos prontos antes de testar, mais de um teste antes de consolidar, card só entra no backlog com decisão humana — continua valendo; o que se adapta é o formato do documento. Se a convenção do framework conflitar com o formato-padrão daqui, o framework em uso prevalece — sinalize a diferença, não decida sozinha.
- Confirme que a história de usuário com critérios de aceite atendidos (skill `modelo-para-user-story`), a especificação (skill `handoff-tecnico-e-especificacao`) e o protótipo validado (skill `prototipacao`) estão prontos. Se algo estiver faltando ou ainda em aberto, sinalize e volte à skill correspondente em vez de seguir com a lacuna.
- Se esta skill conflitar com o que já está documentado no repositório, sinalize e pergunte — nunca decida sozinha (regra transversal).

**1. Planeje o teste com IA — cenários e metas nascem do contexto já pronto, não do zero.**
- Cada cenário de teste mapeia a um critério de aceite ou a um cenário do fluxograma macro — incluindo cenários alternativos/exceção quando fizerem sentido para o que está sendo testado, não só o caminho feliz.
- Defina a meta de cada cenário (o que conta como sucesso) antes de rodar — sem meta clara, a consolidação depois vira julgamento subjetivo.

**2. Conduza o teste aplicando boas práticas de moderação.**
Prática de mercado (Nielsen Norman Group), a considerar na condução:
- Criar rapport e evitar a palavra "teste" para reduzir a ansiedade do participante.
- Avisar sobre observadores/gravação mesmo que isso já tenha sido dito no recrutamento.
- Dar tempo para o participante revisar o consentimento.
- Entregar as tarefas uma de cada vez, por escrito.
- Fazer perguntas abertas antes de perguntas específicas sobre a interface.
- Reservar um tempo final para perguntas dos observadores.

**3. Rode mais de um teste antes de consolidar — não trate um teste isolado como fato.**
Referência de mercado (NN/G): cerca de 5 participantes já revelam a maioria dos problemas de usabilidade de uma interface — use como orientação de quantos testes rodar antes de consolidar com confiança, sem virar regra rígida quando não for viável (público muito nichado, prazo curto). Quando a amostra ficar abaixo disso, sinalize essa limitação no resultado, em vez de apresentar uma confiança que os dados não sustentam.

**4. Consolide quantitativa e qualitativamente, por ponto de atrito.**
- Para cada ponto de atrito: o que atendeu, como atendeu, o que não conseguiu, e se a execução foi fácil ou difícil — nunca reduza a consolidação a "passou/não passou".
- Separe o quantitativo (taxa de sucesso por cenário, tempo, quando aplicável) do qualitativo (o que os participantes disseram/sentiram) — os dois se complementam, um não substitui o outro.

**5. Gere cards de possível melhoria — nunca direto para o backlog.**
A partir da consolidação, gere cards de possíveis melhorias do protótipo — mas eles não entram no backlog sozinhos; precisam de decisão/direcionamento humano explícito antes (regra transversal — IA sugere, uma pessoa aprova). Se aprovados, alimentam de volta a skill `priorizacao-de-backlog` como novos itens a considerar.

**6. Diferencie de entrevista/pesquisa e registre como contexto.**
- Teste de usabilidade avalia desempenho do design — o protótipo funciona na prática? A skill `entrevista-e-pesquisa` explora atitude e contexto — por que o usuário se comporta assim, o que ele precisa. Não confunda os dois nem misture roteiros; se o que surgir no teste for melhor respondido por entrevista, sinalize para a skill `entrevista-e-pesquisa` em vez de forçar a resposta aqui.
- Salve o roteiro, a consolidação e os cards gerados como contexto do repositório, para reaproveitar/atualizar nas próximas rodadas (regra transversal).

## Formato da saída

```
## Framework/estrutura em uso
[Framework/estrutura detectada no repositório, ou nenhum — e em que template de teste o roteiro e a consolidação abaixo foram registrados]

## Conflito com o repositório (se houver)
[O que já está documentado e onde diverge do que esta skill orienta]

## Pré-requisitos confirmados
[US + critérios de aceite / especificação / protótipo validado — ou o que ainda falta]

## Roteiro do teste

### Cenário [nome] — meta: [o que conta como sucesso]
[Tarefa entregue por escrito; critério de aceite/fluxo que originou este cenário]

## Participantes
[Quantidade, perfil; se abaixo de ~5, sinalizar limitação de amostra]

## Consolidação por ponto de atrito
| Ponto de atrito | O que atendeu | Como atendeu | O que não conseguiu | Execução (fácil/difícil) |
|---|---|---|---|---|
| [...] | [...] | [...] | [...] | [...] |

**Quantitativo:** [taxa de sucesso, tempo, etc., quando aplicável]
**Qualitativo:** [o que os participantes disseram/sentiram]

## Cards de possível melhoria (pendentes de decisão humana)
- [Card] — origem: [ponto de atrito]. Aprovado? [sim/não/pendente]

## Pendências
[O que falta para fechar o ciclo — inclusive se algo deveria ir para entrevista/pesquisa]
```

## Cuidados

- Não imponha os formatos de roteiro e consolidação desta skill quando o repositório usa outro template de teste — registre no dele; as exigências (pré-requisitos prontos, mais de um teste, decisão humana no card) permanecem, a forma se adapta.
- Não rode teste sem história de usuário com critérios de aceite atendidos, especificação e protótipo validado prontos — volte à skill correspondente se algo faltar.
- Não trate um teste isolado como fato — rode mais de um antes de consolidar, ou sinalize a limitação se não for viável.
- Não consolide achado só como "passou/não passou" — registre o que atendeu, como, o que não conseguiu e a dificuldade de execução.
- Não deixe um card de melhoria entrar no backlog sozinho — decisão humana explícita sempre antes.
- Não confunda teste de usabilidade com entrevista/pesquisa — são objetivos diferentes.
- Não pule o aviso de observadores/gravação, mesmo que já tenha sido dito no recrutamento.
- Não decida sozinha um conflito entre esta skill e o repositório.
