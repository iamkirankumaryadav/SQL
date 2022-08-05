# `DML` : Data Manipulation Language

### `SELECT`

### `INSERT`
```sql
INSERT INTO Employee(FirstName, LastName, Email)  # Employee_ID will increment automatically. 
VALUES('Kirankumar', 'Yadav', 'Kirankumaryadav@gmail.com')
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
```
