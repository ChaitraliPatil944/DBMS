# Lesson 057 --- Attributes

> **Part 04 --- Relational Model**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What an Attribute is
-   Why attributes are important
-   Attribute vs Column vs Field
-   Types of attributes in the Relational Model
-   Key and Non-Key Attributes
-   Attribute Domains
-   Attribute Constraints
-   SQL examples
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

A database table stores information in **columns**.

In the Relational Model, these columns are formally called
**Attributes**.

Every piece of information about an entity is stored as an attribute.

Example:

    Student

    +-----------+--------+------------+
    | StudentID | Name   | Department |
    +-----------+--------+------------+

Here:

-   StudentID → Attribute
-   Name → Attribute
-   Department → Attribute

------------------------------------------------------------------------

# 2. What is an Attribute?

An **Attribute** is a property or characteristic of a relation.

It describes one aspect of every tuple in that relation.

Example:

    Relation : Student

    Attributes

    StudentID
    Name
    Department
    Email

------------------------------------------------------------------------

# 3. Why Are Attributes Needed?

Imagine storing student data like this:

    Alice
    101
    CSE
    alice@email.com

Without attribute names, nobody knows what each value means.

Attributes provide meaning to data.

------------------------------------------------------------------------

# 4. Child-Friendly Analogy

Think of a school report card.

    Name

    Roll Number

    Class

    Marks

These headings are attributes.

Each student's values are placed under the correct heading.

------------------------------------------------------------------------

# 5. Attribute vs Column vs Field

  Term        Meaning
  ----------- --------------------------
  Attribute   Formal database term
  Column      SQL table representation
  Field       Common application term

In most situations, all three refer to the same concept.

------------------------------------------------------------------------

# 6. Structure of Attributes

    Relation

    Student

    ↓

    Attributes

    StudentID

    Name

    Department

    Email

Each attribute stores one category of information.

------------------------------------------------------------------------

# 7. Types of Attributes (Relational View)

    Attributes
    │
    ├── Key Attribute
    ├── Non-Key Attribute
    ├── Stored Attribute
    ├── Derived Attribute
    ├── Nullable Attribute
    └── Mandatory Attribute

------------------------------------------------------------------------

# 8. Key Attribute

Uniquely identifies each tuple.

Example:

    StudentID

Every student has a unique StudentID.

------------------------------------------------------------------------

# 9. Non-Key Attribute

Stores additional information.

Examples:

    Name

    Email

    Department

    Phone

These values describe the student but do not uniquely identify them.

------------------------------------------------------------------------

# 10. Stored Attribute

Stored physically inside the database.

Example:

    DateOfBirth

------------------------------------------------------------------------

# 11. Derived Attribute

Calculated from another attribute.

Example:

    Age

    ↓

    Derived from

    ↓

    DateOfBirth

Usually calculated when needed.

------------------------------------------------------------------------

# 12. Nullable Attribute

May contain NULL.

Example

    MiddleName

Some people may not have one.

------------------------------------------------------------------------

# 13. Mandatory Attribute

Cannot contain NULL.

Example

    StudentID

    Name

Every record must contain values.

------------------------------------------------------------------------

# 14. Attribute Domain

Every attribute accepts only a specific set of values.

Examples

    Age

    0–150

    Gender

    Male

    Female

    Other

    Department

    CSE

    IT

    ECE

    AIML

A domain improves data accuracy.

------------------------------------------------------------------------

# 15. Attribute Constraints

Common constraints include:

-   PRIMARY KEY
-   NOT NULL
-   UNIQUE
-   CHECK
-   DEFAULT

Example

``` sql
CREATE TABLE Student(
    StudentID INT PRIMARY KEY,
    Name VARCHAR(100) NOT NULL,
    Department VARCHAR(30),
    Age INT CHECK (Age >= 16),
    Country VARCHAR(30) DEFAULT 'India'
);
```

------------------------------------------------------------------------

# 16. Real-World Examples

Library

    Book

    BookID
    Title
    Author
    Price

Hospital

    Patient

    PatientID
    Name
    BloodGroup

Bank

    Account

    AccountNo
    Balance
    Branch

------------------------------------------------------------------------

# 17. Common Mistakes

❌ Treating values as attributes.

    Alice

is a value.

    Name

is an attribute.

❌ Giving duplicate attribute names.

❌ Using one attribute to store multiple values.

    Phone

    9876543210,9988776655

Store one value per attribute.

------------------------------------------------------------------------

# 18. Interview Questions

### Beginner

1.  What is an attribute?
2.  Attribute vs Column?
3.  What is a key attribute?

### Intermediate

1.  Stored vs Derived attribute?
2.  Nullable vs Mandatory attribute?

### Advanced

1.  What is an attribute domain?
2.  Why are constraints important?

------------------------------------------------------------------------

# 19. Practice Problems

1.  Identify all attributes for:

```{=html}
<!-- -->
```
    Student

2.  Classify each attribute as:

-   Key
-   Non-Key
-   Stored
-   Derived
-   Nullable
-   Mandatory

3.  Design suitable attributes for:

-   Employee
-   Product
-   Customer
-   Hospital

------------------------------------------------------------------------

# Revision Notes

    Relation
        ↓
    Attributes
        ↓
    Tuples

Quick Summary

    Attribute
    =
    Column

    Tuple
    =
    Row

    Relation
    =
    Table

Memory Trick

    A T R

    Attribute
    Tuple
    Relation

    ↓

    Column
    Row
    Table

Key Points

-   Attributes describe tuples.
-   Every attribute has a domain.
-   Attributes follow constraints.
-   One attribute stores one type of information.
-   Well-designed attributes improve data quality and reduce errors.

**Remember:**

> Attributes are the vocabulary of a database. They define what
> information can be stored, what values are valid, and how every tuple
> is interpreted. Choose them carefully, because poorly designed
> attributes have an impressive talent for haunting every future query.
