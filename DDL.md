# **DDL: Data Definition Language**

- Creates the data structures (Schemas, Tables, Views, and Indexes) that help organize data.
- All the commands of DDL are auto-committed (Permanently save all the changes in the database)

<a href=#create><strong>CREATE</strong></a> | 
<a href=#alter><strong>ALTER</strong></a> | 
<a href=#rename><strong>RENAME</strong></a> | 
<a href=#truncate><strong>TRUNCATE</strong></a> | 
<a href=#drop><strong>DROP</strong></a>

<h3 name=create><strong>CREATE</strong><h3>

### **CREATE SCHEMA**

```sql
CREATE SCHEMA IF NOT EXISTS SchemaName;
```

### **CREATE TABLE**

```sql
CREATE TABLE Employee
(
    Employee_ID INT NOT NULL IDENTITY(1, 1) PRIMARY KEY,  # IDENTITY(1,1) Start from 1 and Increment by 1 
    FirstName   NVARCHAR(60),
    LastName    NVARCHAR(60),
    Email       NVARCHAR(60)
);
```

### **CREATE VIEW**

```sql
CREATE VIEW Staff_View AS
SELECT S.ID, S.LastName, CD.Company
FROM Staff S
LEFT JOIN Company_Division CD
ON S.Department = CD.Department;
```

### **CREATE INDEX**

```sql
CREATE INDEX idx_staff_last_name
ON Staff
USING (Last_Name);
```

<h3 name=alter><strong>ALTER</strong></h3>

- Alter/Modify/Change table structure (Data type, column names, add or drop columns).
- Either to modify the characteristics of an existing attribute or probably to add a new attribute.

```sql
-- DROP Column:
ALTER Table Employee
DROP Column Email;
```

```sql
-- Add new columns:
ALTER Table Employee
ADD Age INT, Department NVARCHAR(50);
```

```sql
-- Modify the size and data type:
ALTER Table Employee
ALTER Column Country NVARCHAR(30);
```

<h3 name=renam><strong>RENAME</strong></h3>
    
Rename the old table name or any table column to a new name.   

```sql
-- Rename table name:    
ALTER TABLE table_name
RENAME TO new_table_name;    
```    

```sql
-- Rename column name:
ALTER TABLE table_name
RENAME COLUMN old_name TO new_name;   
```
    
<h3 name=truncate><strong>TRUNCATE</strong></h3>
    
Delete data from the table, while retaining the structure of the table.

```sql
TRUNCATE Table Employee
DROP Column Email;
```

<h3 name=drop><strong>DROP</strong></h3>

Delete the entire table data including structure and constraints.

```sql
DROP Table Employee;
```
