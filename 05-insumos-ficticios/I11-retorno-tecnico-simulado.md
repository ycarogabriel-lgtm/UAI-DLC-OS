# I11 retorno tecnico simulado

MATERIAL FICTÍCIO PARA TREINAMENTO — NÃO É PARECER DE ARQUITETURA REAL
Caso: Portal de Solicitações da Aurora.
Participantes fictícios: Nara (Tech Lead), Pedro (desenvolvimento), Lia (QA), Caio (Produto).
Usar após incorporar as respostas I10 e revisar os artefatos afetados.

[00:00] Nara: A proposta do protótipo é viável como demonstração com dados simulados. Isso não comprova que temos autenticação, autorização ou persistência reais.
[00:22] Pedro: A implementação de produção precisa garantir as permissões no servidor. A troca visual de perfil serve apenas para a demonstração.
[00:41] Lia: Quero critérios claros para o limite de R$ 5.000. Vamos conferir R$ 4.999,99, R$ 5.000,00 e R$ 5.000,01.
[01:00] Pedro: A política deve ficar associada ao pedido no envio para preservar o tratamento dos pedidos antigos. A solução técnica exata ainda será desenhada pelo time.
[01:20] Nara: Precisamos tratar dois cliques e decisões concorrentes. Não pode existir aprovação duplicada nem alguém sobrescrever uma decisão final.
[01:41] Lia: Também testar rejeição em cada etapa, histórico preservado, fila correta e tentativa de acesso de outra equipe.
[02:04] Caio: Temos estimativas?
[02:08] Pedro: Para o exercício, proponho faixas preliminares de esforço de desenvolvimento, ainda sujeitas ao refinamento: envio e consulta, 16–24 horas; decisão única e histórico, 12–20; segunda aprovação e coexistência das políticas, mais 16–24.
[02:36] Nara: Essas faixas são fictícias, só de desenvolvimento. Não incluem Design, QA, autenticação real, infraestrutura, integração nem margem para descobertas. Não convertam isso direto em data prometida.
[02:55] Lia: Para planejamento didático, considero 12–20 horas de QA para o conjunto, dependendo dos cenários e da estabilidade. Ainda precisamos comparar com a capacidade informada.
[03:15] Nara: A ausência de aprovador precisa continuar registrada como limitação. Se virar requisito, haverá nova análise.
[03:28] Caio: O que impede chamar tudo de pronto?
[03:32] Nara: Antes de desenvolvimento real, definir autenticação, persistência, trilha de auditoria e data de ativação da política. No exercício de protótipo, basta representar os cenários e deixar esses limites explícitos.
[03:53] Lia: Não vou declarar DoR atendido sem revisar as histórias produzidas. Vamos separar o que está pronto para prototipar do que está pronto para implementar.

FIM DO RETORNO SIMULADO
O arquivo é entrada para revisão e planejamento. Handoff, backlog final e Definition of Ready serão produzidos e revisados no fluxo.
