# `Normalization`

- A series of rules that describe proper database design.
- Normalization process `removes redundant` information from the database.
- Rules for table structure are called `normal forms`
- Helps to keep the data secure, valid and maintain the consistency and efficiency.

### `1NF` : First Normal Form
- `1NF` requires that all the fields only include a single piece of data.
- e.g We should keep the addresses in seperate columns Address, City, Pincode, State, Country instead of keeping in one single column.

### `2NF` : Second Normal Form
- Primary key should uniquely identifed without any comnination of values from the other fields.
- e.g Primary key should not be a combination of Name and DOB.

### `3NF` : Third Normal Form
- All the non key fields should be independent from each others.
- e.g If the State column is having abbreviated values like MH for Maharashtra and HYD for Hyderabad, we should not add another column to enter the State details in full form.

# `Denormalization`

- Denormalization deliberetly `introduces redundancy` in order to increase performance.
- `3NF` is converted to `2NF` to compromise the trade off between speed and storage.
