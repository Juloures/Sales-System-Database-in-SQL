# Sales System Database

This project defines a SQL-based sales system database, including tables for Customers, Products, and Sales. It inserts sample data and includes various queries for generating reports and updating records.

## Database Structure

- **Customers**: Stores customer information, including a unique email for each customer.
- **Products**: Stores product details, including name, price, and available stock.
- **Sales**: Records sales transactions, linking customers to products along with the quantity sold and the date of sale.

## Tables Created

1. **Customers**
    - `customer_id` (INT, PK, Auto Increment)
    - `name` (VARCHAR(100), NOT NULL)
    - `email` (VARCHAR(100), UNIQUE, NOT NULL)
    - `phone` (VARCHAR(15))

2. **Products**
    - `product_id` (INT, PK, Auto Increment)
    - `name` (VARCHAR(100), NOT NULL)
    - `price` (DECIMAL(10, 2), NOT NULL)
    - `stock_quantity` (INT, NOT NULL)

3. **Sales**
    - `sale_id` (INT, PK, Auto Increment)
    - `customer_id` (INT, FK, REFERENCES Customers)
    - `product_id` (INT, FK, REFERENCES Products)
    - `quantity` (INT, NOT NULL)
    - `sale_date` (DATE, NOT NULL)

## Data Insertion

- **Customers**: Adds three customers with names, emails, and phone numbers.
- **Products**: Adds three products with names, prices, and initial stock quantities.
- **Sales**: Records sales transactions linking customers to products.

## Queries and Reports

1. **List All Sales**:
   - Shows all sales, including customer names and product names:
   ```sql
   SELECT Vendas.venda_id, Clientes.nome AS nome_cliente, Produtos.nome AS nome_produto, Vendas.quantidade, Vendas.data_venda
   FROM Vendas
   JOIN Clientes ON Vendas.cliente_id = Clientes.cliente_id
   JOIN Produtos ON Vendas.produto_id = Produtos.produto_id;
