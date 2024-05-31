# **Data Control Language (DCL)**

- DCL commands are used to grant and revoke the authority/permission/privileges from any database user.

### **GRANT**

```sql
# Give user access privileges to a database:
GRANT SELECT, INSERT, UPDATE
ON TABLE TO 'Kirankumar', 'Suraj';
```

### **REVOKE**

```sql
# Take back permissions from the user:
REVOKE SELECT, INSERT, UPDATE
ON TABLE FROM 'Suraj';
```
