# Lesson 077 --- NOT NULL Constraint

> **Part 05 --- Constraints**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What the NOT NULL constraint is
-   Why NOT NULL is important
-   NULL vs Empty String vs Zero
-   Relationship between NOT NULL and PRIMARY KEY
-   SQL implementation
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Consider the following Employee table:

``` text
EmployeeID   Name      Email
--------------------------------
101          Alice     alice@mail.com
102          NULL      bob@mail.com
103          Neha      NULL
```

Can an employee exist without a name?

Sometimes business rules say **No**.

The database enforces this using the **NOT NULL** constraint.

------------------------------------------------------------------------

# 2. What is the NOT NULL Constraint?

The **NOT NULL** constraint ensures that a column **must always contain
a value**.

The DBMS rejects rows where that column is missing.

``` text
Column
   │
Must Have Value
```

------------------------------------------------------------------------

# 3. Why Do We Need NOT NULL?

Without NOT NULL:

-   Important information may be missing.
-   Reports become incomplete.
-   Business rules are violated.
-   Applications may fail unexpectedly.

------------------------------------------------------------------------

# 4. Child-Friendly Analogy

Imagine an examination form.

Required fields:

``` text
Name
Roll Number
Class
```

Leaving the **Name** blank means the form is rejected.

That is exactly how `NOT NULL` works.

------------------------------------------------------------------------

# 5. NULL vs Empty String vs Zero

  Value                 Meaning
  --------------------- -----------------------------------
  `NULL`                Unknown or missing
  `''` (empty string)   Known, but contains no characters
  `0`                   A valid numeric value

Example:

``` text
Age = NULL   → Unknown
Age = 0      → Known value
Name = ''    → Empty text
```

These are **not the same**.

------------------------------------------------------------------------

# 6. NOT NULL and PRIMARY KEY

Every `PRIMARY KEY` is automatically:

-   `NOT NULL`
-   `UNIQUE`

So writing this is unnecessary:

``` sql
StudentID INT PRIMARY KEY NOT NULL
```

because `PRIMARY KEY` already enforces `NOT NULL`.

------------------------------------------------------------------------

# 7. SQL Implementation

## Example 1

``` sql
CREATE TABLE Student(
    StudentID INT PRIMARY KEY,
    Name VARCHAR(100) NOT NULL,
    Email VARCHAR(100),
    Age INT
);
```

------------------------------------------------------------------------

## Example 2

Adding later:

``` sql
ALTER TABLE Student
MODIFY Name VARCHAR(100) NOT NULL;
```

(Syntax varies slightly between DBMSs.)

------------------------------------------------------------------------

# 8. How NOT NULL Works

``` text
User Input
     │
     ▼
Value Present?
     │
 ┌───┴────┐
 │        │
Yes      No
 │        │
 ▼        ▼
Stored  Rejected
```

------------------------------------------------------------------------

# 9. Real-World Examples

## Banking

-   Account Number → NOT NULL
-   Customer Name → NOT NULL

## Hospital

-   PatientID → NOT NULL
-   Date of Birth → NOT NULL

## University

-   StudentID → NOT NULL
-   Student Name → NOT NULL

## E-commerce

-   OrderID → NOT NULL
-   Order Date → NOT NULL

------------------------------------------------------------------------

# 10. Advantages

-   Prevents missing critical data
-   Improves data quality
-   Enforces mandatory fields
-   Simplifies reporting
-   Reduces application errors

------------------------------------------------------------------------

# 11. Common Mistakes

❌ Assuming an empty string is the same as `NULL`.

❌ Forgetting to apply `NOT NULL` to mandatory columns.

❌ Applying `NOT NULL` to optional information.

------------------------------------------------------------------------

# 12. Interview Questions

### Beginner

1.  What is the NOT NULL constraint?
2.  Why is it used?
3.  Can a PRIMARY KEY contain NULL?

### Intermediate

1.  NULL vs Empty String?
2.  NULL vs Zero?

### Advanced

1.  Which columns in a banking database should be NOT NULL?
2.  Can a UNIQUE column contain NULL values?

------------------------------------------------------------------------

# 13. Practice Problems

1.  Design a Student table where:
    -   Name is mandatory.
    -   Email is optional.
    -   StudentID is the Primary Key.
2.  Identify which columns should use NOT NULL in:
    -   Employee
    -   Product
    -   Customer
    -   Order
3.  Predict whether each INSERT succeeds or fails.

------------------------------------------------------------------------

# Revision Notes

``` text
NOT NULL
    │
Mandatory Value
    │
No Missing Data
```

## Memory Trick

``` text
NOT NULL

=

Must Exist
```

## Key Points

-   `NOT NULL` prevents missing values.
-   `NULL` means unknown, not zero or an empty string.
-   `PRIMARY KEY` automatically includes `NOT NULL`.
-   Use `NOT NULL` for mandatory business information.

------------------------------------------------------------------------

# Final Takeaway

The `NOT NULL` constraint ensures that essential information is never
omitted from the database. It is one of the simplest constraints, yet it
prevents countless data quality issues. A database can often cope with
optional information being absent, but it struggles when critical
identity or business fields quietly disappear.
