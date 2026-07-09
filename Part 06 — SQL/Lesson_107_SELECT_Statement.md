# Lesson 107 --- SELECT Statement

> **Part 06 --- Structured Query Language (SQL)**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What the `SELECT` statement is
-   Why `SELECT` is the most important SQL command
-   Basic syntax
-   Selecting specific columns
-   Using `SELECT *`
-   Selecting expressions
-   Column aliases (preview)
-   Internal execution flow
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Imagine asking a librarian:

-   Show me all Computer Science books.
-   Show only book titles.
-   Show book titles and prices.

You are requesting information.

In SQL, those requests are made with **SELECT**.

------------------------------------------------------------------------

# 2. What is SELECT?

`SELECT` is the primary **DQL (Data Query Language)** command used to
retrieve data from one or more tables.

``` text
Database
    │
 SELECT
    │
Required Information
```

It never changes the data. It only reads it.

------------------------------------------------------------------------

# 3. Why Do We Need SELECT?

Without `SELECT`:

-   We cannot view stored data.
-   Reports cannot be generated.
-   Dashboards cannot display information.
-   Applications cannot show user data.

------------------------------------------------------------------------

# 4. Basic Syntax

``` sql
SELECT column_name
FROM table_name;
```

Example:

``` sql
SELECT Name
FROM Student;
```

------------------------------------------------------------------------

# 5. Selecting Multiple Columns

``` sql
SELECT StudentID,
       Name,
       Age
FROM Student;
```

Output:

``` text
StudentID  Name    Age
-----------------------
101        Alice   20
102        Bob     21
```

------------------------------------------------------------------------

# 6. SELECT \*

Retrieve every column.

``` sql
SELECT *
FROM Student;
```

``` text
*
│
All Columns
```

### When to Use

-   Learning SQL
-   Testing
-   Exploring a table

### When to Avoid

-   Production applications
-   Large tables
-   Performance-sensitive queries

------------------------------------------------------------------------

# 7. Selecting Expressions

SQL can calculate values while retrieving data.

``` sql
SELECT Name,
       Salary * 12 AS AnnualSalary
FROM Employee;
```

Result:

``` text
Name    AnnualSalary
--------------------
Riya    780000
```

------------------------------------------------------------------------

# 8. Column Aliases (Preview)

Aliases provide temporary names.

``` sql
SELECT Salary AS MonthlySalary
FROM Employee;
```

Output heading becomes:

``` text
MonthlySalary
```

------------------------------------------------------------------------

# 9. Internal Execution

``` text
SELECT Request
      │
Read Table
      │
Retrieve Columns
      │
Return Result Set
```

If additional clauses exist (`WHERE`, `ORDER BY`, etc.), they are
processed according to SQL's logical execution order.

------------------------------------------------------------------------

# 10. Real-World Example

Display employee names and salaries.

``` sql
SELECT Name,
       Salary
FROM Employee;
```

Application flow:

``` text
User Clicks

↓

SELECT Query

↓

DBMS Reads Table

↓

Results Displayed
```

------------------------------------------------------------------------

# 11. Best Practices

-   Select only required columns.
-   Avoid `SELECT *` in production.
-   Use meaningful aliases.
-   Format queries neatly.
-   Keep queries readable.

------------------------------------------------------------------------

# 12. Common Mistakes

❌ Missing `FROM`.

``` sql
SELECT Name;
```

❌ Misspelled column names.

❌ Assuming `SELECT` changes data.

❌ Using `SELECT *` everywhere.

------------------------------------------------------------------------

# 13. Interview Questions

### Beginner

1.  What is the SELECT statement?
2.  Is SELECT DQL or DML?
3.  What does `SELECT *` mean?

### Intermediate

1.  Why avoid `SELECT *` in production?
2.  What are column aliases?

### Advanced

1.  Explain how SELECT is processed internally.
2.  How does SELECT affect performance?

------------------------------------------------------------------------

# 14. Practice Problems

1.  Display all student names.
2.  Display Name and Age.
3.  Display every column.
4.  Calculate Annual Salary.
5.  Rename a column using an alias.

------------------------------------------------------------------------

# Revision Notes

``` text
SELECT
   │
Choose Columns
   │
FROM
   │
Retrieve Data
```

## Memory Trick

``` text
SELECT

=

See

Data
```

## Key Points

-   `SELECT` retrieves data.
-   It is the primary DQL command.
-   `SELECT *` returns all columns.
-   Expressions and aliases can be used.
-   Selecting only required columns improves performance.

------------------------------------------------------------------------

# Final Takeaway

The `SELECT` statement is the foundation of SQL because almost every
interaction with a relational database begins by retrieving information.
Whether you are building a web application, generating reports, or
analyzing millions of records, `SELECT` is the command that transforms
stored data into useful answers. Learning to write efficient SELECT
queries is one of the most valuable database skills you can develop.
