# Lesson 078 --- UNIQUE Constraint

> **Part 05 --- Constraints**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What the UNIQUE constraint is
-   Why UNIQUE is important
-   UNIQUE vs PRIMARY KEY
-   Can UNIQUE contain NULL values?
-   SQL implementation
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Suppose a university stores student emails.

``` text
StudentID   Name     Email
-----------------------------------------
101         Alice    alice@mail.com
102         Bob      alice@mail.com
```

Two students now have the same email.

If the email is used for login, password recovery, or communication,
this creates problems.

The **UNIQUE** constraint prevents duplicate values.

------------------------------------------------------------------------

# 2. What is the UNIQUE Constraint?

A **UNIQUE** constraint ensures that **all values in a column (or a
combination of columns) are distinct**.

``` text
Column
   │
No Duplicate Values
```

Unlike a PRIMARY KEY, a UNIQUE column is not necessarily the table's
main identifier.

------------------------------------------------------------------------

# 3. Why Do We Need UNIQUE?

Without UNIQUE:

-   Duplicate usernames appear.
-   Duplicate email addresses exist.
-   Duplicate passport numbers are stored.
-   Business rules are violated.

With UNIQUE:

-   Duplicate values are rejected.
-   Data remains consistent.
-   Candidate Keys can be enforced.

------------------------------------------------------------------------

# 4. Child-Friendly Analogy

Imagine every player on a football team has a jersey number.

``` text
Player   Jersey No.
A        7
B        10
C        9
```

No two players on the same team can wear the same jersey number.

That is exactly how a UNIQUE constraint works.

------------------------------------------------------------------------

# 5. UNIQUE vs PRIMARY KEY

  UNIQUE                            PRIMARY KEY
  --------------------------------- -------------------------
  Many per table                    Only one per table
  Prevents duplicates               Prevents duplicates
  May allow NULL (DBMS dependent)   Never allows NULL
  Alternate unique identifier       Official row identifier

------------------------------------------------------------------------

# 6. Can UNIQUE Contain NULL?

This depends on the DBMS.

Generally:

-   PRIMARY KEY → NULL not allowed
-   UNIQUE → Many DBMSs allow one or more NULL values according to their
    implementation

Always check your specific database documentation.

------------------------------------------------------------------------

# 7. SQL Implementation

## Example 1

``` sql
CREATE TABLE Student(
    StudentID INT PRIMARY KEY,
    Email VARCHAR(100) UNIQUE,
    Name VARCHAR(100)
);
```

------------------------------------------------------------------------

## Example 2

Multiple UNIQUE constraints

``` sql
CREATE TABLE Employee(
    EmployeeID INT PRIMARY KEY,
    Email VARCHAR(100) UNIQUE,
    PassportNo VARCHAR(20) UNIQUE
);
```

------------------------------------------------------------------------

## Example 3

Composite UNIQUE

``` sql
CREATE TABLE Employee(
    DepartmentID INT,
    EmployeeCode INT,
    UNIQUE(DepartmentID, EmployeeCode)
);
```

The combination must be unique.

------------------------------------------------------------------------

# 8. How UNIQUE Works

``` text
New Value
    │
    ▼
Already Exists?
    │
 ┌──┴────┐
 │       │
 No     Yes
 │       │
 ▼       ▼
Store  Reject
```

------------------------------------------------------------------------

# 9. Real-World Examples

## Banking

-   Account Number
-   Debit Card Number

## Hospital

-   Patient National ID
-   Insurance Number

## University

-   University Email
-   Registration Number

## E-commerce

-   Coupon Code
-   Product SKU

------------------------------------------------------------------------

# 10. Advantages

-   Prevents duplicate business values
-   Improves data integrity
-   Supports Candidate and Alternate Keys
-   Simplifies searching
-   Enforces business rules

------------------------------------------------------------------------

# 11. Common Mistakes

❌ Assuming UNIQUE and PRIMARY KEY are identical.

❌ Forgetting that a table can have multiple UNIQUE constraints.

❌ Using UNIQUE when duplicates are actually valid.

------------------------------------------------------------------------

# 12. Interview Questions

### Beginner

1.  What is the UNIQUE constraint?
2.  Why is it used?
3.  UNIQUE vs PRIMARY KEY?

### Intermediate

1.  Can a table have multiple UNIQUE constraints?
2.  Can UNIQUE be applied to multiple columns?

### Advanced

1.  How does your DBMS handle NULL values in UNIQUE columns?
2.  When would you choose UNIQUE instead of PRIMARY KEY?

------------------------------------------------------------------------

# 13. Practice Problems

1.  Create a Student table with:

    -   StudentID as PRIMARY KEY
    -   Email as UNIQUE
    -   Phone as UNIQUE

2.  Create a composite UNIQUE constraint.

3.  Predict whether each INSERT succeeds or fails.

------------------------------------------------------------------------

# Revision Notes

``` text
UNIQUE
   │
No Duplicate Values
   │
Data Consistency
```

## Memory Trick

``` text
UNIQUE

=

Only One of Each Value
```

## Key Points

-   UNIQUE prevents duplicate values.
-   A table may have multiple UNIQUE constraints.
-   PRIMARY KEY is always UNIQUE, but UNIQUE is not always a PRIMARY
    KEY.
-   Composite UNIQUE constraints are supported.
-   NULL behavior varies across DBMSs.

------------------------------------------------------------------------

# Final Takeaway

The **UNIQUE** constraint protects business values that must never be
duplicated, even if they are not chosen as the Primary Key. It is
commonly used for email addresses, usernames, registration numbers,
passport numbers, and similar identifiers. Good database design often
combines a surrogate Primary Key with one or more UNIQUE constraints to
enforce real-world business rules cleanly and efficiently.
