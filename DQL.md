# `DQL` : Data Query Language

Keyword Comparison Operators 
```
1. BETWEEN     : Returns data within range of values.
2. IN          : Returns data within a list of values.
3. LIKE        : Returns data similar to given pattern (Using Wildcard %)
4. IS NULL     : Returns null values.
5. IS NOT NULL : Returns not null values.
6. EXISTS      : Determine if a subquery returns values or not.
```
Querying the table with logical operator `LIKE` :
```sql
SELECT Code from Table
WHERE Code LIKE '_2_6'

Results :
`1216`
`1226`
`1236`...
```


