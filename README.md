# SQL
Structured Query Language

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

SELECT * INTO NewTable 
FROM OldTable;

CREATE TABLE NewTable
LIKE OldTable;

INSERT INTO NewTable
SELECT * FROM OldTable;
```

10. Fetch Common Records between 2 Tables
```SQL
SELECT * FROM Table1
INTERSECT
SELECT * FROM Table2;
```

### Employee Table

E_ID | EmployeeName
--- | ---

### Salary Table

E_ID | D_ID |  Salary
--- | --- | ---

### Department Table

D_ID | DepartmentName | Manager
--- | --- | ---

11. Use Joins ( More than 2 Tables )
```SQL
SELECT EmployeeName, DepartmentName, Manager, Salary
FROM Employee E
INNER JOIN Salary S
ON E.E_ID  = S.E_ID
INNER JOIN Department D 
ON D.D_ID = S.D_ID;
```

12. Join using Child Parent Relationship
```SQL
SELECT EmployeeName, DepartmentName, Manager, Salary
FROM Employee E, Salary S, Department D
WHERE E.E_ID = D.E_ID AND D.D_ID = S.D_ID;
```

13. **Increase** Income of all Employees by `5%` in a Table
```SQL
UPDATE Employee
SET Income = Income + (Income * 0.05);
```

14. Find Names of Employee Starting with `A`
```SQL
SELECT Name 
FROM Employee
WHERE Name LIKE 'A%';
```
