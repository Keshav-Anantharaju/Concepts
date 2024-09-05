# SQL: Structured Query Language

## Content

1. [Structure Query Language](#sql-structured-query-language)

    - [Introduction to SQL](#introduction-to-sql)
    - [Basics of SQL](#basic-sql-commands)
    - [Operations on Database (CRUD)](#crud-operations)
    - [Database Management Systems (DBMS)](#types-of-database-management-systems-dbms)
    - [Relational Database Management Systems (RDBMS)](#relational-database-management-system-rdbms)

2. [Data Types](#data-types)

    - [Numerical](#1-numerical)
    - [Character](#2-character)
    - [Large Objects](#3-large-objects)
    - [Date](#4-date)

3. [Constraints](#constraints)

    - [UNIQUE Constraint](#1-unique-constraint)
    - [NOT NULL Constraint](#2-not-null-constraint)
    - [CHECK Constraint](#3-check-constraint)
    - [Foreign Key Constraint](#4-foreign-key-constraint)
    - [Primary Key Constraint](#5-primary-key-constraint)
    - [Default Constraint](#6-default-constraint)
    - [Serial Constraint](#7-serial-constraint)

4. [Types of Commands](#sql-commands-overview)

    - [DDL (Data Definition Language)](#1-ddl-data-definition-language)
    - [DML (Data Manipulation Language)](#2-dml-data-manipulation-language)
    - [TCL (Transaction Control Language)](#3-tcl-transaction-control-language)
    - [DCL (Data Control Language)](#4-dcl-data-control-language)
    - [DQL (Data Query Language)](#5-dql-data-query-language)

5. [Basic SQL Commands](#basic-sql-commands)

6. [Functions](#functions)

    - [Aggregate Functions](#1-aggregate-functions)
    - [Scalar Functions](#2-scalar-functions)

7. [Joins](#joins)

    - [INNER JOIN](#1-inner-join)
    - [LEFT JOIN (LEFT OUTER JOIN)](#2-left-join-or-left-outer-join)
    - [RIGHT JOIN (RIGHT OUTER JOIN)](#3-right-join-or-right-outer-join)
    - [FULL JOIN (FULL OUTER JOIN)](#4-full-join-or-full-outer-join)
    - [CROSS JOIN](#5-cross-join)

8. [Filters in Queries](#sql-clauses)

    - [WHERE](#where-clause)
    - [HAVING](#having-clause)

9. [Normalization](#database-normalization)
    - [First Normal Form (1NF)](#first-normal-form-1nf)
    - [Second Normal Form (2NF)](#second-normal-form-2nf)
    - [Third Normal Form (3NF)](#third-normal-form-3nf)
    - [Boyce-Codd Normal Form (BCNF)](#boyce-codd-normal-form-bcnf)
10. [Indexes](#indexes)

11. [ACID Properties](#acid-properties)

12. [Locking Mechanism](#locking-mechanism)

13. [Database Isolation Levels](#database-isolation-levels)

14. [Triggers](#triggers)

12. [CAP Theorem](#cap-theorem)

13. [Reference](#references)

### Introduction to SQL

**Structured Query Language (SQL)** is a standard programming language used to manage and manipulate relational databases. Developed by IBM in the 1970s, SQL enables users to create, update, delete, and retrieve data from databases such as MySQL, Oracle, and PostgreSQL. SQL serves as a bridge to interact with databases through various operations.

### Basics of SQL

-   **Data:** Raw facts about entities.
-   **Attribute:** A property of an entity.
-   **Entity/Object:** An object or concept that is represented in the database.
-   **Database:** An organized collection of data stored systematically.

### CRUD Operations

The acronym `CRUD` stands for the primary operations performed in databases. Each letter corresponds to a fundamental SQL statement:

| **CRUD** | **SQL Statement** |
| -------- | ----------------- |
| Create   | INSERT            |
| Read     | SELECT            |
| Update   | UPDATE            |
| Delete   | DELETE            |

### Types of Database Management Systems (DBMS)

-   **Object-Oriented Databases:** Data is represented as objects, similar to object-oriented programming.
-   **Distributed Databases:** Composed of multiple files across different locations, which can be spread over several networks or computers.
-   **NoSQL Databases:** Handle unstructured and semi-structured data without a fixed schema, unlike traditional relational databases.
-   **Graph Databases:** Use graph structures for storing data, focusing on the relationships between entities.
-   **Open Source Databases:** Databases with source code available for modification and distribution. They can be either SQL or NoSQL.
-   **Cloud Databases:** Data is stored on cloud platforms, including private, public, or hybrid clouds.
-   **Relational Databases:** Data is organized into tables with rows and columns. Relational databases adhere to E.F. Codd’s rules.

### Relational Database Management System (RDBMS)

An RDBMS uses tables (or relations) to store data in rows and columns. It follows E.F. Codd’s rules and employs SQL for communication and data manipulation.

#### E.F. Codd’s Rules

1. **Atomicity:** Data in a cell must be atomic, meaning indivisible.
2. **Normalization:** Data is stored in multiple tables with relationships established through keys.
3. **Data Integrity:** Data types and constraints are used to validate the data, though constraints are optional.
4. **Consistency:** Data types are required for tables to ensure consistency.

## Data Types

### 1. Numerical

-   **BIT:** Represents binary values. Size ranges from 1 to 64 bits.
-   **INT:** Stores integers, with a range from -2,147,483,648 to 2,147,483,647.
-   **FLOAT:** Stores floating-point numbers with a specified precision and scale.
-   **DOUBLE:** Represents larger floating-point numbers.
-   **DECIMAL:** Used for fixed-point numbers with precision and scale.

### 2. Character

-   **CHAR:** Fixed-length strings, up to 255 characters.
-   **VARCHAR:** Variable-length strings, up to 65,535 characters.
-   **TEXT:** Holds strings with a maximum length of 255 characters.
-   **TINYTEXT:** Holds strings with a maximum length of 255 characters.
-   **MEDIUMTEXT:** Holds strings up to 16,777,215 characters.
-   **LONGTEXT:** Holds strings up to 4,294,967,295 characters.

### 3. Large Objects

-   **CLOB:** Stores large amounts of character data up to 4 GB.
-   **BLOB:** Stores binary large objects like images or documents, up to 65,535 bytes.

### 4. Date

-   **DATE:** Stores dates in 'YYYY-MM-DD' format, ranging from '1000-01-01' to '9999-12-31'.

## Constraints

Certainly! Here’s a detailed explanation of SQL constraints:

---

## Constraints

-   In SQL, constraints are rules applied to table columns to ensure the accuracy and integrity of the data.

### 1. UNIQUE Constraint

Ensures that all values in a column are distinct and unique across the table.

**Syntax:**

```sql
CREATE TABLE table_name (
    column_name datatype UNIQUE
);
```

**Example:**

```sql
CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    Email VARCHAR(255) UNIQUE
);
```

The `Email` column must contain unique values, no two employees can have the same email address.

### 2. NOT NULL Constraint

Ensures that a column cannot have `NULL` values. This constraint enforces that a field must contain a value and cannot be left empty.

**Syntax:**

```sql
CREATE TABLE table_name (
    column_name datatype NOT NULL
);
```

**Example:**

```sql
CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    FirstName VARCHAR(50) NOT NULL,
    LastName VARCHAR(50) NOT NULL
);
```

Here, both `FirstName` and `LastName` columns must contain a value; they cannot be NULL.

### 3. CHECK Constraint

Ensures that all values in a column satisfy a specific condition.

**Syntax:**

```sql
CREATE TABLE table_name (
    column_name datatype CHECK (condition)
);
```

**Example:**

```sql
CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    Salary DECIMAL(10, 2) CHECK (Salary > 0)
);
```

The `Salary` column must have a value greater than 0. The CHECK constraint ensures that invalid salary values (like negative numbers) are not inserted.

### 4. FOREIGN KEY Constraint

Establishes a relationship between columns in two tables. It ensures that the value in one table corresponds to a value in another table, thus maintaining referential integrity.

**Syntax:**

```sql
CREATE TABLE table_name (
    column_name datatype,
    FOREIGN KEY (column_name) REFERENCES other_table(column_name)
);
```

**Example:**

```sql
CREATE TABLE Departments (
    DepartmentID INT PRIMARY KEY,
    DepartmentName VARCHAR(50)
);

CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    DepartmentID INT,
    FOREIGN KEY (DepartmentID) REFERENCES Departments(DepartmentID)
);
```

The `DepartmentID` in the `Employees` table must match an existing `DepartmentID` in the `Departments` table. This enforces referential integrity between the two tables.

### 5. PRIMARY KEY Constraint

Uniquely identifies each record in a table. A primary key constraint ensures that the column(s) designated as the primary key are unique and not NULL.

**Syntax:**

```sql
CREATE TABLE table_name (
    column_name datatype PRIMARY KEY
);
```

**Example:**

```sql
CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    FirstName VARCHAR(50),
    LastName VARCHAR(50)
);
```

The `EmployeeID` column uniquely identifies each employee and cannot contain NULL values. The primary key constraint ensures that each employee has a unique ID.

### 6. DEFAULT Constraint

Provides a default value for a column when no value is specified during the insertion of a record. This ensures that a column will always have a default value even if not explicitly provided.

**Syntax:**

```sql
CREATE TABLE table_name (
    column_name datatype DEFAULT default_value
);
```

**Example:**

```sql
CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    FirstName VARCHAR(50),
    Status VARCHAR(10) DEFAULT 'Active'
);
```

If no value is provided for the `Status` column during insertion, it will default to 'Active'.

### 7. SERIAL Constraint

Automatically generates a unique value for the column each time a new record is inserted. It is commonly used for primary key columns.

**Syntax:**

```sql
CREATE TABLE table_name (
    column_name datatype SERIAL
);
```

**Example:**

```sql
CREATE TABLE Employees (
    EmployeeID INT SERIAL
    FirstName VARCHAR(50),
    LastName VARCHAR(50)
);
```

The `EmployeeID` will automatically increment with each new record, providing a unique identifier for each employee.### SQL Commands Overview

## SQL Commands overview

SQL (Structured Query Language) commands are grouped into different categories based on their functionality.

### 1. DDL (Data Definition Language)

**DDL** commands are used to define, modify, or remove the structure of database objects such as tables, indexes, and schemas. These commands deal with the structure or schema of the database.

-   **CREATE**: Used to create new database objects (tables, views, indexes, schemas).

    ```sql
    CREATE TABLE employees (
        id INT PRIMARY KEY,
        name VARCHAR(50),
        position VARCHAR(50),
        salary DECIMAL(10, 2)
    );
    ```

-   **ALTER**: Used to modify the structure of an existing database object (e.g., add, remove, or modify columns in a table).

    ```sql
    ALTER TABLE employees ADD department VARCHAR(50);
    ```

-   **DROP**: Used to delete database objects (e.g., tables, views).

    ```sql
    DROP TABLE employees;
    ```

-   **TRUNCATE**: Deletes all the data from a table without removing the table structure.

    ```sql
    TRUNCATE TABLE employees;
    ```

-   **RENAME**: Changes the name of a table or other database objects.

    ```sql
    RENAME TABLE employees TO staff;
    ```

-   **Characteristics:**
    -   **Autocommit**: Changes made by DDL commands are automatically committed, which means they cannot be rolled back unless explicitly handled with transactions.
    -   **Irreversible**: Some DDL commands, like `DROP` or `TRUNCATE`, can be destructive as they permanently remove data or structures.

### 2. DML (Data Manipulation Language)

**DML** commands are used to retrieve, store, modify, and delete data in database tables. These commands deal with the manipulation of data within the existing structure (tables).

-   **INSERT**: Adds new rows of data to a table.

    ```sql
    INSERT INTO employees (id, name, position, salary)
    VALUES (1, 'John Doe', 'Manager', 75000.00);
    ```

-   **UPDATE**: Modifies existing data in a table based on certain conditions.

    ```sql
    UPDATE employees
    SET salary = 80000.00
    WHERE id = 1;
    ```

-   **DELETE**: Removes rows from a table based on conditions.

    ```sql
    DELETE FROM employees
    WHERE id = 1;
    ```

-   **Characteristics:**
    -   **Transactional**: DML commands are part of a transaction, meaning the changes can be **committed** or **rolled back** if something goes wrong.
    -   **Affects data**: These commands do not affect the schema or structure of the table, but only the data within the table.

### 3. TCL (Transaction Control Language)

**TCL** commands are used to manage transactions in the database. A **transaction** is a sequence of one or more SQL commands that are executed as a single unit of work, and TCL controls how these transactions are handled.

-   **BEGIN:** Starts a new transaction.
-   **COMMIT**: Saves all changes made during the current transaction permanently to the database.

    ```sql
    COMMIT;
    ```

-   **ROLLBACK**: Reverts changes made during the current transaction to the last committed state, undoing any operations performed after the last `COMMIT`.

    ```sql
    ROLLBACK;
    ```

-   **SAVEPOINT**: Sets a savepoint within a transaction, allowing a partial rollback to that point without rolling back the entire transaction.

    ```sql
    SAVEPOINT sp1;
    ```

-   **RELEASE SAVEPOINT**: Removes a previously defined savepoint from the transaction context.
    ```sql
    RELEASE SAVEPOINT sp1;
    ```
-   **ROLLBACK TO SAVEPOINT**: Rolls back the transaction to a specified savepoint.

    ```sql
    ROLLBACK TO SAVEPOINT savepoint_name;
    ```

-   **Characteristics:**

    -   **Atomicity**: TCL commands ensure that a transaction is treated as a single, indivisible unit, so that all or none of the changes made during the transaction are saved.
    -   **Consistency**: These commands are crucial for maintaining the integrity of the database, especially in cases where multiple SQL commands are executed together.

### 4. DCL (Data Control Language)

**DCL** commands are used to control access to data within the database, defining permissions and access rights for users.

-   **GRANT**: Gives specific privileges to users or roles.

    ```sql
    GRANT SELECT, INSERT ON employees TO user1;
    ```

-   **REVOKE**: Removes specific privileges from users or roles.

    ```sql
    REVOKE INSERT ON employees FROM user1;
    ```

-   **Characteristics:**

    -   **Security**: DCL commands are essential for managing security and ensuring that only authorized users can perform certain actions on the database.
    -   **Privileges**: Privileges can be assigned at different levels, including tables, views, or even the entire database.

### 5. **DQL (Data Query Language)**

**DQL** commands are used to query or retrieve data from the database. Although some people classify DQL as part of DML, it's often considered a separate category because it focuses solely on data retrieval.

-   **SELECT**: Retrieves data from one or more tables. The `SELECT` statement can include various clauses like `WHERE`, `ORDER BY`, `GROUP BY`, and `HAVING` to filter, sort, and group the results.

    ```sql
    SELECT name, position, salary
    FROM employees
    WHERE salary > 50000;
    ```

-   **Characteristics:**

    -   **Non-destructive**: `SELECT` queries do not modify the database; they only retrieve and display data.
    -   **Flexibility**: The `SELECT` statement is highly flexible and can be combined with various clauses and operators to retrieve precise data from the database.

## Basic SQL Commands

**1. SELECT**

The `SELECT` statement retrieves data from one or more tables.

```sql
SELECT column1, column2, ...
FROM table_name;
```

Example:

```sql
SELECT FirstName, LastName
FROM Employees;
```

**2. DISTINCT**

The `DISTINCT` keyword removes duplicate rows from the result set.

```sql
SELECT DISTINCT column1, column2, ...
FROM table_name;
```

Example:

```sql
SELECT DISTINCT City
FROM Customers;
```

**3. WHERE**

The `WHERE` clause filters records based on specified conditions.

```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

Example:

```sql
SELECT EmployeeID, FirstName, LastName, Salary
FROM Employees
WHERE Salary > 50000;
```

**4. LIKE**

The `LIKE` operator searches for a specified pattern in a column.

```sql
SELECT column1, column2, ...
FROM table_name
WHERE column_name LIKE pattern;
```

Example:

```sql
SELECT FirstName, LastName
FROM Employees
WHERE LastName LIKE 'S%';
```

## Functions

### 1. Aggregate Functions

-   **SUM():** Calculates the sum of values in a column.

    ```sql
    SELECT SUM(column_name)
    FROM table_name;
    ```

-   **AVG():** Computes the average of values in a column.

    ```sql
    SELECT AVG(column_name)
    FROM table_name;
    ```

-   **COUNT():** Counts rows or non-null values in a column.

    ```sql
    SELECT COUNT(column_name)
    FROM table_name;
    ```

-   **MIN():** Finds the minimum value in a column.

    ```sql
    SELECT MIN(column_name)
    FROM table_name;
    ```

-   **MAX():** Finds the maximum value in a column.
    ```sql
    SELECT MAX(column_name)
    FROM table_name;
    ```

### 2. Scalar Functions

-   **String Functions:**

    -   **UPPER()**: Converts a string to uppercase.

        ```sql
        SELECT UPPER(column_name)
        FROM table_name;
        ```

    -   **LOWER()**: Converts a string to lowercase.
        ```sql
        SELECT LOWER(column_name)
        FROM table_name;
        ```
    -   **LEFT()**: Extracts a specified number of characters from the beginning of a string.
        ```sql
        SELECT LEFT(column_name, number_of_characters)
        FROM table_name;
        ```
    -   **RIGHT()**: Extracts a specified number of characters from the end of a string.
        ```sql
        SELECT RIGHT(column_name, number_of_characters)
        FROM table_name;
        ```

-   **Numeric Functions:**
    -   **ROUND()**: Rounds a numeric value to a specified number of decimal places.
        ```sql
        SELECT ROUND(column_name, number_of_decimal_places)
        FROM table_name;
        ```
    -   **ABS()**: Returns the absolute value of a number.
        ```sql
        SELECT ABS(column_name)
        FROM table_name;
        ```
    -   **CEILING()**: Rounds a number up to the nearest integer.
        ```sql
        SELECT CEILING(column_name)
        FROM table_name;
        ```
    -   **FLOOR()**: Rounds a number down to the nearest integer.
        ```sql
        SELECT FLOOR(column_name)
        FROM table_name;
        ```
-   **Date and Time Functions:** `GETDATE()`, `DATEADD()`, `DATEDIFF()`

## Joins

Joins combine rows from two or more tables based on related columns.

### 1. INNER JOIN

Returns rows with matches in both tables.

```sql
SELECT columns
FROM table1
INNER JOIN table2 ON table1.column = table2.column;
```

### 2. LEFT JOIN (or LEFT OUTER JOIN)

Returns all rows from the left table and matched rows from the right table.

```sql
SELECT columns
FROM table1
LEFT JOIN table2 ON table1.column = table2.column;
```

### 3. RIGHT JOIN (or RIGHT OUTER JOIN)

Returns all rows from the right table and matched rows from the left table.

```sql
SELECT columns
FROM table1
RIGHT JOIN table2 ON table1.column = table2.column;
```

### 4. FULL JOIN (or FULL OUTER JOIN)

Returns all rows with matches in either table, or NULLs if no match.

```sql
SELECT columns
FROM table1
FULL JOIN table2 ON table1.column = table2.column;
```

### 5. CROSS JOIN

Returns the Cartesian product of both tables, meaning all possible combinations.

```sql
SELECT columns
FROM table1
CROSS JOIN table2;
```

## SQL Clauses

### WHERE Clause

The `WHERE` clause is used to filter records based on specified conditions. It is used to retrieve only the rows that meet certain criteria.

**Syntax:**

```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

**Example:**

```sql
SELECT first_name, last_name
FROM employees
WHERE department = 'Sales';
```

This query retrieves the first and last names of employees who work in the 'Sales' department.

### HAVING Clause

The `HAVING` clause is used to filter groups of rows after the `GROUP BY` clause has been applied. It is used in conjunction with aggregate functions.

**Syntax:**

```sql
SELECT column1, AGGREGATE_FUNCTION(column2)
FROM table_name
GROUP BY column1
HAVING condition;
```

**Example:**

```sql
SELECT department, COUNT(*)
FROM employees
GROUP BY department
HAVING COUNT(*) > 10;
```

This query returns the departments that have more than 10 employees.

## Database Normalization

### First Normal Form (1NF)

The First Normal Form (1NF) ensures that each column in a table contains only atomic (indivisible) values and that each column contains values of a single type. It eliminates repeating groups and ensures that each column contains unique values.

**Criteria:**

1. Each table has a clear primary key.
2. All entries in a column are of the same data type.
3. Each column contains only atomic values (i.e., indivisible).

**Example:** If a table has a column with multiple values separated by commas, it is not in 1NF. Each value should be in a separate row or column.

### Second Normal Form (2NF)

The Second Normal Form (2NF) builds on 1NF by ensuring that all non-key columns are fully functionally dependent on the entire primary key. This eliminates partial dependencies.

**Criteria:**

1. The table must be in 1NF.
2. All non-key columns must be fully functionally dependent on the primary key.

**Example:** In a table with a composite key (multiple columns forming the primary key), if a non-key column is dependent on only a part of the composite key, it violates 2NF.

### Third Normal Form (3NF)

The Third Normal Form (3NF) ensures that all the columns are functionally dependent only on the primary key and not on other non-key columns. This removes transitive dependencies.

**Criteria:**

1. The table must be in 2NF.
2. There should be no transitive dependencies (i.e., non-key columns should not depend on other non-key columns).

**Example:** If a table has a column that depends on another non-key column, rather than directly on the primary key, it violates 3NF.

### Boyce-Codd Normal Form (BCNF)

The Boyce-Codd Normal Form (BCNF) is a stronger version of 3NF. It addresses certain types of anomalies that 3NF does not handle.

**Criteria:**

1. The table must be in 3NF.
2. For every functional dependency, the left side of the dependency must be a superkey.

**Example:** If a table has multiple candidate keys and some columns depend on a candidate key that is not a superkey, it violates BCNF.

## Indexes

**Purpose:** Indexes are used to speed up the retrieval of rows from a table by creating an ordered structure that allows quick lookups. They improve query performance, particularly for large datasets.

**Types:**

-   **B-Tree Indexes:** The most common type, useful for most queries.
-   **Hash Indexes:** Useful for equality comparisons.
-   **GiST (Generalized Search Tree) Indexes:** Useful for complex queries like range queries.
-   **GIN (Generalized Inverted Index) Indexes:** Useful for indexing composite values and arrays.

**Syntax:**

```sql
CREATE INDEX index_name
ON table_name (column_name);
```

**Example:**

```sql
CREATE INDEX idx_last_name
ON employees (last_name);
```

This creates an index on the `last_name` column of the `employees` table.

## ACID Properties

ACID properties ensure reliable processing of database transactions. They stand for Atomicity, Consistency, Isolation, and Durability.

1. **Atomicity**:
Ensures that all operations within a transaction are completed successfully or none are. It is an "all-or-nothing" approach.

2. **Consistency**:
Ensures that a transaction brings the database from one valid state to another, maintaining database integrity.

3. **Isolation**:
Ensures that transactions are executed in isolation from one another, meaning the interim results of a transaction are not visible to others until the transaction is complete.

4. **Durability**:
Ensures that once a transaction is committed, the changes are permanent and survive any subsequent system failures.

## Locking Mechanism

Locking mechanisms control concurrent access to database resources to ensure data consistency and prevent conflicts.

**Types:**

-   **Row-Level Locking:** Locks individual rows to allow multiple transactions to work on different rows simultaneously.
-   **Table-Level Locking:** Locks entire tables, which can be more restrictive but simpler.

**Example:**

```sql
BEGIN;
SELECT * FROM accounts WHERE account_id = 1 FOR UPDATE;
-- perform operations
COMMIT;
```

This locks the selected row until the transaction is completed.

## Database Isolation Levels
![Database Isolation Levels](https://github.com/user-attachments/assets/2c7cd5af-e293-4414-82e9-5111dd03dd84)


Isolation levels define the degree to which the operations in one transaction are isolated from those in other concurrent transactions.

1. **Read Uncommitted**: Allows transactions to read uncommitted changes made by other transactions. This level provides the least isolation and may result in dirty reads.

2. **Read Committed**: Ensures that transactions can only read committed changes. It prevents dirty reads but does not prevent non-repeatable reads.

3. **Repeatable Read**: Ensures that if a transaction reads a row, it will see the same data if it reads the row again. It prevents dirty reads and non-repeatable reads but may allow phantom reads.

4. **Serializable**: Provides the highest level of isolation, ensuring that transactions execute in a manner that makes them appear as though they were executed serially. It prevents dirty reads, non-repeatable reads, and phantom reads.

## Triggers

Triggers are automatic actions executed in response to certain events on a table or view. They can enforce complex business rules or maintain data integrity.

**Types:**

-   **BEFORE Trigger:** Executes before an insert, update, or delete operation.
-   **AFTER Trigger:** Executes after an insert, update, or delete operation.
-   **INSTEAD OF Trigger:** Executes in place of the insert, update, or delete operation.

**Syntax:**

```sql
CREATE TRIGGER trigger_name
BEFORE / AFTER
INSERT/UPDATE/DELETE
ON TABLE_NAME
FOR EACH ROW
EXECUTE FUNCTION trigger_function();
```

**Example:**

```sql
CREATE TRIGGER safety
ON DATABASE
FOR
create_table,alter_table,drop_table
AS
PRINT 'You can not create,drop and alter tab
```

This trigger logs message when user try to create/alter/drop a table from database.

## CAP Theorem

The CAP Theorem, also known as Brewer's Theorem, states that a distributed data store cannot simultaneously guarantee all three of the following:

1. **Consistency:** All nodes see the same data at the same time.
2. **Availability:** Every request receives a response, without guarantee that it contains the most recent data.
3. **Partition Tolerance:** The system continues to operate despite network partitions.

The theorem implies that a distributed system can achieve at most two of the three properties.

**Example:**
-   **CP Systems (Consistency and Partition Tolerance):** Traditional relational databases.
-   **AP Systems (Availability and Partition Tolerance):** NoSQL databases like Cassandra.
-   **CA Systems (Consistency and Availability):** Systems that require a reliable network and cannot handle network partitions.


## References

-   [Geeks For Geeks - Database and Constraints](https://www.geeksforgeeks.org/what-is-database/)
-   [JAVA T Point - SQL Data Types](https://www.javatpoint.com/sql-data-types)
-   [Geeks For Geeks - SQL Joins](https://www.geeksforgeeks.org/sql-join-set-1-inner-left-right-and-full-joins/)

For additional learning, consider these resources:

-   [SQL Tutorials for Beginners by MOSH](https://youtu.be/7S_tz1z_5bA?si=MmWdK9AtoBjv8QwP)
-   [SQL Tutorial by FreeCodeCamp.org](https://www.youtube.com/watch?v=HXV3zeQKqGY)
