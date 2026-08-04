# Lesson 091 --- SQL Syntax & Rules

> **Part 06 --- Structured Query Language (SQL)**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   Basic SQL syntax
-   SQL keywords and identifiers
-   SQL statement structure
-   Case sensitivity
-   Comments in SQL
-   Naming conventions
-   SQL syntax rules
-   Writing your first SQL queries
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Why Learn SQL Syntax?

Knowing SQL commands is not enough.

You must also know **how SQL statements are written**.

Think of SQL like English.

Correct words + Correct grammar = Correct sentence

Similarly:

``` text
Correct SQL Commands
        +
Correct SQL Syntax
        =
Successful Query
```

------------------------------------------------------------------------

# 2. What is SQL Syntax?

**SQL syntax** is the set of rules that defines how SQL statements must
be written so the DBMS can understand them.

Example:

``` sql
SELECT Name
FROM Student;
```

Incorrect:

``` sql
Name SELECT Student FROM;
```

------------------------------------------------------------------------

# 3. Structure of a SQL Statement

A basic query follows this pattern:

``` sql
SELECT column_name
FROM table_name
WHERE condition;
```

ASCII flow:

``` text
SELECT
   │
Columns
   │
FROM
   │
Table
   │
WHERE
   │
Condition
```

------------------------------------------------------------------------

# 4. SQL Keywords

Keywords are reserved words with special meaning.

Examples:

``` text
SELECT
FROM
WHERE
INSERT
UPDATE
DELETE
CREATE
ALTER
DROP
```

Keywords should not be used as table or column names unless quoted.

------------------------------------------------------------------------

# 5. Identifiers

Identifiers are names you create.

Examples:

``` text
Student
Employee
OrderDetails
CustomerName
Salary
```

Good identifiers should be:

-   Meaningful
-   Short
-   Consistent

------------------------------------------------------------------------

# 6. SQL Case Sensitivity

Most DBMSs treat SQL keywords as case-insensitive.

These are usually equivalent:

``` sql
SELECT * FROM Student;
```

``` sql
select * from student;
```

Common convention:

-   SQL Keywords → UPPERCASE
-   Table/Column Names → PascalCase or snake_case

Example:

``` sql
SELECT StudentName
FROM Student;
```

------------------------------------------------------------------------

# 7. SQL Comments

Single-line comment:

``` sql
-- Show all students
SELECT * FROM Student;
```

Multi-line comment:

``` sql
/*
Retrieve
all active
students
*/
SELECT * FROM Student;
```

Comments improve readability and documentation.

------------------------------------------------------------------------

# 8. Naming Conventions

Good:

``` text
Student
Employee
DepartmentID
OrderDate
```

Avoid:

``` text
abc
x1
table1
temp123
```

General guidelines:

-   Start with a letter.
-   Avoid spaces.
-   Avoid special characters.
-   Be descriptive.

------------------------------------------------------------------------

# 9. SQL Syntax Rules

-   End statements with `;` (recommended and required in many tools).
-   Separate multiple columns with commas.
-   Match parentheses correctly.
-   Use quotes for string literals.
-   Use numeric values without quotes.

Correct:

``` sql
SELECT Name, Age
FROM Student
WHERE City = 'Pune';
```

------------------------------------------------------------------------

# 10. Your First SQL Query

``` sql
SELECT *
FROM Student;
```

Meaning:

``` text
SELECT → Retrieve

* → All Columns

FROM → Student Table
```

Result:

``` text
StudentID   Name    Age
-----------------------
101         Alice   20
102         Bob     21
```

------------------------------------------------------------------------

# 11. Common Syntax Errors

❌ Missing comma

``` sql
SELECT Name Age
FROM Student;
```

✔ Correct

``` sql
SELECT Name, Age
FROM Student;
```

------------------------------------------------------------------------

❌ Missing quotes

``` sql
WHERE City = Pune
```

✔ Correct

``` sql
WHERE City = 'Pune'
```

------------------------------------------------------------------------

❌ Misspelled keyword

``` sql
SELEKT * FROM Student;
```

------------------------------------------------------------------------

# 12. Real-World Example

Employee Management System

``` sql
SELECT Name, Salary
FROM Employee
WHERE Salary > 50000;
```

The DBMS:

``` text
Read Query
      │
Find Table
      │
Filter Rows
      │
Return Results
```

------------------------------------------------------------------------

# 13. Best Practices

-   Write keywords in uppercase.
-   Use meaningful names.
-   Indent long queries.
-   Comment complex logic.
-   Keep formatting consistent.

------------------------------------------------------------------------

# 14. Interview Questions

### Beginner

1.  What is SQL syntax?
2.  What are SQL keywords?
3.  What are identifiers?

### Intermediate

1.  Is SQL case-sensitive?
2.  Why are comments used?

### Advanced

1.  Explain the structure of a SELECT statement.
2.  What are common SQL syntax mistakes?

------------------------------------------------------------------------

# 15. Practice Problems

1.  Write a query to display all columns from the Student table.
2.  Write a query to display Name and Age.
3.  Add comments to a query.
4.  Identify syntax errors in incorrect SQL statements.

------------------------------------------------------------------------

# Revision Notes

``` text
SELECT
   │
Columns
   │
FROM
   │
Table
   │
WHERE
   │
Condition
```

## Memory Trick

``` text
S F W

SELECT
FROM
WHERE
```

## Key Points

-   SQL syntax defines how SQL statements are written.
-   Keywords are reserved words.
-   Identifiers are user-defined names.
-   SQL keywords are generally case-insensitive.
-   Good formatting makes SQL easier to read and debug.

------------------------------------------------------------------------

# Final Takeaway

Learning SQL syntax is like learning the grammar of a language. Once you
understand the structure of SQL statements, writing queries becomes much
easier. Good syntax not only helps the DBMS understand your commands but
also makes your code readable for teammates and for your future self,
who will eventually wonder why Past You thought a one-line,
300-character query was a reasonable life choice.
