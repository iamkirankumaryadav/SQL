### `TOP N`

### `TOP`

- Top 3 highest salary.

```sql
SELECT 
TOP 3 *
FROM Employee
ORDER BY Salary DESC
```

- Top 3 lowest salary

```sql
SELECT 
TOP 3 *
FROM Employee
ORDER BY Salary
```

### `LIMIT`
```sql
SELECT *
FROM Employee
ORDER BY Salary DESC
LIMIT 3
```

### `FETCH FIRST`

```sql
SELECT 
*
FROM Employee
ORDER BY Salary DESC
FETCH FIRST 10 ROWS ONLY
```
