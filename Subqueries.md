# `Subqueries`

`SELECT` Statment can be used at 3 places.

### For specifying `Column Values`

```sql
SELECT
E1.FirstName, 
E1.LastName, 
E1.DepartmentID,
(SELECT 
  ROUND(AVG(E2.Salary),2) AS AverageSalary 
  FROM Employee E2
  WHERE E1.DepartmentID = E2.DepartmentID)
FROM Employee E1
```

### Subqueries in `FROM` Clause

- Subquery in FROM must have an `alias`

```sql
SELECT 
ROUND(AVG(E1.Salary),2) AS AverageSalary
FROM (SELECT * FROM Employee WHERE Salary > 100000) E1
       
```

### Subqueries in `WHERE` Clause

Expressions returns a `BOOLEAN` result.
 
```sql
SELECT
DepartmentID
FROM Employee E1
WHERE (SELECT MAX(Salary) FROM Employee E2) = E1.Salary
```
