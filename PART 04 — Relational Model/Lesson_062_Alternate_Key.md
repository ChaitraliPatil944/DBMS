# Lesson 062 --- Alternate Key

> **Part 04 --- Relational Model**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What an Alternate Key is
-   Why Alternate Keys are needed
-   How Alternate Keys are formed
-   Characteristics of Alternate Keys
-   Alternate Key vs Candidate Key
-   Alternate Key vs Primary Key
-   Alternate Key vs Super Key
-   SQL implementation
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

In the previous lesson, we learned that a table may have **multiple
Candidate Keys**, but only **one** of them is selected as the Primary
Key.

What happens to the remaining Candidate Keys?

They become **Alternate Keys**.

------------------------------------------------------------------------

# 2. What is an Alternate Key?

An **Alternate Key** is a **Candidate Key that was not selected as the
Primary Key**.

It still uniquely identifies each tuple but is not the table's official
primary identifier.

------------------------------------------------------------------------

# 3. Why Do We Need Alternate Keys?

Suppose a Student table contains:

    StudentID
    Email
    PassportNo
    Name

Unique attributes:

-   StudentID
-   Email
-   PassportNo

Choose:

    Primary Key → StudentID

Remaining unique identifiers:

    Email
    PassportNo

These become Alternate Keys.

------------------------------------------------------------------------

# 4. Key Hierarchy

    Super Keys
          │
    Remove Extra Attributes
          ▼
    Candidate Keys
          │
    Choose One
          ▼
    Primary Key

    Remaining Candidate Keys
          ▼
    Alternate Keys

------------------------------------------------------------------------

# 5. Characteristics of an Alternate Key

An Alternate Key:

-   Is unique
-   Is minimal
-   Cannot contain duplicate values
-   Usually should not contain NULL values
-   Can become a Primary Key if needed

------------------------------------------------------------------------

# 6. Example

    Student

    +-----------+----------------------+------------------+------+
    |StudentID  |Email                 |PassportNo        |Name  |
    +-----------+----------------------+------------------+------+
    |101        |alice@mail.com        |P123456           |Alice |
    |102        |bob@mail.com          |P654321           |Bob   |
    +-----------+----------------------+------------------+------+

Candidate Keys:

-   StudentID
-   Email
-   PassportNo

Primary Key:

-   StudentID

Alternate Keys:

-   Email
-   PassportNo

------------------------------------------------------------------------

# 7. Alternate Key vs Primary Key

  Primary Key           Alternate Key
  --------------------- -----------------------------
  One per table         Zero or more
  Official identifier   Backup unique identifier
  Cannot be NULL        Usually UNIQUE and NOT NULL

------------------------------------------------------------------------

# 8. Alternate Key vs Candidate Key

  Candidate Key                    Alternate Key
  -------------------------------- --------------------------
  Eligible to become Primary Key   Candidate Key not chosen
  Exists before selection          Exists after selection

------------------------------------------------------------------------

# 9. Alternate Key vs Super Key

  Alternate Key   Super Key
  --------------- ------------------------------
  Minimal         May contain extra attributes
  Candidate Key   May or may not be minimal

------------------------------------------------------------------------

# 10. SQL Implementation

``` sql
CREATE TABLE Student(
    StudentID INT PRIMARY KEY,
    Email VARCHAR(100) UNIQUE NOT NULL,
    PassportNo VARCHAR(20) UNIQUE,
    Name VARCHAR(100)
);
```

Here:

-   StudentID → Primary Key
-   Email → Alternate Key
-   PassportNo → Alternate Key

The `UNIQUE` constraint helps enforce Alternate Keys.

------------------------------------------------------------------------

# 11. Real-World Examples

## Banking

Primary Key:

    AccountNumber

Alternate Key:

    UPI_ID

------------------------------------------------------------------------

## Hospital

Primary Key:

    PatientID

Alternate Key:

    NationalHealthID

------------------------------------------------------------------------

## Library

Primary Key:

    BookID

Alternate Key:

    ISBN

------------------------------------------------------------------------

## University

Primary Key:

    StudentID

Alternate Key:

    UniversityEmail

------------------------------------------------------------------------

# 12. Common Mistakes

❌ Thinking Alternate Keys are optional duplicates.

❌ Confusing UNIQUE columns with ordinary columns.

❌ Assuming every UNIQUE column is automatically an Alternate Key. It
must also be a Candidate Key.

------------------------------------------------------------------------

# 13. Interview Questions

### Beginner

1.  What is an Alternate Key?
2.  How is it formed?
3.  Can a table have multiple Alternate Keys?

### Intermediate

1.  Alternate Key vs Primary Key?
2.  Alternate Key vs Candidate Key?

### Advanced

Given:

    Employee(
    EmployeeID,
    Email,
    PassportNo,
    Phone
    )

Assume EmployeeID, Email, and PassportNo are unique.

Identify:

-   Primary Key
-   Alternate Keys

------------------------------------------------------------------------

# 14. Practice Problems

1.  Find the Alternate Keys:

```{=html}
<!-- -->
```
    Book(
    BookID,
    ISBN,
    Barcode,
    Title
    )

Assume BookID, ISBN, and Barcode are unique.

2.  Write SQL using PRIMARY KEY and UNIQUE constraints.

3.  Explain why only one Candidate Key becomes the Primary Key.

------------------------------------------------------------------------

# Revision Notes

    Super Key
          │
    Candidate Keys
          │
    Selected
          ▼
    Primary Key

    Remaining
          ▼
    Alternate Keys

Memory Trick

    Alternate

    =

    Alternative Choice

Quick Summary

  Concept         Meaning
  --------------- --------------------------------------
  Super Key       Unique, may contain extra attributes
  Candidate Key   Minimal Super Key
  Primary Key     Selected Candidate Key
  Alternate Key   Remaining Candidate Keys

Key Points

-   Alternate Keys are Candidate Keys that were not selected.
-   They remain unique identifiers.
-   Usually implemented using `UNIQUE`.
-   A relation may have multiple Alternate Keys.

**Remember:**

> Alternate Keys are the qualified candidates that were not chosen as
> the Primary Key. They still uniquely identify records and remain
> valuable for enforcing data integrity. Think of them as backup
> captains for the database. They may not wear the badge, but they're
> still fully capable of leading when needed.
