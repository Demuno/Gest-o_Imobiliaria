# Banco de Dados: Gestão Imobiliária

## Objetivo
`Este projeto tem como objetivo gerenciar as operações de um sistema imobiliário, incluindo o cadastro de clientes, proprietários, propriedades, contratos e manutenções.`

## Estrutura do Banco de Dados
### Tabelas e Relacionamentos
1. **CLIENTES**: Cadastro de clientes.
2. **PROPRIETARIOS**: Cadastro de proprietários.
3. **PROPRIEDADES**: Registro de propriedades com status, preço e proprietário.
4. **CONTRATOS**: Registro de contratos entre clientes e propriedades.
5. **MANUTENCOES_PROPRIEDADE**: Controle de manutenções realizadas em propriedades.

### Relacionamentos
- **PROPRIETARIOS** é pai de **PROPRIEDADES**.
- **PROPRIEDADES** é pai de **CONTRATOS** e **MANUTENCOES_PROPRIEDADE**.
- **CLIENTES** está relacionado com **CONTRATOS**.

## Índices
- **IDX_PROPRIEDADES_STATUS**: Acelera consultas por status de propriedades.
- **IDX_CONTRATOS_DATA_INICIO**: Acelera consultas por data de início dos contratos.

## Como Executar os Scripts
No Oracle Database, é possível fazer a conexão com o sqlplus, seguindo o seguinte exemplo:
```sqlplus username/password@hostname:port/service_name```

### Para carregar o scritp DDL
`@caminho/Ate/A/Pasta/Do/Projeto/DDL/estrutura.sql`

### Para carregar o scritp DML
`@caminho/Ate/A/Pasta/Do/Projeto/DML/dados.sql`

## Membros
- Mateus Demuno Baptista: 184876
- Julia Santos Souza: 180442
- Ana Claudia Figueredo: 185172