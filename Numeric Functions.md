# **Numeric Functions + Operations**

**Aggregate Functions** | **Description**
:--- | :---
**SUM()** | Calculates the sum of values in a column
**AVG()** | Calculates the average of values in a column
**MIN()** | Returns the minimum value in a column
**MAX()** | Returns the maximum value in a column
**COUNT()** | Counts the number of rows in a column

```sql
SELECT
SUM(Salary) AS TotalSalary,
AVG(Salary) AS AverageSalary,
MIN(Salary) AS MinimumSalary,
MAX(Salary) AS MaximumSalary
FROM Employee;
```

### `TRUNC` : Drop all the decimal values

```sql
SELECT TRUNC(1234.5678) AS Amount;
```

Amount
:---
1234

### `ROUND`

```sql
SELECT ROUND(1234.5678, 2) AS Amount;
```

Amount
:---
1235.57

### `CEIL`

```sql
SELECT CEIL(1234.56) AS Amount;
```

Amount
:---
1235
