# `CTE` : Common Table Expressions

- CTE's is a useful tool to generate `temporary` tables used only within a query.
- `CTE` must be followed by a single `SELECT`, `INSERT`, `UPDATE` or `DELETE` statement that references CTE columns.
- `WITH` clause can include one or more CTE's seperated by using `,` ( Commas )
- Enables user to write and maintain complex queries more easily with good readability and simplification.

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


