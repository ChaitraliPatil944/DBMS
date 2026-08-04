# Lesson 058 --- Domains

> **Part 04 --- Relational Model**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What a Domain is
-   Why Domains are important
-   Mathematical origin of Domains
-   Domain vs Data Type
-   Domain Constraints
-   Valid vs Invalid Domain Values
-   SQL implementation
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Imagine a database where someone enters:

    Age = Banana

    Salary = Blue

    Gender = 999

Technically, if no rules exist, the database may accept such values.

Clearly, these values make no sense.

To prevent invalid data, the Relational Model introduces **Domains**.

------------------------------------------------------------------------

# 2. What is a Domain?

A **Domain** is the set of all valid values that an attribute is allowed
to contain.

Think of it as a rule book for a column.

Example:

    Age

    ↓

    0 to 150

Only values within this range are valid.

------------------------------------------------------------------------

# 3. Mathematical Origin

The idea of a domain comes from **Set Theory**.

A domain is simply a **set of permissible values**.

Example

    Blood Group Domain

    {A+, A-, B+, B-, AB+, AB-, O+, O-}

Only these values belong to the domain.

------------------------------------------------------------------------

# 4. Why Do We Need Domains?

Without domains:

    Age = Elephant

With domains:

    Age = 21 ✔

    Age = Elephant ✘

Domains improve:

-   Data accuracy
-   Consistency
-   Reliability
-   Validation

------------------------------------------------------------------------

# 5. Child-Friendly Analogy

Imagine a classroom attendance sheet.

    Present?

    ↓

    Allowed Answers

    Yes

    No

If someone writes:

    Pizza

it is not valid.

The allowed answers form the domain.

------------------------------------------------------------------------

# 6. Domain vs Data Type

Many beginners confuse these.

  Data Type                Domain
  ------------------------ -----------------------------
  Defines storage format   Defines allowed values
  INT                      1--100
  VARCHAR                  Only valid department names
  DATE                     Dates after 2000

Example

    Age

    Data Type → INT

    Domain → 18 to 60

Both are needed.

------------------------------------------------------------------------

# 7. Types of Domains

## Numeric Domain

    Marks

    0–100

------------------------------------------------------------------------

## Character Domain

    Department

    CSE
    IT
    ECE
    AIML

------------------------------------------------------------------------

## Date Domain

    Joining Date

    01-01-2000

    ↓

    Today's Date

------------------------------------------------------------------------

## Boolean Domain

    Paid?

    TRUE

    FALSE

------------------------------------------------------------------------

## Enumerated Domain

    Order Status

    Pending

    Processing

    Delivered

    Cancelled

------------------------------------------------------------------------

# 8. Domain Constraints

A **Domain Constraint** ensures that every value belongs to the domain.

Example

    Age

    Allowed

    18–60

Valid

    21
    45
    60

Invalid

    5
    -10
    1000

------------------------------------------------------------------------

# 9. SQL Implementation

``` sql
CREATE TABLE Student(
    StudentID INT PRIMARY KEY,
    Name VARCHAR(100) NOT NULL,
    Age INT CHECK (Age BETWEEN 16 AND 60),
    Department VARCHAR(20)
        CHECK (Department IN
        ('CSE','IT','ECE','AIML'))
);
```

The `CHECK` constraint enforces the domain.

------------------------------------------------------------------------

# 10. Real-World Examples

## Banking

    Account Type

    Savings
    Current
    Salary

------------------------------------------------------------------------

## Hospital

    Blood Group

    A+
    A-
    B+
    B-
    AB+
    AB-
    O+
    O-

------------------------------------------------------------------------

## E-commerce

    Order Status

    Pending
    Packed
    Shipped
    Delivered
    Cancelled

------------------------------------------------------------------------

## University

    Semester

    1

    2

    3

    ...

    8

------------------------------------------------------------------------

# 11. Valid vs Invalid Values

  Attribute     Valid    Invalid
  ------------- -------- ---------------------------
  Age           20       Apple
  Blood Group   O+       Purple
  Semester      6        12 (if only 1--8 allowed)
  Gender        Female   999

------------------------------------------------------------------------

# 12. Advantages of Domains

-   Prevent invalid data
-   Improve consistency
-   Simplify validation
-   Reduce application errors
-   Improve data quality
-   Support business rules

------------------------------------------------------------------------

# 13. Common Mistakes

❌ Assuming the data type alone is enough.

    INT

allows many values.

The domain decides which integer values are acceptable.

❌ Using free-text values when a fixed list exists.

Example:

    Department

    Computer
    Comp
    CSE
    Computer Science

Use one standardized domain.

------------------------------------------------------------------------

# 14. Interview Questions

### Beginner

1.  What is a Domain?
2.  Why are domains required?
3.  Domain vs Data Type?

### Intermediate

1.  What is a Domain Constraint?
2.  Give real-world examples of domains.

### Advanced

1.  Design suitable domains for:
    -   Banking
    -   Hospital
    -   Airline
    -   University
2.  How do domains improve data integrity?

------------------------------------------------------------------------

# 15. Practice Problems

1.  Create domains for:

-   Employee Age
-   Salary
-   Product Category
-   Blood Group
-   Order Status

2.  Write SQL using CHECK constraints.

3.  Identify whether the following values belong to their domains.

------------------------------------------------------------------------

# Revision Notes

    Domain

    ↓

    Allowed Values

    ↓

    Valid Data

    ↓

    Reliable Database

Quick Summary

    Relation
    =
    Table

    Tuple
    =
    Row

    Attribute
    =
    Column

    Domain
    =
    Allowed Values

Memory Trick

    D A V

    Domain

    ↓

    Allowed

    ↓

    Values

Key Points

-   Every attribute has a domain.
-   A domain is a set of valid values.
-   Domains are different from data types.
-   CHECK constraints commonly enforce domains.
-   Good domains improve data integrity.

**Remember:**

> A domain is the database's way of saying, "These are the only values
> that make sense here." It quietly rejects nonsense before it becomes
> tomorrow's debugging session, which is considerably kinder than
> letting bad data spread through an entire system.
