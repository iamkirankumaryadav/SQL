# SQL Case Statement

### Multiple IF THEN ELSE Statement

```SQL
CASE
  WHEN Condition1 THEN Result1
  WHEN Condition2 THEN Result2
  WHEN Condition3 THEN Result3
  ELSE Result4
END;
```

### Search Condition
```SQL
SELECT first_name, last_name, age,
CASE
  WHEN salary < 300000 THEN 'Nil'
  WHEN salary BETWEEN 300000 AND 600000 THEN '5%'
  WHEN salary BETWEEN 600000 AND 900000 THEN '10%'
  WHEN salary BETWEEN 900000 AND 1200000 THEN '15%'
  WHEN salary BETWEEN 1200000 AND 1500000 THEN '20%'
  ELSE '30%'
END AS tax
FROM payroll;
```

### Update using CASE
```SQL
UPDATE Employees 
SET Rating = CASE
                WHEN RATE < 3 THEN 'Satisfactory'
                WHEN RATE = 3 THEN 'Acceptable'
                WHEN RATE > 3 THEN 'Excellent'
                ELSE "Okay"
             END;  
```

### DECODE

```sql
---  Syntax:
SELECT DECODE (ColumnName, IF, THEN value, ELSE IF, THEN value, ELSE, Value)
AS Alias
FROM TableName

--- Example:
SELECT DECODE (Grade, 'A', 1, `B`, 2, `C`, 3, `D`, 4, 0)
AS Points
FROM Students
```

### DECODE vs CASE

DECODE | CASE
:--- | :---
Function | Statement
Only works for `=` operator | Works for all the logical `=`, `<>`, `>`, `>=`, `<`, `<=` operators
Use only in SQL SELECT statement | Also used in PL-SQL
