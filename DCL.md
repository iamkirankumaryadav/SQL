# **Data Control Language (DCL)**

- DCL commands are used to grant and revoke the authority/permission from any database user.

<a href=#grant><strong>GRANT</strong></a> | <a href=#revoke><strong>REVOKE</strong></a> 

<h2 name=grant><strong>GRANT</strong></h2>

```sql
# Give user access privileges to a database:
GRANT SELECT, INSERT, UPDATE ON TABLE TO 'Kirankumar', 'Suraj';
```

<h2 name=revoke><strong>REVOKE</strong></h2>

```sql
# Take back permissions from the user:
REVOKE SELECT, INSERT, UPDATE ON TABLE FROM 'Suraj';
```
