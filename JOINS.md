# JOINS

## Tables (Example)

### Employee Table

E_ID | EmployeeName
--- | ---

### Salary Table

E_ID | D_ID |  Salary
--- | --- | ---

### Department Table

D_ID | DepartmentName | Manager
--- | --- | ---

### Inner Join
```SQL
SELECT Orders.ID, Customers.Name
FROM Orders
INNER JOIN Customers 
ON Orders.ID = Customers.ID;
```

### LEFT Join
```SQL
SELECT O.ID, C.Name
FROM Orders O
LEFT JOIN Customers C
ON O.ID = C.ID;
```

### RIGHT Join
```SQL
SELECT O.ID, C.Name
FROM Orders O
RIGHT JOIN Customers C
ON O.ID = C.ID;
```

### SELF Join
```SQL
SELECT DISTINCT E.Name
FROM Employees E
INNER JOIN Managers M
ON E.ID = M.ID;
```

### Joins ( More than 2 Tables )
```SQL
SELECT EmployeeName, DepartmentName, Manager, Salary
FROM Employee E
INNER JOIN Salary S
ON E.E_ID  = S.E_ID
INNER JOIN Department D 
ON D.D_ID = S.D_ID;
```

### Join using Child Parent Relationship
```SQL
SELECT EmployeeName, DepartmentName, Manager, Salary
FROM Employee E, Salary S, Department D
WHERE E.E_ID = D.E_ID AND D.D_ID = S.D_ID;
```
