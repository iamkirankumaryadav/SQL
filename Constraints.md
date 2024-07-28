# **Constraints**
- SQL constraints specify rules for the data in a table.
- Invalid data won't be allowed in the database.
- Ensure that stored records meet the table's requirements.

```sql
-- Syntax
CREATE TABLE table_name(
  column1 datatype constraint,
  column2 datatype constraint,
  column3 datatype constraint
)
```

```sql
CREATE TABLE IF NOT EXISTS <Database Name>.<Schema Name>.<Table Name>(
  employee_id INT NOT NULL UNIQUE PRIMARY KEY,
  first_name VARCHAR(25),
  last_name VARCHAR(25),
  age INT CHECK (age >= 18),
  birthdate DATE,
  city VARCHAR(25) DEFAULT 'Bengaluru'
)
```

**Constraints** | **Definition**
:--- | :---
**NOT NULL** | Ensures that a column cannot have a NULL value
**UNIQUE** | Ensures that all values in a column are unique
**PRIMARY KEY** | A combination of a **NOT NULL** and **UNIQUE**. Uniquely identifies each row in a table
**FOREIGN KEY** | A **FOREIGN KEY** is a column in one table, that refers to the **PRIMARY KEY** in another table.
**CHECK** | Ensures that the values in a column satisfy a specific condition
**DEFAULT** | Sets a default value for a column if no value is specified

### INDEXES
- Keep track of records and help to retrieve the records easily and quickly.
- Added to any columns used in frequent searches or joins.
- Primary keys are created as a clustered index.
- Indexes can also be added to any additional field other than the primary key (Non Clustered Index)
- Adding an index slows down the insert operations, after every insert or update the indexes are rebuilt.
