## 1. Introduction to Databases

- **Definition:**
  A **database** is an organized collection of data that can be easily accessed, managed, and updated. It provides a way to store information systematically.

- **Types of Databases**:
- Relational Databases: Organize data in tables (rows and columns). Example: MySQL, PostgreSQL.
- Non-Relational Databases (NoSQL): Use different data models such as key-value pairs, documents, graphs. Example: MongoDB.

---

## 2. SQL (Structured Query Language)

- **Definition:**
  SQL is a standardized programming language used to manage and manipulate relational databases.

- **Use Cases:**
  - Querying data (SELECT)
  - Inserting data (INSERT)
  - Updating data (UPDATE)
  - Deleting data (DELETE)
  - Creating tables (CREATE)
  - Managing user access (GRANT, REVOKE)

```
-- Example: SELECT query to fetch data from a table.
SELECT * FROM employees;
-- Fetch all rows from 'employees' table
```

---

## 3. SQL Keywords

Here’s a quick overview of commonly used SQL keywords:

- **CREATE**: Used to create a database or table.
- **DATABASE**: Refers to a collection of organized data.
- **TABLE**: Refers to a collection of rows and columns.
- **USE**: Selects which database to use.
- **INTEGER**: A data type for numbers.
- **SELECT**: Retrieves data from a table.
- **FROM**: Specifies the table to retrieve data from.
- **WHERE**: Filters records based on conditions.
- **ORDER BY**: Sorts result sets by one or more columns.
- **INSERT INTO**: Adds data to a table.
- **UPDATE**: Modifies existing data in a table.
- **DELETE**: Removes data from a table.

```
-- Example: Create a new table
CREATE TABLE employees (
    employee_id INT PRIMARY KEY,  -- A primary key for unique identification
    first_name VARCHAR(50),       -- Employee's first name
    last_name VARCHAR(50),        -- Employee's last name
    hire_date DATE                -- Date when the employee was hired
);
```

---

## 4. SQL Queries: Basic Operations

**SELECT (Querying Data)**

- **Purpose**: Retrieves data from a database table.

```
-- Fetch all columns from 'employees' table
SELECT * FROM employees;

-- Fetch specific columns (first_name, last_name)
SELECT first_name, last_name FROM employees;
```

**INSERT (Adding Data)**

- **Purpose**: Inserts data into a table.

```
-- Insert a new record into the 'employees' table
INSERT INTO employees (employee_id, first_name, last_name, hire_date)
VALUES (1, 'John', 'Doe', '2023-05-01');
```

**UPDATE (Modifying Data)**

- **Purpose**: Updates existing records.

```
-- Update an employee's last name where the employee ID is 1
UPDATE employees
SET last_name = 'Smith'
WHERE employee_id = 1;
```

**DELETE (Removing Data)**

- **Purpose**: Deletes data from a table.

```
-- Delete a record where the employee ID is 1
DELETE FROM employees
WHERE employee_id = 1;
```

---

## 5. SQL Joins

Joins are used to combine rows from two or more tables based on a related column.

- **INNER JOIN**: Returns records that have matching values in both tables.
- **LEFT JOIN**: Returns all records from the left table and matched records from the right table.
- **RIGHT JOIN**: Returns all records from the right table and matched records from the left table.
- **FULL OUTER JOIN**: Returns all records when there is a match in either left or right table.
- **CROSS JOIN**: Returns the Cartesian product of two tables.

```
-- Example of INNER JOIN
SELECT employees.first_name, departments.department_name
FROM employees
INNER JOIN departments ON employees.department_id = departments.department_id;
```

---

## 6. SQL Functions

**Aggregate Functions**
Used to perform calculations on multiple rows of a table.

- **AVG()**: Returns the average value.
- **COUNT()**: Returns the number of rows.
- **SUM()**: Returns the total sum.
- **MIN()**: Returns the smallest value.
- **MAX()**: Returns the largest value.

```
-- Get the total count of employees
SELECT COUNT(*) FROM employees;

-- Calculate the average salary from 'salaries' table
SELECT AVG(salary) FROM salaries;
```

---

## 7. SQL String Functions

- **CONCAT()**: Concatenates two or more strings.
- **LEFT()**: Extracts a specified number of characters from the left.
- **RIGHT()**: Extracts a specified number of characters from the right.
- **SUBSTRING()**: Extracts a substring starting from a specified position.
- **LOWER()**: Converts a string to lowercase.
- **UPPER()**: Converts a string to uppercase.
- **LEN()**: Returns the length of a string.

```
-- Concatenate first_name and last_name
SELECT CONCAT(first_name, ' ', last_name) AS full_name FROM employees;

-- Extract first 5 characters from employee name
SELECT LEFT(first_name, 5) FROM employees;
```

---

## 8. Date Functions

- **GETDATE()**: Returns the current date and time.
- **DATEADD()**: Adds a time period to a date.
- **DATEDIFF()**: Returns the difference between two dates.
- **DATEPART()**: Returns a specific part of a date (year, month, day).

```
-- Get current date and time
SELECT GETDATE();

-- Add 4 days to the current date
SELECT DATEADD(day, 4, GETDATE());

-- Calculate the difference in days between two dates
SELECT DATEDIFF(day, '2023-05-01', '2023-06-01');
```

---

## 9. Keys in SQL

Keys are used to define relationships between tables and uniquely identify records.

- **Primary Key**: Uniquely identifies each record in a table.
- **Foreign Key**: Links two tables by referring to the primary key of another table.
- **Unique Key**: Ensures all values in a column are unique.
- **Super Key**: A set of one or more columns that can uniquely identify a record.
- **Alternate Key**: A candidate key that is not chosen as the primary key.
- **Candidate Key**: Columns that can qualify as a primary key.
- **Composite Key**: A combination of two or more columns that uniquely identify a record.

**Examples:**

```
-- Example: Primary Key
CREATE TABLE employees (
    employee_id INT PRIMARY KEY,  -- Primary key for unique identification
    first_name VARCHAR(50),
    last_name VARCHAR(50)
);

-- Example: Foreign Key
CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    employee_id INT,
    order_date DATE,
    FOREIGN KEY (employee_id) REFERENCES employees(employee_id)  -- Refers to employee_id in employees table
);

-- Unique Key ensures no duplicates
CREATE TABLE users (
    user_id INT PRIMARY KEY,
    email VARCHAR(100) UNIQUE  -- Email must be unique for each user
);
```

---

## 10. Data Types in SQL

Data types define the type of data that can be stored in a column.

- **CHAR**: Fixed-length string. Length is predefined.
- **VARCHAR**: Variable-length string.
- **INT**: Integer value, typically used for whole numbers.
- **FLOAT/DOUBLE**: Floating point numbers.
- **DATE**: Stores date in YYYY-MM-DD format.
- **TIMESTAMP**: Stores the number of seconds since the Unix epoch (January 1, 1970).

**Examples**

```
-- Example of data types in a table
CREATE TABLE products (
    product_id INT,             -- Integer for product ID
    product_name VARCHAR(100),   -- Variable-length string for product name
    price FLOAT,                -- Floating-point number for price
    manufacture_date DATE       -- Date for manufacturing date
);
```

- **CHAR vs VARCHAR**:
  - CHAR(10) will store exactly 10 characters (even if less are provided, extra spaces are added).
  - VARCHAR(10) will store up to 10 characters (space is not reserved).

---

## 11. Relational Databases

- **Relational Database (RDBMS)**:
  - Works with SQL.
  - Data is organized into tables (rows and columns).
  - Relationships between tables are established via keys (primary and foreign keys).
  - Ideal for structured data with a clear schema.
  - Examples: MySQL, PostgreSQL, SQLite, SQL Server, Oracle.

**Use Case**:

- An e-commerce system with tables for customers, orders, and products:
- customers stores customer information.
- orders stores order details, referencing customers with a foreign key.
- products contains product information, and each order references multiple products.

```
-- Example: Basic schema for an e-commerce system

-- Customers table
CREATE TABLE customers (
    customer_id INT PRIMARY KEY,
    first_name VARCHAR(50),
    last_name VARCHAR(50)
);

-- Orders table
CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    customer_id INT,
    order_date DATE,
    FOREIGN KEY (customer_id) REFERENCES customers(customer_id)  -- Foreign key linking orders to customers
);

-- Products table
CREATE TABLE products (
    product_id INT PRIMARY KEY,
    product_name VARCHAR(100),
    price FLOAT
);
```

---

## 12. Non-Relational Databases (NoSQL)

- **NoSQL Database**:
  - Does not use traditional table structures like relational databases.
  - No fixed schema (schema-less).
  - Data is stored in collections, key-value pairs, or as documents (JSON-like format).
  - Used for unstructured or semi-structured data (e.g., social media data, logs).
- Examples: MongoDB, Cassandra, DynamoDB.

**Use Case**:

- For real-time analytics on streaming data (e.g., log files, user behavior tracking).

- Key differences between SQL and NoSQL:

  - **SQL**: Structured, supports relationships between tables.
  - **NoSQL**: More flexible, handles large amounts of unstructured data, but less suited for relational queries.

```
// Example of a NoSQL document in MongoDB (JavaScript-like syntax)
{
    "_id": ObjectId("507f1f77bcf86cd799439011"),
    "firstName": "John",
    "lastName": "Doe",
    "orders": [
        { "order_id": 1, "product": "Laptop", "quantity": 1 },
        { "order_id": 2, "product": "Mouse", "quantity": 2 }
    ]
}
```

---

## 13. Database Normalization

Normalization is the process of structuring a database to reduce redundancy and improve data integrity.

- 1st Normal Form (1NF):
  Each table cell should contain a single value, and each record must be unique.

- 2nd Normal Form (2NF):
  Achieved when the table is in 1NF and all non-primary key columns are fully dependent on the primary key.

- 3rd Normal Form (3NF):
  Achieved when the table is in 2NF and all non-primary key columns are dependent only on the primary key, and not on other non-key attributes.

**Example:**

```
-- Denormalized table (without normalization)
CREATE TABLE orders_denormalized (
    order_id INT PRIMARY KEY,
    customer_name VARCHAR(100),
    product_name VARCHAR(100),
    order_date DATE
);

-- Normalized (3NF) version
CREATE TABLE customers (
    customer_id INT PRIMARY KEY,
    customer_name VARCHAR(100)
);

CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    customer_id INT,
    order_date DATE,
    FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
);

CREATE TABLE products (
    product_id INT PRIMARY KEY,
    product_name VARCHAR(100),
    price FLOAT
);
```

---

## 14. Indexes

Indexes are used to speed up the retrieval of data from a database. They work like an index in a book, allowing the database to find data without scanning the entire table.

- Clustered Index: The data is physically stored in the order of the index.
- Non-clustered Index: The index and data are stored separately.
  **Example:**

```
-- Create an index on 'last_name' column of 'employees' table
CREATE INDEX idx_last_name ON employees (last_name);
```

---

## 15. Views

A view is a virtual table based on the result of a SQL query. It does not store data physically but presents data from one or more tables.

**Example:**

```
-- Create a view that shows customer orders
CREATE VIEW customer_orders AS
SELECT customers.customer_name, orders.order_date, products.product_name
FROM customers
JOIN orders ON customers.customer_id = orders.customer_id
JOIN products ON orders.product_id = products.product_id;

-- Query the view like a table
SELECT * FROM customer_orders;
```

---

## 16. Transactions

A transaction in SQL ensures a series of SQL queries execute in a safe, atomic manner. If part of the transaction fails, the entire transaction can be rolled back.

- ACID Properties:
  - Atomicity: All operations in a transaction must succeed or fail as a whole.
  - Consistency: Ensures data integrity.
  - Isolation: Each transaction is isolated from others.
  - Durability: Once committed, the transaction’s changes are permanent.
    **Example:**

```
-- Start a transaction
BEGIN TRANSACTION;

-- Transfer funds from account A to B
UPDATE accounts SET balance = balance - 100 WHERE account_id = 1;
UPDATE accounts SET balance = balance + 100 WHERE account_id = 2;

-- Commit the transaction if no errors
COMMIT;

-- If there's an error, rollback the changes
ROLLBACK;
```
