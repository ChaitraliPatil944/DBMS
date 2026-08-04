# Lesson 055 --- Relations

> **Part 04 --- Relational Model**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What a Relation is
-   Why Codd used the word "Relation"
-   Mathematical foundation
-   Relation vs Table
-   Relation Schema
-   Relation Instance
-   Degree of a Relation
-   Cardinality of a Relation
-   Properties of a Relation
-   Valid vs Invalid Relations
-   SQL examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

The Relational Model is built around one central concept:

> **Relation**

Although people often say "table", the formal database term is
**Relation**.

Every SQL table is based on the mathematical idea of a relation.

------------------------------------------------------------------------

# 2. Why is it Called a Relation?

The word **Relation** comes from **Mathematics**, specifically **Set
Theory**.

A relation represents a relationship between sets of values.

entity\["people","Edgar F. Codd","Relational model pioneer"\]
borrowed this mathematical idea to organize data in databases.

------------------------------------------------------------------------

# 3. What is a Relation?

A **Relation** is a collection of tuples (rows) having the same
attributes (columns).

In practice:

    Relation
        =
    Table

Example

    Student

    +-----------+---------+------+
    | ID | Name | Dept    |
    +-----------+---------+------+
    |101 | Alice| CSE     |
    |102 | Bob  | AIML    |
    |103 | Ravi | IT      |
    +-----------+---------+------+

The entire table is one **Relation**.

------------------------------------------------------------------------

# 4. Relation Terminology

    Relation
    │
    ├── Relation Name
    ├── Attributes (Columns)
    ├── Tuples (Rows)
    ├── Domain
    └── Keys

------------------------------------------------------------------------

# 5. Relation Schema

A **Relation Schema** defines the structure of a relation.

It specifies:

-   Relation name
-   Attributes
-   Data types
-   Constraints

Notation

    Student(
    StudentID,
    Name,
    Department,
    Email
    )

The schema is the **blueprint**.

------------------------------------------------------------------------

# 6. Relation Instance

A **Relation Instance** is the actual data stored at a particular
moment.

Schema

    Student(ID, Name, Department)

Instance

    +-----+-------+------+
    |101  |Alice  |CSE   |
    |102  |Bob    |IT    |
    +-----+-------+------+

The schema rarely changes.

The instance changes whenever data is inserted, updated, or deleted.

------------------------------------------------------------------------

# 7. Degree of a Relation

The **Degree** of a relation is the number of attributes (columns).

Example

    Student

    ID
    Name
    Department
    Email
    Phone

Degree = **5**

Formula

    Degree
    =
    Number of Columns

------------------------------------------------------------------------

# 8. Cardinality of a Relation

The **Cardinality** of a relation is the number of tuples (rows).

Example

    Student

    101 Alice
    102 Bob
    103 Ravi
    104 Neha

Cardinality = **4**

Formula

    Cardinality
    =
    Number of Rows

------------------------------------------------------------------------

# 9. Degree vs Cardinality

  Degree              Cardinality
  ------------------- --------------------
  Number of Columns   Number of Rows
  Usually fixed       Changes frequently

Memory Trick

    Degree

    ↓

    Columns

    Cardinality

    ↓

    Rows

------------------------------------------------------------------------

# 10. Properties of a Relation

A valid relation follows these rules:

### 1. Unique Relation Name

Every relation has a unique name.

------------------------------------------------------------------------

### 2. Unique Attribute Names

No duplicate column names.

✔

    StudentID
    Name
    Department

✘

    Name
    Name
    Department

------------------------------------------------------------------------

### 3. Atomic Values

Each cell contains only one value.

✔

    Phone

    9876543210

✘

    Phone

    9876543210,9988776655

------------------------------------------------------------------------

### 4. Same Domain

Values in one column come from the same domain.

Example

    Age

    21
    19
    22

Not

    21
    Apple
    Blue

------------------------------------------------------------------------

### 5. No Duplicate Tuples

Duplicate rows are not allowed in a relation.

------------------------------------------------------------------------

### 6. Order of Rows Does Not Matter

    101 Alice

    102 Bob

is equivalent to

    102 Bob

    101 Alice

------------------------------------------------------------------------

### 7. Order of Columns Does Not Affect Meaning

Changing column order does not change the relation.

------------------------------------------------------------------------

# 11. Valid vs Invalid Relation

### Valid

    +----+-------+------+
    |ID  |Name   |Dept  |
    +----+-------+------+
    |101 |Alice  |CSE   |
    |102 |Bob    |IT    |
    +----+-------+------+

### Invalid

    +----+----------------------+
    |ID  |Phone                 |
    +----+----------------------+
    |101 |9876,9988             |
    +----+----------------------+

Reason:

Phone contains multiple values.

------------------------------------------------------------------------

# 12. SQL Example

``` sql
CREATE TABLE Student(
    StudentID INT PRIMARY KEY,
    Name VARCHAR(100),
    Department VARCHAR(50),
    Email VARCHAR(100)
);
```

This table represents one **Relation**.

------------------------------------------------------------------------

# 13. Real-World Examples

Library

    Book(
    BookID,
    Title,
    Author,
    Price
    )

Bank

    Account(
    AccountNo,
    Balance,
    Branch
    )

Hospital

    Patient(
    PatientID,
    Name,
    BloodGroup
    )

------------------------------------------------------------------------

# 14. Common Mistakes

❌ Confusing Relation with Relationship.

-   Relation → Table
-   Relationship → Association between tables/entities

❌ Confusing Degree with Cardinality.

Columns ≠ Rows.

------------------------------------------------------------------------

# 15. Interview Questions

### Beginner

1.  What is a Relation?
2.  Relation vs Table?
3.  What is Relation Schema?

### Intermediate

1.  Relation Schema vs Relation Instance?
2.  Degree vs Cardinality?

### Advanced

1.  Explain the properties of a Relation.
2.  Why must attribute values be atomic?

------------------------------------------------------------------------

# 16. Practice Problems

1.  Find the degree of:

```{=html}
<!-- -->
```
    Student(ID, Name, Dept, Email, Phone)

2.  A table has 8 columns and 250 rows.

Find:

-   Degree
-   Cardinality

3.  Identify whether each relation is valid or invalid and explain why.

------------------------------------------------------------------------

# Revision Notes

    Relation
    =
    Table

    Schema
    =
    Structure

    Instance
    =
    Current Data

    Degree
    =
    Columns

    Cardinality
    =
    Rows

Memory Map

    Relation
       │
       ├── Schema
       ├── Instance
       ├── Degree
       ├── Cardinality
       └── Properties

**Remember:**

> A **Relation** is the fundamental building block of the Relational
> Model. It is much more than a table on a screen. It follows
> mathematical rules that ensure data remains organized, consistent, and
> easy to query. Those rules may seem strict, but they are the reason
> your database doesn't quietly descend into chaos every Monday morning.
