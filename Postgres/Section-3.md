## Data Types in PostgreSQL

Data types in PostgreSQL define the kind of data that can be stored in each column of a table. Choosing the correct data type ensures efficient data storage and accurate operations.

### Common Data Types

- **Numeric**: For storing numbers.
  - `INT`: Integer numbers.
  - `DOUBLE`, `FLOAT`: Floating-point numbers with varying precision.
  - `DECIMAL`: Precise decimal numbers, useful for financial data.

- **String**: For storing text.
  - `VARCHAR`: Variable-length character string with a specified maximum length.
  - `TEXT`: Variable-length character string without a specified maximum length.

- **Date and Time**: For storing dates and times.
  - `DATE`: A calendar date (year, month, day).
  - `TIMESTAMP`: A date and time, including a time zone.

- **Boolean**: For storing true/false values.
  - `BOOLEAN`: Stores `TRUE`, `FALSE`, or `NULL`.

### Example of the `DECIMAL` Data Type

The `DECIMAL` data type can be defined with two numbers: `DECIMAL(5,2)`.
- **5**: Total number of digits that can be stored (precision).
- **2**: Number of digits after the decimal point (scale).

**Example**: `DECIMAL(5,2)` can store values like:
- `155.38`
- `119.12`
- `28.15`

It cannot store values like `1150.89` because it exceeds the precision of 5 digits.

---

## Constraints in PostgreSQL

Constraints are rules applied to columns in a table to ensure data integrity. They define what values can be stored in a column.

### Primary Key Constraint

The `PRIMARY KEY` constraint uniquely identifies each record in a table. The primary key enforces the following rules:
- **Uniqueness**: No two rows can have the same value in the primary key column(s).
- **Non-NULL**: The primary key column(s) cannot contain `NULL` values.

A table can only have one primary key, but it can consist of multiple columns (a composite key).

```sql
CREATE TABLE person (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    city VARCHAR(100)
);
```

In this example:
- The `id` column is the primary key.
- Each `id` in the `person` table must be unique and not `NULL`.

---

## CRUD Operations in PostgreSQL

CRUD stands for Create, Read, Update, and Delete. These operations represent the core actions that can be performed on a database.

### Creating a Table

A table is a collection of related data held in a database. Here’s an example of how to create a table:

```sql
CREATE TABLE employees (
  emp_id SERIAL PRIMARY KEY,
  fname VARCHAR(50) NOT NULL,
  lname VARCHAR(50) NOT NULL,
  email VARCHAR(100) NOT NULL UNIQUE,
  dept VARCHAR(50),
  salary DECIMAL(10,2) DEFAULT 30000.00,
  hire_date DATE NOT NULL DEFAULT CURRENT_DATE
);
```

### Inserting Data

After creating a table, you can insert data into it:

```sql
INSERT INTO employees (fname, lname, email, dept, salary)
VALUES ('Raj', 'Sharma', 'raj.sharma@example.com', 'IT', 50000.00);
```

### Reading Data

Retrieve data from a table using the `SELECT` statement:

```sql
SELECT * FROM employees;
```

### Updating Data

To modify existing data in a table, use the `UPDATE` statement:

```sql
UPDATE employees
SET salary = 55000.00
WHERE emp_id = 1;
```

### Deleting Data

To remove data from a table, use the `DELETE` statement:

```sql
DELETE FROM employees
WHERE emp_id = 10;
```

---

## Auto-Incrementing Primary Key

The `SERIAL` data type automatically generates a unique, incrementing integer for each row in the table. This is often used for primary keys.

---

## Visual References

### Example of Data Types and Constraints
![Data Types](https://github.com/shyama7004/Aiida-Personal_Documentation/blob/main/Postgres/Images/53.jpg)
![Constraints](https://github.com/shyama7004/Aiida-Personal_Documentation/blob/main/Postgres/Images/54.jpg)
![CRUD Operations](https://github.com/shyama7004/Aiida-Personal_Documentation/blob/main/Postgres/Images/55.jpg)

### Auto-Incrementing Primary Key
![Auto-Increment](https://github.com/shyama7004/Aiida-Personal_Documentation/blob/main/Postgres/Images/57.jpg)

---

## Task: Creating a New Table

![Task](https://github.com/shyama7004/Aiida-Personal_Documentation/blob/main/Postgres/Images/59.jpg)

### Solution

```sql
CREATE TABLE employees (
	emp_id SERIAL PRIMARY KEY,
	fname VARCHAR(50) NOT NULL,
	lname VARCHAR(50) NOT NULL,
	email VARCHAR(100) NOT NULL UNIQUE,
	dept VARCHAR(50),
	salary DECIMAL(10,3) DEFAULT 40000.00,
	hire_date DATE NOT NULL DEFAULT CURRENT_DATE
);
```

### Inserting Data

```sql
INSERT INTO employees (emp_id, fname, lname, email, dept, salary, hire_date)
VALUES
(1, 'Raj', 'Sharma', 'raj.sharma@example.com', 'IT', 50000.00, '2020-01-15'),
(2, 'Priya', 'Singh', 'priya.singh@example.com', 'HR', 45000.00, '2019-03-22'),
(3, 'Arjun', 'Verma', 'arjun.verma@example.com', 'IT', 55000.00, '2021-06-01'),
(4, 'Suman', 'Patel', 'suman.patel@example.com', 'Finance', 60000.00, '2018-07-30'),
(5, 'Kavita', 'Rao', 'kavita.rao@example.com', 'HR', 47000.00, '2020-11-10'),
(6, 'Amit', 'Gupta', 'amit.gupta@example.com', 'Marketing', 52000.00, '2020-09-25'),
(7, 'Neha', 'Desai', 'neha.desai@example.com', 'IT', 48000.00, '2019-05-18'),
(8, 'Rahul', 'Kumar', 'rahul.kumar@example.com', 'IT', 53000.00, '2021-02-14'),
(9, 'Anjali', 'Mehta', 'anjali.mehta@example.com', 'Finance', 61000.00, '2018-12-03'),
(10, 'Vijay', 'Nair', 'vijay.nair@example.com', 'Marketing', 50000.00, '2020-04-19');
```

---

## Common Issues and Debugging

### Issue: Inserting Data Fails

If an error occurs during data insertion, such as assigning a duplicate primary key or not following the sequence, PostgreSQL will throw an error. Here are some steps to debug:

1. **Error Example**: Trying to insert a duplicate `emp_id`.

   ![Error Image](https://github.com/shyama7004/Aiida-Personal_Documentation/blob/main/Postgres/Images/3.png)

2. **Check Sequence**: Use the following command to check the sequence of the auto-incremented field.

   ![Sequence Check](https://github.com/shyama7004/Aiida-Personal_Documentation/blob/main/Postgres/Images/4.png)

3. **Correcting the Sequence**: If you mistakenly assign a value to `currval`, you need to reset the sequence.

   ![Sequence Reset](https://github.com/shyama7004/Aiida-Personal_Documentation/blob/main/Postgres/Images/6.png)

4. **Try Again**: After correcting the sequence, retry the data insertion.

   ![Success Image](https://github.com/shyama7004/Aiida-Personal_Documentation/blob/main/Postgres/Images/7.png)
