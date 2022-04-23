# `DQL` : Data Query Language

### `CREATE` 
```sql
CREATE Table Employee
(
    Employee_ID INT NOT NULL IDENTITY(1,1) PRIMARY KEY,  # IDENTITY(1,1) Start from 1 and Increment by 1 
    First_Name  NVARCHAR(60),
    Last_Name   NVARCHAR(60),
    Email       NVARCHAR(60)
)
```

### `INSERT`
```sql
INSERT INTO Employee(First_Name, Last_Name, Email)  # Employee_ID will increment automatically. 
VALUES('Kirankumar', 'Yadav', 'Kirankumaryadav@gmail.com')
```

### `ALTER`
Change the structure (Data type, column names, add or drop columns) of table.
```sql
ALTER Table Employee
DROP Column Email
```
