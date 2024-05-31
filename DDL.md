# **DDL: Data Definition Language**

- Creates the data structures (Schemas, Tables, Views, and Indexes) that help organize data.
- All the commands of DDL are auto-committed (Permanently save all the changes in the database)

<a href=#create><strong>CREATE</strong></a> | 
<a href=#alter><strong>ALTER</strong></a> | 
<a href=#drop><strong>DROP</strong></a> | 
<a href=#truncate><strong>TRUNCATE</strong></a> 

<h3 name=create><strong>CREATE</strong></h3>

```sql
# Create Schema:
CREATE SCHEMA IF NOT EXISTS SchemaName;
```

```sql
# Create Table:
CREATE TABLE Employee
(
    Employee_ID INT NOT NULL IDENTITY(1, 1) PRIMARY KEY,  # IDENTITY(1,1) Start from 1 and Increment by 1 
    FirstName   NVARCHAR(60),
    LastName    NVARCHAR(60),
    Email       NVARCHAR(60)
);
```

```sql
# Create View:
CREATE VIEW Staff_View AS
SELECT s.ID, s.LastName, cd.Company
FROM Staff s
LEFT JOIN Company_Division cd
ON s.Department = cd.Department;
```

```sql
# Create Index:
CREATE INDEX idx_staff_last_name
ON Staff
USING (Last_Name);
```

<h3 name=alter><strong>ALTER</strong></h3>

- Alter/Modify/Change table structure (data type, column names, add or drop columns).
- Either to modify the characteristics of an existing attribute or probably to add a new attribute.

```sql
# Drop Column:
ALTER TABLE Employee
DROP COLUMN Email;
```

```sql
# Add new columns:
ALTER TABLE Employee
ADD Age INT, Department NVARCHAR(50);
```

```sql
# Modify the size and data type:
ALTER TABLE Employee
ALTER COLUMN Country NVARCHAR(30);
```

```sql
# Rename table name:    
ALTER TABLE table_name
RENAME TO new_table_name;    
```    

```sql
# Rename column name:
ALTER TABLE table_name
RENAME COLUMN old_name TO new_name;   
```

<h3 name=drop><strong>DROP</strong></h3>

```sql
# Delete the entire table data including structure and constraints.
DROP TABLE Employee;
```
    
<h3 name=truncate><strong>TRUNCATE</strong></h3>

```sql
# Delete data from the table, while retaining the structure of the table.
TRUNCATE TABLE Employee
DROP COLUMN Email;
```
