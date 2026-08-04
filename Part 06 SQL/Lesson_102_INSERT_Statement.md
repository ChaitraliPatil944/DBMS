# Lesson 102 --- INSERT Statement

> **Part 06 --- Structured Query Language (SQL)**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What the `INSERT` statement is
-   Why `INSERT` is used
-   INSERT syntax
-   Inserting single and multiple rows
-   INSERT INTO ... SELECT
-   Inserting partial column values
-   Common insertion errors
-   Best practices
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

A table without records is like a notebook with blank pages.

The structure exists, but no useful information is stored.

The **INSERT** statement fills the table with data.

------------------------------------------------------------------------

# 2. What is INSERT?

`INSERT` is a **DML (Data Manipulation Language)** command used to add
new rows to a table.

``` text
Application
     │
INSERT
     │
New Row
     │
Database Table
```

------------------------------------------------------------------------

# 3. Why Do We Need INSERT?

Without INSERT:

-   No customer records
-   No employee details
-   No products
-   No transactions

A database remains empty until data is inserted.

------------------------------------------------------------------------

# 4. Basic Syntax

``` sql
INSERT INTO table_name(column1, column2, ...)
VALUES(value1, value2, ...);
```

------------------------------------------------------------------------

# 5. Insert a Single Row

``` sql
INSERT INTO Student
(StudentID, Name, Age)
VALUES
(101, 'Alice', 20);
```

Result:

``` text
StudentID  Name   Age
----------------------
101        Alice  20
```

------------------------------------------------------------------------

# 6. Insert Multiple Rows

``` sql
INSERT INTO Student
(StudentID, Name, Age)
VALUES
(102, 'Bob', 21),
(103, 'Charlie', 22),
(104, 'David', 20);
```

Multiple rows are inserted with one statement.

------------------------------------------------------------------------

# 7. Insert into Selected Columns

``` sql
INSERT INTO Student
(StudentID, Name)
VALUES
(105, 'Eva');
```

Other columns receive:

-   DEFAULT values (if defined)
-   NULL (if allowed)

------------------------------------------------------------------------

# 8. INSERT INTO ... SELECT

Copy data from one table to another.

``` sql
INSERT INTO StudentBackup
SELECT *
FROM Student;
```

Or copy selected columns:

``` sql
INSERT INTO Alumni(Name, Age)
SELECT Name, Age
FROM Student;
```

------------------------------------------------------------------------

# 9. How INSERT Works

``` text
INSERT Statement
        │
Validate Data Types
        │
Check Constraints
        │
Store Row
        │
Commit Transaction
```

If validation fails, the DBMS rejects the row.

------------------------------------------------------------------------

# 10. Real-World Example

A new employee joins a company.

``` sql
INSERT INTO Employee
(EmployeeID, Name, Department, Salary)
VALUES
(1001, 'Riya', 'IT', 65000);
```

The employee record is immediately available for payroll and HR systems.

------------------------------------------------------------------------

# 11. Common Errors

### Missing Required Column

``` sql
INSERT INTO Student
(StudentID)
VALUES (101);
```

Fails if `Name` is `NOT NULL`.

------------------------------------------------------------------------

### Duplicate PRIMARY KEY

``` sql
INSERT INTO Student
VALUES (101, 'John', 22);
```

Fails if StudentID 101 already exists.

------------------------------------------------------------------------

### Data Type Mismatch

``` sql
Age = 'Twenty'
```

Invalid for an `INT` column.

------------------------------------------------------------------------

### Constraint Violation

``` sql
Age = -5
```

Fails if a `CHECK (Age >= 0)` constraint exists.

------------------------------------------------------------------------

# 12. Best Practices

-   Always specify column names.
-   Validate data before inserting.
-   Insert multiple rows together for better performance.
-   Use transactions for important data loads.
-   Check constraints before execution.

------------------------------------------------------------------------

# 13. Interview Questions

### Beginner

1.  What is the `INSERT` statement?
2.  Is `INSERT` DDL or DML?
3.  Can multiple rows be inserted at once?

### Intermediate

1.  Why specify column names?
2.  What happens if a NOT NULL column is omitted?

### Advanced

1.  Explain `INSERT INTO ... SELECT`.
2.  How does the DBMS validate an INSERT?

------------------------------------------------------------------------

# 14. Practice Problems

1.  Insert one student record.
2.  Insert five product records.
3.  Insert only selected columns.
4.  Copy all rows into a backup table.
5.  Predict errors caused by duplicate PRIMARY KEY values.

------------------------------------------------------------------------

# Revision Notes

``` text
INSERT
   │
Single Row
Multiple Rows
Selected Columns
INSERT...SELECT
```

## Memory Trick

``` text
INSERT

=

Add New Records
```

## Key Points

-   `INSERT` adds new rows to a table.
-   Always prefer specifying column names.
-   Multiple rows can be inserted in one statement.
-   `INSERT INTO ... SELECT` copies data between tables.
-   Constraints are checked before data is stored.

------------------------------------------------------------------------

# Final Takeaway

The `INSERT` statement is the primary way new information enters a
relational database. Every customer registration, online order, hospital
admission, or bank transaction begins with an INSERT operation. Writing
reliable INSERT statements means understanding not only the syntax but
also how constraints, defaults, and data types work together to protect
the quality of your data.
