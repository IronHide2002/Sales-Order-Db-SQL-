# SQL Queries for Sales Data Management

## Overview
This repository contains SQL scripts to manage and analyze sales data involving products, customers, employees, and orders. It includes queries for key business insights, such as total sales, average purchase costs, order statuses, and customer-product relationships.

The dataset involves four tables:
1. **Products**: Contains product details like price, name, and release date.
2. **Customers**: Stores customer information such as name and email.
3. **Employees**: Contains employee names and their roles in handling sales.
4. **Sales Orders**: Tracks each sale's details, including quantity, status, customer, and employee involved.

---
## Table of Contents
- [Setup](#setup)
- [Tables and Sample Data](#tables-and-sample-data)
- [Queries](#queries)
  - [Basic Insights](#basic-insights)
  - [Intermediate Queries](#intermediate-queries)
  - [Advanced Analysis](#advanced-analysis)
- [Key Highlights](#key-highlights)

---
## Setup
1. Clone this repository to your local machine:
   ```bash
   git clone https://github.com/yourusername/sales-data-sql.git
   ```
2. Run the SQL script in your PostgreSQL-compatible database.
3. Use a tool like **pgAdmin** or **DBeaver** to visualize results.

---
## Tables and Sample Data
### 1. **Products**
```sql
CREATE TABLE products (
    id INT GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
    name VARCHAR(100),
    price FLOAT,
    release_date DATE
);
```
| id | name          | price | release_date |
|----|---------------|-------|--------------|
| 1  | iPhone 15     | 800   | 2023-08-22   |
| 2  | Macbook Pro   | 2100  | 2022-10-12   |
| 3  | Apple Watch 9 | 550   | 2022-09-04   |
| 4  | iPad          | 400   | 2020-08-25   |
| 5  | AirPods       | 420   | 2024-03-30   |

### 2. **Customers**
```sql
CREATE TABLE customers (
    id INT GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(30)
);
```
| id | name          | email            |
|----|---------------|------------------|
| 1  | Meghan Harley | mharley@demo.com |
| 2  | Rosa Chan     | rchan@demo.com   |
| 3  | Logan Short   | lshort@demo.com  |
| 4  | Zaria Duke    | zduke@demo.com   |

### 3. **Employees**
```sql
CREATE TABLE employees (
    id INT GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
    name VARCHAR(100)
);
```
| id | name         |
|----|--------------|
| 1  | Nina Kumari  |
| 2  | Abrar Khan   |
| 3  | Irene Costa  |

### 4. **Sales Orders**
```sql
CREATE TABLE sales_order (
    order_id INT GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
    order_date DATE,
    quantity INT,
    prod_id INT REFERENCES products(id),
    status VARCHAR(20),
    customer_id INT REFERENCES customers(id),
    emp_id INT REFERENCES employees(id)
);
```
| order_id | order_date | quantity | prod_id | status     | customer_id | emp_id |
|----------|------------|----------|---------|------------|-------------|--------|
| 1        | 2024-01-01 | 2        | 1       | Completed  | 1           | 1      |
| 2        | 2024-01-01 | 3        | 1       | Pending    | 2           | 2      |
| 3        | 2024-01-02 | 3        | 2       | Completed  | 3           | 2      |
| ...      | ...        | ...      | ...     | ...        | ...         | ...    |

## Key Highlights
- The script demonstrates the use of:
  - **Joins**: INNER JOIN, LEFT JOIN, and RIGHT JOIN.
  - **Aggregation**: Using `SUM`, `COUNT`, `AVG`, and `GROUP BY`.
  - **Subqueries**: For advanced filtering and comparisons.
  - **Case-insensitive queries**: Using `LOWER()` or `UPPER()`.


