# Data Control Language (DCL)
DCL commands are used to **grant** and **revoke** the authority/permission/privileges from any database user.

### GRANT

**Here, SQL_COMMANDS means SELECT, INSERT, UPDATE, DELETE, etc.**
```sql
-- Syntax: 
GRANT SQL_COMMANDS
ON table_name TO 'username1', 'username2';
```  
**Grant access privilege to the users:**
```sql
GRANT SELECT, INSERT, UPDATE
ON employee TO 'Kirankumar', 'Suraj';
```

### **REVOKE**
```sql
-- Syntax: 
REVOKE SQL_COMMANDS
ON table_name FROM 'username1', 'username2';
```  

```sql
-- Revoke permission from the users:
REVOKE SELECT, INSERT, UPDATE
ON employee FROM 'Suraj';
```
