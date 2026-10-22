# I05 direcionamento capacidade e dados

MATERIAL FICTÍCIO PARA TREINAMENTO — NÃO É DADO OPERACIONAL REAL
Caso: Portal de Solicitações da Aurora. Momento: início do Upstream.
Mensagem simulada de Marina, com anotações fictícias de Ana e Nara.

DIRECIONAMENTO
Queremos reduzir a necessidade de perguntar por mensagem se o pedido foi visto e diminuir a espera até uma decisão. O piloto abrange uma equipe fictícia de 12 colaboradores e um gestor.
A janela desejada é de quatro semanas de avaliação. O time deve propor o que cabe; não há promessa prévia de entrega em produção.
O recorte continua sendo pedido, decisão e acompanhamento. Compra, estoque, pagamento e fornecedores seguem fora.
Não há meta percentual aprovada. A equipe deve propor métricas relacionadas aos objetivos e explicitar o que consegue medir.

CAPACIDADE INFORMADA PARA O EXERCÍCIO
Produto: 12 horas por semana.
Design: 16 horas por semana.
Pessoa desenvolvedora: 24 horas por semana.
QA: 8 horas por semana.
São disponibilidades hipotéticas por quatro semanas, não estimativas de funcionalidades. Não somar disciplinas como se fossem intercambiáveis.
Na semana 1, 4 horas de Design serão usadas em outro compromisso.
O time técnico ainda não estimou as histórias. Dependências e capacidade devem aparecer como premissas do roadmap.

RECORTE SIMULADO DE 10 PEDIDOS ENCERRADOS
Período fictício: uma quinzena anterior ao piloto.
dias_ate_decisao = dias corridos entre envio e decisão final.
contatos_de_status = quantas vezes a pessoa perguntou por mensagem sobre andamento.
informacao_ausente_no_envio = registro manual “sim” ou “não”.

pedido | dias_ate_decisao | contatos_de_status | informacao_ausente_no_envio
A01 | 2 | 1 | não
A02 | 5 | 3 | sim
A03 | 3 | 1 | não
A04 | 7 | 4 | sim
A05 | 1 | 0 | não
A06 | 4 | 2 | sim
A07 | 6 | 3 | sim
A08 | 2 | 1 | não
A09 | 5 | 2 | não
A10 | 3 | 1 | não

LIMITES DO RECORTE
A seleção contém somente pedidos encerrados e não mostra os que seguem parados.
O registro de contatos é manual e pode estar incompleto.
Os dados são inteiramente sintéticos, preparados para praticar análise e visualização.
Não há comparação antes/depois nem resultado de melhoria comprovado.

Marina: “Quero ver como vocês relacionam a proposta de métricas ao problema. Não adotem uma meta só porque parece boa no gráfico.”
Ana: “Se o piloto registrar envio e decisão, conseguimos medir espera. Precisaremos combinar como registrar os contatos fora do portal.”

FIM DO INSUMO
KPIs, OKRs, gráficos, priorização e roadmap devem ser produzidos no fluxo, com revisão humana.
