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
SUBSTRING(Designation,0,Charindex(' ',Designation))
FROM Employee;
```
