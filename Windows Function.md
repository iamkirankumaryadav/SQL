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
