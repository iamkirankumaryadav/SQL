# **Data Control Language (DCL)**

DCL commands are used to **grant** and **revoke** the authority/permission/privileges from any database user.

### **GRANT**

```sql
-- Grant access privileges to the user:
GRANT SELECT, INSERT, UPDATE
ON employee TO 'Kirankumar', 'Suraj';
```

### **REVOKE**

```sql
-- Revoke permissions from the user:
REVOKE SELECT, INSERT, UPDATE
ON employee FROM 'Suraj';
```
