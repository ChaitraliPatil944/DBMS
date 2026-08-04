# Lesson 093 --- SQL Operators

> **Part 06 --- Structured Query Language (SQL)**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What SQL operators are
-   Why operators are important
-   Arithmetic operators
-   Comparison operators
-   Logical operators
-   Special operators
-   Operator precedence
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. What are SQL Operators?

SQL operators are symbols or keywords used to perform calculations,
compare values, and filter records.

``` text
Data
 │
Operators
 │
Meaningful Results
```

------------------------------------------------------------------------

# 2. Why Do We Need Operators?

Imagine a table with 1 million employees.

Without operators:

``` text
Return all employees
```

With operators:

``` text
Return employees whose salary > 50000
```

Operators help retrieve only the required data.

------------------------------------------------------------------------

# 3. Categories of SQL Operators

``` text
SQL Operators
│
├── Arithmetic
├── Comparison
├── Logical
└── Special
```

------------------------------------------------------------------------

# 4. Arithmetic Operators

  Operator   Meaning          Example
  ---------- ---------------- -------------------
  \+         Addition         Salary + Bonus
  \-         Subtraction      Marks - 5
  \*         Multiplication   Price \* Quantity
  /          Division         Total / Students
  \%         Modulus          Age % 2

Example:

``` sql
SELECT Salary + Bonus AS TotalIncome
FROM Employee;
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
WHERE Salary >= 50000;
```

------------------------------------------------------------------------

# 6. Logical Operators

## AND

Both conditions must be true.

``` sql
SELECT *
FROM Student
WHERE Age > 18
AND City = 'Pune';
```

## OR

At least one condition must be true.

``` sql
WHERE City='Pune'
OR City='Mumbai';
```

## NOT

Reverses a condition.

``` sql
WHERE NOT City='Delhi';
```

------------------------------------------------------------------------

# 7. Special Operators

## IN

``` sql
WHERE Department IN
('IT','CSE','ECE');
```

------------------------------------------------------------------------

## BETWEEN

``` sql
WHERE Salary BETWEEN 30000 AND 60000;
```

------------------------------------------------------------------------

## LIKE

``` sql
WHERE Name LIKE 'A%';
```

Common wildcards:

``` text
% → Any number of characters
_ → Exactly one character
```

------------------------------------------------------------------------

## IS NULL

``` sql
WHERE Email IS NULL;
```

------------------------------------------------------------------------

## EXISTS

Checks whether a subquery returns rows.

``` sql
WHERE EXISTS (...);
```

------------------------------------------------------------------------

## ANY

True if the condition matches any value returned by a subquery.

------------------------------------------------------------------------

## ALL

True only if the condition matches all returned values.

------------------------------------------------------------------------

# 8. Operator Precedence

Default order:

``` text
()

↓

Arithmetic

↓

Comparison

↓

NOT

↓

AND

↓

OR
```

Use parentheses to avoid ambiguity.

Example:

``` sql
WHERE (City='Pune' OR City='Mumbai')
AND Age > 18;
```

------------------------------------------------------------------------

# 9. Real-World Example

``` sql
SELECT Name, Salary
FROM Employee
WHERE Salary > 50000
AND Department='IT';
```

Flow:

``` text
Employee Table
      │
Salary > 50000
      │
Department = IT
      │
Matching Employees
```

------------------------------------------------------------------------

# 10. Common Mistakes

❌ Using `=` instead of `LIKE`.

❌ Comparing NULL using `=`.

Wrong:

``` sql
WHERE Email = NULL;
```

Correct:

``` sql
WHERE Email IS NULL;
```

❌ Forgetting parentheses in complex conditions.

------------------------------------------------------------------------

# 11. Interview Questions

### Beginner

1.  What are SQL operators?
2.  Name the operator categories.
3.  Difference between `=` and `LIKE`?

### Intermediate

1.  Explain `IN` and `BETWEEN`.
2.  AND vs OR?
3.  Why use `IS NULL`?

### Advanced

1.  Explain operator precedence.
2.  ANY vs ALL?
3.  EXISTS vs IN?

------------------------------------------------------------------------

# 12. Practice Problems

1.  Retrieve employees with Salary \> 40000.
2.  Find students from Pune or Mumbai.
3.  Display products priced between 100 and 500.
4.  Find names beginning with 'S'.
5.  Retrieve rows where Email is NULL.

------------------------------------------------------------------------

# Revision Notes

``` text
Arithmetic
│
+ - * / %

Comparison
│
= <> > < >= <=

Logical
│
AND OR NOT

Special
│
IN
BETWEEN
LIKE
IS NULL
EXISTS
ANY
ALL
```

## Memory Trick

``` text
A C L S

Arithmetic
Comparison
Logical
Special
```

## Key Points

-   Operators help filter and manipulate data.
-   Comparison operators evaluate conditions.
-   Logical operators combine conditions.
-   Special operators simplify common queries.
-   Parentheses improve readability and correctness.

------------------------------------------------------------------------

# Final Takeaway

SQL operators are the decision-making tools of a query. They determine
which rows are selected, how values are compared, and how conditions are
combined. Mastering operators is essential before moving to clauses like
`WHERE`, `GROUP BY`, and `HAVING`, because almost every useful SQL query
depends on them.
