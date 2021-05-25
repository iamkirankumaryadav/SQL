# Difference

###  Delete vs Truncate vs Drop

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

### Where vs Having

WHERE | HAVING
--- | ---
`Filter` Rows | Works on `Aggregated` Data

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
