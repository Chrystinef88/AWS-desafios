# AWS-desafios
Componentes da Arquitetura
AWS Step Functions (Máquina de Estado): O orquestrador central que define o fluxo de trabalho (Workflow).

Tipo: Workflow Padrão (Standard) para processos de longa duração e alta confiabilidade.

Função AWS Lambda 1: ValidarPedido

Função: Recebe a entrada do pedido (ex: ID, itens) e verifica a validade (estoque, dados do cliente).

Saída: Retorna um status (APROVADO ou REPROVADO).

Função AWS Lambda 2: ProcessarPagamento

Função: É chamada somente se o pedido for APROVADO. Simula a comunicação com um gateway de pagamento.

Saída: Retorna o status do pagamento (SUCESSO ou FALHA).

Função AWS Lambda 3: EnviarConfirmacao

Função: É chamada somente se o pagamento for um SUCESSO. Envia um e-mail de confirmação ou notificação.

Saída: Sinaliza o fim do processo com sucesso.

Estado de Falha/Compensação (FalhaNoProcesso):

Função: Um estado de parada que é alcançado se o pedido for reprovado ou o pagamento falhar, podendo, neste ponto, iniciar uma lógica de compensação (ex: estornar o estoque ou notificar um administrador)
