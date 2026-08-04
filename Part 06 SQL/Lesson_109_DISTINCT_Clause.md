# Lesson 109 --- DISTINCT Clause

> **Part 06 --- Structured Query Language (SQL)**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What the `DISTINCT` clause is
-   Why duplicate values occur
-   Basic syntax
-   DISTINCT on one column
-   DISTINCT on multiple columns
-   How DISTINCT works internally
-   DISTINCT vs GROUP BY
-   Best practices
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Imagine a college database.

Many students belong to the same department.

``` text
Alice   CSE
Bob     CSE
Riya    IT
Aman    IT
Sara    CSE
```

If you want **all departments**, you don't want:

``` text
CSE
CSE
IT
IT
CSE
```

You want:

``` text
CSE
IT
```

This is exactly what `DISTINCT` does.

------------------------------------------------------------------------

# 2. What is DISTINCT?

`DISTINCT` removes duplicate values from the result set.

``` text
Table
 │
SELECT DISTINCT
 │
Unique Values
```

It does **not** modify the table. It only affects the query output.

------------------------------------------------------------------------

# 3. Why Do We Need DISTINCT?

Without `DISTINCT`:

``` sql
SELECT Department
FROM Student;
```

Output:

``` text
CSE
CSE
IT
IT
CSE
```

With `DISTINCT`:

``` sql
SELECT DISTINCT Department
FROM Student;
```

Output:

``` text
CSE
IT
```

------------------------------------------------------------------------

# 4. Basic Syntax

``` sql
SELECT DISTINCT column_name
FROM table_name;
```

------------------------------------------------------------------------

# 5. DISTINCT on a Single Column

``` sql
SELECT DISTINCT City
FROM Customer;
```

Returns every city only once.

------------------------------------------------------------------------

# 6. DISTINCT on Multiple Columns

``` sql
SELECT DISTINCT Department,
                City
FROM Employee;
```

Here SQL returns unique **combinations** of Department and City.

Example:

``` text
Department   City
-------------------
IT           Pune
IT           Mumbai
HR           Pune
```

Even if individual values repeat, each combination is unique.

------------------------------------------------------------------------

# 7. How DISTINCT Works Internally

``` text
Read Rows
    │
Compare Values
    │
Remove Duplicates
    │
Return Unique Rows
```

The DBMS typically sorts or hashes data internally to identify
duplicates.

------------------------------------------------------------------------

# 8. DISTINCT vs GROUP BY

  DISTINCT                 GROUP BY
  ------------------------ ----------------------------
  Removes duplicate rows   Groups rows
  No aggregates required   Often used with aggregates
  Simpler                  More powerful

Example:

``` sql
SELECT DISTINCT Department
FROM Employee;
```

vs

``` sql
SELECT Department
FROM Employee
GROUP BY Department;
```

Both may produce the same departments, but `GROUP BY` is designed for
aggregation.

------------------------------------------------------------------------

# 9. Real-World Example

An online store wants to display available product categories.

``` sql
SELECT DISTINCT Category
FROM Product;
```

Instead of showing thousands of repeated categories, only unique
category names are displayed.

------------------------------------------------------------------------

# 10. Best Practices

-   Use `DISTINCT` only when duplicates are unnecessary.
-   Avoid using it to hide poor database design.
-   Index frequently queried columns for better performance.
-   Retrieve only required columns.

------------------------------------------------------------------------

# 11. Common Mistakes

❌ Assuming DISTINCT changes stored data.

It only changes the query result.

❌ Using DISTINCT with unnecessary columns.

``` sql
SELECT DISTINCT *
FROM Employee;
```

If every row is already unique, DISTINCT provides no benefit.

❌ Confusing DISTINCT with GROUP BY.

------------------------------------------------------------------------

# 12. Interview Questions

### Beginner

1.  What is DISTINCT?
2.  Why is DISTINCT used?
3.  Does DISTINCT modify the table?

### Intermediate

1.  DISTINCT vs GROUP BY?
2.  Can DISTINCT work on multiple columns?

### Advanced

1.  How does DISTINCT work internally?
2.  Why can DISTINCT affect query performance?

------------------------------------------------------------------------

# 13. Practice Problems

1.  Display unique departments.
2.  Display unique cities.
3.  Display unique Department-City combinations.
4.  Compare DISTINCT and GROUP BY.
5.  Explain when DISTINCT should not be used.

------------------------------------------------------------------------

# Revision Notes

``` text
SELECT DISTINCT
        │
 Remove Duplicate Values
        │
 Return Unique Rows
```

## Memory Trick

``` text
DISTINCT

=

Display

Individual

Values

Only

Once
```

## Key Points

-   `DISTINCT` removes duplicate results.
-   It affects only the query output.
-   It works on one or multiple columns.
-   Multiple columns produce unique combinations.
-   Use `GROUP BY` when aggregation is required.

------------------------------------------------------------------------

# Final Takeaway

The `DISTINCT` clause is a simple but powerful tool for eliminating
duplicate results from SQL queries. It helps present clean, meaningful
information without changing the underlying data. Use it thoughtfully,
because while it improves readability, it also requires extra work from
the database to identify duplicate rows. Like many SQL features, it's
most effective when solving an actual problem rather than being added
automatically.
