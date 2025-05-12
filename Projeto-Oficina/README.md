# 🛠️ Projeto conceitual de Banco de Dados
## Sistema de Gerenciamento de Ordem de Serviço - Oficina Mecânica

- Segundo desafio de projeto do curso "Formação SQL Database Specialist" <a href="https://www.dio.me/" target="__blank">da DIO.</a>

Este repositório contém o modelo de dados (diagrama Entidade-Relacionamento - ER) de um sistema de gerenciamento de ordens de serviço para uma oficina mecânica. O objetivo é permitir o controle eficiente de clientes, veículos, ordens de serviço, serviços prestados, peças utilizadas e equipe técnica.

## 📚 Descrição Geral

Este modelo visa suportar as principais operações de uma oficina mecânica, organizando os dados em tabelas normalizadas com relacionamentos adequados. A estrutura foi desenhada para garantir:

- Integridade referencial;
- Escalabilidade;
- Clareza na representação dos processos da oficina;
- Facilidade para geração de relatórios e integrações com sistemas externos.

---

## 🧱 Entidades e Atributos

### 👤 Cliente

Armazena os dados de pessoas físicas ou jurídicas que solicitam serviços.

- `idCliente` (PK) - Identificador único.
- `Nome` - Nome completo do cliente.
- `Telefone` - Número de contato.
- `Email` - Endereço eletrônico.
- `Endereco` - Endereço físico.

📌 **Relacionamento:** Um cliente pode possuir múltiplos veículos.

---

### 🚗 Veículo

Registra os veículos pertencentes aos clientes.

- `idVeiculo` (PK) - Identificador único.
- `Placa` - Placa do veículo.
- `Modelo` - Modelo do veículo.
- `Ano` - Ano de fabricação.
- `Cliente_idCliente` (FK) - Referência ao cliente.

📌 **Relacionamento:** Um veículo pode ter várias ordens de serviço.

---

### 📄 Ordem de Serviço (OS)

Representa o atendimento técnico de um veículo.

- `idOrdemServico` (PK) - Identificador da OS.
- `dataEmissao` - Data de emissão da OS.
- `valorTotal` - Valor total da OS.
- `Status` - Situação da OS (Aberta, Em Andamento, Concluída, etc.).
- `dataConclusao` - Data de finalização.
- `Veiculo_idVeiculo` (FK) - Veículo atendido.
- `Equipe_idEquipe` (FK) - Equipe responsável.

📌 **Relacionamento:**
- Uma OS pode conter vários serviços (`Ordem_Servico`).
- Uma OS pode utilizar várias peças (`Ordem_Peca`).

---

### 🛠️ Serviço

Contém os tipos de serviços prestados pela oficina.

- `idServico` (PK)
- `Descricao` - Nome e tipo do serviço.
- `Preco` - Custo padrão do serviço.

---

### 🔁 Ordem_Servico

Tabela de junção entre Ordem de Serviço e Serviços.

- `OrdemServico_idOrdemServico` (PK, FK)
- `Servico_idServico` (PK, FK)
- `Quantidade` - Quantidade de vezes que o serviço foi realizado.

---

### 🧩 Peça

Catálogo de peças usadas nas manutenções.

- `idPeca` (PK)
- `Descricao` - Nome da peça.
- `Preco` - Valor unitário.

---

### 🔗 Ordem_Peca

Tabela de junção entre Ordem de Serviço e Peças.

- `OrdemServico_idOrdemServico` (PK, FK)
- `Peca_idPeca` (PK, FK)
- `Quantidade` - Quantidade utilizada.

---

### 👨‍🔧 Equipe

Times de mecânicos responsáveis por ordens de serviço.

- `idEquipe` (PK)
- `Nome` - Nome da equipe.

📌 **Relacionamento:** Cada equipe pode executar várias OS's.

---

### 🧑‍🔧 Mecânico

Profissionais que integram as equipes técnicas.

- `idMecanico` (PK)
- `Nome`
- `Endereco`
- `Especialidade` - Ex: Motor, Elétrica, Suspensão.
- `Equipe_idEquipe` (FK)

📌 **Relacionamento:** Um mecânico pertence a uma única equipe.

---

📷 Diagrama:

<img src=https://github.com/AlcenirGomes/dio-formacao-sql-database-specialist/blob/main/Projeto-Oficina/Oficina_Ordem_Servico.png />

