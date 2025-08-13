## Sub Query

- *Definition:* A query inside another query.  
- *Also Known As:* Nested Query  

### Working Principles
1. The *inner query* executes first and produces output.  
2. The *output of the inner query* acts as input to the outer query.  
3. The *outer query* depends on the inner query, but the inner query does not depend on the outer query.  

### Rules
1. The column in the inner query and the column in the outer query must have the *same datatype*.  
2. You can select *only one column* inside the inner query.  

### Syntax (Example)
sql
SELECT * 
FROM emps 
WHERE sal < (SELECT sal FROM emps WHERE fname = 'priya');

## Sub Query Case 2
*Condition from one table, data from another table.*  
CrossTable

### Example Syntax
sql
SELECT city 
FROM locations 
WHERE lid = (SELECT lid FROM emps WHERE fname = 'kiran');

## Types of Sub Query

1. *Single Row Subquery* – Inner query returns single value; can use normal (=, !=, >, <) and special operators (IN, NOT IN, ALL, ANY).  
Single

2. *Multi Row Subquery* – Inner query returns more than one value; can use IN, NOT IN, ALL, ANY.  
Multi
## Employee–Manager Relationship

Queries linking employees to their managers.  
Hierarchy

*Example Syntax*
sql
SELECT * 
FROM emps 
WHERE eid = (SELECT mgr FROM emps WHERE fname = 'suresh');

---
## ALL Operator
Multi value operator with relational operators, works like AND condition.  
All

*Example Syntax*
sql
SELECT * 
FROM emps 
WHERE sal < ALL(SELECT sal FROM emps WHERE job='waiter');

---
## ANY Operator
Multi value operator with relational operators, works like OR condition.  
Any

*Example Syntax*
sql
SELECT * 
FROM emps 
WHERE sal < ANY(SELECT sal FROM emps WHERE job='waiter');

---
## Drawback of Subquery
Cannot retrieve data from multiple tables simultaneously.  
Limit

---
## Joins
Retrieve data from multiple tables simultaneously.  
Join

*Types*
1. Cross Join / Cartesian Join  
2. Inner Join  
3. Outer Join (Left / Right)  
4. Self Join  
5. Natural Join  

## 1. Cross Join
Merges records of one table with another.  

*Cross*  

sql
SELECT *  
FROM locations l CROSS JOIN emps e;


## 2. Inner Join
Retrieves matched records from different tables.  

*Match*  

sql
SELECT * 
FROM locations l 
INNER JOIN emps e ON l.lid = e.lid;


## 3. Outer Join
Retrieves both matched and unmatched records depending on join type.

- *Left Outer Join* – All records from left table + matched from right table.  

sql
SELECT * 
FROM customers c 
LEFT OUTER JOIN locations l 
ON c.lid = l.lid;

- *Right Outer Join* – All right + matched left. Right
sql
SELECT * 
FROM customers c RIGHT OUTER JOIN locations l 
ON c.lid = l.lid;

## 4. Self Join
Join a table to itself to compare or relate its rows.
Self
sql
SELECT e1.fname AS emp_name, e2.fname AS manager_name 
FROM emps e1 
JOIN emps e2 ON e1.mgr = e2.eid;

## 5. Natural Join
Match automatically on same column names.
Natural
sql
SELECT * 
FROM emps NATURAL JOIN locations;

---
## 4. Set Operators
Combine results of multiple queries.

- *UNION* – Merge results, remove duplicates.  

sql
(SELECT column_name FROM table1)
UNION
(SELECT column_name FROM table2);

- *UNION ALL* – Merge results with duplicates.
  sql
  (SELECT column_name FROM table1)
  UNION ALL
  (SELECT column_name FROM table2);
  
- *INTERSECT* – Common rows.
  sql
  (SELECT column_name FROM table1)
  INTERSECT
  (SELECT column_name FROM table2);
  
*Syntax Rule:* Same number of columns in SELECT, use brackets, semicolon at last query.

---
## 5. TCL (Transaction Control Language)
Manages database transactions.

1. *COMMIT* – Save changes permanently. (Save)  
sql
COMMIT;

2. *ROLLBACK* – Undo changes until last commit. Undo
sql
ROLLBACK;

3.	*SAVEPOINT* – Mark a position between transactions. Mark
sql
SAVEPOINT savepoint_name;

## DCL (Data Control Language)
Controls access to data.

- *GRANT* – Give permission.

sql
GRANT SELECT ON emps TO 'pentagon'@'localhost';

- *REVOKE* – Remove permission.
sql
REVOKE DELETE ON emps FROM 'pentagon'@'localhost';

---
## 6. Table Duplication & Data Insertion

- *Duplicate table with data*  
sql
CREATE TABLE new_table AS (SELECT * FROM existing_table);

- •	Duplicate table without data:
sql
CREATE TABLE new_table (SELECT * FROM existing_table WHERE 1=0);

- Insert data from another table:
sql
INSERT INTO table_name (SELECT * FROM another_table WHERE job='delivery');

---
## 7. Views

- *Definition:* Virtual table based on a query, no physical storage.  

- *Create a View*  
sql
CREATE VIEW view_name AS (SELECT ...);
DROP VIEW view_name;

---
## 8. Correlated Subquery

- *Definition:* Inner and outer query depend on each other.  

- *Example:*  
sql
SELECT e1.fname 
FROM emps e1 
WHERE e1.sal > (
    SELECT AVG(sal) 
    FROM emps e2 
    WHERE e1.job = e2.job
);

---
## 9. Keys

- *Primary Key* – Unique identifier. (Primary)
- *Foreign Key* – Links tables. (Foreign)
- *Composite Key* – Multiple columns. (Composite)
- *Compound Key* – Composite containing a foreign key. (Compound)
---
## 10. Ranking Functions / Window Functions

Assign ranks to records.

- *ROW_NUMBER()* – Unique rank even for ties. (RowNum)
- *RANK()* – Gaps in rank for ties. (Rank)
- *DENSE_RANK()* – No gaps for ties. (Dense)

*Syntax:*
sql
SELECT fname, job, sal, 
       ROW_NUMBER() OVER(PARTITION BY job ORDER BY sal DESC) 
FROM emps;

## 11. Dependency Types

Define how attributes depend on keys.

- *Total Dependency* – All attributes depend on the key. (Total)
- *Partial Dependency* – Attribute depends on part of a composite key. (Partial)
- *Transitive Dependency* – Attribute depends on a non-key, which depends on the key. (Transitive)
---
## 12. Redundancy
Repetition of data. (Repeat)

---

## 13. Anomalies
Problems from DML operations. (Problem)

- *Insert Anomaly* – Issue when adding new data.
- *Delete Anomaly* – Issue when removing data.
- *Update Anomaly* – Issue when modifying data.  
(Insert / Delete / Update)

---

## 14. Normalization
Splitting tables to reduce redundancy and anomalies. (Normal)

- *1NF* – Unique rows, atomic values.
- *2NF* – 1NF + No partial dependency.
- *3NF* – 2NF + No transitive dependency.
