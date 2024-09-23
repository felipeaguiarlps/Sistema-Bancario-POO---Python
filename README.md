# Sistema Bancário

Este projeto é um sistema bancário simples que permite a gestão de contas correntes e suas respectivas transações, como depósitos e saques. Ele foi implementado em Python utilizando conceitos de orientação a objetos.

## Funcionalidades

O sistema oferece as seguintes funcionalidades:

- **Criar Cliente**: Cadastro de clientes com CPF, nome completo, data de nascimento e endereço.
- **Criar Conta Corrente**: Criação de contas correntes para clientes cadastrados, com limite de saque e limite de transações.
- **Depósito**: Realização de depósitos em contas correntes.
- **Saque**: Realização de saques, verificando saldo disponível e limites.
- **Extrato**: Exibição de extrato com as transações realizadas.
- **Listar Contas**: Lista as contas criadas no sistema.

## Classes e Métodos

### `Cliente`

- `__init__(self, endereco)`: Inicializa um cliente com um endereço e uma lista de contas.
- `realizar_transacao(self, conta, transacao)`: Realiza uma transação (saque ou depósito) em uma conta.
- `adicionar_conta(self, conta)`: Adiciona uma conta ao cliente.

### `PessoaFisica` (herda de `Cliente`)

- `__init__(self, cpf, nome, data_nascimento, endereco)`: Inicializa uma pessoa física com CPF, nome, data de nascimento e endereço.

### `Conta`

- `__init__(self, numero, cliente)`: Inicializa uma conta com número, cliente, saldo inicial de 0, agência "0001" e um histórico de transações.
- Métodos para `sacar`, `depositar` e propriedades para acessar atributos da conta.

### `ContaCorrente` (herda de `Conta`)

- `__init__(self, numero, agencia, cliente, limite=500, limite_saques=3)`: Inicializa uma conta corrente com limites de saque e transações.
- Sobrescreve o método `sacar` para aplicar regras de limite de saques e valor.

### `Transacao` (classe abstrata)

Define a interface para transações como `Saque` e `Deposito`.

### `Saque` (herda de `Transacao`)

- `__init__(self, valor)`: Inicializa a transação de saque com um valor específico.
- `registrar(self, conta)`: Registra a transação no histórico da conta se o saque for bem-sucedido.

### `Deposito` (herda de `Transacao`)

- `__init__(self, valor)`: Inicializa a transação de depósito com um valor específico.
- `registrar(self, conta)`: Registra a transação no histórico da conta se o depósito for bem-sucedido.

### `Historico`

- `__init__(self)`: Inicializa o histórico de transações.
- `adicionar_transacoes(self, transacao)`: Adiciona uma transação ao histórico.

## Menu de Operações

O sistema oferece um menu interativo onde o usuário pode:

- Depositar
- Sacar
- Exibir extrato
- Criar nova conta
- Listar contas
- Criar novo usuário
- Exibir o menu novamente
- Sair do sistema

## Exemplo de Uso

Ao rodar o código, o sistema exibirá um menu de opções. O usuário poderá escolher a ação que deseja realizar, como cadastrar um novo cliente, criar uma conta, realizar saques ou depósitos, e muito mais.

```bash
==================== Menu ===================
[d]     Depositar
[s]     Sacar
[e]     Extrato
[nc]    Nova conta
[lc]    Listar contas
[nu]    Novo usuário
[m]     Exibe novamente o menu
[q]     Sair
