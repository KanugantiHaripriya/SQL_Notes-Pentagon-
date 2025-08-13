# Database Management System (DBMS) & SQL Concepts

---

## 1. DBMS (Database Management System)
Software to maintain and manage databases with security and authorization. Management

#### Types of DBMS
* *Network DBMS* – Stores data in network structure, shareable across networks. Network
* *Object-Oriented DBMS* – Stores data as objects, uses more space. Objects
* *Hierarchical DBMS* – Data in nested/tree form, inefficient for large scale. Tree
* *RDBMS* – Stores data in tables following relational model and Codd rules. Tables

---

## 2. Relational Model
E.F. Codd’s table/relations concept; supports meta-data (data about data). Relations

---

## 3. Difference Between DBMS and RDBMS
Compares features like storage type, relationships, constraints, security, and users. Comparison

---

## 4. EF Codd Rules
Fundamental principles of relational databases. Rules
* Data must be single/atomic. Atomic
* Multiple tables linked via keys. Keys
* Datatypes mandatory, constraints optional. Types

---

## 5. RDBMS vs Excel Sheet
Handles large, relational, multi-user data vs flat simple spreadsheets. Spreadsheet

---

## 6. Data Types
Define the types and format of stored data. Types

* *CHAR* – Fixed-length characters. Fixed
    *Syntax Example:*
    sql
    column_name CHAR(size);
    
* *VARCHAR* – Variable-length characters. Variable
    *Syntax Example:*
    sql
    column_name VARCHAR(size);
    
* *VARCHAR2* – Updated variable length up to 4000 chars. Extended
    *Syntax Example:*
    sql
    column_name VARCHAR2(size);
    
* *CLOB* – Large character object (up to 4GB). Characters
    *Syntax Example:*
    sql
    column_name CLOB;
    
* *BLOB* – Binary object (images, audio, video). Binary
    *Syntax Example:*
    sql
    column_name BLOB;
    
* *DATE* – Date values. Date
    *Syntax Example:*
    sql
    column_name DATE;
    
* *NUMBER* – Numeric values (precision/scale). Numeric
    *Syntax Example:*
    sql
    column_name NUMBER(precision, scale);
    

---

## 7. Constraints
Rules for data validation in tables. Restrictions

* *UNIQUE* – No duplicate values. Distinct
    *Syntax Example:*
    sql
    column_name datatype UNIQUE;
    
* *NOT NULL* – Value is mandatory. Mandatory
    *Syntax Example:*
    sql
    column_name datatype NOT NULL;
    
* *CHECK* – Condition must be met. Condition
    *Syntax Example:*
    sql
    column_name datatype CHECK (condition);
    
* *PRIMARY KEY* – Unique identifier (only one per table). Identifier
    *Syntax Example:*
    sql
    PRIMARY KEY (column_name);
    
* *FOREIGN KEY* – References another table. Reference
    *Syntax Example:*
    sql
    FOREIGN KEY (column_name) REFERENCES parent_table(parent_column);
    

---

## 8. SQL Statements
Categories of SQL commands. Commands

* *DDL (Data Definition Language)* – Commands to create/alter structure. Structure
    *Syntax Examples:*
    sql
    CREATE TABLE table_name (column datatype constraints);
    ALTER TABLE table_name ADD column_name datatype;
    DROP TABLE table_name;
    
* *DML (Data Manipulation Language)* – Insert, update, delete data. Manipulation
    *Syntax Examples:*
    sql
    INSERT INTO table_name (columns) VALUES (values);
    UPDATE table_name SET column=value WHERE condition;
    DELETE FROM table_name WHERE condition;
    
* *DCL (Data Control Language)* – Grant or revoke permissions. Control
    *Syntax Examples:*
    sql
    GRANT privilege ON object TO user;
    REVOKE privilege ON object FROM user;
    
* *TCL (Transaction Control Language)* – Manage transactions. Transaction
    *Syntax Examples:*
    sql
    COMMIT;
    ROLLBACK;
    SAVEPOINT savepoint_name;
    
* *DQL (Data Query Language)* – Data retrieval queries (SELECT etc). Query
    *Syntax Example:*
    sql
    SELECT column1, column2 FROM table_name WHERE condition;
    

---

## 9. Data Query Language Details
* *SELECT* – Retrieve data. Retrieve
    sql
    SELECT column1, column2 FROM table_name;
    
* *PROJECTION* – Select columns. Columns
* *SELECTION* – Select rows by condition. Filter
* *JOINS* – Fetch data from more than one table. Combine

---

## 10. Expressions & Operators
Operators work with operands to form expressions. Expression

#### Operators and Syntax Examples:
* *Arithmetic Operators* (+, -, *, /, %) Math
    sql
    SELECT salary + bonus FROM employees;
    
* *Relational Operators* (<, >, <=, >=, =) Compare
    sql
    SELECT * FROM employees WHERE age > 30;
    
* *Logical Operators* (AND, OR, NOT) Logic
    sql
    SELECT * FROM employees WHERE age > 30 AND department = 'Sales';
    
* *Special Operators* (IN, NOT IN, BETWEEN, LIKE, IS) Special
    sql
    SELECT * FROM customers WHERE city IN ('Paris', 'London');
    
* *Subquery Operators* (ALL, ANY) Nested
    sql
    SELECT * FROM employees WHERE salary > ALL (SELECT salary FROM managers);
    

---

## 11. Functions

### Aggregate Functions
Summarize column data. Summary
* *MAX()* – Highest value. Maximum
    sql
    SELECT MAX(salary) FROM employees;
    
* *MIN()* – Smallest value. Minimum
    sql
    SELECT MIN(age) FROM employees;
    
* *AVG()* – Average value. Average
    sql
    SELECT AVG(salary) FROM employees;
    
* *SUM()* – Total value. Total
    sql
    SELECT SUM(sales) FROM orders;
    
* *COUNT()* – Number of rows/values. Count
    sql
    SELECT COUNT(*) FROM employees;
    

### Character Functions
Manipulate strings. String
* *LOWER()* – Converts to lowercase. Lower
    sql
    SELECT LOWER(name) FROM employees;
    
* *UPPER()* – Converts to uppercase. Upper
    sql
    SELECT UPPER(name) FROM employees;
    
* *LENGTH()* – Counts characters. Length
    sql
    SELECT LENGTH(name) FROM employees;
    
* *REVERSE()* – Reverses string. Reverse
    sql
    SELECT REVERSE(name) FROM employees;
    
* *CONCAT()* – Concatenates strings. Join
    sql
    SELECT CONCAT(first_name, ' ', last_name) FROM employees;
    
* *SUBSTR()* – Extract substring. Substring
    sql
    SELECT SUBSTR(name, 1, 3) FROM employees;
    
* *REPLACE()* – Replaces substring. Replace
    sql
    SELECT REPLACE(name, 'old', 'new') FROM employees;
    

### Number Functions
Numeric operations. Numbers
* *ABS()* – Absolute value. Absolute
    sql
    SELECT ABS(-15);
    
* *MOD()* – Modulus (remainder). Modulo
    sql
    SELECT MOD(10, 3);
    
* *ROUND()* – Round number. Round
    sql
    SELECT ROUND(14.56);
    
* *CEIL()* – Round up. Ceiling
    sql
    SELECT CEIL(14.1);
    
* *FLOOR()* – Round down. Floor
    sql
    SELECT FLOOR(14.9);
    
* *TRUNCATE()* – Truncate decimals. Truncate
    sql
    SELECT TRUNCATE(14.987, 2);
    
* *POW()* – Power. Power
    sql
    SELECT POW(2, 3);
    
* *SQRT()* – Square root. Root
    sql
    SELECT SQRT(16);
    

### Date Functions
Date/time operations. Date
* *CURDATE()* – Current date. Now
    sql
    SELECT CURDATE();
    
* *SYSDATE()* – Current system date & time. System
    sql
    SELECT SYSDATE();
    
* *YEAR()* – Extract year. Year
    sql
    SELECT YEAR(order_date) FROM orders;
    
* *MONTH()* – Extract month. Month
    sql
    SELECT MONTH(order_date) FROM orders;
    
* *DAY()* – Extract day. Day
    sql
    SELECT DAY(order_date) FROM orders;
    
* *DATEDIFF()* – Difference between dates. Gap
    sql
    SELECT DATEDIFF('2025-08-13', '2025-01-01');
    
* *DATE_ADD()* – Add interval to date. Add
    sql
    SELECT DATE_ADD('2025-08-13', INTERVAL 10 DAY);
    
* *DATE_SUB()* – Subtract interval from date. Subtract
    sql
    SELECT DATE_SUB('2025-08-13', INTERVAL 5 DAY);
    
* *DATE_FORMAT()* – Format date output. Format
    sql
    SELECT DATE_FORMAT('2025-08-13', '%d-%m-%Y');
    

---

## 12. Group By / Having
* *GROUP BY* – Groups rows by column values. Group
    sql
    SELECT department, COUNT(*) FROM employees GROUP BY department;
    
* *HAVING* – Filters groups by condition. GroupFilter
    sql
    SELECT department, COUNT(*) FROM employees GROUP BY department HAVING COUNT(*) > 5;
    

---

## 13. Ordering & Limiting
* *ORDER BY* – Sort rows. Sort
    sql
    SELECT * FROM employees ORDER BY salary DESC;
    
* *LIMIT* – Limit number of rows. Restrict
    sql
    SELECT * FROM employees LIMIT 10;
    
* *OFFSET* – Skip rows. Skip
    sql
    SELECT * FROM employees LIMIT 10 OFFSET 5;
    

---

## 14. Character/Pattern Matching
* *LIKE* – Matches pattern. Pattern
    sql
    SELECT * FROM employees WHERE name LIKE 'A%';
    
* *NOT LIKE* – Does not match pattern. Exclude
    sql
    SELECT * FROM employees WHERE name NOT LIKE 'A%';
    
