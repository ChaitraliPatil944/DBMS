# Lesson 106 --- DQL (Data Query Language) Overview

> **Part 06 --- Structured Query Language (SQL)**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What DQL is
-   Why DQL is important
-   What a query is
-   How SQL retrieves data
-   Major DQL clauses
-   DQL vs DML vs DDL
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Imagine a library containing one million books.

You ask:

-   Show all books written by J.K. Rowling.
-   Show books published after 2020.
-   Show the five most expensive books.

You are **querying** the library.

Databases work the same way.

------------------------------------------------------------------------

# 2. What is DQL?

**DQL (Data Query Language)** is the part of SQL used to **retrieve
information** from a database.

The primary DQL command is:

``` text
SELECT
```

Everything else helps refine the results.

``` text
Database
    │
 SELECT Query
    │
 Required Data
```

------------------------------------------------------------------------

# 3. Why Do We Need DQL?

Without DQL:

-   Data exists but cannot be viewed.
-   Reports cannot be generated.
-   Analytics cannot be performed.

DQL transforms stored data into useful information.

------------------------------------------------------------------------

# 4. What is a Query?

A **query** is simply a request for information.

Example:

``` sql
SELECT Name
FROM Student;
```

Meaning:

> "Show me the Name column from the Student table."

------------------------------------------------------------------------

# 5. Major DQL Clauses

``` text
DQL
│
├── SELECT
├── FROM
├── WHERE
├── DISTINCT
├── GROUP BY
├── HAVING
├── ORDER BY
├── LIMIT / OFFSET
```

Each clause has a specific responsibility.

------------------------------------------------------------------------

# 6. How DQL Works

``` text
User
 │
SQL Query
 │
DBMS
 │
Read Table
 │
Filter Rows
 │
Return Results
```

The database does not return everything unless you ask for everything.

------------------------------------------------------------------------

# 7. Example Query

``` sql
SELECT Name, Salary
FROM Employee
WHERE Department = 'IT'
ORDER BY Salary DESC;
```

Process:

``` text
Employee Table
      │
Department = IT
      │
Sort by Salary
      │
Display Result
```

------------------------------------------------------------------------

# 8. DQL vs DML vs DDL

  DQL              DML                             DDL
  ---------------- ------------------------------- ---------------------
  Retrieves data   Changes data                    Changes structure
  SELECT           INSERT, UPDATE, DELETE, MERGE   CREATE, ALTER, DROP

------------------------------------------------------------------------

# 9. Real-World Applications

DQL powers:

-   Banking account statements
-   Hospital patient searches
-   E-commerce product listings
-   Airline booking searches
-   Student result portals
-   Business dashboards

Almost every screen showing database information is backed by a DQL
query.

------------------------------------------------------------------------

# 10. Best Practices

-   Retrieve only required columns.
-   Avoid `SELECT *` in production when unnecessary.
-   Filter data using `WHERE`.
-   Sort results only when needed.
-   Write readable SQL.

------------------------------------------------------------------------

# 11. Common Mistakes

❌ Using `SELECT *` for every query.

❌ Forgetting the `WHERE` clause when filtering.

❌ Confusing DQL with DML.

❌ Selecting unnecessary columns.

------------------------------------------------------------------------

# 12. Interview Questions

### Beginner

1.  What is DQL?
2.  Which command belongs to DQL?
3.  What is a query?

### Intermediate

1.  Why is SELECT considered the heart of SQL?
2.  DQL vs DML?

### Advanced

1.  Explain how the DBMS processes a SELECT query.
2.  Why should `SELECT *` be avoided in production systems?

------------------------------------------------------------------------

# 13. Practice Problems

1.  Write a query to display all students.
2.  Display employee names only.
3.  List products costing more than 1000.
4.  Display employees sorted by salary.
5.  Explain DQL in your own words.

------------------------------------------------------------------------

# Revision Notes

``` text
DQL
 │
SELECT
 │
Retrieve Data
 │
WHERE
 │
ORDER BY
 │
GROUP BY
 │
HAVING
```

## Memory Trick

``` text
DQL

=

Discover

Query

Learn
```

## Key Points

-   DQL retrieves data from databases.
-   The primary DQL command is `SELECT`.
-   Clauses such as `WHERE`, `ORDER BY`, and `GROUP BY` refine results.
-   DQL does not modify database contents.
-   Efficient queries improve application performance.

------------------------------------------------------------------------

# Final Takeaway

DQL is the part of SQL that turns stored data into meaningful answers.
Every search result, report, dashboard, and analytics screen ultimately
depends on DQL queries. Mastering data retrieval is one of the most
valuable SQL skills because asking the right question is often more
important than simply storing the data in the first place.
