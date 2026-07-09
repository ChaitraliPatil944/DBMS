# Lesson 113 --- GROUP BY Clause

> **Part 06 --- Structured Query Language (SQL)**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What the `GROUP BY` clause is
-   Why grouping is important
-   Basic syntax
-   Aggregate functions with `GROUP BY`
-   Grouping by one and multiple columns
-   Internal execution flow
-   `GROUP BY` vs `DISTINCT`
-   Best practices
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Imagine a company with thousands of employees.

Instead of viewing every employee individually, the manager wants
answers like:

-   How many employees are in each department?
-   What is the average salary of each department?
-   Which city has the highest number of employees?

These questions require **grouping**.

That is the purpose of `GROUP BY`.

------------------------------------------------------------------------

# 2. What is GROUP BY?

`GROUP BY` groups rows that have the same value in one or more columns.

After grouping, aggregate functions are applied to each group.

``` text
Employee Table
      │
 GROUP BY Department
      │
IT      HR      Sales
│       │         │
AVG     AVG      AVG
COUNT   COUNT    COUNT
```

------------------------------------------------------------------------

# 3. Why Do We Need GROUP BY?

Without grouping:

``` text
IT
IT
HR
IT
Sales
HR
```

With grouping:

``` text
IT      → 3 Employees

HR      → 2 Employees

Sales   → 1 Employee
```

------------------------------------------------------------------------

# 4. Basic Syntax

``` sql
SELECT column_name,
       aggregate_function(column_name)
FROM table_name
GROUP BY column_name;
```

Example:

``` sql
SELECT Department,
       COUNT(*) AS TotalEmployees
FROM Employee
GROUP BY Department;
```

------------------------------------------------------------------------

# 5. Aggregate Functions

Common aggregate functions:

  Function   Purpose
  ---------- ---------------------
  COUNT()    Counts rows
  SUM()      Adds values
  AVG()      Calculates average
  MAX()      Finds highest value
  MIN()      Finds lowest value

Example:

``` sql
SELECT Department,
       AVG(Salary) AS AverageSalary
FROM Employee
GROUP BY Department;
```

------------------------------------------------------------------------

# 6. Grouping by Multiple Columns

``` sql
SELECT Department,
       City,
       COUNT(*) AS Employees
FROM Employee
GROUP BY Department,
         City;
```

Groups are created using the combination of both columns.

``` text
Department
      │
City
      │
COUNT
```

------------------------------------------------------------------------

# 7. Internal Working

``` text
Read Table
    │
Apply WHERE
    │
Create Groups
    │
Calculate Aggregates
    │
Return Results
```

------------------------------------------------------------------------

# 8. GROUP BY vs DISTINCT

  GROUP BY               DISTINCT
  ---------------------- ------------------------
  Creates groups         Removes duplicates
  Used with aggregates   Usually no aggregates
  Summarizes data        Displays unique values

Example:

``` sql
SELECT DISTINCT Department
FROM Employee;
```

Returns unique departments.

``` sql
SELECT Department,
COUNT(*)
FROM Employee
GROUP BY Department;
```

Returns department-wise employee count.

------------------------------------------------------------------------

# 9. Real-World Example

Display the number of orders placed by each customer.

``` sql
SELECT CustomerID,
       COUNT(*) AS TotalOrders
FROM Orders
GROUP BY CustomerID;
```

Output:

``` text
CustomerID   TotalOrders
------------------------
101          8
102          3
103          15
```

------------------------------------------------------------------------

# 10. Best Practices

-   Group only necessary columns.
-   Use meaningful aliases for aggregate values.
-   Filter rows with `WHERE` before grouping.
-   Filter groups with `HAVING` after grouping.
-   Index grouping columns for large datasets.

------------------------------------------------------------------------

# 11. Common Mistakes

❌ Selecting non-grouped columns.

``` sql
SELECT Name,
Department
FROM Employee
GROUP BY Department;
```

This is invalid in standard SQL because `Name` is neither grouped nor
aggregated.

❌ Confusing `GROUP BY` with `DISTINCT`.

❌ Using `WHERE` with aggregate functions instead of `HAVING`.

------------------------------------------------------------------------

# 12. Interview Questions

### Beginner

1.  What is the purpose of `GROUP BY`?
2.  Which functions are commonly used with `GROUP BY`?
3.  Can `GROUP BY` group multiple columns?

### Intermediate

1.  `GROUP BY` vs `DISTINCT`?
2.  Why can't non-grouped columns usually appear in the SELECT list?

### Advanced

1.  Explain the internal execution of `GROUP BY`.
2.  Why is `HAVING` used after `GROUP BY`?

------------------------------------------------------------------------

# 13. Practice Problems

1.  Count employees in each department.
2.  Find the average salary by department.
3.  Find the highest salary in each city.
4.  Count orders by customer.
5.  Group employees by department and city.

------------------------------------------------------------------------

# Revision Notes

``` text
Read Rows
    │
WHERE
    │
GROUP BY
    │
Aggregate Functions
    │
Results
```

## Memory Trick

``` text
GROUP BY

=

Gather

Related

Objects

Using

Properties
```

## Key Points

-   `GROUP BY` creates groups of similar rows.
-   Aggregate functions operate on each group.
-   Multiple grouping columns are allowed.
-   `WHERE` filters rows before grouping.
-   `HAVING` filters groups after grouping.

------------------------------------------------------------------------

# Final Takeaway

The `GROUP BY` clause transforms detailed records into meaningful
summaries. It is the foundation of reporting, dashboards, analytics, and
business intelligence because it allows SQL to answer questions about
groups instead of individual rows. Whenever someone asks for totals,
averages, counts, or summaries by category, `GROUP BY` is almost always
part of the solution.
