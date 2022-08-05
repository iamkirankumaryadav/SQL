# `DML` : Data Manipulation Language

### `SELECT`

### `INSERT`
```sql
INSERT INTO Employee(First_Name, Last_Name, Email)  # Employee_ID will increment automatically. 
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
