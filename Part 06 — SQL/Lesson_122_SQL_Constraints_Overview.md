# Lesson 122 --- SQL Constraints Overview

> **Part 06 --- Structured Query Language (SQL)**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What SQL constraints are
-   Why constraints are important
-   Types of constraints
-   Data integrity
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Imagine a school admission form.

Rules:

-   Student ID cannot be empty.
-   Roll Number must be unique.
-   Age cannot be negative.
-   Department must exist.

These rules prevent invalid information.

SQL uses **constraints** to enforce similar rules.

------------------------------------------------------------------------

# 2. What are SQL Constraints?

**Constraints** are rules applied to table columns that control what
data can be stored.

``` text
User Input
    │
Constraints Check
    │
Valid?
│         │
Yes       No
│         │
Stored   Rejected
```

Constraints improve **data integrity**.

------------------------------------------------------------------------

# 3. Why Do We Need Constraints?

Without constraints:

-   Duplicate IDs
-   Missing names
-   Invalid ages
-   Broken relationships

A database would quickly become unreliable.

------------------------------------------------------------------------

# 4. What is Data Integrity?

**Data Integrity** means data remains:

-   Accurate
-   Consistent
-   Valid
-   Reliable

Constraints help maintain these qualities.

------------------------------------------------------------------------

# 5. Types of SQL Constraints

``` text
Constraints
│
├── PRIMARY KEY
├── FOREIGN KEY
├── UNIQUE
├── NOT NULL
├── CHECK
└── DEFAULT
```

Each solves a different problem.

------------------------------------------------------------------------

# 6. Constraint Overview

  Constraint    Purpose
  ------------- ------------------------------
  PRIMARY KEY   Uniquely identifies each row
  FOREIGN KEY   Maintains relationships
  UNIQUE        Prevents duplicate values
  NOT NULL      Prevents empty values
  CHECK         Validates conditions
  DEFAULT       Supplies default values

------------------------------------------------------------------------

# 7. Example Table

``` sql
CREATE TABLE Student
(
    StudentID INT PRIMARY KEY,
    Name VARCHAR(100) NOT NULL,
    Email VARCHAR(100) UNIQUE,
    Age INT CHECK (Age >= 16),
    Country VARCHAR(50) DEFAULT 'India'
);
```

ASCII view:

``` text
Student
│
├── StudentID → PRIMARY KEY
├── Name → NOT NULL
├── Email → UNIQUE
├── Age → CHECK
└── Country → DEFAULT
```

------------------------------------------------------------------------

# 8. How Constraints Work

``` text
INSERT
   │
Constraint Validation
   │
 ┌───────┴────────┐
 │                │
Valid          Invalid
 │                │
Stored        Error
```

The DBMS validates constraints before accepting data.

------------------------------------------------------------------------

# 9. Real-World Example

Bank Account:

``` text
Account Number
     │
PRIMARY KEY

Balance
     │
CHECK (Balance >= 0)

Customer Name
     │
NOT NULL
```

These rules help protect the quality of stored information.

------------------------------------------------------------------------

# 10. Benefits

-   Prevents invalid data
-   Improves consistency
-   Protects relationships
-   Reduces application errors
-   Simplifies validation

------------------------------------------------------------------------

# 11. Best Practices

-   Define constraints during table creation.
-   Use meaningful constraint names.
-   Apply only necessary constraints.
-   Validate business rules at the database level.

------------------------------------------------------------------------

# 12. Common Mistakes

❌ Depending only on application validation.

❌ Creating tables without a PRIMARY KEY.

❌ Ignoring FOREIGN KEY constraints.

❌ Adding unnecessary constraints that slow maintenance.

------------------------------------------------------------------------

# 13. Interview Questions

### Beginner

1.  What are SQL constraints?
2.  Why are constraints important?
3.  Name six common constraints.

### Intermediate

1.  What is data integrity?
2.  Why should constraints be enforced in the database?

### Advanced

1.  How do constraints improve reliability?
2.  When should constraints be added?

------------------------------------------------------------------------

# 14. Practice Problems

1.  List all SQL constraints.
2.  Explain data integrity.
3.  Design a Student table with appropriate constraints.
4.  Compare PRIMARY KEY and UNIQUE (preview).

------------------------------------------------------------------------

# Revision Notes

``` text
Constraints
 │
PRIMARY KEY
FOREIGN KEY
UNIQUE
NOT NULL
CHECK
DEFAULT
```

## Memory Trick

``` text
Constraints

=

Control

Reliable

Input
```

## Key Points

-   Constraints enforce rules on data.
-   They maintain data integrity.
-   Different constraints solve different validation problems.
-   Invalid data is rejected before storage.
-   Constraints are a core feature of relational databases.

------------------------------------------------------------------------

# Final Takeaway

SQL constraints act as the database's built-in quality control system.
Instead of trusting every application or user to provide correct data,
the database enforces important business rules itself. This keeps
information accurate, consistent, and reliable across every application
that connects to it, which is considerably less stressful than cleaning
up corrupted data after the fact.
