# Lesson 074 --- Key Constraint

> **Part 05 --- Constraints**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What a Key Constraint is
-   Why Key Constraints are required
-   How Key Constraints enforce uniqueness
-   Relationship with Super, Candidate and Primary Keys
-   SQL implementation
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Imagine an employee table:

``` text
EmployeeID  Name
101         Alice
101         Bob
```

Which employee does **EmployeeID = 101** refer to?

Nobody knows.

A database must prevent duplicate identities.

This is the job of a **Key Constraint**.

------------------------------------------------------------------------

# 2. What is a Key Constraint?

A **Key Constraint** ensures that every tuple can be uniquely identified
using one or more key attributes.

It prevents duplicate identifiers.

------------------------------------------------------------------------

# 3. Why Do We Need Key Constraints?

Without Key Constraints:

-   Duplicate records appear.
-   Relationships become unreliable.
-   Updates and deletes affect the wrong rows.
-   Data integrity is lost.

With Key Constraints:

-   Every record has a unique identity.
-   Relationships remain consistent.
-   Searching becomes reliable.

------------------------------------------------------------------------

# 4. Child-Friendly Analogy

Every student receives a roll number.

``` text
Roll No.

101
102
103
```

Two students cannot share the same roll number.

The roll number follows a Key Constraint.

------------------------------------------------------------------------

# 5. How Key Constraints Work

``` text
New Record
     │
     ▼
Check Existing Keys
     │
 ┌───┴────┐
 │        │
Unique Duplicate
 │        │
 ▼        ▼
Stored Rejected
```

------------------------------------------------------------------------

# 6. Key Constraint and Different Keys

``` text
Super Key
     │
Candidate Key
     │
Primary Key
```

A Key Constraint guarantees that the chosen key uniquely identifies each
row.

------------------------------------------------------------------------

# 7. SQL Example

``` sql
CREATE TABLE Student(
    StudentID INT PRIMARY KEY,
    Email VARCHAR(100) UNIQUE,
    Name VARCHAR(100)
);
```

Here:

-   `StudentID` has a PRIMARY KEY constraint.
-   `Email` has a UNIQUE constraint.

Both enforce uniqueness.

------------------------------------------------------------------------

# 8. PRIMARY KEY vs UNIQUE

  PRIMARY KEY           UNIQUE
  --------------------- -----------------------------
  One per table         Multiple allowed
  Cannot be NULL        NULL allowed in many DBMSs
  Official identifier   Alternate unique identifier

------------------------------------------------------------------------

# 9. Real-World Examples

## Banking

``` text
AccountNumber
```

Must be unique.

------------------------------------------------------------------------

## Hospital

``` text
PatientID
```

Must uniquely identify each patient.

------------------------------------------------------------------------

## University

``` text
StudentID
UniversityEmail
```

Both should be unique.

------------------------------------------------------------------------

## E-commerce

``` text
OrderID
```

Every order has a unique identifier.

------------------------------------------------------------------------

# 10. Advantages

-   Prevents duplicate identities
-   Improves data integrity
-   Supports relationships
-   Makes searching efficient
-   Enforces business rules

------------------------------------------------------------------------

# 11. Common Mistakes

❌ Using names as unique identifiers.

❌ Forgetting UNIQUE constraints on natural identifiers.

❌ Assuming data types prevent duplicates.

------------------------------------------------------------------------

# 12. Interview Questions

### Beginner

1.  What is a Key Constraint?
2.  Why is it required?
3.  PRIMARY KEY vs UNIQUE?

### Intermediate

1.  Can multiple UNIQUE constraints exist?
2.  Can two rows have the same Primary Key?

### Advanced

1.  Why is a Key Constraint important for Referential Integrity?
2.  When would you use UNIQUE instead of PRIMARY KEY?

------------------------------------------------------------------------

# 13. Practice Problems

1.  Design an Employee table with:
    -   Primary Key
    -   Alternate unique identifier
2.  Identify suitable key constraints for:
    -   Library
    -   Banking
    -   Hospital
    -   Airline
3.  Write SQL using PRIMARY KEY and UNIQUE.

------------------------------------------------------------------------

# Revision Notes

``` text
Key Constraint
      │
Unique Identification
      │
Data Integrity
```

## Memory Trick

``` text
K U I

Key
Unique
Identity
```

## Key Points

-   Key Constraints enforce uniqueness.
-   PRIMARY KEY and UNIQUE are the most common implementations.
-   Every Primary Key satisfies a Key Constraint.
-   Duplicate key values are rejected automatically.

------------------------------------------------------------------------

# Final Takeaway

A Key Constraint ensures that every important record in a database has a
unique identity. It is one of the fundamental building blocks of
relational databases because almost every relationship, query, and
transaction depends on reliably identifying rows. Once uniqueness is
lost, confusion spreads surprisingly quickly, and databases are much
less forgiving than humans pretending they remember which "John" they
meant.
