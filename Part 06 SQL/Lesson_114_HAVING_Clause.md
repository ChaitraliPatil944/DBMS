# Lesson 114 --- HAVING Clause

> **Part 06 --- Structured Query Language (SQL)**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What the `HAVING` clause is
-   Why `HAVING` is needed
-   Basic syntax
-   `WHERE` vs `HAVING`
-   Using aggregate functions
-   `GROUP BY` with `HAVING`
-   Internal execution order
-   Best practices
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Imagine a company wants to know:

-   Departments with more than **20 employees**
-   Cities where the **average salary exceeds ₹50,000**

These questions cannot be answered by filtering individual rows.

They require filtering **groups**.

That is the purpose of the **HAVING** clause.

------------------------------------------------------------------------

# 2. What is HAVING?

`HAVING` filters **groups** created by the `GROUP BY` clause.

``` text
Rows
 │
GROUP BY
 │
Groups
 │
HAVING
 │
Qualified Groups
```

Unlike `WHERE`, it works **after grouping**.

------------------------------------------------------------------------

# 3. Why Do We Need HAVING?

Suppose we have:

``` text
Department
IT
IT
IT
HR
HR
Sales
```

We first group the rows.

``` text
IT → 3

HR → 2

Sales → 1
```

Then we filter:

``` sql
HAVING COUNT(*) > 2
```

Result:

``` text
IT
```

------------------------------------------------------------------------

# 4. Basic Syntax

``` sql
SELECT column_name,
       aggregate_function(column_name)
FROM table_name
GROUP BY column_name
HAVING aggregate_function(column_name) condition;
```

------------------------------------------------------------------------

# 5. Using HAVING

Example:

``` sql
SELECT Department,
       COUNT(*) AS TotalEmployees
FROM Employee
GROUP BY Department
HAVING COUNT(*) > 5;
```

Only departments having more than five employees are returned.

------------------------------------------------------------------------

# 6. HAVING with Different Aggregate Functions

Average salary:

``` sql
SELECT Department,
       AVG(Salary) AS AvgSalary
FROM Employee
GROUP BY Department
HAVING AVG(Salary) > 60000;
```

Highest salary:

``` sql
SELECT Department,
       MAX(Salary)
FROM Employee
GROUP BY Department
HAVING MAX(Salary) > 100000;
```

------------------------------------------------------------------------

# 7. WHERE vs HAVING

  -----------------------------------------------------------------------
  WHERE                             HAVING
  --------------------------------- -------------------------------------
  Filters rows                      Filters groups

  Executes before grouping          Executes after grouping

  Cannot normally use aggregate     Designed for aggregate functions
  functions                         
  -----------------------------------------------------------------------

Example:

``` sql
SELECT Department,
       COUNT(*)
FROM Employee
WHERE Salary > 30000
GROUP BY Department
HAVING COUNT(*) > 5;
```

Explanation:

``` text
WHERE
 │
Removes employees earning ≤ 30000

↓

GROUP BY

↓

HAVING
 │
Keeps only departments with more than 5 employees
```

------------------------------------------------------------------------

# 8. Internal Execution Order

``` text
FROM
 │
WHERE
 │
GROUP BY
 │
HAVING
 │
SELECT
 │
ORDER BY
 │
LIMIT
```

This order explains why `HAVING` can use aggregates while `WHERE`
generally cannot.

------------------------------------------------------------------------

# 9. Real-World Example

Find customers who placed more than 10 orders.

``` sql
SELECT CustomerID,
       COUNT(*) AS TotalOrders
FROM Orders
GROUP BY CustomerID
HAVING COUNT(*) > 10;
```

------------------------------------------------------------------------

# 10. Best Practices

-   Use `WHERE` to reduce rows before grouping.
-   Use `HAVING` only for filtering groups.
-   Use meaningful aliases for aggregate columns.
-   Avoid unnecessary grouping.

------------------------------------------------------------------------

# 11. Common Mistakes

❌ Using aggregate functions in `WHERE`.

Wrong:

``` sql
WHERE COUNT(*) > 5
```

Correct:

``` sql
HAVING COUNT(*) > 5
```

------------------------------------------------------------------------

❌ Using `HAVING` when `WHERE` is sufficient.

Filtering before grouping is usually more efficient.

------------------------------------------------------------------------

# 12. Interview Questions

### Beginner

1.  What is the HAVING clause?
2.  Why is HAVING used?
3.  HAVING vs WHERE?

### Intermediate

1.  Can HAVING be used without GROUP BY?
2.  Which aggregate functions work with HAVING?

### Advanced

1.  Explain SQL execution order involving HAVING.
2.  Why is WHERE usually faster than HAVING?

------------------------------------------------------------------------

# 13. Practice Problems

1.  Display departments with more than 10 employees.
2.  Find cities where the average salary exceeds ₹75,000.
3.  Find customers with more than five orders.
4.  Compare WHERE and HAVING with examples.
5.  Rewrite a HAVING query using WHERE wherever possible.

------------------------------------------------------------------------

# Revision Notes

``` text
WHERE
 │
Filter Rows
 │
GROUP BY
 │
Create Groups
 │
HAVING
 │
Filter Groups
```

## Memory Trick

``` text
HAVING

=

Has

Aggregates

Viewing

Individual

Groups
```

## Key Points

-   `HAVING` filters grouped data.
-   It is evaluated after `GROUP BY`.
-   Aggregate functions are commonly used in `HAVING`.
-   `WHERE` filters rows before grouping.
-   Use `WHERE` whenever row-level filtering is sufficient.

------------------------------------------------------------------------

# Final Takeaway

The `HAVING` clause completes SQL's grouping workflow by allowing you to
filter summarized results rather than individual records. Whenever you
need to ask questions like "Which departments have more than 20
employees?" or "Which products generated more than ₹1,00,000 in sales?",
`HAVING` is the correct tool. Understanding the distinction between
`WHERE` and `HAVING` is one of the clearest signs that you've moved
beyond basic SQL into writing analytical queries.
