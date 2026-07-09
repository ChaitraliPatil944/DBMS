# Lesson 122 --- SQL Execution Order

> **Part 06 --- SQL Fundamentals**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   Why SQL execution order matters
-   Logical execution order vs written query order
-   How the DBMS processes a query
-   Common mistakes related to execution order
-   Performance implications
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

When beginners write SQL, they usually believe the database executes a
query exactly as it is written.

Example:

``` sql
SELECT Name
FROM Employee
WHERE Salary > 50000
ORDER BY Salary DESC;
```

The query is **written** from top to bottom, but the DBMS does **not**
execute it in that order.

Understanding the logical execution order is essential for writing
correct and efficient SQL queries.

------------------------------------------------------------------------

# 2. Written Order vs Logical Execution Order

## Written Order

``` text
SELECT
FROM
WHERE
GROUP BY
HAVING
ORDER BY
LIMIT
```

## Logical Execution Order

``` text
1. FROM
2. JOIN
3. WHERE
4. GROUP BY
5. HAVING
6. SELECT
7. DISTINCT
8. ORDER BY
9. LIMIT / OFFSET (or TOP)
```

The logical order is how the SQL engine actually processes the query.

------------------------------------------------------------------------

# 3. Step-by-Step Execution

## Step 1 --- FROM

Choose the table(s).

``` sql
FROM Employee
```

``` text
Employee Table
      │
Rows Loaded
```

------------------------------------------------------------------------

## Step 2 --- JOIN

If multiple tables exist, combine them.

``` text
Employee
    │
 JOIN
    │
Department
```

------------------------------------------------------------------------

## Step 3 --- WHERE

Filter individual rows.

``` sql
WHERE Salary > 50000
```

Only matching rows continue.

------------------------------------------------------------------------

## Step 4 --- GROUP BY

Create groups.

``` sql
GROUP BY Department
```

------------------------------------------------------------------------

## Step 5 --- HAVING

Filter the groups.

``` sql
HAVING COUNT(*) > 5
```

------------------------------------------------------------------------

## Step 6 --- SELECT

Choose the required columns.

``` sql
SELECT Department,
       COUNT(*)
```

------------------------------------------------------------------------

## Step 7 --- DISTINCT

Remove duplicate rows if requested.

------------------------------------------------------------------------

## Step 8 --- ORDER BY

Sort the final result.

``` sql
ORDER BY Salary DESC
```

------------------------------------------------------------------------

## Step 9 --- LIMIT / OFFSET

Return only the requested rows.

``` sql
LIMIT 10;
```

------------------------------------------------------------------------

# 4. Complete Execution Flow

``` text
FROM
 │
JOIN
 │
WHERE
 │
GROUP BY
 │
HAVING
 │
SELECT
 │
DISTINCT
 │
ORDER BY
 │
LIMIT / OFFSET
```

------------------------------------------------------------------------

# 5. Example

``` sql
SELECT Department,
       COUNT(*) AS Employees
FROM Employee
WHERE Salary > 50000
GROUP BY Department
HAVING COUNT(*) > 3
ORDER BY Employees DESC
LIMIT 5;
```

Execution:

``` text
Employee
   │
WHERE Salary > 50000
   │
GROUP BY Department
   │
HAVING COUNT > 3
   │
SELECT
   │
ORDER BY
   │
LIMIT 5
```

------------------------------------------------------------------------

# 6. Common Mistakes

❌ Using aggregate functions in WHERE.

``` sql
WHERE COUNT(*) > 5
```

✔ Correct:

``` sql
HAVING COUNT(*) > 5
```

❌ Expecting SELECT aliases to be available in WHERE.

------------------------------------------------------------------------

# 7. Performance Tips

-   Filter early with WHERE.
-   Avoid unnecessary DISTINCT.
-   Use indexes on filtering and join columns.
-   Limit returned rows whenever possible.

------------------------------------------------------------------------

# 8. Interview Questions

### Beginner

1.  What is SQL execution order?
2.  Does SQL execute from top to bottom?

### Intermediate

1.  Why does WHERE execute before SELECT?
2.  Why can't WHERE use aggregate functions?

### Advanced

1.  Explain the logical execution order of SQL.
2.  How does execution order affect performance?

------------------------------------------------------------------------

# 9. Practice Problems

1.  Write the logical execution order of SQL.
2.  Explain WHERE vs HAVING using execution order.
3.  Trace the execution of a query with GROUP BY and ORDER BY.
4.  Why is LIMIT processed last?

------------------------------------------------------------------------

# Revision Notes

``` text
Logical SQL Execution

FROM
 ↓
JOIN
 ↓
WHERE
 ↓
GROUP BY
 ↓
HAVING
 ↓
SELECT
 ↓
DISTINCT
 ↓
ORDER BY
 ↓
LIMIT / OFFSET
```

## Memory Trick

``` text
FROM
JOIN
WHERE
GROUP
HAVING
SELECT
DISTINCT
ORDER
LIMIT

=

Find
Joined
Wanted
Groups
Having
Selected
Distinct
Ordered
List
```

## Key Points

-   SQL is not executed in the order it is written.
-   WHERE filters rows before grouping.
-   HAVING filters groups after grouping.
-   ORDER BY sorts the final result.
-   LIMIT/OFFSET is applied at the end.

------------------------------------------------------------------------

# Final Takeaway

Understanding SQL execution order is one of the biggest steps from
beginner to intermediate SQL. It explains why certain queries work, why
others fail, and how the database transforms raw data into the final
result set. Mastering this sequence makes debugging easier, improves
query performance, and is a favorite topic in technical interviews.
