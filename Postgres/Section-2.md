# PostgreSQL CLI and Database Management on Mac M1

## Accessing PostgreSQL CLI

To access the PostgreSQL command-line interface (CLI) on your Mac M1:

1. **Open Spotlight Search**: Press `F4` or use `Command + Space`, then type `psql` to launch the PostgreSQL CLI.
2. **Connect to a Database**: Upon launching the CLI, you'll be connected to the default `postgres` database, displayed as:

   ```bash
   postgres=#
   ```

3. **Common Commands**:
   - `\l` - List all databases.
   - `\c <db_name>` - Connect to a specific database.
   - `\dt` - List all tables in the current database.
   - `\d <table_name>` - Describe the structure of a table.
   - `\d+ <table_name>` - Detailed information on columns.
   - `\q` - Quit the PostgreSQL CLI.

## Understanding Database Structures

### 1. **Database**
   - **Definition**: A collection of organized data, the highest level in a database management system (DBMS).
   - **Purpose**: Containers for schemas, tables, views, and other objects.
   - **Example**: A database named `company_db` for storing a company's data.

### 2. **Schema**
   - **Definition**: A logical grouping of database objects like tables, views, indexes, and sequences within a database.
   - **Purpose**: Organizes data within the same database, allowing multiple users or applications to manage data independently.
   - **Example**: Schemas like `sales`, `hr`, and `inventory` in the `company_db` database.

### 3. **Table**
   - **Definition**: A structured collection of data entries with columns and rows within a schema.
   - **Purpose**: Stores data in a structured format, with rows as records and columns as attributes.
   - **Example**: An `employees` table in the `hr` schema with columns for `id`, `name`, `position`, and `salary`.

### **Summary**
- **Database**: The overarching container for all data and database objects.
- **Schema**: A logical grouping of related database objects within a database.
- **Table**: The structure within a schema where data is stored.

### **Analogy**
- A **Database** is like a filing cabinet.
- A **Schema** is like a drawer within the cabinet.
- A **Table** is like a folder within a drawer, containing related documents (data records).

### **Visual Structure**

```
Database: company_db
│
├── Schema: sales
│   ├── Table: customers
│   ├── Table: orders
│
├── Schema: hr
│   ├── Table: employees
│   ├── Table: payroll
│
└── Schema: inventory
    ├── Table: products
    ├── Table: suppliers
```

## Managing Databases

### Listing Databases

To list all existing databases:

```sql
SELECT datname FROM pg_database;
```

Or use:

```bash
\l
```

*Note: PostgreSQL is case-insensitive.*

### Creating a Database

To create a new database:

```sql
CREATE DATABASE <db_name>;
```

Replace `<db_name>` with the desired database name.

### Connecting to a Database

To switch to another database:

```bash
\c <db_name>
```

Replace `<db_name>` with the target database's name.

### Deleting a Database

To delete a database:

```sql
DROP DATABASE <db_name>;
```

*Warning: This command permanently removes the database.*

*Note: The database refreshes automatically in pgAdmin when you right-click and select refresh.*

## CRUD Operations

### Creating a Table

To create a table in PostgreSQL:

```sql
CREATE TABLE person (
    id INT,
    name VARCHAR(100),
    city VARCHAR(100)
);
```

To view the table structure:

```bash
\d person
```

### Explanation

1. **`CREATE TABLE person`**: Creates a new table named `person`.
2. **`id INT`**: An integer column for storing unique identifiers.
3. **`name VARCHAR(100)`**: A text column for storing names, up to 100 characters.
4. **`city VARCHAR(100)`**: A text column for storing city names, up to 100 characters.

### Inserting Data

To insert data into the table:

```sql
INSERT INTO person (id, name, city)
VALUES (101, 'Raju', 'Delhi'),
       (102, 'Sham', 'Delhi');
```

### Reading Data

To retrieve all data:

```sql
SELECT * FROM person;
```

To retrieve specific columns:

```sql
SELECT name, city FROM person;
```

### Updating Data

To update existing data:

```sql
UPDATE person
SET city = 'London'
WHERE id = 101;
```

### Deleting Data

To delete a row:

```sql
DELETE FROM person
WHERE name = 'Raju';
```

*Note: Queries can be executed individually by selecting them and clicking the run button.*

## Handling Data Integrity

### Common Issues
1. **Duplicate IDs**: 
   If the same `id` is accidentally assigned to multiple rows, it may lead to data integrity issues.
   ![Duplicate ID Issue](https://github.com/shyama7004/Aiida-Personal_Documentation/blob/main/Postgres/Images/1.png)

2. **Missing Data**:
   If a column value, such as `city`, is not provided, it will result in a `NULL` value.
   ![Missing Data Issue](https://github.com/shyama7004/Aiida-Personal_Documentation/blob/main/Postgres/Images/2.png)

### Solutions
- **Enforce Uniqueness**: Use constraints like `PRIMARY KEY` on the `id` column to prevent duplicate entries.
- **Handle NULL Values**: Ensure all required fields are populated or use default values.

---
