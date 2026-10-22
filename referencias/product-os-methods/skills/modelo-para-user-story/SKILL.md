---
name: modelo-para-user-story
description: "Escrever, ajustar ou revisar user story: template completo com critérios BDD, RF/RNF, regras de negócio, DoR e DoD, incluindo considerações do tech lead."
---

# Modelo para User Story (US)

> As menções a "(regra transversal)" abaixo remetem às regras transversais deste plugin, em `${CLAUDE_SKILL_DIR}/../../docs/REGRAS_TRANSVERSAIS.md` (o arquivo `docs/REGRAS_TRANSVERSAIS.md` na raiz do plugin, não no repositório em que você está trabalhando). Leia esse arquivo antes de aplicar a skill. Fora do Claude Code, as regras precisam ser fornecidas junto com esta skill.

## O princípio inegociável

Nenhuma história entra em sprint sem atender à Definition of Ready (DoR), e nenhuma é dada como concluída sem atender à Definition of Done (DoD). O template completo é sempre o destino final — a história pode nascer como rascunho simples, mas não fecha sem passar por todas as seções.

## Como conduzir

**0. Parta do refinamento de negócio já resolvido, do repositório e do framework em uso.**
- **Framework em uso (verifique primeiro).** Identifique como o repositório de destino organiza produto e trabalhe no padrão dele (regra transversal — ver `${CLAUDE_SKILL_DIR}/../../docs/REGRAS_TRANSVERSAIS.md`, "Adaptação ao framework em uso"):
  - *O repositório já adota um framework ou estrutura própria* (Scrum/SAFe/Shape Up, ou um template de história/issue próprio): o template completo abaixo é o destino de qualidade, mas o **formato de entrega** segue o do framework — mapeie as seções (descrição, critérios de aceite, RF/RNF, DoR, DoD) para os campos do template de história ou issue que o framework já usa.
  - *Nenhum*: use o template desta skill como está.
  As seções de qualidade que a skill exige (cláusula de benefício, critérios BDD, RNF, DoR, DoD) continuam obrigatórias; o que se adapta é onde cada uma é registrada. Se a convenção do framework conflitar com o formato-padrão daqui, o framework em uso prevalece — sinalize a diferença, não decida sozinha.
- Não escreva US a partir de uma decisão de negócio ainda divergente ou sem SSOT confirmado — volte à skill `refinamento-de-negocio` se isso não estiver resolvido.
- Use o template de História de Usuário completa descrito abaixo. Se o repositório definir um template diferente já em uso, reaproveite o do repositório e sinalize o conflito para o usuário escolher (regra transversal) — não recrie outro modelo por conta própria.

**1. Siga a história evolutiva — três estágios, nunca pule etapa.**
- *Rascunho inicial*: descrição simples, no formato clássico. Aceitável como ponto de partida, nunca como versão final.
- *Refinada*: descrição detalhada após discovery — nasce do refinamento de negócio já resolvido.
- *Pronta para desenvolvimento*: o template completo — descrição clássica + critérios de aceite (BDD) + RFs + RNFs + regras de negócio + fluxos de exceção. Só neste estágio a história pode entrar na Definition of Ready.

Gere a história de acordo com a profundidade de contexto disponível (uma reunião isolada, uma transcrição, o repositório) e pontue o estágio atingido pelos critérios realmente atendidos — nunca marque um estágio maduro sem o critério correspondente cumprido. **Com repositório:** registre e organize a história pelo estágio de maturidade na estrutura do projeto, para reaproveitar e atualizar depois (regra transversal — reaproveitamento de contexto do repositório). **Sem repositório:** devolva o estágio atual e o que falta para amadurecer diretamente nesta conversa, para a pessoa completar o entendimento e decidir os próximos passos (regra transversal 4) — a lógica de avaliação é a mesma nos dois casos; muda só para onde o resultado vai.

**2. Preencha o template completo, seção por seção.**
- **Descrição (formato clássico)**: Como [tipo de usuário], quero [objetivo] para [benefício esperado]. A cláusula de benefício é obrigatória — nunca só o objetivo.
- **Critérios de Aceite (BDD — Given/When/Then)**: herdados do refinamento de negócio — "Dado que [contexto], quando [ação], então [resultado esperado]." Múltiplos critérios, cobrindo caminho esperado e casos de borda.
- **Requisitos Funcionais (RF)**: "O sistema deve [função]" — numerados.
- **Requisitos Não Funcionais (RNF)**: "O sistema deve [restrição de desempenho/tempo de resposta/segurança/usabilidade]" — numerados. Não deixe RNF de fora só porque ninguém mencionou — pergunte explicitamente sobre desempenho, segurança e usabilidade quando não aparecerem.
- **Regras de Negócio**: alinhadas ao que foi decidido no refinamento.
- **Fluxos de exceção**: o que acontece quando algo foge do caminho esperado — exigido no estágio "pronta para desenvolvimento".

**3. Rode a Definition of Ready (DoR) antes de considerar a história elegível para sprint.**
Descrição clara no formato clássico; critérios de aceite definidos; RFs e RNFs identificados; regras de negócio levantadas; dependências mapeadas (se houver dependência explícita de outro time, mapeie — não bloqueia sozinho, mas precisa estar visível, ver nota do INVEST abaixo); estimativa do time realizada (reaproveite da planilha de esforço/priorização quando já existir, ou peça nova estimativa). **Uma história só entra na conta de capacidade do roadmap (skill `construcao-alinhamento-roadmap`) depois de passar na DoR.**

**4. Incorpore as considerações técnicas do tech lead antes de fechar a DoR.**
Considerações técnicas entram dentro do próprio refinamento da US (nos RFs, RNFs e regras de negócio), não como etapa separada.

**5. Use o INVEST como verificação de qualidade complementar — o template acima já cobre a maior parte dele.**
- *Independente*: se a DoR mapeou dependência explícita de outro time, aponte como risco — não é bloqueio automático, mas precisa ficar visível.
- *Negociável*: a própria história evolutiva (rascunho → refinada → pronta) já é prova desse critério — a história não nasce fechada.
- *Valiosa*: a cláusula de benefício na descrição clássica precisa deixar isso claro.
- *Estimável / Pequena*: cobertos pela DoR — se o time não conseguir estimar, ou a história não couber numa sprint, sinalize e sugira quebrar em histórias menores.
- *Testável*: os critérios de aceite BDD já cobrem isso.

**6. Rode a Definition of Done (DoD) só no fechamento da história, não na criação.**
Código desenvolvido e revisado; testes unitários e funcionais realizados com sucesso; critérios de aceite atendidos; documentação atualizada; publicado em ambiente de produção; validado pelo PO/usuário final. Esse checklist normalmente é preenchido mais à frente no processo (perto do handoff/teste), não na escrita inicial da US — mas o template já reserva o espaço para isso.

**7. Aceite ajuste por gravação, com a mesma regra de divergência do refinamento.**
Se o usuário fornecer uma gravação como fonte de ajuste, use-a como insumo — mas trate divergência com o que já estava escrito questionando, nunca assumindo qual versão vale.

**8. Mantenha o template como padrão consistente.**
Não proponha outro formato de US sem o usuário pedir para reconsiderar (regra transversal).

## Formato da saída

```
## Framework/estrutura em uso
[Framework/estrutura detectada no repositório, ou nenhum — e para quais campos as seções abaixo foram mapeadas]

## Conflito com o repositório (se houver)
[...]

## Estágio atual
[Rascunho inicial / Refinada / Pronta para desenvolvimento]

## Descrição
Como [tipo de usuário], quero [objetivo] para [benefício esperado].

## Critérios de Aceite (BDD)
- Dado que [contexto], quando [ação], então [resultado esperado].
[...]

## Requisitos Funcionais (RF)
1. O sistema deve [função].

## Requisitos Não Funcionais (RNF)
1. O sistema deve [restrição de desempenho/segurança/usabilidade].

## Regras de Negócio
- [Regra]

## Fluxos de exceção
[Apenas no estágio "pronta para desenvolvimento"]

## Definition of Ready
- [ ] Descrição clara no formato clássico
- [ ] Critérios de aceite definidos
- [ ] RFs e RNFs identificados
- [ ] Regras de negócio levantadas
- [ ] Dependências mapeadas
- [ ] Estimativa do time realizada

## Definition of Done
- [ ] Código desenvolvido e revisado
- [ ] Testes unitários e funcionais realizados com sucesso
- [ ] Critérios de aceite atendidos
- [ ] Documentação atualizada
- [ ] Publicado em ambiente de produção
- [ ] Validado pelo PO/usuário final

## Notas do INVEST (complementar)
[Independente: risco de dependência, se houver / Valiosa / Estimável-Pequena / demais conforme aplicável]

## Observações
[Anotações adicionais, dependências ou riscos]
```

## Cuidados

- Não imponha o formato de US desta skill quando o repositório usa outro framework — mapeie as seções de qualidade para o template dele; as exigências (benefício, BDD, RNF, DoR, DoD) permanecem, a forma se adapta.
- Não pule estágio da história evolutiva — um rascunho não é "pronta para desenvolvimento".
- Não deixe RNF de fora — pergunte explicitamente sobre desempenho, segurança e usabilidade quando ninguém trouxer isso.
- Não marque a DoR como atendida sem estimativa do time.
- Não rode a DoD na criação da história — ela se aplica no fechamento, mais à frente no processo.
- Não aceite critério de aceite vago ou não testável.
- Não decida sozinha um conflito entre esta skill e o repositório.
- Não assuma qual versão vale quando uma gravação divergir do que já estava escrito — pergunte, mesma regra do refinamento de negócio.
