# Banco de Dados: Gestão Imobiliária

## Objetivo
Este projeto tem como objetivo gerenciar as operações de um sistema imobiliário, incluindo o cadastro de clientes, proprietários, propriedades, contratos e manutenções.

## Estrutura do Banco de Dados

### Tabelas e Relacionamentos

1. **CLIENTES**
   - **Descrição**: Armazena as informações dos clientes do sistema imobiliário, como dados pessoais, contato e endereço.
   - **Colunas**:
     - `CLIENTE_ID`: Identificador único do cliente.
     - `NOME`: Nome completo do cliente.
     - `TELEFONE`: Número de telefone de contato.
     - `EMAIL`: Endereço de e-mail do cliente.
     - `ENDERECO`: Endereço residencial do cliente.
   - **Relacionamento**:
     - Um cliente pode ter múltiplos contratos registrados, o que está relacionado à tabela **CONTRATOS**.

2. **PROPRIETARIOS**
   - **Descrição**: Armazena as informações dos proprietários de imóveis, incluindo dados pessoais e de contato.
   - **Colunas**:
     - `PROPRIETARIO_ID`: Identificador único do proprietário.
     - `NOME`: Nome completo do proprietário.
     - `TELEFONE`: Número de telefone do proprietário.
     - `EMAIL`: Endereço de e-mail do proprietário.
   - **Relacionamento**:
     - Um proprietário pode ser responsável por várias propriedades, o que está relacionado à tabela **PROPRIEDADES**.

3. **PROPRIEDADES**
   - **Descrição**: Armazena as propriedades imobiliárias, incluindo dados sobre tipo, preço, status de disponibilidade e vínculo com o proprietário.
   - **Colunas**:
     - `PROPRIEDADE_ID`: Identificador único da propriedade.
     - `ENDERECO`: Endereço completo da propriedade.
     - `TIPO`: Tipo da propriedade (ex.: Apartamento, Casa, Sala Comercial).
     - `PRECO`: Preço de venda ou aluguel da propriedade.
     - `STATUS`: Status da propriedade (ex.: Disponível, Alugada, Em Manutenção).
     - `PROPRIETARIO_ID`: Relacionamento com o proprietário da propriedade (chave estrangeira para **PROPRIETARIOS**).
   - **Relacionamento**:
     - Uma propriedade pode ter múltiplos contratos (relacionado com a tabela **CONTRATOS**) e manutenções registradas (relacionado com a tabela **MANUTENCOES_PROPRIEDADE**).

4. **CONTRATOS**
   - **Descrição**: Registra os contratos firmados entre clientes e propriedades, incluindo detalhes sobre a vigência, valor mensal e tipo de contrato.
   - **Colunas**:
     - `CONTRATO_ID`: Identificador único do contrato.
     - `PROPRIEDADE_ID`: Relacionamento com a propriedade contratada (chave estrangeira para **PROPRIEDADES**).
     - `PROPRIETARIO_ID`: Relacionamento com o proprietário da propriedade (chave estrangeira para **PROPRIETARIOS**).
     - `CLIENTE_ID`: Relacionamento com o cliente que firmou o contrato (chave estrangeira para **CLIENTES**).
     - `DATA_INICIO`: Data de início do contrato.
     - `DATA_FIM`: Data de término do contrato (pode ser nula para contratos abertos).
     - `VALOR_MENSAL`: Valor mensal pago pelo cliente pelo aluguel ou serviço da propriedade.
     - `TIPO`: Tipo de contrato (ex.: Residencial, Comercial).
   - **Relacionamento**:
     - Um contrato sempre está associado a uma propriedade, um proprietário e um cliente.

5. **MANUTENCOES_PROPRIEDADE**
   - **Descrição**: Controla as manutenções realizadas nas propriedades, incluindo tipo de manutenção, custo e data.
   - **Colunas**:
     - `MANUTENCAO_ID`: Identificador único da manutenção.
     - `PROPRIEDADE_ID`: Relacionamento com a propriedade onde a manutenção foi realizada (chave estrangeira para **PROPRIEDADES**).
     - `DATA_MANUTENCAO`: Data em que a manutenção foi realizada.
     - `DESCRICAO`: Descrição do serviço realizado.
     - `CUSTO`: Custo da manutenção.
   - **Relacionamento**:
     - Cada manutenção está associada a uma única propriedade.

### Relacionamentos entre as Tabelas

- **CLIENTES ↔ CONTRATOS**: Um cliente pode ter múltiplos contratos com diferentes propriedades.
- **PROPRIETARIOS ↔ PROPRIEDADES**: Um proprietário pode ter várias propriedades registradas no sistema.
- **PROPRIEDADES ↔ CONTRATOS**: Cada propriedade pode estar associada a vários contratos, mas cada contrato está vinculado a uma única propriedade.
- **PROPRIEDADES ↔ MANUTENCOES_PROPRIEDADE**: Cada propriedade pode ter diversas manutenções registradas.
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