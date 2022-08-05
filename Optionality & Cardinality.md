# `Optionality`

- Minimum number of associated records.
- Usually 0 or 1
- If product `must` have a supplier, `optionality = 1` (Mandatory)
- If product `might` have a supplier, `optionality = 0` (Optional)


# `Cardinality`

- Maximum number of associated records.
- Usually 1 or N
- If the product can have only one supplier, `cardinality = 1`
- If the product can have multiple supplier, `cardinality = N`


### Optionality and Cardinality are controlled automatically based on constraints.

Relationship | Constraints
:--- | :---
0..1 | NULL + UNIQUE
1..1 | NOT NULL + UNIQUE
1..N | NOT NULL + Not UNIQUE
0..N | NULL + Not UNIQUE
