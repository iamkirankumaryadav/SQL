# `TCL` - `Transaction Control Language`

`TCL` commands can only used with `DML` commands like `INSERT`, `UPDATE` and `DELETE` only.

These operations are auto commited in the database that's why they cannot be used while creating tables or dropping them.

<a href=#commit><code>COMMIT</commit></a> <a href=#rollback><code>ROLLBACK</commit></a> <a href=#savepoint><code>SAVEPOINT</commit></a>

<h2 name=commit><code>COMMIT</code></h2>

Save all the transactions to the database.

```sql
DELETE FROM Customers
WHERE Age=25;
COMMIT;
```

<h2 name=rollback><code>ROLLBACK</code></h2>

`Undo` transactions that have not already been saved to the database.

```sql
DELETE FROM Customers
WHERE Age=25;
ROLLBACK;
```

<h2 name=savepoint><code>SAVEPOINT</code></h2>

Roll the transaction back to certain point without rolling back the entire transaction.
