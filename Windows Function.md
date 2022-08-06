# `Windows Function`

- Window functions are used to apply a function to a `group` of rows in a relation.

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
FROM Employee;
```

Numeric function should be applied on entire window.

```sql
SELECT
DepartmentID,
FirstName,
LastName,
ROUND(AVG(salary) OVER (PARTITION BY DepartmentID ORDER BY Salary DESC), 2) AS AverageSalary
FROM Employee;
```

### `NTILE`

```sql
SELECT
DepartmentID,
FirstName,
LastName,
NTILE(4) OVER (PARTITION BY DepartmentID ORDER BY Salary DESC) AS Quartile
FROM Employee;
```

### `NTH_VALUE`

N value in the entire result set:

```sql
SELECT
DepartmentID,
FirstName,
LastName,
nth_value(Salary, 2) OVER (PARTITION BY DepartmentID ORDER BY Salary DESC)
FROM Employee;
```

### `RANK`

Assign a `rank` based on desired column value for each group.

```sql
SELECT
DepartmentID,
FirstName,
LastName,
RANK() OVER (PARTITION BY DepartmentID ORDER BY Salary DESC) AS Rank
FROM Employee;
```

Assign a `rank` based on desired column value for entire table.

```sql
SELECT
DepartmentID,
FirstName,
LastName,
RANK() OVER (ORDER BY Salary DESC) AS Rank
FROM Employee;
```

### `LEAD`

- Provide leading row value (Just looking one row ahead by 1 offset)
- By default offset is 1, if we pass LEAD(x, 2) then it will get value from 2 rows ahead.

```sql
SELECT
DepartmentID,
FirstName,
LastName,
LEAD(Salary) OVER (PARTITION BY DepartmentID ORDER BY Salary DESC) AS Leading
FROM Employee;
```

### `LAG`

```sql
SELECT
DepartmentID,
FirstName,
LastName,
LAG(Salary) OVER (PARTITION BY DepartmentID ORDER BY Salary DESC) AS Lagging
FROM Employee;
```

### `WIDTH_BUCKET`

- Ranking with `%`

```sql
SELECT
DepartmentID,
FirstName,
LastName,
WIDTH_BUCKET(Salary, 0, 150000, 10) -- Start = 0, End = 150000, Bucket Size = 10
FROM Employee;
```

### `CUME_DIST`

- Cummulative Distribution

```sql
SELECT
DepartmentID,
FirstName,
LastName,
ROUND((CUME_DIST() OVER (ORDER BY Salary DESC) * 100)::NUMERIC, 2) -- ::NUMERIC Casting double precision to NUMERIC.
FROM Employee;
```
