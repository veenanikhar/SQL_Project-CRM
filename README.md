# Customer Relationship Management Database

## Overview

This database schema is designed for an E-Commerce project, managing customer information, orders, products, and order items.

## Tables

### Customers

- `ID` (INT): Primary key, auto-incremented.
- `NAME` (VARCHAR): Customer name.
- `ADDRESS` (TEXT): Customer address.

### Orders

- `ID` (INT): Primary key, auto-incremented.
- `CUSTOMER_ID` (INT): Foreign key referencing `CUSTOMERS(ID)`.
- `ORDER_NUMBER` (VARCHAR): Order number.
- `ORDER_AT` (DATETIME): Order timestamp.

### Products

- `ID` (INT): Primary key, auto-incremented.
- `NAME` (VARCHAR): Product name.
- `PRICE` (DECIMAL): Product price.

### Order Items

- `ID` (INT): Primary key, auto-incremented.
- `ORDER_ID` (INT): Foreign key referencing `ORDERS(ID)`.
- `PRODUCT_ID` (INT): Foreign key referencing `PRODUCTS(ID)`.
- `PRICE` (DECIMAL): Item price.
- `QUANTITY` (BIGINT): Quantity of products in the order.

## Foreign Key Relationships

- `ORDERS.CUSTOMER_ID` references `CUSTOMERS.ID`.
- `ORDER_ITEMS.ORDER_ID` references `ORDERS.ID`.
- `ORDER_ITEMS.PRODUCT_ID` references `PRODUCTS.ID`.

## Usage

1. **Database Setup:**
   - Execute the SQL script provided in `ECommerce_Schema.sql` to create the necessary database tables.
   - Establish foreign key relationships by executing the SQL script in `ECommerce_Schema.sql`.

2. **Common Queries and Operations:**
   - Retrieve all customers: `SELECT * FROM CUSTOMERS;`
   - Retrieve all orders: `SELECT * FROM ORDERS;`
   - Retrieve all products: `SELECT * FROM PRODUCTS;`
   - Retrieve all order items: `SELECT * FROM ORDER_ITEMS;`

3. **Advanced Queries:**
   - Retrieve orders for a specific customer: `SELECT * FROM ORDERS WHERE CUSTOMER_ID = 1;`
   - Calculate the total price of an order: `SELECT SUM(PRICE * QUANTITY) AS TOTAL_PRICE FROM ORDER_ITEMS WHERE ORDER_ID = 123;`
   - Retrieve address starting with vowels : `SELECT DISTINCT ADDRESS FROM CUSTOMERS WHERE UPPER(LEFT(ADDRESS, 1)) IN ('A', 'E', 'I', 'O', 'U');`
     
4. **Database Schema Diagram**

![DB2](https://github.com/veenanikhar/SQL_Project-CRM/assets/128398071/1bf30997-447e-4963-9231-91b06b130607)
