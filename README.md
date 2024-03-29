<p align=right><a href='https://github.com/KIRANKUMAR7296/CSharp'>Navigate to C#</a></p>

# `SQL` - `Structured Query Language`
- Programming language used to manage and manipulate the data within the relational databases.
- Standard language used by most `RDBMS`, i.e. `MySQL`, `Oracle`, `SQL Server`, etc.
- Allows `developers` and `database administrators` to manage large amount of data effectively.
- `C.R.U.D`: `Create`, `Retrieve`, `Update` and `Delete` 
- Used to `create`, `retrieve`, `update`, `delete`, `modify`, `filter`, `sort`, `aggregate` and `query` databases. 
- `Join` multiple tables using a shared key.
-  Organize data in the selected order ( `ASC` or `DESC` )
-  SQL `commands` are instructions used to communicate with the `database`

### Difference in databases
- `Syntax` of a particular database may be different ( i.e. `TOP` : Microsoft SQL and `LIMIT` : MySQL )
- `Data types` may be different. 
- `Funtions` might be different based on name or argument types or order of arguments.

### SQL Categories | Subset of SQL
<table>
  <tr>
    <th><h3>DDL</h3></th><th><h3>DQL</h3></th><th><h3>DML</h3></th><th><h3>DCL</h3></th>
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
      <ol>
        <li>SELECT</li>     
      </ol>
    </td>
    <td>
      <ol>
        <li>INSERT</li>
        <li>UPDATE</li>
        <li>DELETE</li>
        <li>MERGE</li>
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


1. Select Name in **Upper Case** as Alias
```SQL
SELECT
UPPER(Name) as UpperCaseName
FROM Employee;
```

2. Fetch `Top` N Employee and `Order By` Salary in `Descending` Order
```SQL
SELECT * 
FROM Employee
ORDER BY Salary DESC
LIMIT 5;
```

3. Retrieve Employee **First Name** and Employee **Last Name** in a Single Column Employee **Full Name** with Space.
```SQL
SELECT 
CONCAT(FirstName, ' ', LastName) AS FullName
FROM Employee;
```

4. Retrieve **Designation** along with Total Salaries Paid for each of them.
```SQL
SELECT Designation, SUM(Salary)
FROM Employee
GROUP BY Designation;
```

5. Retrieve **Name** of Employee which includes Name Kiran
```SQL
SELECT * 
FROM Employee
WHERE Name Like 'Kiran%';
```

6. Retrieve Only First Name from FullName
```SQL
SELECT 
SUBSTRING(FullName,0,Charindex(' ',FullName))
FROM Employee;
```

7. Fetch Duplicate Records from Table
```SQL
SELECT EID, Department, COUNT(*)
FROM Employee
GROUP BY EID, FullName
HAVING COUNT(*) > 1;
```

8. Remove Duplicates
```SQL
DELETE FROM Employee
WHERE EID IN (SELECT EID FROM Employee
              GROUP BY Department
              HAVING COUNT(*) > 1);
```

9. Clone Table or Empty Table with Same Structure
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

10. Fetch Common Records between 2 Tables
```SQL
SELECT * FROM Table1
INTERSECT
SELECT * FROM Table2;
```

11. **Increase** Income of all Employees by `5%` in a Table
```SQL
UPDATE Employee
SET Income = Income + (Income * 0.05);
```

12. Find Names of Employee Starting with `A`
```SQL
SELECT Name 
FROM Employee
WHERE Name LIKE 'A%';
```

13. Find Number of Employees working in Department of Data Science
```SQL
SELECT COUNT(*) 
FROM Employee
WHERE Department = 'Data Science';
```

14. Find Details of Employee whose FirstName End with 'A' and contains 6 Alphabets
```SQL
SELECT * FROM Employee
WHERE FirstName LIKE '______A'
```

15. Find Employees whose Salary lies `between` 10,000 and 50,000
```SQL
SELECT * FROM Employee
WHERE Salary BETWEEN 10000 AND 50000;
```

16. Highest Salary in Department
```SQL
SELECT ID, MAX(Salary) 
FROM Employees
GROUP BY ID;
```

Select from Multiple Tables
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

17. Second Highest Salary

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

18. Find all Duplicate Emails

```SQL
SELECT Email
FROM Employee
GROUP BY Email
HAVING COUNT(Email) > 1;
```

### Drop Duplicates from Table

```SQL
-- Create temporary table:
SELECT DISTINCT * 
INTO NewTable
FROM OldTable;

-- DROP old table:
DROP * FROM OldTable;

-- INSERT into old table from new table:
INSERT INTO OldTable
SELECT * FROM NewTable;

-- DROP new table:
DROP TABLE NewTable;
```

### Compare Two Columns

```SQL
SELECT * FROM Employee
WHERE Employee_Name IN (SELECT Employee_Name FROM Department);
```
