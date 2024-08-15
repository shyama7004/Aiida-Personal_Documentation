# PostgreSQL SQL Operations and Clauses

## Inserting Data into a Table

The `INSERT INTO` statement is used to add new records to a table. Below is an example of inserting multiple records into an `employees` table:

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

### Explanation:
- **INSERT INTO**: Specifies the table to insert the data into.
- **VALUES**: Lists the values to insert for each record. Each set of values corresponds to the columns defined in the `INSERT INTO` statement.

---

## SQL Clauses and Operations

### 1. **WHERE Clause**
The `WHERE` clause is used to filter records based on specified conditions.

**Example: Find employees whose salary is greater than 65,000**
```sql
SELECT * FROM employees
WHERE salary > 65000;
```

### 2. **Relational Operators**
Relational operators compare values. Common operators include `=`, `>`, `<`, `>=`, `<=`, and `!=`.

### 3. **Logical Operators**
Logical operators combine multiple conditions in a `WHERE` clause.
- **AND**: Both conditions must be true.
- **OR**: At least one condition must be true.

**Example:**
```sql
-- Find employees with a salary of 25,000 and in the Loan department
SELECT * FROM employees
WHERE salary = 25000 AND dept = 'Loan';

-- Find employees with a salary of 65,000 or with the designation 'Lead'
SELECT * FROM employees
WHERE salary = 65000 OR desig = 'Lead';
```

### 4. **IN and NOT IN**
The `IN` operator is used to specify multiple possible values for a column.

**Example: Find employees from the IT, HR, and Finance departments**
```sql
SELECT * FROM employees
WHERE dept IN ('IT', 'HR', 'Finance');
```

### 5. **BETWEEN**
The `BETWEEN` operator filters the result set within a certain range.

**Example: Find employees whose salary is between 40,000 and 65,000**
```sql
SELECT * FROM employees
WHERE salary BETWEEN 40000 AND 65000;
```

### 6. **DISTINCT**
The `DISTINCT` keyword is used to return only distinct (different) values.

**Example: Get distinct first names of employees**
```sql
SELECT DISTINCT fname FROM employees;
```

### 7. **ORDER BY**
The `ORDER BY` clause sorts the result set by one or more columns.

**Example: Sort employees by their first name**
```sql
SELECT * FROM employees ORDER BY fname;
```

### 8. **LIMIT**
The `LIMIT` clause specifies the number of records to return.

**Example: Return the first 3 employees**
```sql
SELECT * FROM employees LIMIT 3;
```

### 9. **LIKE**
The `LIKE` operator is used to search for a specified pattern in a column.

**Examples:**
```sql
-- Find departments that contain 'Acc'
SELECT * FROM employees WHERE dept LIKE '%Acc%';

-- Starts with 'A'
SELECT * FROM employees WHERE fname LIKE 'A%';

-- Ends with 'A'
SELECT * FROM employees WHERE fname LIKE '%A';

-- Contains 'A'
SELECT * FROM employees WHERE fname LIKE '%A%';

-- Second character is 'A'
SELECT * FROM employees WHERE fname LIKE '_A%';

-- Case-insensitive search for 'john'
SELECT * FROM employees WHERE fname ILIKE '%john%';
```

### 10. **Other Clauses and Operators**
- **GROUP BY**: Groups rows that have the same values into summary rows.
- **HAVING**: Filters groups based on a condition (used with `GROUP BY`).
- **JOIN**: Combines rows from two or more tables based on a related column.
- **UNION**: Combines the result sets of two or more `SELECT` statements.

