# Data Control Language (DCL)
- Data Control Language (DCL) commands are used to control access to data within a database.
- DCL commands manage user privileges and permissions, ensuring data security and integrity.
- **Data Security:** Protects sensitive data by restricting access to authorized users.
- **Data Integrity:** Prevents unauthorized modifications to data.
- **GRANT:** Assigns specific privileges to users or roles.
- **REVOKE:** Revokes previously granted privileges.
- Here, **SQL_COMMANDS** means SELECT, INSERT, UPDATE, DELETE, etc.

### GRANT
```sql
-- Syntax: 
GRANT SQL_COMMANDS
ON table_name TO 'username1', 'username2';

-- Example:
GRANT SELECT, INSERT, UPDATE, DELETE 
ON employee TO 'Kirankumar', 'Suraj';
```

### REVOKE
```sql
-- Syntax: 
REVOKE SQL_COMMANDS
ON table_name FROM 'username1', 'username2';

-- Example:
REVOKE SELECT, INSERT, UPDATE, DELETE
ON employee FROM 'Suraj';
```
