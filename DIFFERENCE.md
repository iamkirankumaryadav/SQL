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
WHERE EID IN (1,2,3)
```

### TRUNCATE
```SQL
TRUNCATE Table Employee
```

### DROP 
```SQL
DROP Table Employee
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
WHERE Designation = 'Data Scientist'
```

### HAVING
```SQL
SELECT MAX(Salary)
FROM Employee
GROUP BY Designation
HAVING MAX(Salary) > 100000
```

### 3. Union vs Union All

Combines 2 or more Tables
- Tables must have same Number of `Columns`.
- Columns must have same `Data Types`.
- Columns must have same `Order`.

UNION | UNION
`Remove` Duplicate Records | `Keep` Duplicate Records

### UNION
```SQL
SELECT * FROM Sales
UNION
SELECT * FROM Product
ORDER BY ProductName
```

### UNION ALL
```SQL
SELECT * FROM Sales
UNION ALL
SELECT * FROM Product
ORDER BY ProductName
```
