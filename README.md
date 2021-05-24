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
SELECT
TOP N * 
FROM Employee
ORDER BY Salary
DESC;
```
