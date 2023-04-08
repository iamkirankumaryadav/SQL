# `DCL` - `Data Control Language`

DCL commands are used to `grant` and take back the authority from any database user.

<a href=#grant><code>GRANT</code></a> <a href=#revoke><code>REVOKE</code></a> 

<h2 name=grant><code>GRANT</code></h2>

Give user access privileges to a database.

```sql
GRANT SELECT, UPDATE ON TABLE TO USER1, USER2;
```

<h2 name=revoke><code>REVOKE</code></h2>

Take back permissions from the user.

```sql
REVOKE SELECT, UPDATE ON TABLE FROM USER1, USER2;
```
