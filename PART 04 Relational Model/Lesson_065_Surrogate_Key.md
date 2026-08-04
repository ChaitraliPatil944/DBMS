# Lesson 065 --- Surrogate Key

> **Part 04 --- Relational Model**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What a Surrogate Key is
-   Why Surrogate Keys were introduced
-   Natural Key vs Surrogate Key
-   Characteristics of Surrogate Keys
-   Auto Increment and UUID
-   Industry best practices
-   SQL implementation
-   Advantages and disadvantages
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Imagine an employee database.

    EmployeeID
    PassportNo
    Email
    Name

Initially, the company decides to use **Email** as the Primary Key.

Later:

-   Employees change email addresses.
-   Some employees have multiple emails.

The Primary Key becomes unstable.

To solve this, databases often use an **artificial identifier** that
never changes.

This is called a **Surrogate Key**.

------------------------------------------------------------------------

# 2. Why Were Surrogate Keys Introduced?

Natural identifiers can:

-   Change over time
-   Be long
-   Contain business meaning
-   Be reused accidentally

A Surrogate Key avoids these problems.

------------------------------------------------------------------------

# 3. What is a Surrogate Key?

A **Surrogate Key** is an **artificially generated unique identifier**
with **no business meaning**.

It exists only to uniquely identify a row.

Examples:

    1
    2
    3
    4

or

    550e8400-e29b-41d4-a716-446655440000

(UUID)

------------------------------------------------------------------------

# 4. Child-Friendly Analogy

Imagine every student receives a locker number.

    Locker No. 501

The number does not describe the student.

It simply identifies one locker.

A Surrogate Key works the same way.

------------------------------------------------------------------------

# 5. Characteristics of a Surrogate Key

A Surrogate Key:

-   Is unique
-   Has no business meaning
-   Never changes
-   Is usually generated automatically
-   Is often numeric or a UUID

------------------------------------------------------------------------

# 6. Natural Key vs Surrogate Key

  Natural Key            Surrogate Key
  ---------------------- ---------------------
  Real-world value       Artificial value
  Has business meaning   No business meaning
  May change             Stable
  May be long            Usually short

Example:

Natural Key

    ISBN
    Passport Number
    Email

Surrogate Key

    BookID
    CustomerID
    OrderID

------------------------------------------------------------------------

# 7. Auto Increment

Most databases can automatically generate IDs.

Example:

``` sql
CREATE TABLE Student(
    StudentID INT AUTO_INCREMENT PRIMARY KEY,
    Name VARCHAR(100)
);
```

New rows receive:

    1
    2
    3
    4

automatically.

------------------------------------------------------------------------

# 8. UUID

UUID stands for **Universally Unique Identifier**.

Example:

    550e8400-e29b-41d4-a716-446655440000

Advantages:

-   Globally unique
-   Useful in distributed systems
-   No central ID generator required

------------------------------------------------------------------------

# 9. SQL Examples

## MySQL

``` sql
CREATE TABLE Customer(
    CustomerID INT AUTO_INCREMENT PRIMARY KEY,
    Name VARCHAR(100)
);
```

## PostgreSQL

``` sql
CREATE TABLE Customer(
    CustomerID SERIAL PRIMARY KEY,
    Name TEXT
);
```

## SQL Server

``` sql
CREATE TABLE Customer(
    CustomerID INT IDENTITY(1,1) PRIMARY KEY,
    Name NVARCHAR(100)
);
```

------------------------------------------------------------------------

# 10. Real-World Examples

## E-commerce

    OrderID

## Banking

    CustomerID

## Hospital

    PatientID

## University

    StudentID

These IDs are often surrogate keys.

------------------------------------------------------------------------

# 11. Advantages

-   Stable identifiers
-   Faster joins (numeric IDs)
-   Independent of business rules
-   Easy to generate
-   Simplifies foreign key relationships

------------------------------------------------------------------------

# 12. Disadvantages

-   Adds one extra column
-   Users cannot understand the value directly
-   Natural uniqueness still needs UNIQUE constraints

------------------------------------------------------------------------

# 13. Industry Best Practices

✔ Use surrogate keys for most transactional tables.

✔ Preserve natural identifiers using UNIQUE constraints.

Example:

``` sql
CREATE TABLE Employee(
    EmployeeID INT AUTO_INCREMENT PRIMARY KEY,
    Email VARCHAR(100) UNIQUE,
    PassportNo VARCHAR(20) UNIQUE
);
```

------------------------------------------------------------------------

# 14. Common Mistakes

❌ Assuming surrogate keys replace business validation.

❌ Forgetting UNIQUE constraints on natural identifiers.

❌ Using changing business values as Primary Keys.

------------------------------------------------------------------------

# 15. Interview Questions

### Beginner

1.  What is a Surrogate Key?
2.  Why is it used?

### Intermediate

1.  Surrogate Key vs Natural Key?
2.  What is AUTO_INCREMENT?

### Advanced

1.  When should UUID be preferred over integers?
2.  Why do large companies often use surrogate keys?

------------------------------------------------------------------------

# 16. Practice Problems

1.  Design a Customer table using a surrogate key.
2.  Add UNIQUE constraints for Email and Passport Number.
3.  Compare surrogate and natural keys for a Library system.

------------------------------------------------------------------------

# Revision Notes

    Natural Key
          │
    Business Meaning

    Surrogate Key
          │
    Artificial Identifier

Memory Trick

    Surrogate

    =

    Substitute

Quick Summary

  Key Type        Meaning
  --------------- ----------------------------
  Natural Key     Real-world identifier
  Surrogate Key   Artificial identifier
  Primary Key     Official row identifier
  Foreign Key     Reference to another table

Key Points

-   Surrogate Keys are artificial identifiers.
-   They have no business meaning.
-   They are stable and rarely change.
-   AUTO_INCREMENT and UUID are common implementations.
-   Natural keys should still be protected using UNIQUE constraints.

**Remember:**

> A Surrogate Key exists purely for the database's benefit. It doesn't
> describe the data, it simply identifies it efficiently. Modern
> database systems frequently prefer surrogate keys because business
> rules evolve, names change, emails change, but a good identifier
> quietly stays the same for the lifetime of the record.
