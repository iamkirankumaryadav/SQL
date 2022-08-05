# `DML` : Data Manipulation Language

### `SELECT`

### `INSERT`

`Single` row:

```sql
-- Employee_ID will increment automatically. 
INSERT INTO Employee(FirstName, LastName, Email)  
VALUES('Kirankumar', 'Yadav', 'Kirankumaryadav@gmail.com')
```

`Multiple` rows:

```sql
INSERT INTO Employee(FirstName, LastName, Email)  
VALUES('Kirankumar', 'Yadav', 'Kirankumar.Yadav@gmail.com'),
      ('Kisankumar', 'Yadav', 'Kisankumar.Yadav@gmail.com'),
      ('Rohit', 'Yadav', 'Rohit.Yadav@gmail.com'),
      ('Arpit', 'Yadav', 'Arpit.Yadav@gmail.com')
```

### `UPDATE` 
```sql
UPDATE Employee
SET Designation = 'Data Scientist'
WHERE FirstName = 'Kirankumar' 
AND LastName = 'Yadav' 
AND DateOfBirth = '07/02/1996'
```

### `DELETE`
```sql
DELETE 
FROM Supplier
WHERE SupplierID = 2
-- WHERE Clause is only used with DELETE command ( Not with DROP and TRUNCATE commands )
```
