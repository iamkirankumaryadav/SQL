# Difference

###  1. Delete vs Truncate vs Drop

DELETE | TRUNCATE | DROP
--- | --- | ---
DML | DDL | DDL
Remove `Some` or `All` Rows | Remove `All` Rows | Remove `Table` from Database
WHERE Clause | `No` WHERE Clause | `No` WHERE Clause
Roll Back | `No` Roll Back | `No` Roll Back
Do not Remove Permanently | Remove Records Permanently | Remove Records, Indexes, Structures Permanently

### DELETE 
```SQL 
DELETE FROM Employee
WHERE EID IN (1,2,3);
```

### TRUNCATE
```SQL
TRUNCATE Table Employee;
```

### DROP 
```SQL
DROP Table Employee;
```

### 2. Where vs Having

WHERE | HAVING
--- | ---
`Filter` Rows | Works on `Aggregated` Data

**Aggregate Functions** are use to `Summarize` Data ( Returns Single Value for Multiple Rows )

### SUM | AVG | COUNT | MAX | MIN

### WHERE
```SQL
SELECT * 
FROM Employee
WHERE Designation = 'Data Scientist';
```

### HAVING
```SQL
SELECT MAX(Salary)
FROM Employee
GROUP BY Designation
HAVING MAX(Salary) > 100000;
```

### 3. Union vs Union All

Combines `2` or `more` Tables
- Tables must have same Number of `Columns`
- Columns must have same `Data Types`
- Columns must have same `Order`

UNION | UNION
`Remove` Duplicate Records | `Keep` Duplicate Records

### UNION
```SQL
SELECT * FROM Sales
UNION
SELECT * FROM Product
ORDER BY ProductName;
```

### UNION ALL
```SQL
SELECT * FROM Sales
UNION ALL
SELECT * FROM Product
ORDER BY ProductName;
```

### 4. In vs Exist 

### IN 
- Multiple `OR`

```SQL
SELECT * FROM Employee
WHERE City = 'Mumbai' OR City = 'Bangalore' OR City = 'Pune';
```

```SQL
SELECT * FROM Employee
WHERE City IN (`Mumbai`, `Bangalore`, `Pune`);
```

```SQL
SELECT * FROM Sales
WHERE City IN (SELECT City FROM Returns)
```

### EXISTS
- Returns either `True` or `False` Value ( Tests for Existance of Record in a Sub Query )

```SQL
SELECT * FROM Sales
WHERE EXISTS (SELECT City FROM Returns
              WHERE Returns.ID = Sales.ID AND Price < 500)
```

### 5. Order By vs Group By

ORDER BY | GROUP BY
--- | ---
Sorting in `ASC` or `DESC` Order | Used with `Aggregate` Functions

### ORDER BY

```SQL
SELECT * FROM Sales
ORDER BY City 
DESC;
```

### GROUP BY
```SQL
SELECT IsActive, COUNT(*)
FROM Customers
GROUP BY IsActive;
```

WHERE Clause is Used with SELECT Clause before GROUP BY
```SQL
SELECT Designation, Salary 
FROM Employee
WHERE Designation IN ('Data Scientist', 'Data Analyst', 'Business Analyst', 'Data Architect', 'Machine Learning Engineer')
GROUP BY Designation;
```

HAVING Clause is used with GROUP BY and WHERE Clause `cannot` be used after GROUP BY
```SQL
SELECT Model, Price 
FROM Vehicles
GROUP BY Model
HAVING SUM(Price) > 5000000
ORDER BY Price DESC;
```

### 6. Join vs Sub Query

`Combine` Data from Different Tables into a Single Table

### Sub Query

Select only from `First` Table

```SQL
SELECT Phone, CustomerName
FROM Customers
WHERE C_ID IN (SELECT C_ID 
               FROM Orders)
```

### JOIN

Select from `Either` of the Table

```SQL
SELECT Phone, CustomerName, OrderID
FROM Customers C
JOIN Orders O
ON O.CustomerID = C.CustomerID
```

### Union vs Join

UNION | JOIN
--- | ---
`Combine` Rows | `Merge` Columns  
Number of `Columns` and Data Type of Columns should be same | Combines on the basis of Common `Column` ( ID )

### UNION 
```SQL
SELECT City from Table1
UNION
SELECT City from Table2;
```

### JOIN
```SQL
SELECT A.City, B.Name
FROM Departments A
JOIN Employee B
ON A.ID = B.ID;
```
