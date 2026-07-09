# Lesson 108 --- WHERE Clause

> **Part 06 --- Structured Query Language (SQL)**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What the `WHERE` clause is
-   Why filtering is important
-   Basic `WHERE` syntax
-   Comparison operators
-   Logical operators
-   Filtering numbers, text, and dates
-   Performance tips
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Imagine a school with **10,000 students**.

You don't want every student.

You only want:

-   Students in Computer Science
-   Students older than 18
-   Students from Pune

Instead of reading every record, you **filter** the data.

That is the job of the **WHERE** clause.

------------------------------------------------------------------------

# 2. What is WHERE?

The `WHERE` clause filters rows based on a condition.

``` text
Table
 │
WHERE Condition
 │
Matching Rows
```

Only rows satisfying the condition are returned.

------------------------------------------------------------------------

# 3. Why Do We Need WHERE?

Without `WHERE`:

``` sql
SELECT *
FROM Student;
```

Every record is returned.

With `WHERE`:

``` sql
SELECT *
FROM Student
WHERE City = 'Pune';
```

Only students from Pune are returned.

------------------------------------------------------------------------

# 4. Basic Syntax

``` sql
SELECT column_list
FROM table_name
WHERE condition;
```

------------------------------------------------------------------------

# 5. Comparison Operators

  Operator     Meaning
  ------------ -----------------------
  =            Equal
  \<\> or !=   Not Equal
  \>           Greater Than
  \<           Less Than
  \>=          Greater Than or Equal
  \<=          Less Than or Equal

Example:

``` sql
SELECT *
FROM Employee
WHERE Salary > 50000;
```

------------------------------------------------------------------------

# 6. Filtering Numeric Values

``` sql
SELECT *
FROM Product
WHERE Price >= 1000;
```

------------------------------------------------------------------------

# 7. Filtering Text Values

``` sql
SELECT *
FROM Student
WHERE City = 'Mumbai';
```

String values are enclosed in quotes.

------------------------------------------------------------------------

# 8. Filtering Date Values

``` sql
SELECT *
FROM Orders
WHERE OrderDate > '2026-01-01';
```

------------------------------------------------------------------------

# 9. Logical Operators

## AND

Both conditions must be true.

``` sql
SELECT *
FROM Employee
WHERE Department='IT'
AND Salary > 60000;
```

------------------------------------------------------------------------

## OR

Either condition may be true.

``` sql
SELECT *
FROM Student
WHERE City='Pune'
OR City='Mumbai';
```

------------------------------------------------------------------------

## NOT

Reverses a condition.

``` sql
SELECT *
FROM Product
WHERE NOT Price < 500;
```

------------------------------------------------------------------------

# 10. Internal Working

``` text
Read Table
    │
Apply WHERE
    │
Discard Non-Matching Rows
    │
Return Matching Rows
```

------------------------------------------------------------------------

# 11. Real-World Example

Display active customers from Delhi.

``` sql
SELECT Name, Email
FROM Customer
WHERE City='Delhi'
AND Status='Active';
```

------------------------------------------------------------------------

# 12. Performance Tips

-   Filter as early as possible.
-   Index frequently filtered columns.
-   Avoid unnecessary conditions.
-   Retrieve only required columns.

------------------------------------------------------------------------

# 13. Common Mistakes

❌ Missing quotes around text.

``` sql
WHERE City = Pune
```

✔ Correct

``` sql
WHERE City = 'Pune'
```

------------------------------------------------------------------------

❌ Using `=` with NULL.

Wrong:

``` sql
WHERE Email = NULL;
```

Correct:

``` sql
WHERE Email IS NULL;
```

------------------------------------------------------------------------

❌ Forgetting operator precedence.

``` sql
WHERE City='Pune'
OR City='Mumbai'
AND Age>18;
```

Prefer:

``` sql
WHERE (City='Pune' OR City='Mumbai')
AND Age>18;
```

------------------------------------------------------------------------

# 14. Interview Questions

### Beginner

1.  What is the WHERE clause?
2.  Why is WHERE used?
3.  Can WHERE be used without SELECT?

### Intermediate

1.  Explain AND, OR, and NOT.
2.  Why are quotes needed for text values?
3.  Why can't `=` be used with NULL?

### Advanced

1.  How does WHERE improve performance?
2.  Explain predicate filtering.
3.  How do indexes help WHERE queries?

------------------------------------------------------------------------

# 15. Practice Problems

1.  Display students older than 20.
2.  Show employees from the IT department.
3.  Display products costing less than 500.
4.  Retrieve orders placed after January 1, 2026.
5.  Find active customers from Pune.

------------------------------------------------------------------------

# Revision Notes

``` text
SELECT
   │
FROM
   │
WHERE
   │
Matching Rows
```

## Memory Trick

``` text
WHERE

=

Which

Rows

Exactly
```

## Key Points

-   `WHERE` filters rows.
-   It works before the result is returned.
-   Supports comparison and logical operators.
-   Proper filtering improves performance.
-   Parentheses improve readability in complex conditions.

------------------------------------------------------------------------

# Final Takeaway

The `WHERE` clause transforms a simple `SELECT` statement into a precise
question. Instead of retrieving every record, it allows you to request
only the information that matches your conditions. Efficient filtering
is one of the foundations of SQL because the fastest data to process is
often the data you never retrieve in the first place.
