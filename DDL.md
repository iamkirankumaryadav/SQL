# `DDL` : Data Definition Language

Creates the data structures ( `Schemas`, `Tables`, `Views` and `Indexes` ) which helps to organize data.

All the `commands` of DDL are auto commited (Permanently save all the changes in the database)

<a href=#create><code>CREATE</code></a> <a href=#alter><code>ALTER</code></a> <a href=#drop><code>DROP</code></a> <a href=#rename><code>RENAME</code></a> <a href=#truncate><code>TRUNCATE</code></a>

<h2 name=create><code>CREATE</code><h2>

### `CREATE SCHEMA`

```sql
CREATE SCHEMA IF NOT EXISTS SchemaName;
```

### `CREATE TABLE`

```sql
CREATE Table Employee
(
    Employee_ID INT NOT NULL IDENTITY(1,1) PRIMARY KEY,  # IDENTITY(1,1) Start from 1 and Increment by 1 
    FirstName   NVARCHAR(60),
    LastName    NVARCHAR(60),
    Email       NVARCHAR(60)
);
```

### `CREATE VIEW`

```sql
CREATE VIEW Staff_View AS
SELECT
S.ID
S.LastName
CD.Company
FROM Staff S
LEFT JOIN Company_Division CD
ON S.Department = CD.Department;
```

### `CREATE INDEX`

```sql
CREATE INDEX idx_staff_last_name
ON Staff
USING (Last_Name);
```

<h2 name=alter><code>ALTER</code></h2>

Alter | Change the structure (Data type, column names, add or drop columns) of table.

Either to `modify` the characteristics of an existing attribute or probably to `add` a new attribute.

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
-- Modify size and data type:
ALTER Table Employee
ALTER Column Country NVARCHAR(30);
```

<h2 name=truncate><code>TRUNCATE</code></h2>
    
Delete data from the table, while retaining the structure of the table.

```sql
TRUNCATE Table Employee
DROP Column Email;
```

<h2 name=drop><code>DROP</code></h>

Delete the entire table data including structure and constraints.

```sql
DROP Table Employee;
```
