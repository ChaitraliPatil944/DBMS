# Lesson 110 --- ORDER BY Clause

> **Part 06 --- Structured Query Language (SQL)**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What the `ORDER BY` clause is
-   Why sorting is important
-   Basic syntax
-   Ascending and descending sorting
-   Sorting by multiple columns
-   Sorting numbers, text, and dates
-   Internal execution
-   Best practices
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Imagine an online shopping website.

Would you like products displayed in a random order?

Probably not.

Most users prefer:

-   Lowest price first
-   Highest rating first
-   Newest products first

SQL performs this sorting using the **ORDER BY** clause.

------------------------------------------------------------------------

# 2. What is ORDER BY?

`ORDER BY` sorts the result set returned by a query.

``` text
Rows
 │
ORDER BY
 │
Sorted Rows
```

It does **not** change the order of data stored in the table.

------------------------------------------------------------------------

# 3. Why Do We Need ORDER BY?

Without sorting:

``` text
45000
22000
70000
15000
```

With sorting:

``` text
15000
22000
45000
70000
```

Sorted data is easier to understand and analyze.

------------------------------------------------------------------------

# 4. Basic Syntax

``` sql
SELECT column_list
FROM table_name
ORDER BY column_name;
```

Example:

``` sql
SELECT Name, Salary
FROM Employee
ORDER BY Salary;
```

------------------------------------------------------------------------

# 5. Ascending Order (ASC)

Ascending order is the default.

``` sql
SELECT *
FROM Employee
ORDER BY Salary ASC;
```

Result:

``` text
25000
40000
55000
80000
```

------------------------------------------------------------------------

# 6. Descending Order (DESC)

``` sql
SELECT *
FROM Employee
ORDER BY Salary DESC;
```

Result:

``` text
80000
55000
40000
25000
```

------------------------------------------------------------------------

# 7. Sorting by Multiple Columns

If two employees have the same department, sort them by salary.

``` sql
SELECT Name,
       Department,
       Salary
FROM Employee
ORDER BY Department ASC,
         Salary DESC;
```

Sorting order:

``` text
Department
     │
Salary
```

------------------------------------------------------------------------

# 8. Sorting Different Data Types

### Numbers

``` sql
ORDER BY Price;
```

### Text

``` sql
ORDER BY Name;
```

Alphabetical order:

``` text
A
B
C
...
Z
```

### Dates

``` sql
ORDER BY OrderDate DESC;
```

Newest records appear first.

------------------------------------------------------------------------

# 9. Internal Working

``` text
Read Rows
    │
Apply WHERE (if present)
    │
Retrieve Result
    │
Sort Rows
    │
Display Output
```

Sorting is performed after filtering and selection.

------------------------------------------------------------------------

# 10. Real-World Example

Display the five highest-paid employees.

``` sql
SELECT Name, Salary
FROM Employee
ORDER BY Salary DESC
LIMIT 5;
```

------------------------------------------------------------------------

# 11. Best Practices

-   Sort only when necessary.
-   Use indexes on frequently sorted columns.
-   Combine `ORDER BY` with `LIMIT` for top-N queries.
-   Sort using meaningful columns.

------------------------------------------------------------------------

# 12. Common Mistakes

❌ Assuming SQL always returns rows in insertion order.

❌ Forgetting `DESC` when highest values are required.

❌ Sorting unnecessary columns.

------------------------------------------------------------------------

# 13. Interview Questions

### Beginner

1.  What is the ORDER BY clause?
2.  What is the default sorting order?
3.  Difference between ASC and DESC?

### Intermediate

1.  Can ORDER BY sort multiple columns?
2.  Can ORDER BY sort text and dates?

### Advanced

1.  How does ORDER BY affect performance?
2.  Why are indexes useful for sorting?

------------------------------------------------------------------------

# 14. Practice Problems

1.  Display employees sorted by salary.
2.  Display students alphabetically.
3.  Show newest orders first.
4.  Sort products by category and then price.
5.  Display the top 10 highest-scoring students.

------------------------------------------------------------------------

# Revision Notes

``` text
ORDER BY
    │
 ASC (Default)
 DESC
    │
 Sorted Results
```

## Memory Trick

``` text
ORDER BY

=

Organize

Data

Efficiently

Results
```

## Key Points

-   `ORDER BY` sorts query results.
-   `ASC` is the default order.
-   `DESC` sorts from highest to lowest.
-   Multiple columns can be used for sorting.
-   Sorting affects only the result set, not stored data.

------------------------------------------------------------------------

# Final Takeaway

The `ORDER BY` clause makes query results easier to read by arranging
them in a meaningful sequence. Whether you're listing the highest-paid
employees, the latest orders, or customers alphabetically, sorting is an
essential part of presenting data. Databases are excellent at storing
information efficiently, but humans generally prefer information that
arrives in some recognizable order rather than what appears to be
organized by cosmic coincidence.
