# Lesson 112 --- SQL Aliases

> **Part 06 --- Structured Query Language (SQL)**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What SQL aliases are
-   Why aliases are important
-   Column aliases
-   Table aliases
-   Aliases with expressions
-   Aliases with aggregate functions
-   Aliases in joins
-   Best practices
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Imagine calling someone by their full name every time.

``` text
Chaitrali Patil

instead of

Chaitrali
```

A shorter name is easier.

SQL aliases do the same for columns and tables.

------------------------------------------------------------------------

# 2. What is an Alias?

An **alias** is a temporary name assigned to a column or table during
query execution.

Aliases exist **only for the result of the query**.

``` text
Original Name
      │
   Alias
      │
Displayed Result
```

------------------------------------------------------------------------

# 3. Why Do We Need Aliases?

Aliases improve:

-   Readability
-   Simplicity
-   Report formatting
-   Complex joins

------------------------------------------------------------------------

# 4. Column Alias

Basic syntax:

``` sql
SELECT Salary AS MonthlySalary
FROM Employee;
```

Result:

``` text
MonthlySalary
-------------
65000
```

The actual column name remains `Salary`.

------------------------------------------------------------------------

# 5. Alias Without AS

`AS` is optional in most DBMSs.

``` sql
SELECT Salary MonthlySalary
FROM Employee;
```

Using `AS` is generally clearer.

------------------------------------------------------------------------

# 6. Aliases with Expressions

``` sql
SELECT Name,
       Salary * 12 AS AnnualSalary
FROM Employee;
```

Output:

``` text
Name     AnnualSalary
---------------------
Riya     780000
```

------------------------------------------------------------------------

# 7. Aliases with Aggregate Functions

``` sql
SELECT Department,
       AVG(Salary) AS AverageSalary
FROM Employee
GROUP BY Department;
```

Instead of:

``` text
AVG(Salary)
```

the heading becomes:

``` text
AverageSalary
```

------------------------------------------------------------------------

# 8. Table Aliases

Useful for long table names.

``` sql
SELECT S.Name,
       S.Age
FROM Student AS S;
```

Here:

``` text
Student

↓

S
```

------------------------------------------------------------------------

# 9. Aliases in Joins

``` sql
SELECT S.Name,
       D.DepartmentName
FROM Student AS S
JOIN Department AS D
ON S.DepartmentID = D.DepartmentID;
```

ASCII view:

``` text
Student (S)
      │
 JOIN
      │
Department (D)
```

Without aliases, long queries become harder to read.

------------------------------------------------------------------------

# 10. Real-World Example

``` sql
SELECT ProductName AS Product,
       Price AS SellingPrice
FROM Product;
```

Displayed report:

``` text
Product      SellingPrice
--------------------------
Laptop       65000
Mouse        1200
```

------------------------------------------------------------------------

# 11. Best Practices

-   Use meaningful aliases.
-   Prefer `AS` for readability.
-   Keep table aliases short.
-   Be consistent across queries.
-   Avoid confusing abbreviations.

------------------------------------------------------------------------

# 12. Common Mistakes

❌ Using spaces without quotes where required.

❌ Giving unrelated alias names.

❌ Forgetting aliases in complex joins.

❌ Assuming aliases permanently rename columns.

------------------------------------------------------------------------

# 13. Interview Questions

### Beginner

1.  What is an alias?
2.  Why use aliases?
3.  Is `AS` mandatory?

### Intermediate

1.  Column alias vs table alias?
2.  Why are aliases useful in joins?

### Advanced

1.  Can aliases be used with aggregate functions?
2.  Why can't a column alias usually be referenced in the `WHERE`
    clause?

------------------------------------------------------------------------

# 14. Practice Problems

1.  Rename `Salary` as `MonthlySalary`.
2.  Rename `AVG(Salary)` as `AverageSalary`.
3.  Use aliases in a join.
4.  Create aliases for calculated columns.
5.  Rewrite a long query using table aliases.

------------------------------------------------------------------------

# Revision Notes

``` text
Aliases
│
├── Column Alias
├── Table Alias
├── Expressions
└── Aggregates
```

## Memory Trick

``` text
ALIAS

=

Alternative

Label

Improves

SQL
```

## Key Points

-   Aliases are temporary names.
-   They improve readability.
-   `AS` is optional in many DBMSs.
-   Table aliases simplify joins.
-   Aliases do not modify database objects.

------------------------------------------------------------------------

# Final Takeaway

SQL aliases make queries easier to read and reports easier to understand
without changing the underlying database structure. They become
especially valuable in joins, calculations, and aggregated results where
long names quickly make queries difficult to follow. Clear aliases help
both the database professional writing the query today and the one
trying to understand it months later.
