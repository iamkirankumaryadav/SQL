# Concepts

### Changing Schema

1. Adding columns in an existing table.
2. Removing columns from an existing table.
3. Adding or changing constraints of an existing table.
4. Changing data type.

```sql
CREATE TABLE Employee
(
  First_Name TEXT,
  Last_Name TEXT,
  Designation TEXT
);

INSERT INTO Test
VALUES ('Kirankumar', 'Yadav', 'Data Scientist'),
VALUES ('Suraj', 'MS', 'MLE'),
VALUES ('Pavan', 'Kumar', 'Statistician');

SELECTT * FROM Employee;

ALTER TABLE 
ADD Department TEXT DEFAULT 'Data Science';
```   
