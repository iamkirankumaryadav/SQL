# SQL: Structured Query Language
- A standard language used to manage and manipulate the data within the relational databases.
- To execute **SQL** queries we use a relational database management system **(RDBMS)** 
- Allows developers and database administrators to manage large amounts of data effectively.
- SQL is used to perform **C.R.U.D** operations: Create, Retrieve (Read/Select), Update (Alter) and Delete (Drop)
- Used to create, retrieve, update, delete, modify, filter, sort, group, aggregate and query databases. 
- Apply SQL constraints to specify and apply rules for the data in a table.
- Join multiple tables using a shared key (column) (JOINS | UNION | UNION ALL)
- Organize data in the desired order **ASC** (Ascending) or **DESC** (Descending)
- SQL commands are instructions and language used to communicate with the database.

### Relational Database:
- A database that uses the tabular schema of rows and columns to store and manage data.
- SQL (Structured Query Language) is used to manage and manipulate the data within the relational databases.
- **Relational DBMS:** A program/software/application used to create, update, and manage relational databases.
- The most well-known **RDBMS:** MySQL, PostgreSQL, MariaDB, Microsoft SQL Server, and Oracle Database.

### Non-Relational Database
- A database that does not use the tabular schema of rows and columns found in most traditional database systems.
- Non-relational databases store data as simple key/value pairs, as JSON, or as a graph consisting of edges and vertices.
- **Non-RDBMS:** MongoDB, Amazon DynamoDB, Redis, Google Cloud Firestore, etc.

### Differences in the databases
- **Syntax/Keywords** of a particular database may be different (i.e. **TOP:** Microsoft SQL and **LIMIT:** MySQL)
- **Data types** and default keywords may be different. 
- **Functions** might be different based on name or argument types or order of arguments.

### **SQL Categories | Subset of SQL**
<table>
  <tr>
    <th><h3><a href="DDL - Data Definition Language.md">DDL</a></h3></th>
    <th><h3><a href="DQL - Data Query Language.md"> DQL</a></h3></th>
    <th><h3><a href="DML - Data Manipulation Language.md">DML</a></h3></th>
    <th><h3><a href="DCL - Data Control Language.md">DCL</a></h3></th>
  </tr>
  <tr>
    <th>Data Definition Language</th><th>Data Query Language</th><th>Data Manipulation Language</th><th>Data Control Language</th>
  </tr>
  <tr>
    <td>Define Data Structure</td><td>Retrieve Data from Database</td><td>Manipulate Data in Database</td><td>Control Access to Data stored in Database</td>
  </tr>
  <tr>
    <td>
      <ol>
        <li>CREATE</li>
        <li>ALTER</li>
        <li>DROP</li>
        <li>RENAME</li>
        <li>TRUNCATE</li>
        <li>COMMENT</li>
      </ol>
    </td>
    <td>
        SELECT
    </td>
    <td>
      <ol>
        <li>INSERT</li>
        <li>UPDATE</li>
        <li>DELETE</li>
      </ol>
    </td>    
    <td>
      <ol>
        <li>GRANT</li>
        <li>REVOKE</li>
      </ol>
    </td>    
  </tr>
</table>

### Most Basic and Common Queries:

```SQL
SELECT * <All Columns>
FROM     <Table Name>
```

```SQL
SELECT   <Columns>
FROM     <Table>
JOIN     <Another Table>
ON       <Common Columns>
WHERE    <Filter Condition>
GROUP BY <Grouping>
HAVING   <Aggregate Filter>
ORDER BY <Column List>
LIMIT    <No. of Rows>
```

1. **Select the name in upper case as an alias**
```SQL
SELECT
UPPER(Name) as UpperCaseName
FROM Employee;
```

2. **Fetch top N employee and order by salary in descending order**
```SQL
SELECT * 
FROM Employee
ORDER BY Salary DESC
LIMIT 5;
```

3. **Concat employees **first name** and **last name** in a single column as **full name** with whitespace**
```SQL
SELECT 
CONCAT(FirstName, ' ', LastName) AS FullName
FROM Employee;
```

4. **Retrieve the designation along with the total salaries paid for each of them**
```SQL
SELECT Designation, SUM(Salary)
FROM Employee
GROUP BY Designation;
```

5. **Retrieve the name of the employee which includes the name "Kiran"**
```SQL
SELECT * 
FROM Employee
WHERE Name Like 'Kiran%';
```

6. **Retrieve only first name from full name**
```SQL
SELECT 
SUBSTRING(FullName, 0, Charindex(' ',FullName))
FROM Employee;
```

7. **Fetch duplicate records from a table**
```SQL
SELECT EID, Department, COUNT(*)
FROM Employee
GROUP BY EID, FullName
HAVING COUNT(*) > 1;
```

8. **Remove duplicates**
```SQL
DELETE FROM Employee
WHERE EID IN (SELECT EID FROM Employee
              GROUP BY Department
              HAVING COUNT(*) > 1);
```

9. **Clone table or empty table with same structure**
```SQL
CREATE TABLE NewTable 
SELECT * FROM OldTable;

SELECT * 
INTO NewTable 
FROM OldTable
WHERE 0 = 1;

CREATE TABLE NewTable
LIKE OldTable;

INSERT 
INTO NewTable
SELECT * 
FROM OldTable;
```

10. **Fetch common records between 2 tables**
```SQL
SELECT * FROM Table1
INTERSECT
SELECT * FROM Table2;
```

11. **Increase the income of all employees by 5% in a table**
```SQL
UPDATE Employee
SET Income = Income + (Income * 0.05);
```

12. **Find names of employees starting with "A"**
```SQL
SELECT Name 
FROM Employee
WHERE Name LIKE 'A%';
```

13. **Find the number of employees working in the Department of Data Science**
```SQL
SELECT COUNT(*) 
FROM Employee
WHERE Department = 'Data Science';
```

14. **Find details of the employees whose first name ends with 'A' and contains 6 alphabets**
```SQL
SELECT * FROM Employee
WHERE FirstName LIKE '______A'
```

15. **Find Employees whose Salary lies between 10,000 and 50,000**
```SQL
SELECT * FROM Employee
WHERE Salary BETWEEN 10000 AND 50000;
```

16. **Find the highest salary in the department**
```SQL
SELECT ID, MAX(Salary) 
FROM Employees
GROUP BY ID;
```

**Select from multiple tables (JOINS)** 
```SQL
SELECT D.Name AS 'Department', E.Name AS 'Employee', E.Salary
FROM Employee E
INNER JOIN Department D
ON E.ID = D.ID
WHERE (ID, Salary)
IN (SELECT ID, MAX(Salary) 
    FROM Employees 
    GROUP BY ID)
```

17. **Select second highest salary**

```SQL
-- MAX:
SELECT MAX(Salary) 
FROM Employee
WHERE Salary < (SELECT MAX(Salary) FROM Employee);                               

-- LIMIT:
SELECT Salary
FROM (SELECT Salary FROM Employee ORDER BY  Salary DESC LIMIT 2)
AS EmployeeSalary 
ORDER BY Salary LIMIT 1;

-- TOP:
SELECT Top 1 Salary
FROM (SELECT Top 2 Salary FROM Employee ORDER BY  Salary DESC)
AS EmployeeSalary 
ORDER BY Salary ASC;
```

18. **Find all duplicate emails**

```SQL
SELECT Email
FROM Employee
GROUP BY Email
HAVING COUNT(Email) > 1;
```

### **Drop duplicates from the table**

```SQL
-- Create a temporary table:
SELECT DISTINCT * 
INTO NewTable
FROM OldTable;

-- DROP old table:
DROP * FROM OldTable;

-- INSERT into an old table from the new table:
INSERT INTO OldTable
SELECT * FROM NewTable;

-- DROP new table:
DROP TABLE NewTable;
```

### **Compare two columns**

```SQL
SELECT * FROM Employee
WHERE Employee_Name IN (SELECT Employee_Name FROM Department);
```
