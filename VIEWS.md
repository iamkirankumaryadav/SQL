# **Views**

### **Virtual Table** (Do not exist in reality)

- You can't modify data in the **VIEW**.
- Database object that presents data from one or more tables.
- Selecting fields/columns from one or more tables present in database.
- There is no records/rows in the VIEW (Only holds definition of table and fetches data from the table and view it)

### **CREATE VIEWS**

```SQL
-- Single Table:
CREATE VIEW details AS
SELECT name, address
FROM students 
WHERE age > 18;
```

We can also add GROUP BY, HAVING, ORDER BY...

```SQL
-- Multiple Tables:
CREATE VIEW details AS
SELECT s.name, s.address, m.marks
FROM students s, marks m
WHERE s.ID = m.ID
```

### **DROP VIEWS**
```SQL
DROP VIEW details
```
