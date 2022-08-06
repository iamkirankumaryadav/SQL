# `CTE` : Common Table Expressions

```sql
-- Syntax:
WITH CTE_Name AS (CTE Query...);

-- Example 1: Retrieve a snapshot from a table.
WITH CTE1 
AS (SELECT * FROM Employee LIMIT 10)
SELECT * FROM CTE1;

-- Example 2: Retrieve Maximum Average Salary from Employee Table.
WITH CTE2 
AS (SELECT Dept_ID, AVG(Salary) AS AVG_Salary FROM Employee GROUP BY Dept_ID)
SELECT MAX(AVG_Salary) FROM CTE2;
```

- `WITH` clause can include one or more CTE's seperated by `,`
- Enables user to write and maintain complex queries more easily with good readability and simplification.
- CTE's can be a useful tool when you need to generate `temporary` tables used only within a query.
- CTE's tables can be used by `SELECT`, `INSERT`, `UPDATE`, `DELETE` and `MERGE` statement.
- A `CTE` must be followed by a single `SELECT`, `INSERT`, `UPDATE` or `DELETE` statement that references some or all CTE columns.
