Aluno: Gabrielly Cristina dos Reis
RA:25000906






1. Regras de Negócio (RN)
As RNs definem o "como" o negócio funciona independentemente do software.
RN01 - Venda de Controlados: Medicamentos controlados exigem obrigatoriamente a validação de um Farmacêutico e retenção de receita.
RN02 - Estoque Mínimo: O sistema deve gerar um alerta visual quando o estoque de um produto atingir o limite de segurança definido pelo Gerente.
RN03 - Venda a Prazo: Somente clientes com cadastro ativo e sem débitos atrasados podem realizar compras na modalidade "A Prazo".
RN04 - Atualização de Estoque: Toda entrada (compra) ou saída (venda/perda) deve atualizar o inventário em tempo real.
RN05 - Fechamento de Caixa: O sistema não deve permitir a exclusão de registros de vendas finalizados, apenas cancelamentos com justificativa e perfil de Gerente.

<img width="606" height="799" alt="Captura de tela 2026-03-25 210318" src="https://github.com/user-attachments/assets/708fdd2d-790e-4502-bce2-d57d4d7a4bb7" />


3. Requisitos Funcionais (RF)
O que o sistema deve fazer.
RF01: O sistema deve permitir o cadastro e pesquisa de produtos por código de barras, nome ou fabricante.
RF02: O sistema deve registrar vendas à vista e a prazo.
RF03: O sistema deve validar a existência de estoque antes de confirmar a venda.
RF04: O sistema deve emitir comprovante não fiscal/cupom de venda.
RF05: O sistema deve permitir o cadastro de clientes e fornecedores.
RF06: O sistema deve gerar lançamentos automáticos em "Contas a Pagar" após a confirmação de uma compra.
RF07: O sistema deve gerar lançamentos em "Contas a Receber" para vendas conveniadas.
RF08: O sistema deve emitir relatórios de produtos que nunca foram vendidos (estoque parado).

<img width="683" height="346" alt="Captura de tela 2026-03-25 210437" src="https://github.com/user-attachments/assets/fb462e74-5f32-45ff-976b-14cc677b95b4" />


3. Requisitos Não Funcionais (RNF)
Qualidades e restrições técnicas.
RNF01 (Segurança): O sistema deve exigir login e senha, com controle de acesso baseado em perfis (RBAC).
RNF02 (Disponibilidade): O sistema deve estar disponível 99% do tempo durante o horário comercial.
RNF03 (Performance): A consulta de estoque entre unidades não deve exceder 2 segundos.
RNF04 (Integridade): O sistema deve utilizar transações de banco de dados para garantir que a venda e a baixa no estoque ocorram simultaneamente.

<img width="677" height="436" alt="Captura de tela 2026-03-25 210536" src="https://github.com/user-attachments/assets/cd6dd78c-dac9-4d2f-8785-59278f7374ef" />

5. Exemplo de Documentação de Caso de Uso (UC)
UC01: Efetuar Venda
Ator Principal: Atendente.
Pré-condição: Usuário logado no sistema.
Fluxo Principal:
O atendente inicia a venda.
O atendente insere os produtos (RF01).
O sistema verifica o estoque (<<include>> UC: Consultar Estoque).
O sistema calcula o total.
O atendente seleciona a forma de pagamento.
O sistema registra a venda e emite o comprovante.
Fluxo Alternativo (Cliente Novo):
3a. Se o cliente não possuir cadastro, o atendente seleciona "Novo Cadastro" (<<extend>> UC: Cadastrar Cliente).


6. Exemplo de Diagrama de Atividade
Para o caso de uso "Registrar Compra":
Início
Selecionar Fornecedor.
Adicionar Itens e Quantidades.
Ação Paralela:
Atualizar Saldo de Estoque da Unidade.
Gerar Título em Contas a Pagar.
Fim

