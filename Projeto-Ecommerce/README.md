# Refinando um design conceitual de Banco de Dados
- Primeiro desafio de projeto do curso "Formação SQL Database Specialist" <a href="https://www.dio.me/" target="__blank">da DIO.</a>

# 📦 E-Commerce - Modelo de Banco de Dados

Este projeto representa o modelo de banco de dados relacional para uma aplicação de E-Commerce. O diagrama inclui tabelas para clientes, produtos, fornecedores, pedidos, formas de pagamento, entre outros componentes essenciais para o funcionamento de uma plataforma de vendas online.

---

## 🗂️ Visão Geral das Tabelas

### 🧑 Cliente
- `idCliente` (PK)
- `Nome`
- `Identificação (CPF/CNPJ)`
- `Endereço`

Relaciona-se com as tabelas:
- `Pessoa_Fisica`
- `Pessoa_Juridica`
- `Forma_Pagamento`
- `Pedido`

---

### 👤 Pessoa_Fisica / Pessoa_Juridica
Especializações de `Cliente`:
- `Pessoa_Fisica`: possui `CPF`
- `Pessoa_Juridica`: possui `CNPJ`

---

### 💳 Forma_Pagamento
- `idFormaPagamento` (PK)
- `Tipo` (Ex: Cartão, Pix)
- FK para `Cliente`

Subtipos:
- **Cartão**
  - `Numero`
  - `DataValidade`
  - `CVV`
- **Pix**
  - `ChavePix`

---

### 📦 Produto
- `idProduto` (PK)
- `Categoria`
- `Preço`

Relacionamentos:
- Pode ser fornecido por múltiplos `Fornecedor`
- Pode estar em múltiplos `Estoque`
- Pode ser vendido por `Outros_Vendedores`

---

### 🧾 Pedido
- `idPedido` (PK)
- `Status`
- `Descrição`
- `Envio`
- FK para `Cliente`, `Pessoa_Fisica`, `Pessoa_Juridica`

Relacionamentos:
- 1:N com `Entrega`
- N:M com `Produto` (via `Pedido_Do_Produto`)

---

### 🚚 Entrega
- `idEntrega` (PK)
- `Status`
- `Rastreamento`
- FK para `Pedido` e cliente associado

---

### 🏬 Fornecedor
- `idFornecedor` (PK)
- `razaoSocial`
- `CNPJ`

Relacionamento N:M com `Produto`

---

### 🧱 Estoque
- `idEstoque` (PK)
- `Local`

Relacionamento N:M com `Produto`

---

### 🛒 Pedido_Do_Produto
Tabela associativa entre `Pedido` e `Produto`, com os campos:
- `Pedido_idPedido`
- `Produto_idProduto`
- `Quantidade`

---

### 🧾 Produtos_Outros_Vendedores
Relaciona produtos vendidos por terceiros com:
- `Outros_Vendedores`
- `Produto`

---

## 📌 Relacionamentos Chave

- Um cliente pode ter múltiplas formas de pagamento.
- Cada pedido pertence a um cliente (físico ou jurídico).
- Um produto pode ser vendido por múltiplos vendedores e fornecido por múltiplos fornecedores.
- Estoque e pedidos possuem relacionamentos N:M com produtos.
- As entregas são associadas a pedidos específicos.

---

## 🛠️ Tecnologias Recomendadas

- **SGDB**: MySQL
- **Ferramentas de Modelagem**: MySQL Workbench, DBDesigner, ERD Tools

---

## 📎 Observações

- Este modelo é ideal para um sistema de e-commerce que atenda tanto pessoas físicas quanto jurídicas.
- Suporta múltiplos meios de pagamento e múltiplos fornecedores e vendedores.

📷 Diagrama:

<img src=https://raw.githubusercontent.com/AlcenirGomes/dio-formacao-sql-database-specialist/refs/heads/main/E-Commerce%20Refinamento.png />
