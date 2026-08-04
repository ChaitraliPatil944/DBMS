# Lesson 111 --- LIMIT, OFFSET & TOP

> **Part 06 --- Structured Query Language (SQL)**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What `LIMIT`, `OFFSET`, and `TOP` are
-   Why they are used
-   Pagination concepts
-   Syntax in different DBMSs
-   LIMIT vs TOP
-   Internal working
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Imagine an online shopping website with **1,000,000 products**.

Should it display all products at once?

No.

Instead it shows:

``` text
Page 1 → 20 Products

Next →

Page 2 → Next 20 Products
```

SQL uses `LIMIT`, `OFFSET`, and `TOP` to achieve this.

------------------------------------------------------------------------

# 2. Why Do We Need LIMIT?

Without limiting results:

``` sql
SELECT *
FROM Product;
```

Millions of rows may be returned.

With `LIMIT`:

``` sql
SELECT *
FROM Product
LIMIT 20;
```

Only 20 rows are returned.

------------------------------------------------------------------------

# 3. What is LIMIT?

`LIMIT` restricts the number of rows returned.

``` text
Query Result
     │
 LIMIT
     │
Required Number of Rows
```

------------------------------------------------------------------------

# 4. LIMIT Syntax

``` sql
SELECT column_list
FROM table_name
LIMIT number;
```

Example:

``` sql
SELECT *
FROM Student
LIMIT 5;
```

Output:

``` text
Only first 5 rows
```

------------------------------------------------------------------------

# 5. What is OFFSET?

`OFFSET` skips a specified number of rows before returning results.

Syntax:

``` sql
SELECT *
FROM Student
LIMIT 10
OFFSET 20;
```

Meaning:

``` text
Skip first 20 rows

↓

Return next 10 rows
```

------------------------------------------------------------------------

# 6. Pagination Example

``` text
Page Size = 10

Page 1

LIMIT 10 OFFSET 0

Page 2

LIMIT 10 OFFSET 10

Page 3

LIMIT 10 OFFSET 20
```

This is how websites implement page navigation.

------------------------------------------------------------------------

# 7. What is TOP?

`TOP` is primarily used in Microsoft SQL Server.

Syntax:

``` sql
SELECT TOP 5 *
FROM Employee;
```

Result:

``` text
First 5 rows
```

------------------------------------------------------------------------

# 8. LIMIT vs TOP

  LIMIT                       TOP
  --------------------------- ---------------------------------
  MySQL, PostgreSQL, SQLite   SQL Server
  Appears at end              Appears after SELECT
  Supports OFFSET naturally   OFFSET/FETCH used with ORDER BY

------------------------------------------------------------------------

# 9. Internal Working

``` text
Read Rows
    │
Apply WHERE
    │
Apply ORDER BY
    │
Skip OFFSET Rows
    │
Return LIMIT/TOP Rows
```

Without `ORDER BY`, the returned rows are not guaranteed to be in any
particular order.

------------------------------------------------------------------------

# 10. Real-World Example

Display the newest five orders.

``` sql
SELECT *
FROM Orders
ORDER BY OrderDate DESC
LIMIT 5;
```

SQL Server:

``` sql
SELECT TOP 5 *
FROM Orders
ORDER BY OrderDate DESC;
```

------------------------------------------------------------------------

# 11. Best Practices

-   Combine `ORDER BY` with `LIMIT`.
-   Use pagination for large datasets.
-   Retrieve only required columns.
-   Avoid very large OFFSET values when possible.

------------------------------------------------------------------------

# 12. Common Mistakes

❌ Using LIMIT without ORDER BY.

❌ Confusing LIMIT with WHERE.

❌ Assuming TOP works in every DBMS.

------------------------------------------------------------------------

# 13. Interview Questions

### Beginner

1.  What is LIMIT?
2.  What is OFFSET?
3.  What is TOP?

### Intermediate

1.  LIMIT vs TOP?
2.  Why is ORDER BY recommended with LIMIT?
3.  What is pagination?

### Advanced

1.  How does OFFSET affect performance?
2.  Why do large OFFSET values become slower?

------------------------------------------------------------------------

# 14. Practice Problems

1.  Display the first 10 students.
2.  Display products 21--30.
3.  Display the top 5 highest-paid employees.
4.  Implement pagination for page 4 with page size 20.
5.  Compare LIMIT and TOP.

------------------------------------------------------------------------

# Revision Notes

``` text
LIMIT
 │
Rows Returned

OFFSET
 │
Rows Skipped

TOP
 │
SQL Server Limit
```

## Memory Trick

``` text
LIMIT

= Return Few

OFFSET

= Skip Few

TOP

= First Few
```

## Key Points

-   `LIMIT` restricts returned rows.
-   `OFFSET` skips rows.
-   `TOP` is SQL Server's equivalent.
-   Always combine with `ORDER BY` for predictable results.
-   Pagination improves application performance and user experience.

------------------------------------------------------------------------

# Final Takeaway

`LIMIT`, `OFFSET`, and `TOP` allow SQL to return only the portion of
data that users actually need. These features are essential for web
applications, APIs, dashboards, and reports where loading every row
would waste time and resources. Efficient pagination keeps applications
fast and users happy, which is a pleasantly rare outcome in software
engineering.
