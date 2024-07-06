# SQL

`Structure Query Language` is a standard database language used to access and manipulate data in databases. SQL stands for Structured Query Language. It was developed by IBM Computer Scientists in the 1970s. By executing queries SQL can create, update, delete, and retrieve data in databases like MySQL, Oracle, PostgreSQL, etc. Overall, SQL is a query language that communicates with databases.

## Basics of SQL

- **Data:** Data is a raw fact that describes the attribute of an entity.
- **Attribute:** It is a properties of an Entity/object
- **Entity/object:** Anything which is physically present is called object.
- **Database:** Is a place/media, where we cans store data in systematic and organised manner.

## Operation on Database `CRUD`
The acronym `CRUD` refers to the major operations that are implemented by databases. Each letter in the acronym can be mapped to a standard Structured Query Language (SQL) statement.

| **CRUD** | **SQL** |
| -------- | ------- |
| Create   | INSERT  |
| Read     | SELECT  |
| Update   | UPDATE  |
| Delete   | DELETE  |

## Database Managing System

DBMS provide two important features. One is security and the other is authorization. Maintenance and managing to communicate with DBMS software we use a language called query language.

### Types of DBMS

- **Object-Oriented Databases:** Similar to object-oriented programming, data in an object-oriented database is represented as objects.
- **Distributed Databases:** A distributed database is made up of two or more files that are spread across multiple locations. The database could be dispersed across many networks, housed in one physical place, or kept on several computers.
- **NoSQL Databases:** Unlike relational databases, which specify how all data input must be formatted, NoSQL, or non-relational databases, permit the storage and manipulation of unstructured and semistructured data.
- **Graph Databases:** Data is stored in a graph database using entities and their relationships.
- **Open source databases:** A database system that is open source can have either a SQL or NoSQL database as its source code.
- **Cloud databases:** A collection of organized or unorganized data that is housed on a private, public, or hybrid cloud computing platform is known as a cloud database.

- **Relational Databases:** A relational database’s contents are arranged as a collection of tables with rows and columns.

## Relational Database management System (RDBMS)

- It is a type of DBMS software where we store data in form of tables or relations. Ie, the form of rows and columns.

- A DBMS that follows `E-F-Codd` rules is called a RDBMS.

- If the DBMS that follows a relational model is called RDBMS.

- To communicate with RDBMS we use a language called Structured Query Language.

**Structured Query Language**.

### E-F-Codd Rules

1. The data entered into a cell must be single valued data or atomic data.
2. We can store the data in multiple tables, and also we can establish a connection between multiple tables by using key attribute.
3. We can assign data types and constraints to validate the data.
4. The data types are mandatory for the table, but **constraints are optional**.

## Data Types

### 1. Numerical

#### A. BIT

- **Syntax:** BIT(Size)
- It is used for a bit-value type. The number of bits per value is specified in 'size'. Its 'size' can be 1 to 64. The default value is 1.

#### B. INT

- **Syntax:** INT(size)
- It is used for the integer value. Its signed range varies from -2147483648 to 2147483647 and unsigned range varies from 0 to 4294967295. The 'size' parameter specifies the max display width that is 255.

#### C. FLOAT

- **Syntax:** FLOAT(size, d)
- It is used to specify a floating point number. Its 'size' parameter specifies the total number of digits. The number of digits after the decimal point is specified by 'd' parameter.

#### D. DOUBLE

- **Syntax:** DOUBLE(size, d)
- It is a normal size floating point number. Its 'size' parameter specifies the total number of digits. The number of digits after the decimal is specified by 'd' parameter.

#### E. DECIMAL

- **Syntax:** DECIMAL(size, d)
- It is used to specify a fixed point number. Its 'size' parameter specifies the total number of digits. The number of digits after the decimal parameter is specified by 'd' parameter.
- The maximum value for the size is 65, and the default value is 10.
- The maximum value for d is 30, and the default value is 0.

### 2. Character

#### A. CHAR
- Syntax: CHAR(Size)
- It is used to specify a fixed length string that can contain numbers, letters, and special characters. Its size can be 0 to 255 characters. Default is 1.

#### B. VARCHAR

- **Syntax:** VARCHAR(Size)
- It is used to specify a variable length string that can contain numbers, letters, and special characters. Its size can be from 0 to 65535 characters.

#### C. TEXT

- **Syntax:** TEXT(Size)
- It holds a string that can contain a maximum length of 255 characters.

#### D. TINYTEXT

- TINYTEXT
- It holds a string with a maximum length of 255 characters.

#### E. MEDIUMTEXT

- **Syntax:** MEDIUMTEXT
- It holds a string with a maximum length of 16,777,215.

#### F. LONGTEXT

- **Syntax:** LONGTEXT
- It holds a string with a maximum length of 4,294,967,295 characters.

### 3. Large Objects
In SQL, data types for handling large objects (often referred to as LOBs) are specifically designed to manage and store large amounts of data, such as text, images, audio, video, and other multimedia files.
#### A. CLOB: 
Used for storing large amounts of character data, up to 4 GB in size.

#### B. BLOB: 
Stores large binary data, such as images or documents.
- Syntax: BLOB(size)
- For BLOBs (Binary Large Objects). Holds up to 65,535 bytes of data

### 4. Date 
It is used to specify date format 'YYYY-MM-DD'. Its supported range is from '1000-01-01' to '9999-12-31'.

## Constraints
### 1. UNIQUE Constraint:
- This Constraints is used to avoid duplicate values which are entered into a column.
### 2. NOT NULL Constraint
- Null is a keyword which represents nothing or an empty cell.
- Null does not occupy any memory.
- Two nulls are not the same in RDBMS.
- Any operation performed with null, will result null.
- It is used to provide NULL values entered into columns, ie it represents the cell should not be empty.

### 3. Check Constraint
- It is used to provide a user defined/customised condition for a column.

### 4. Foreign Key Constraint or refrential integrity constraint
- A foreign key is used to establish connection between multiple tables.

### 5. Primary Key Constraint
- It is used to uniquely identify the records from the table.

## Types of commands
### DDL: Data defination language
- CREATE 
- RENAME
- ALTER
- TRUNCATE 
- DROP

### DML: Data Manipulation Language
- INSERT
- UPDATE
- DELETE

### TCL: Transaction Control Language
- COMMIT
- SAVEPOINT
- ROLLBACK

### DCL: Data Control Language
- GRANT
- REVOKE

### DQL: Data Query Language
- SELECT
- JOINS

## Basic SQL Commands
#### 1. SELECT
- The SELECT command in SQL is used to retrieve data from one or more tables in a database.

    ```
    SELECT column1, column2, ...
    FROM table_name;
    ```
    Example:
    ```
    SELECT FirstName, LastName
    FROM Employees;
    ```
    This will select columns 'FirstName' and 'LastName' from 'Employee' table.

#### 2. DISTINCT
- In SQL, the DISTINCT keyword is used in conjunction with the SELECT statement to eliminate duplicate rows from the result set.

    ```
    SELECT DISTINCT column1, column2, ...
    FROM table_name;
    ```
    Example:
    ```
    SELECT DISTINCT City
    FROM Customers;
    ```
    This query will return a list of unique cities from the 'Customers' table.

#### 3. WHERE
- In SQL, the WHERE clause is used in conjunction with the SELECT statement to filter rows from a table based on specified conditions.

    ```
    SELECT column1, column2, ...
    FROM table_name
    WHERE condition;
    ```
    Example:
    ```
    SELECT EmployeeID, FirstName, LastName, Salary
    FROM Employees
    WHERE Salary > 50000;
    ```
    This query will return rows where the 'Salary' column value is greater than 50000.

#### 4. LIKE
- In SQL, the LIKE operator is used in the WHERE clause to search for a specified pattern in a column.

    ```
    SELECT column1, column2, ...
    FROM table_name
    WHERE column_name LIKE pattern;
    ```
    Example:
    ```
    SELECT FirstName, LastName
    FROM Employees
    WHERE LastName LIKE 'S%';
    ```

## Functions
In SQL, functions provide a way to perform computations, manipulate data, or transform values within queries.
### 1. Aggregate functions
Aggregate functions operate on sets of rows and calculate a single return value for a group of rows. 
- **SUM():** Calculates the sum of values in a column.
    ```
    SELECT Category, SUM(Revenue) AS TotalRevenue
    FROM Sales
    GROUP BY Category;
    ```
    This query will return the total revenue for each category from the 'Sales' table.

- **AVG():** Calculates the average of values in a column.
    ```
    SELECT Department, AVG(Salary) AS AverageSalary
    FROM Employees
    GROUP BY Department;
    ```
    This query will calculate the average salary for each department.

- **COUNT():** Counts the number of rows or non-null values in a column.
    ```
    SELECT CustomerID, COUNT(*) AS NumOrders
    FROM Orders
    GROUP BY CustomerID;
    ```
    This query will count the number of orders for each customer.

- **MIN():** Finds the minimum value in a column.
    ```
    SELECT Department, MIN(Salary) AS MinSalary
    FROM Employees
    GROUP BY Department;
    ```
    This query will retrieve the minimum salary for each department.


- **MAX():** Finds the maximum value in a column.
    ```
    SELECT Product, MAX(Revenue) AS MaxRevenue
    FROM Sales
    GROUP BY Product;
    ```
    This query will find the maximum revenue for each product.

### 2. Scalar Functions
Scalar functions operate on a single value and return a single value.
- String functions like LEN(), UPPER(), LOWER(), SUBSTRING().
    - **UPPER() and LOWER():** Convert text to uppercase or lowercase.

        ```
        UPPER() and LOWER(): Convert text to uppercase or lowercase.
        ```
    - **LEFT() and RIGHT():** Extract a specified number of characters from the left or right side of a string.

        ```
        SELECT FirstName, LEFT(FirstName, 3) AS FirstThreeChars
        FROM Employees;
        ```

- Numeric functions like ROUND(), ABS(), CEILING(), FLOOR().
    - **ROUND():** Rounds a numeric value to a specified precision.

        ```
        SELECT Salary, ROUND(Salary, 2) AS RoundedSalary
        FROM Employees;
        ```
    - **ABS():** Returns the absolute value of a number.
        ```
        SELECT Discount, ABS(Discount) AS AbsoluteDiscount
        FROM Orders;
        ```
    - **CEILING() and FLOOR():** Round up or down to the nearest integer.
        ```
        SELECT Price, CEILING(Price) AS CeilingPrice, FLOOR(Price) AS FloorPrice
        FROM Products;
        ```


- Date and time functions like GETDATE(), DATEADD(), DATEDIFF().
    - **GETDATE():** Returns the current date and time.

        ```
        SELECT GETDATE() AS CurrentDateTime;
        ```
    - **DATEPART():** Extracts a specific part of a date (e.g., year, month, day).

        ```
        SELECT OrderDate, DATEPART(year, OrderDate) AS OrderYear
        FROM Orders;
        ```
    - **DATEDIFF():** Calculates the difference between two dates.
        ```
        SELECT OrderDate, ShippedDate, DATEDIFF(day, OrderDate, ShippedDate) AS DaysToShip
        FROM Orders;
        ```
## Joins
Joins are used to combine rows from two or more tables based on a related column between them. Joins allow you to retrieve data that spans across multiple tables, making it possible to query related data together. 

### 1. INNER JOIN
- An INNER JOIN returns only the rows where there is a match between the columns in both tables.
    ```
    SELECT columns
    FROM table1
    INNER JOIN table2 ON table1.column = table2.column;
    ```
    Example:

    ```
    SELECT Employees.EmployeeID, Employees.FirstName, Employees.LastName, Departments.DepartmentName
    FROM Employees
    INNER JOIN Departments ON Employees.DepartmentID = Departments.DepartmentID;
    ```
    This query retrieves the 'EmployeeID', 'FirstName', 'LastName', and 'DepartmentName' for all employees along with their corresponding departments.

### 2. LEFT JOIN (or LEFT OUTER JOIN)

- A LEFT JOIN returns all rows from the left table (table1), and the matched rows from the right table (table2). If there is no match, the result is NULL for the right side.

    ```
    SELECT columns
    FROM table1
    LEFT JOIN table2 ON table1.column = table2.column;
    ```
    Example:

    ```
    SELECT Employees.EmployeeID, Employees.FirstName, Employees.LastName, Departments.DepartmentName
    FROM Employees
    LEFT JOIN Departments ON Employees.DepartmentID = Departments.DepartmentID;
    ```
    This query will retrieve all employees and their corresponding departments, including employees who do not have a department assigned.

### 3. RIGHT JOIN (or RIGHT OUTER JOIN)
- A RIGHT JOIN returns all rows from the right table (table2), and the matched rows from the left table (table1). If there is no match, the result is NULL for the left side.
    ```
    SELECT columns
    FROM table1
    RIGHT JOIN table2 ON table1.column = table2.column;
    ```
    Example:

    ```
    SELECT Employees.EmployeeID, Employees.FirstName, Employees.LastName, Departments.DepartmentName
    FROM Employees
    RIGHT JOIN Departments ON Employees.DepartmentID = Departments.DepartmentID;
    ```
    This query will retrieve all departments and their employees, including departments that do not have any employees.

### 4. FULL JOIN (or FULL OUTER JOIN)
- A FULL JOIN returns all rows when there is a match in either the left (table1) or right (table2) table records. If there is no match, the result is NULL for the side that lacks a match.

    ```
    SELECT columns
    FROM table1
    FULL JOIN table2 ON table1.column = table2.column;
    ```
    Example:
    ```
    SELECT Employees.EmployeeID, Employees.FirstName, Employees.LastName, Departments.DepartmentName
    FROM Employees
    FULL JOIN Departments ON Employees.DepartmentID = Departments.DepartmentID;
    ```
    This query will retrieve all employees and all departments, showing where there are matches and where there aren't.



### 5. CROSS JOIN
- A CROSS JOIN returns the Cartesian product of the two tables, meaning all possible combinations of rows from the tables are returned.

    ```
    SELECT columns
    FROM table1
    CROSS JOIN table2;
    ```
    Example:

    ```
    SELECT Employees.EmployeeID, Employees.FirstName, Employees.LastName, Departments.DepartmentName
    FROM Employees
    CROSS JOIN Departments;
    ```

    This query will retrieve all possible combinations of employees and departments.


## Reference
- Database and Constraints from [Geeks For Geeks](https://www.geeksforgeeks.org/what-is-database/)
- Data Types from [JAVA T Point](https://www.javatpoint.com/sql-data-types)
- SQL Joins from [Geeks For Geeks](https://www.geeksforgeeks.org/sql-join-set-1-inner-left-right-and-full-joins/)
### Also refer following videos for more content:
- [SQL Tutorials for beginner by MOSH](https://youtu.be/7S_tz1z_5bA?si=MmWdK9AtoBjv8QwP)
- [SQL Tutorial by FreeCodeCamp.org](https://www.youtube.com/watch?v=HXV3zeQKqGY)

