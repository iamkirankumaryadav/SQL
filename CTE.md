# `CTE` : Common Table Expressions

```sql
-- Syntax:
WITH CTE_Name AS (CTE Query...);

-- Example:
WITH CTE1 AS (SELECT * FROM Employee LIMIT 10)
SELECT * FROM CTE1;

WITH CTE2 AS (SELECT Dept_ID, AVG(Sales) AS AVG_Sale FROM Employee GROUP BY Dept_ID)
SELECT MAX(AVG_Sale) FROM CTE2;
```

- `WITH` clause can include one or more CTE's seperated by `,`
- Enables user to write and maintain complex queries more easily with good readability and simplification.
- CTE's can be a useful tool when you need to generate `temporary` result sets that can be accessed by `SELECT`, `INSERT`, `UPDATE`, `DELETE` and `MERGE` statement.
- A CTE must be followed by a single `SELECT`, `INSERT`, `UPDATE` or `DELETE` statement that references some or all CTE columns.
