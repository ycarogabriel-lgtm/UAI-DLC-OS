---
name: priorizacao-de-backlog
description: "Priorizar backlog: recomendar e aplicar Impacto×Esforço, MoSCoW, RGT, RICE ou WSJF para decidir o que entra primeiro, com aprovação humana do método e do resultado."
---

# Priorização de Backlog

Priorizar não é ordenar por urgência de quem pediu por último. É aplicar um método consistente — e disponível para auditoria — que qualquer pessoa da equipe consiga entender e questionar depois.

> As menções a "(regra transversal)" abaixo remetem às regras transversais deste plugin, em `${CLAUDE_SKILL_DIR}/../../docs/REGRAS_TRANSVERSAIS.md` (o arquivo `docs/REGRAS_TRANSVERSAIS.md` na raiz do plugin, não no repositório em que você está trabalhando): aprovação humana antes da vigência, e sinalização antes de resolver conflito. Leia esse arquivo antes de aplicar a skill. Fora do Claude Code, as regras precisam ser fornecidas junto com esta skill.

## O princípio inegociável

A IA recomenda o método e pode sugerir os inputs (score de impacto, esforço, classificação R/G/T, etc.). **Quem decide aplicar, e quem aprova o resultado final, é sempre uma pessoa.** Nenhuma priorização gerada por esta skill entra em vigor sem aprovação explícita (regra transversal).

## Como conduzir

**0. Verifique o repositório e o framework em uso antes de recomendar.**
Esta skill roda em conjunto com o repositório do projeto/cliente, que pode já ter um método de priorização definido ou regras próprias. Se o que esta skill orienta conflitar com o que está documentado no repositório, **não decida sozinha** — sinalize o conflito para o usuário e peça para ele escolher qual seguir (regra transversal).

- **Framework em uso (verifique primeiro).** Identifique como o repositório de destino organiza produto e trabalhe no padrão dele (regra transversal — ver `${CLAUDE_SKILL_DIR}/../../docs/REGRAS_TRANSVERSAIS.md`, "Adaptação ao framework em uso"):
  - *O repositório já adota um framework ou estrutura própria* (Scrum/SAFe/Shape Up, ou um board/processo próprio de priorização): os métodos e nomes desta skill são só o padrão — mapeie para o equivalente do framework (ex.: o campo de prioridade ou o método já adotado no board) e registre a priorização no formato dele.
  - *Nenhum*: use os métodos e formatos desta skill como estão.
  A lógica de priorização desta skill continua valendo; o que se adapta é como registrar e nomear. Se a convenção do framework conflitar com o formato-padrão daqui, o framework em uso prevalece — sinalize a diferença, não decida sozinha.

**0.1 Reconheça itens que chegam de fora do fluxo normal de backlog.**
Cards de melhoria/oportunidade aprovados pelo usuário na skill `teste-de-usabilidade` ou em `entrevista-e-pesquisa` entram aqui como novos itens a priorizar — trate-os como qualquer outro item do backlog, não como uma categoria à parte.

**1. Apresente o contexto e recomende, com justificativa.**
Olhe o contexto disponível (tipo de projeto, se é sistema novo ou existente, volume de itens, prazo) e responda nesse formato: "Temos disponíveis os métodos [lista]. Pelo contexto que vejo aqui, o mais indicado é [X], porque [justificativa breve]. Quer seguir com ele ou prefere outro?" Guia de recomendação:
- Projeto novo, poucos dados históricos, decisões mais estratégicas → Matriz de Impacto x Esforço.
- Backlog grande, prazo apertado, necessidade de comunicar simples/não-simples → MoSCoW.
- Produto/sistema já existente, portfólio a balancear entre manutenção e inovação → RGT.
- Muitos itens concorrendo por atenção e o time quer um score único, comparável e com grau de confiança embutido → RICE.
- Time já opera em Agile em escala e precisa justificar urgência por custo de atraso, não só valor → WSJF.
- Se o usuário já souber qual método quer, pule a recomendação e vá direto para os pré-requisitos daquele método.

**2. Se o usuário pedir um método de mercado que não está nesta lista:**
Pesquise as boas práticas desse método específico em fontes confiáveis (não invente critérios). Volte para o usuário explicando o método encontrado e **solicitando os critérios/insumos necessários** para aplicá-lo — já que ele não está documentado internamente e você não tem esses dados de antemão.

**3. Aplique o método escolhido, respeitando as regras de cada um.**

Antes de pedir estimativa de esforço ao usuário (em qualquer método abaixo que use esforço/tamanho do job): confira se o item já tem estimativa de horas na planilha de composição de esforço do projeto — a planilha de horas que o projeto já mantém (uma CBS, um dimensionamento, o que o projeto usar), quando existir. Se tiver, use esse dado como esforço — convertendo para a escala que o método pede (ex.: pessoa-mês no RICE, tamanho relativo no WSJF) — em vez de pedir para o usuário estimar de novo. Só peça estimativa nova quando o item ainda não estiver nessa planilha.

*Matriz de Impacto x Esforço*
- Pré-requisito: score de impacto (negócio) e esforço (fazer) por item — esforço vem da planilha de esforço do projeto quando disponível (ver regra acima).
- A IA pode sugerir o score de impacto, mas só se solicitada — e o score final é sempre aprovado por uma pessoa responsável, nunca só pela IA.
- Priorize alto impacto / baixo esforço; sinalize como candidato a descartar ou adiar o que cair em baixo impacto / alto esforço — mas nunca remova sozinha, sempre proponha.

*MoSCoW*
- Classifique em Must / Should / Could / Won't Have.
- Regra dura: itens "Must Have" não podem ocupar mais que 60% do tempo/esforço total estimado do projeto. Se ultrapassar, avise e peça para revisar antes de fechar.
- Exija que o "Won't Have" também seja preenchido explicitamente, não só o que entra.

*RGT (Run, Grow, Transform)*
- A IA sugere a classificação R/G/T por item; o usuário aprova.
- Indicado só para sistemas/produtos já existentes.
- Alerta opcional: se a distribuição do portfólio fugir muito de ~30–50% Run, 30–50% Grow, 10–25% Transform, sinalize como observação — nunca como bloqueio.

*RICE (Reach, Impact, Confidence, Effort)*
- Pré-requisito: estimativa de alcance (quantas pessoas/período), impacto (escala qualitativa, ex. 0,25 a 3), confiança na estimativa (%) e esforço (pessoa-mês ou similar) por item — esforço vem da planilha de esforço do projeto quando disponível (ver regra acima).
- Score = (Alcance × Impacto × Confiança) / Esforço. A IA pode calcular o score a partir dos inputs, mas os inputs em si vêm do usuário ou são sugeridos e aprovados por ele — nunca estimados sozinhos pela IA sem aviso.
- Útil quando o time quer comparar itens muito diferentes entre si num único número; não substitui julgamento de negócio, é apoio a ele.

*WSJF (Weighted Shortest Job First)*
- Pré-requisito: valor de negócio, criticidade de tempo e redução de risco/viabilização de oportunidade (os três compõem o "custo do atraso"), mais o tamanho estimado do job — tamanho do job vem da planilha de esforço do projeto quando disponível (ver regra acima).
- Score = Custo do Atraso / Tamanho do Job. Itens com maior score vêm primeiro — jobs menores com alto custo de atraso saem na frente de jobs grandes com o mesmo valor.
- Mais indicado quando o cliente já opera em Agile em escala (múltiplos times/trens) e precisa justificar urgência de forma explícita.

**4. Use um score quantitativo interno como apoio opcional, se o usuário pedir.**
Se o projeto mantém uma planilha de priorização quantitativa (SCORE → Índice de Complexidade → Story Points em Fibonacci → alocação em sprint), ofereça-a apenas quando o usuário quiser um método mais numérico — nunca a imponha por padrão, e nunca gere números "por conta própria" quando os dados de entrada não foram fornecidos.

**5. Registre a decisão.**
Todo resultado de priorização final deve deixar claro: método usado (e se foi recomendação da IA ou escolha do usuário), quem aprovou, data, e o que ficou de fora (no MoSCoW, o "Won't Have"; nos outros métodos, os itens de menor prioridade/score).

**6. Salve o método escolhido como contexto do repositório, se houver repositório.**
Quando esta skill rodar em um projeto que tem repositório, grave o método aprovado (e os parâmetros usados, como a distribuição-alvo do RGT ou os pesos do WSJF) como contexto do projeto. Da próxima vez que o backlog desse mesmo projeto precisar de priorização, **reaplique o método já salvo em vez de recomendar do zero** — só volte a recomendar/perguntar se o usuário pedir explicitamente para reconsiderar o método (regra transversal).

## Formato da saída

```
## Framework/estrutura em uso
[Framework/estrutura detectada no repositório, ou nenhum — e como a priorização abaixo foi mapeada para ele]

## Conflito com o repositório (se houver)
[O que o repositório já define e onde isso diverge do que esta skill orienta — só aparece se houver conflito real]

## Recomendação
[Se já houver método salvo no repositório do projeto: informe que está reaplicando o método já definido, e qual é. Caso contrário: métodos documentados disponíveis + qual foi recomendado e por quê — ou método de mercado pesquisado, se aplicável]

## Método usado
[Nome do método efetivamente escolhido pelo usuário]

## Priorização proposta
[Lista dos itens com a classificação/score de cada um, conforme o método]

## Pontos de atenção
[Ex.: Must Have acima de 60%; distribuição RGT desbalanceada; item sem score informado]

## Aguardando aprovação
[Quem precisa aprovar antes de esta priorização valer]
```

## Cuidados

- Não imponha os métodos e nomes desta skill quando o repositório usa outro framework — mapeie para o equivalente e registre no padrão dele; a lógica de priorização permanece, a forma se adapta.
- Não decida sozinha um conflito entre esta skill e o repositório.
- Não estime score de impacto, alcance ou custo de atraso sozinha quando ninguém informou — pergunte a quem tem a visão de negócio.
- Não deixe o "Won't Have" implícito no MoSCoW.
- Não aplique RGT em projeto novo sem sistema existente para classificar.
- Não gere números de uma planilha de score sem os dados de entrada reais.
- Ao receber pedido de método de mercado não documentado, não aplique de memória sem pesquisar — e não aplique sem antes pedir os critérios necessários ao usuário.
- Nenhuma priorização é definitiva sem aprovação humana registrada.
- Havendo repositório com método já salvo, não recomende outro método do zero a cada nova priorização — reaplique o salvo, e só reabra a escolha se o usuário pedir para reconsiderar.
- Antes de pedir estimativa de esforço/tamanho do job ao usuário, confira a planilha de esforço do repositório — não peça de novo o que já está estimado lá.
