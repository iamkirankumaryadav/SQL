# JOINS

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
