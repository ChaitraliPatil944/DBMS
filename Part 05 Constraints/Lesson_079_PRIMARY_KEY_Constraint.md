# Lesson 079 --- PRIMARY KEY Constraint

> **Part 05 --- Constraints**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What the PRIMARY KEY constraint is
-   Why PRIMARY KEY is important
-   Rules of the PRIMARY KEY constraint
-   PRIMARY KEY vs UNIQUE
-   PRIMARY KEY vs FOREIGN KEY
-   SQL implementation
-   Composite PRIMARY KEY
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Imagine a bank database.

``` text
AccountNo   Customer
-------------------------
1001        Alice
1001        Bob
```

Which customer owns Account **1001**?

The database cannot decide.

To avoid this confusion, every table needs one official identifier.

That identifier is enforced using the **PRIMARY KEY** constraint.

------------------------------------------------------------------------

# 2. What is the PRIMARY KEY Constraint?

A **PRIMARY KEY** constraint ensures that one column (or a combination
of columns) uniquely identifies every row in a table.

It automatically enforces:

-   UNIQUE
-   NOT NULL

``` text
PRIMARY KEY
      │
UNIQUE + NOT NULL
```

------------------------------------------------------------------------

# 3. Why Do We Need It?

Without a PRIMARY KEY:

-   Duplicate rows appear.
-   Rows cannot be identified reliably.
-   Foreign Keys cannot reference rows correctly.
-   Data integrity suffers.

------------------------------------------------------------------------

# 4. Child-Friendly Analogy

Every citizen has a passport number.

``` text
Passport No.
-------------
P12345
P67890
```

Two people cannot share the same passport number, and nobody should have
an unknown passport number.

That's exactly how a PRIMARY KEY works.

------------------------------------------------------------------------

# 5. Rules of a PRIMARY KEY

-   Only one PRIMARY KEY per table.
-   Values must be unique.
-   Values cannot be NULL.
-   Every row must have one.
-   It should be stable and rarely change.

------------------------------------------------------------------------

# 6. SQL Implementation

## Single-column PRIMARY KEY

``` sql
CREATE TABLE Student(
    StudentID INT PRIMARY KEY,
    Name VARCHAR(100) NOT NULL,
    Email VARCHAR(100) UNIQUE
);
```

------------------------------------------------------------------------

## Composite PRIMARY KEY

``` sql
CREATE TABLE Enrollment(
    StudentID INT,
    CourseID INT,
    Grade CHAR(1),
    PRIMARY KEY(StudentID, CourseID)
);
```

------------------------------------------------------------------------

## Adding Later

``` sql
ALTER TABLE Student
ADD PRIMARY KEY(StudentID);
```

------------------------------------------------------------------------

# 7. How PRIMARY KEY Works

``` text
New Row
   │
   ▼
Duplicate?
   │
┌──┴───┐
│      │
No    Yes
│      │
▼      ▼
Store Reject
```

If the value is NULL:

``` text
Reject
```

------------------------------------------------------------------------

# 8. PRIMARY KEY vs UNIQUE

  PRIMARY KEY               UNIQUE
  ------------------------- -------------------------------
  One per table             Many allowed
  NOT NULL                  NULL handling depends on DBMS
  Official row identifier   Alternate unique value

------------------------------------------------------------------------

# 9. PRIMARY KEY vs FOREIGN KEY

  PRIMARY KEY         FOREIGN KEY
  ------------------- ------------------------
  Identifies a row    References another row
  Unique              Duplicates allowed
  NOT NULL            May allow NULL
  Parent identifier   Child reference

------------------------------------------------------------------------

# 10. Real-World Examples

## Banking

-   AccountNumber

## Hospital

-   PatientID

## University

-   StudentID

## E-commerce

-   OrderID

## Library

-   BookID

------------------------------------------------------------------------

# 11. Advantages

-   Guarantees unique identity
-   Prevents duplicate records
-   Supports relationships
-   Improves indexing and searches
-   Strengthens data integrity

------------------------------------------------------------------------

# 12. Common Mistakes

❌ Using a frequently changing value as a PRIMARY KEY.

❌ Creating multiple PRIMARY KEY constraints in one table.

❌ Assuming PRIMARY KEY and UNIQUE are identical.

❌ Choosing a business value that may change instead of a surrogate key.

------------------------------------------------------------------------

# 13. Interview Questions

### Beginner

1.  What is a PRIMARY KEY?
2.  Why can't it contain NULL values?
3.  Can a table have two PRIMARY KEY constraints?

### Intermediate

1.  PRIMARY KEY vs UNIQUE?
2.  PRIMARY KEY vs FOREIGN KEY?

### Advanced

1.  When should you use a Composite PRIMARY KEY?
2.  Why do many production databases use surrogate PRIMARY KEYs?

------------------------------------------------------------------------

# 14. Practice Problems

1.  Create a Student table with:

    -   StudentID as PRIMARY KEY
    -   Email as UNIQUE
    -   Name as NOT NULL

2.  Design an Enrollment table using a Composite PRIMARY KEY.

3.  Predict whether each INSERT succeeds or fails based on duplicate and
    NULL values.

------------------------------------------------------------------------

# Revision Notes

``` text
PRIMARY KEY
      │
UNIQUE
      +
NOT NULL
      │
Unique Row Identity
```

## Memory Trick

``` text
Primary

=

Principal Identity
```

## Key Points

-   PRIMARY KEY uniquely identifies every row.
-   Only one PRIMARY KEY is allowed per table.
-   PRIMARY KEY automatically enforces UNIQUE and NOT NULL.
-   Composite PRIMARY KEYs use multiple columns.
-   PRIMARY KEYs are commonly referenced by FOREIGN KEYs.

------------------------------------------------------------------------

# Final Takeaway

The **PRIMARY KEY** constraint is the foundation of relational database
design. It gives every row a permanent identity, enabling reliable
relationships, indexing, and efficient querying. Without a strong
PRIMARY KEY, the rest of the database has nothing stable to build upon.
Every well-designed table begins by answering one question: *How will
this row be uniquely identified?*
