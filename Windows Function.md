# `Windows Function`

### `first_value()`

- Get the first value of the row from the group.
- `DESC` will return the `largest` value.
- `ASC` will return the `smallest` value.

```sql
SELECT
DepartmentID,
FirstName,
LastName,
Salary,
first_value(salary) OVER (PARTITION BY DepartmentID ORDER BY Salary DESC)
FROM Employee
```

Numeric function should be applied on entire window.

```sql
SELECT
DepartmentID,
FirstName,
LastName,
ROUND(AVG(salary) OVER (PARTITION BY DepartmentID ORDER BY Salary DESC), 2) AS AverageSalary
FROM Employee
```

### `NTILE`

```sql
SELECT
DepartmentID,
FirstName,
LastName,
NTILE(4) OVER (PARTITION BY DepartmentID ORDER BY Salary DESC) AS Quartile
FROM Employee
```

### `NTH_VALUE`
