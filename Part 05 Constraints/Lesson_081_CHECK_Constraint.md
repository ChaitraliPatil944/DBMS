# Lesson 081 --- CHECK Constraint

> **Part 05 --- Constraints**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What the CHECK constraint is
-   Why CHECK constraints are needed
-   Column-level vs Table-level CHECK
-   SQL implementation
-   Range and list validation
-   CHECK vs NOT NULL vs DEFAULT
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Suppose a database stores:

``` text
Age = -25
Marks = 145
Salary = -10000
```

These values are valid data types, but they are invalid business values.

A **CHECK** constraint prevents such data from being stored.

------------------------------------------------------------------------

# 2. What is the CHECK Constraint?

A **CHECK** constraint ensures that a value satisfies a specified
condition before it is stored.

``` text
Input Value
     │
CHECK Condition
     │
Valid? → Store
Invalid? → Reject
```

------------------------------------------------------------------------

# 3. Why Do We Need CHECK?

Without CHECK:

-   Impossible values can be stored.
-   Business rules are ignored.
-   Reports become inaccurate.

With CHECK:

-   Only meaningful values are accepted.
-   Validation happens inside the DBMS.
-   Data quality improves.

------------------------------------------------------------------------

# 4. Child-Friendly Analogy

Imagine a ride in an amusement park.

Rule:

``` text
Height ≥ 120 cm
```

A child who is 110 cm is not allowed.

The ride operator is acting like a CHECK constraint.

------------------------------------------------------------------------

# 5. Column-Level CHECK

Applies to a single column.

``` sql
CREATE TABLE Student(
    StudentID INT PRIMARY KEY,
    Age INT CHECK (Age BETWEEN 16 AND 60)
);
```

Only ages from 16 to 60 are accepted.

------------------------------------------------------------------------

# 6. Table-Level CHECK

Applies to multiple columns together.

``` sql
CREATE TABLE Employee(
    Salary DECIMAL(10,2),
    Bonus DECIMAL(10,2),
    CHECK (Bonus <= Salary)
);
```

The rule compares two columns.

------------------------------------------------------------------------

# 7. Range Validation

``` sql
CHECK (Marks BETWEEN 0 AND 100)
```

Valid:

``` text
0
55
100
```

Invalid:

``` text
-5
120
```

------------------------------------------------------------------------

# 8. List Validation

``` sql
CHECK (Department IN
('CSE','IT','ECE','AIML'))
```

Only listed values are allowed.

------------------------------------------------------------------------

# 9. CHECK vs NOT NULL vs DEFAULT

  -----------------------------------------------------------------------
  CHECK                   NOT NULL                DEFAULT
  ----------------------- ----------------------- -----------------------
  Validates values        Requires a value        Supplies a value if
                                                  omitted

  Uses conditions         Rejects NULL            Uses predefined value

  Enforces business rules Enforces mandatory      Improves convenience
                          fields                  
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# 10. SQL Examples

## Salary

``` sql
Salary DECIMAL(10,2)
CHECK (Salary >= 0)
```

## Age

``` sql
Age INT
CHECK (Age >= 18)
```

## Status

``` sql
Status VARCHAR(20)
CHECK (Status IN
('Pending','Approved','Rejected'))
```

------------------------------------------------------------------------

# 11. Real-World Examples

### Banking

``` text
Balance >= 0
```

### Hospital

``` text
Age > 0
```

### University

``` text
Semester BETWEEN 1 AND 8
```

### E-commerce

``` text
Quantity > 0
```

------------------------------------------------------------------------

# 12. Advantages

-   Enforces business rules
-   Prevents invalid values
-   Improves data quality
-   Reduces application-side validation
-   Keeps data consistent

------------------------------------------------------------------------

# 13. Common Mistakes

❌ Confusing CHECK with data types.

❌ Using CHECK when a FOREIGN KEY is required.

❌ Forgetting that CHECK conditions should reflect business rules.

------------------------------------------------------------------------

# 14. Interview Questions

### Beginner

1.  What is a CHECK constraint?
2.  Why is it used?
3.  Give one example.

### Intermediate

1.  Column-level vs Table-level CHECK?
2.  CHECK vs NOT NULL?

### Advanced

1.  Can CHECK compare multiple columns?
2.  Why is CHECK better than validating only in application code?

------------------------------------------------------------------------

# 15. Practice Problems

1.  Create a Product table where:

    -   Price \>= 0
    -   Quantity \> 0

2.  Restrict Semester to 1--8.

3.  Restrict Order Status to:

    -   Pending
    -   Packed
    -   Shipped
    -   Delivered
    -   Cancelled

4.  Write a CHECK comparing Salary and Bonus.

------------------------------------------------------------------------

# Revision Notes

``` text
CHECK
   │
Business Rule
   │
Valid Data
```

## Memory Trick

``` text
CHECK

=

Condition Must Be True
```

## Key Points

-   CHECK validates values using logical conditions.
-   It can validate ranges, lists, and comparisons.
-   It can be applied at column or table level.
-   It complements NOT NULL, UNIQUE, and DEFAULT.
-   Strong CHECK constraints improve database reliability.

------------------------------------------------------------------------

# Final Takeaway

The **CHECK** constraint gives a database the ability to enforce
business rules instead of merely storing data. It ensures values are not
only present but also meaningful. A database that validates its own data
is far less dependent on every application behaving perfectly, and
experience has shown that this is a remarkably sensible design choice.
