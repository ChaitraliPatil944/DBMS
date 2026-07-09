# Lesson 061 --- Primary Key

> **Part 04 --- Relational Model**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What a Primary Key is
-   Why Primary Keys are important
-   Characteristics of a good Primary Key
-   How a Candidate Key becomes a Primary Key
-   Primary Key vs Candidate Key
-   Primary Key vs Alternate Key
-   Natural vs Surrogate Primary Keys
-   SQL implementation
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Imagine a classroom where two students have the same name.

    Name

    Rahul

    Rahul

How do you uniquely identify one student?

Schools use a **Roll Number**.

Databases use a **Primary Key**.

------------------------------------------------------------------------

# 2. Why Do We Need a Primary Key?

Without a Primary Key:

-   Duplicate records can exist
-   Updates become confusing
-   Deletes may affect the wrong row
-   Relationships between tables become unreliable

A Primary Key gives every row a unique identity.

------------------------------------------------------------------------

# 3. What is a Primary Key?

A **Primary Key** is the **Candidate Key chosen to uniquely identify
every tuple in a relation**.

A table can have many Candidate Keys, but **only one Primary Key**.

------------------------------------------------------------------------

# 4. Key Hierarchy

    Super Key
         │
    Remove Extra Attributes
         ▼
    Candidate Key
         │
    Choose One
         ▼
    Primary Key

------------------------------------------------------------------------

# 5. Example

    Student

    +-----------+--------+----------------------+
    | StudentID | Name   | Email                |
    +-----------+--------+----------------------+
    | 101       | Alice  | alice@mail.com       |
    | 102       | Bob    | bob@mail.com         |
    +-----------+--------+----------------------+

Candidate Keys:

-   StudentID
-   Email

Chosen Primary Key:

    StudentID

------------------------------------------------------------------------

# 6. Characteristics of a Good Primary Key

A good Primary Key should be:

-   Unique
-   Never NULL
-   Stable
-   Minimal
-   Simple
-   Permanent

------------------------------------------------------------------------

# 7. Rules of a Primary Key

✔ Only one Primary Key per table

✔ Cannot contain duplicate values

✔ Cannot contain NULL values

✔ Every row must have one

------------------------------------------------------------------------

# 8. Child-Friendly Analogy

Think of a school ID card.

    Roll Number

    ↓

    Unique

    ↓

    Never shared

Even if two students have the same name, the roll number remains unique.

------------------------------------------------------------------------

# 9. Primary Key vs Candidate Key

  Candidate Key            Primary Key
  ------------------------ --------------
  Many may exist           Only one
  Eligible for selection   Selected key
  Minimal                  Minimal

------------------------------------------------------------------------

# 10. Primary Key vs Alternate Key

  Primary Key              Alternate Key
  ------------------------ --------------------------
  Selected Candidate Key   Remaining Candidate Keys
  One per table            Zero or more

Example

Candidate Keys:

-   StudentID
-   Email

Primary Key:

-   StudentID

Alternate Key:

-   Email

------------------------------------------------------------------------

# 11. Natural vs Surrogate Primary Key

### Natural Key

Exists in the real world.

Examples:

-   Passport Number
-   ISBN
-   Aadhaar Number

### Surrogate Key

Artificially generated.

Examples:

-   Auto Increment ID
-   UUID

------------------------------------------------------------------------

# 12. SQL Example

``` sql
CREATE TABLE Student(
    StudentID INT PRIMARY KEY,
    Name VARCHAR(100) NOT NULL,
    Email VARCHAR(100) UNIQUE
);
```

Here:

-   StudentID → Primary Key
-   Email → Candidate/Alternate Key

------------------------------------------------------------------------

# 13. Real-World Examples

## Banking

    AccountNumber

## Hospital

    PatientID

## Library

    BookID

## University

    StudentID

------------------------------------------------------------------------

# 14. Common Mistakes

❌ Using names as Primary Keys.

❌ Choosing values that change frequently.

❌ Allowing NULL values.

❌ Assuming every unique column must be the Primary Key.

------------------------------------------------------------------------

# 15. Interview Questions

### Beginner

1.  What is a Primary Key?
2.  Why is it important?
3.  Can it contain NULL values?

### Intermediate

1.  Primary Key vs Candidate Key?
2.  Why can there be only one Primary Key?

### Advanced

1.  When would you use a Surrogate Key instead of a Natural Key?
2.  Can a Primary Key consist of multiple columns?

------------------------------------------------------------------------

# 16. Practice Problems

1.  Choose the best Primary Key for:

```{=html}
<!-- -->
```
    Employee(
    EmployeeID,
    Email,
    Phone,
    Name
    )

2.  Explain why the remaining Candidate Keys become Alternate Keys.

3.  Write SQL to create a table with a Primary Key.

------------------------------------------------------------------------

# Revision Notes

    Super Key
          │
    Candidate Key
          │
    Selected
          ▼
    Primary Key

Memory Trick

    Primary

    =

    Principal

    =

    Main Key

Key Points

-   Only one Primary Key per relation.
-   A Primary Key is always a Candidate Key.
-   It must be unique and NOT NULL.
-   It is used to identify every row and build relationships with other
    tables.

**Remember:**

> A Primary Key is the official identity of every row in a table.
> Choosing a stable and meaningful Primary Key makes the entire database
> easier to maintain. Choose poorly, and every related table inherits
> that decision for years. Databases are remarkably loyal to yesterday's
> design choices.
