# SQL
Structured Query Language

### Most Basic Query

```SQL
SELECT * <All Columns>
FROM     <Table Name>
LIMIT    <No. of Rows>
```

```SQL
SELECT   <Columns>
FROM     <Table>
JOIN     <Another Table>
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
ORDER BY Salary
DESC
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

MAX | LIMIT | TOP

A. MAX 
```SQL
SELECT MAX(Salary) 
FROM Employee
WHERE Salary < (SELECT MAX(Salary) 
                FROM Employee);                               
```

18. Find all Duplicate Emails
```SQL
SELECT Email
FROM Employee
GROUP BY Email
HAVING COUNT(Email) > 1
```

B. LIMIT
```SQL
SELECT Salary
FROM (SELECT Salary FROM Employee ORDER BY  Salary DESC LIMIT 2)
AS EmployeeSalary 
ORDER BY Salary LIMIT 1;
```

C. TOP
```SQL
SELECT Top 1 Salary
FROM (SELECT Top 2 Salary FROM Employee ORDER BY  Salary DESC)
AS EmployeeSalary 
ORDER BY Salary ASC;
```

### Constraints ( Rules )

CREATE Table and ALTER Table

1. NOT NULL (Non Empty Values in the Column)
```SQL
CREATE TABLE Employee
(
  ID           INT NOT NULL,
  EmployeeName VARCHAR(255) NOT NULL
);

ALTER TABLE Employee
MODIFY EmployeeName NOT NULL;
```

2. UNIQUE (Different Values in the Column)
```SQL
ALTER TABLE Employee
ADD UNIQUE(ID);
```

3. PRIMARY KEY
```SQL
CREATE TABLE Employee
(
  ID INT NOT NULL PRIMARY KEY,
  Name VARCHAR(255)
);
```

4. FOREIGN KEY
```SQL
CREATE TABLE Employee
(
  EID INT NOT NULL PRIMARY KEY,
  Name VARCHAR(255),
  DID INT NOT NULL FOREIGN KEY REFERENCES Department(DID)
)
```

5. CHECK
```SQL
CREATE TABLE Employee
(
  ID INT NOT NULL,
  Age INT CHECK(AGE >= 18)
);
```

### Drop Duplicates from Table

1. Using `Temporary` Table

```SQL
SELECT DISTINCT * 
INTO NewTable
FROM OldTable
```

```SQL
DROP * FROM OldTable
```

```SQL
INSERT INTO OldTable
SELECT * FROM NewTable
```

```SQL
DROP TABLE NewTable
```
