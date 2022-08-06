# `HAVING`

- Only used after `GROUP BY` clause.
- Supports Aggregate Conditions ( i.e SUM(Salary) > 200000, AVG(Salary) < 1000000 )

```sql
SELECT
D.Department, count(*) AS EmployeeCount
FROM Employee E
JOIN Department D
ON E.DepartmentID = D.ID
GROUP BY D.DepartmentName
HAVING EmployeeCount > 50
ORDER BY D.DepartmentName
```
