# SQL Case Statement

### Multiple IF THEN ELSE Statement
```SQL
CASE
  WHEN condition1 THEN result1
  WHEN condition2 THEN result2
  WHEN condition3 THEN result3
  ELSE result4
END;
```

### Search Condition
**Create a new column:**
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
**Mapping with the existing column:**
```SQL
SELECT first_name, last_name, age,
CASE gender
  WHEN 'F' THEN 'Female'
  WHEN 'M' THEN 'Male'
  ELSE 'Transgender'
END AS gender
FROM employee;
```

### Update using CASE
**Updating the column value based on conditions:**
```SQL
UPDATE employees 
SET rating = CASE
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
SELECT DECODE (grade, 'A', 1, `B`, 2, `C`, 3, `D`, 4, 0)
AS points
FROM students
```

### DECODE vs CASE

DECODE | CASE
:--- | :---
Function | Statement
Only works for `=` operator | Works for all the logical `=`, `<>`, `>`, `>=`, `<`, `<=` operators
Use only in SQL SELECT statement | Also used in PL-SQL
