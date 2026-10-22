# I06 refinamento fluxo simulado

MATERIAL FICTÍCIO PARA TREINAMENTO — NÃO É REUNIÃO REAL
Caso: Portal de Solicitações da Aurora. Momento: após o alinhamento estratégico.
Participantes fictícios: Caio (Produto), Marina (Operações), Bia (colaboradora), Lucas (gestor).

[00:00] Caio: Vamos detalhar o envio e a decisão do pedido. Ainda estamos no cenário de aprovação única.
[00:14] Marina: Certo. O gestor da equipe decide todos os valores nesta primeira versão.
[00:30] Caio: Quais dados a pessoa informa?
[00:35] Bia: Descrição do item, justificativa e valor estimado total.
[00:48] Marina: Esses três são obrigatórios. A descrição pode ter até 120 caracteres e a justificativa até 500. O valor deve ser maior que zero, em reais, com até duas casas decimais.
[01:15] Lucas: Nome e equipe não deveriam ser digitados toda vez. No protótipo podemos obtê-los do perfil simulado.
[01:34] Caio: Se faltar informação?
[01:39] Marina: Não envia. Mostra o problema junto do campo e preserva o que já foi preenchido.
[01:56] Bia: Quero revisar os dados antes de confirmar.
[02:07] Caio: O que acontece após o envio?
[02:13] Marina: O pedido ganha um número único, data e hora, e fica “Aguardando aprovação”. A pessoa vê a confirmação e pode abrir o detalhe.
[02:36] Lucas: Na minha fila vejo só os pedidos da minha equipe. Os mais antigos primeiro. Posso abrir o detalhe e conferir valor, descrição e justificativa.
[02:58] Caio: Aprovar exige alguma informação?
[03:02] Marina: Exige confirmação da ação, mas comentário não é obrigatório. Registrar quem decidiu e quando.
[03:20] Caio: E rejeitar?
[03:24] Marina: Precisa de motivo obrigatório, até 500 caracteres. Sem motivo, não conclui. O solicitante deve ver esse motivo no detalhe.
[03:44] Bia: Se o pedido foi rejeitado, posso corrigir e enviar de novo?
[03:50] Marina: No piloto, criar um novo pedido. Não vamos editar um pedido já enviado, seja pendente ou concluído.
[04:09] Caio: Então o que foi decidido e o valor permanecem vinculados à versão enviada.
[04:17] Lucas: Isso resolve a minha dúvida sobre aprovar um valor que muda depois.
[04:28] Caio: Cancelar pedido entra?
[04:31] Marina: Não neste recorte. Registrar como necessidade futura.
[04:40] Caio: Quem vê o quê?
[04:45] Marina: O colaborador vê os próprios pedidos. O gestor vê os da equipe pela qual responde. A visualização por outros perfis fica para definição posterior.
[05:02] Lucas: No piloto cada equipe tem um único gestor definido. Ausência e substituição continuam fora; precisamos apontar essa limitação.
[05:21] Caio: Se uma ação falhar?
[05:25] Marina: O portal não deve dizer que aprovou ou enviou se não concluiu. Mostrar erro e permitir tentar novamente, evitando pedido duplicado.
[05:47] Caio: No protótipo vamos representar esse estado. A solução real de concorrência será revisada com o time técnico.
[05:58] Marina: Perfeito. E “Aprovado” continua sendo apenas autorização. Sem status de compra ou entrega.
[06:10] Bia: Gostaria de ver o número, descrição, valor, data e status na consulta, e o histórico da decisão no detalhe.
[06:28] Caio: Vamos gerar histórias e critérios a partir desta conversa e pedir a revisão de vocês.

FIM DA TRANSCRIÇÃO SIMULADA
O arquivo contém definições fictícias para o exercício. Não contém histórias de usuário, BDD ou telas prontas.
Uma alteração de política só será introduzida em um insumo posterior.
