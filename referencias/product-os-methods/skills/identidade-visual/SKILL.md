---
name: identidade-visual
description: "Organizar identidade visual ou design system antes de prototipar: cores, tipografia, tokens, componentes e estados, com acessibilidade e versionamento."
---

# Identidade Visual

> As menções a "(regra transversal)" abaixo remetem às regras transversais deste plugin, em `${CLAUDE_SKILL_DIR}/../../docs/REGRAS_TRANSVERSAIS.md` (o arquivo `docs/REGRAS_TRANSVERSAIS.md` na raiz do plugin, não no repositório em que você está trabalhando). Leia esse arquivo antes de aplicar a skill. Fora do Claude Code, as regras precisam ser fornecidas junto com esta skill.

## O princípio inegociável

Nenhum protótipo (skill `prototipacao`) começa sem a identidade visual reunida e documentada — reunir os artefatos é pré-requisito, não uma tarefa em paralelo que pode ficar para depois.

## Como conduzir

**0. Verifique o repositório e o framework em uso antes de reunir do zero.**
- **Framework em uso (verifique primeiro).** Identifique como o repositório de destino organiza produto e trabalhe no padrão dele (regra transversal — ver `${CLAUDE_SKILL_DIR}/../../docs/REGRAS_TRANSVERSAIS.md`, "Adaptação ao framework em uso"):
  - *O repositório já adota um framework ou estrutura própria* (um design system próprio, uma convenção de tokens, uma estrutura de style guide já adotada): documente na estrutura de tokens/design system que o framework já adota — as camadas desta skill (tokens → componentes com estados → diretrizes → acessibilidade) são o conteúdo mínimo, não o formato obrigatório.
  - *Nenhum*: use a estrutura de documentação desta skill como está.
  As exigências desta skill — todos os estados dos componentes, acessibilidade obrigatória, versionamento, nada de valor inventado — continuam valendo; o que se adapta é a estrutura do documento. Se a convenção do framework conflitar com o formato-padrão daqui, o framework em uso prevalece — sinalize a diferença, não decida sozinha.
- Se já existir um brand book, style guide ou design system documentado no repositório, reaproveite-o como base — não peça para recriar do zero.
- Se esta skill conflitar com o que já está documentado, sinalize e pergunte — nunca decida sozinha (regra transversal).

**1. Reúna os artefatos visuais.**
- Cores, tipografia, design system, componentes — o que já existir, de onde vier (Figma, brand book, repositório, etc.).
- Se algo específico estiver faltando (ex.: a cor de marca exata do cliente), pergunte antes de inventar um valor que represente identidade real de alguém.

**1.1 Se não houver nada no repositório nem em nenhuma fonte, consolide um documento básico — não bloqueie o processo.**
Quando a busca no repositório e a pergunta ao usuário confirmarem que não existe brand book, style guide ou design system nenhum ainda: monte você mesma um documento básico de identidade visual, com valores neutros e sensatos (paleta neutra, tipografia padrão do sistema, componentes nos estados essenciais), deixando explícito que é uma **base provisória, a validar** — não é a mesma coisa que inventar a cor de marca de um cliente real. Isso evita travar o processo, mas o documento nasce marcado como provisório até alguém validar ou substituir.

**2. Estruture a documentação por camada.**
- Tokens de design (cor, espaçamento, tipografia) como a camada mais atômica.
- Componentes com todos os estados: default, hover, active, disabled, error, loading — não documente só o estado "feliz".
- Diretrizes de uso (quando e como usar cada componente).
- Requisitos de acessibilidade: contraste, leitor de tela, navegação por teclado.

**3. Adapte o nível de detalhe por público.**
- Dev precisa de especificação técnica (valores exatos, nomenclatura de tokens/componentes).
- Design precisa de diretriz visual (intenção, quando usar o quê).
- Pergunte para quem é a documentação, se não estiver claro pelo contexto.

**4. Mantenha versionamento.**
- Changelog de mudanças.
- Revisão periódica (ex.: trimestral) para o material não ficar desatualizado — sinalize proativamente quando a última revisão estiver velha, em vez de esperar reclamação.

**5. Capture novos artefatos visuais sempre que chegarem, não só na coleta inicial.**
Esta skill não termina depois da primeira consolidação. Sempre que surgir um novo artefato visual — um arquivo de logo, uma imagem anexada no chat, um link de pasta na nuvem, o que for — capture, incorpore ao documento de identidade visual já consolidado (substituindo ou complementando o que hoje é base provisória) e atualize a referência salva no repositório. Não deixe esse artefato "solto" na conversa sem virar parte da identidade visual de referência — é isso que garante que os próximos materiais gerados já usem a versão mais atual.

**6. Registre como contexto para o resto do processo — e trate como referência obrigatória, não sugestão.**
Salve a identidade visual reunida (ou o documento básico consolidado no passo 1.1) como contexto do repositório. A partir daqui, **todo material gerado depois — protótipo, telas, componentes, qualquer artefato visual — usa essa base como referência obrigatória**, para manter consistência entre tudo o que é produzido. Se um material precisar fugir do que está documentado, isso é sinalizado e perguntado, nunca decidido sozinho no meio da geração de outro artefato (regra transversal). Quando o documento for a base provisória do passo 1.1, deixe isso visível também nos materiais que a usarem, até ela ser validada ou substituída.

## Formato da saída

```
## Framework/estrutura em uso
[Framework/estrutura detectada no repositório, ou nenhum — e em que estrutura de design system a documentação abaixo foi registrada]

## Conflito com o repositório (se houver)
[O que já está documentado e onde diverge do que esta skill orienta]

## Artefatos reunidos
[Cores, tipografia, componentes — e de onde vieram. Se nada foi encontrado: sinalizar que este é um documento básico consolidado pela IA, marcado como base provisória a validar]

## Atualizações (novos artefatos capturados após a consolidação inicial)
[Sempre que chegar um novo artefato visual — logo, imagem no chat, link de nuvem — registrar aqui: o que chegou, quando, e como foi incorporado ao documento consolidado. Vazio se ainda não houve atualização desde a consolidação inicial]

## Documentação por camada

### Tokens de design
[...]

### Componentes (com estados: default / hover / active / disabled / error / loading)
[...]

### Diretrizes de uso
[...]

### Acessibilidade
[Contraste, leitor de tela, navegação por teclado]

## Público-alvo desta documentação
[Dev / Design / ambos — com nível de detalhe ajustado]

## Versionamento
[Última revisão, changelog, próxima revisão programada]

## Pendências
[O que ainda falta reunir ou definir]
```

## Cuidados

- Não imponha a estrutura de documentação desta skill quando o repositório usa outro design system — documente no dele; o conteúdo mínimo (estados, acessibilidade, versionamento) permanece, a forma se adapta.
- Não invente valor de cor, tipografia ou componente que não foi fornecido — pergunte.
- Não documente um componente só no estado "feliz" — sempre cubra hover/active/disabled/error/loading.
- Não ignore acessibilidade — é parte obrigatória da documentação, não um extra opcional.
- Não deixe a documentação desatualizada sem sinalizar.
- Não decida sozinha um conflito entre esta skill e o repositório.
- Não deixe o processo travado só porque não existe identidade visual definida ainda — consolide a base provisória e siga, deixando claro que é provisória.
- Não gere nenhum material depois (protótipo, tela, componente) com estilo inventado na hora — sempre referencie a identidade visual já reunida/consolidada aqui.
- Não deixe um novo artefato visual enviado a qualquer momento "solto" na conversa — capture, incorpore e atualize a referência salva no repositório assim que ele chegar.
