# 3. DOCUMENTO DE ESPECIFICAÇÃO DE REQUISITOS DE SOFTWARE

## 3.1 Objetivos deste documento
Descrever e especificar as necessidades das locadoras pequenas e/ou médias de veículos que devem ser atendidas pelo projeto MasterCar, um sistema de gestão de locadoras de veículos, o qual contempla o ciclo completo da locação, gerenciamento de veículos, reservas, funcionários e controle de acesso ao sistema.

## 3.2 Escopo do produto

### 3.2.1 Nome do produto e seus componentes principais
O produto possui o nome MasterCar. Ele terá um único componente (módulo) principal com os elementos necessários à gestão completa de uma locadora pequena e/ou média de veículos, incluindo controle de acesso, gerenciamento de veículos, reservas e dashboard gerencial.

### 3.2.2 Missão do produto
Gerenciar informações sobre veículos, reservas, funcionários e clientes de locadoras de veículos de pequeno e médio porte, com uma interface moderna, simples e intuitiva atendendo o ciclo completo da locação de veículos.

### 3.2.3 Limites do produto
O MasterCar não contempla funcionalidades voltadas para locadoras de grande porte ou redes regionais com múltiplas filiais. O sistema também não realiza avaliações de condutores ou scoring de crédito de clientes.

### 3.2.4 Benefícios do produto

| # | Benefício | Valor para a Locadora |
|--------------------|------------------------------------|----------------------------------------|
|1	| Interface moderna e intuitiva para operadores sem formação técnica |	Essencial |
|2 | Facilidade no cadastro e consulta de veículos e reservas | Essencial | 
|3 | Controle de acesso com diferentes níveis de permissão | Essencial | 
|4	| Dashboard com indicadores gerenciais em tempo real	| Recomendável |
|5	| Prevenção de duplicidade de dados e reservas conflitantes	| Essencial |
|6	| Segurança no acesso com autenticação por senha	| Essencial | 

## 3.3 Descrição geral do produto

### 3.3.1 Requisitos Funcionais

| Código | Requisito Funcional (Funcionalidade) | Descrição |
|--------------------|------------------------------------|----------------------------------------|
| RF1 | Gerenciar Acesso ao Sistema |	O administrador pode cadastrar, editar, excluir e consultar funcionários, além de definir níveis de acesso (administrador ou funcionário). |
| RF2 |	Autenticar Usuário	| O sistema deve permitir login seguro com validação de credenciais, concedendo acesso conforme o nível do usuário cadastrado. |
| RF3	| Gerenciar Veículos |	Processamento de Inclusão, Alteração, Exclusão e Consulta de veículos da frota, incluindo dados como modelo, placa, disponibilidade e características. |
| RF4	| Registrar Reservas |	O sistema deve registrar reservas, informando dados do cliente, veículo reservado e datas definidas. |
| RF5	| Consultar Dashboard |	O sistema apresenta indicadores gerenciais como total de reservas, veículos disponíveis, veículos reservados e histórico de movimentações. |
| RF6	| Validação de Dados Únicos |	O sistema atualiza automaticamente a disponibilidade de veículos conforme reservas são criadas, alteradas ou canceladas, prevenindo duplicidade de dados. |

### 3.3.2 Requisitos Não Funcionais

| Código | Requisito Não Funcional (Restrição) |
|--------------------|------------------------------------|
| RNF1 | O sistema deve ser uma aplicação web compatível com navegadores modernos (Chromium) |
| RNF2 | O sistema deve utilizar banco de dados relacional (SQL) para garantir integridade e consistência dos dados. |
| RNF3 |	O sistema deve garantir segurança de acesso por meio de autenticação com login e senha, com senhas de no mínimo 8 caracteres contendo ao menos um número. |
| RNF4 |	A interface deve ser simples, intuitiva e responsiva, adequada para usuários sem formação técnica em TI. |

### 3.3.3 Usuários 

| Ator | Descrição |
|--------------------|------------------------------------|
| Administrador |	Usuário gerente do sistema responsável pelo cadastro e manutenção de funcionários e pelo controle geral da locadora. Possui acesso completo a todas as funcionalidades do sistema, incluindo o dashboard gerencial. |
| Funcionário |	Usuário operacional responsável pelo registro de reservas, atualização de disponibilidade de veículos e atendimento aos clientes. Possui acesso às funcionalidades operacionais do sistema. |

## 3.4 Modelagem do Sistema

### 3.4.1 Diagrama de Casos de Uso
Como observado no diagrama de casos de uso da Figura 1, o Funcionário poderá realizar reservas de veículos, manter a disponibilidade de veículos e consultar o dashboard do sistema. O Administrador, além dessas funções, poderá gerenciar o acesso ao sistema, cadastrando e configurando os funcionários.

#### Figura 1: Diagrama de Casos de Uso do Sistema.

<img width="1286" height="816" alt="Diagrama-CSU" src="https://github.com/user-attachments/assets/5b541f16-27e0-4ad6-8d43-59957d3cfbbe" />

 
### 3.4.2 Descrições de Casos de Uso

Cada caso de uso deve ter a sua descrição representada nesta seção. Exemplo:

#### Gerenciar Acesso ao Sistema (CSU01)

Sumário: Permite ao administrador cadastrar funcionários e definir níveis de acesso.

Ator Primário: Administrador.

Pré-condições: Administrador autenticado.

Fluxo Principal:

1.	O administrador acessa o sistema 
2.	Solicita o cadastro de um novo funcionário 
3.	Informa os dados do funcionário 
4.	Define o nível de acesso 
5.	O sistema confirma o cadastro 

Fluxo Alternativo:
- Dados inválidos → o sistema solicita correção

Pós-condição: Funcionário cadastrado

#### Realizar Reserva de Veículo (CSU02)

Sumário: Permite ao funcionário registrar uma reserva para um cliente.

Ator Primário: Funcionário.

Ator Secundário: Cliente.

Pré-condições: Funcionário autenticado.

Fluxo Principal:

1.	O funcionário acessa o sistema
2.	Solicita a criação de reserva
3.	Informa os dados do cliente
4.	Seleciona um veículo disponível
5.	Define a data da reserva
6.	O sistema apresenta os dados
7.	O funcionário confirma
8.	O sistema confirma a reserva

Fluxos Alternativos:

- Veículo indisponível → selecionar outro
- Cliente não cadastrado → realizar cadastro

Pós-condição: Reserva registrada

#### Consultar Dashboard (CSU03)

Sumário: Permite ao usuário visualizar indicadores do sistema.

Ator Primário: Usuário.

Pré-condições: Usuário autenticado.

Fluxo Principal:

1.	O usuário acessa o sistema
2.	O sistema exibe o dashboard
3.	O usuário analisa os dados

Pós-condição: Informações visualizadas

#### Manter Disponibilidade de Veículos (CSU04)

Sumário: Permite atualizar dados de veículos para garantir reservas corretas.

Ator Primário: Funcionário.

Pré-condições: Funcionário autenticado.

Fluxo Principal:

1.	O funcionário acessa o sistema
2.	Visualiza a lista de veículos
3.	Atualiza informações necessárias
4.	O sistema confirma a atualização

Fluxo Alternativo:
- Dados duplicados → sistema bloqueia

Pós-condição: Dados atualizados

#### Autenticar Usuário (CSU05)

Sumário: Permite acesso seguro ao sistema.

Ator Primário: Usuário.

Pré-condições: Usuário cadastrado.

Fluxo Principal:

1.	O usuário acessa a tela de login
2.	Informa login e senha
3.	O sistema valida
4.	O sistema concede acesso

Fluxo Alternativo:
- Dados incorretos → sistema informa erro

Pós-condição: Usuário autenticado

### 3.4.3 Diagrama de Classes 

A Figura 2 mostra o diagrama de classes do sistema. A Matrícula deve conter a identificação do funcionário responsável pelo registro, bem com os dados do aluno e turmas. Para uma disciplina podemos ter diversas turmas, mas apenas um professor responsável por ela.

#### Figura 2: Diagrama de Classes do Sistema.

<img width="1371" height="816" alt="Diagrama-Classes" src="https://github.com/user-attachments/assets/39c79328-a014-4b0b-978e-13608e407e7c" />

### 3.4.4 Descrições das Classes 

| # | Nome | Descrição |
|--------------------|------------------------------------|----------------------------------------|
| 1	|	Usuario |	Classe base que representa qualquer usuário do sistema MasterCar, contendo atributos comuns de autenticação e identificação. |
| 2	| Administrador |	Especialização de Usuário com acesso completo ao sistema. Responsável pelo cadastro e gestão de funcionários e configurações gerais. |
| 3 |	Funcionário | Especialização de Usuário com acesso operacional. Responsável pelo registro de reservas e atualização de disponibilidade de veículos. |
| 4 |	Veículo |	Cadastro de veículos da frota da locadora, incluindo dados como modelo, placa, ano, categoria e status atual de disponibilidade. |
| 5	|	Reserva |	Registro de locação de um veículo por um cliente, contendo período, status e referências ao funcionário responsável, ao cliente e ao veículo reservado. |
| 6	|	Cliente |	Cadastro de informações dos clientes da locadora, como nome, CPF, telefone, e-mail e endereço, vinculado às reservas. |
| 7	|	Pagamento | Representa pagamento vinculado a uma reserva, contendo informações como valor total, data, forma de pagamento e status da transação (pendente, aprovado ou cancelado). |
