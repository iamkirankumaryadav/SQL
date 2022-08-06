# `Windows Function`

### `first_value()`

Get the first value of the row from the group

```sql
SELECT
DepartmentID,
FirstName,
LastName,
Salary,
first_value(salary) OVER (PARTITION BY DepartmentID)
FROM Employee
```
