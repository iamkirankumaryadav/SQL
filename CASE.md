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
SELECT Customer, CustomerName,
CASE
  WHEN Payment > 1000 THEN 'Payment is More than 1000'
  WHEN Payment < 1000 THEN 'Payment is Less than 1000'
  ELSE 'Payment is Equal to 1000'
END AS Result
FROM Customers;
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

