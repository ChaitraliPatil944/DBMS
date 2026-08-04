# Lesson 075 --- Entity Integrity Constraint

> **Part 05 --- Constraints**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What Entity Integrity is
-   Why Entity Integrity is important
-   Rules of Entity Integrity
-   Relationship with Primary Keys
-   Why Primary Keys cannot contain NULL values
-   SQL implementation
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Consider the following table:

``` text
Student

StudentID   Name
----------------------
101         Alice
NULL        Bob
103         Neha
```

How can the database uniquely identify **Bob**?

It cannot.

This problem is solved by the **Entity Integrity Constraint**.

------------------------------------------------------------------------

# 2. What is Entity Integrity?

**Entity Integrity** is a rule of the Relational Model stating:

> **Every table must have a Primary Key, and every Primary Key value
> must be UNIQUE and NOT NULL.**

This ensures every row has a valid identity.

------------------------------------------------------------------------

# 3. Why Do We Need Entity Integrity?

Without Entity Integrity:

-   Rows cannot be uniquely identified.
-   Duplicate identities may appear.
-   Relationships with other tables become unreliable.
-   Updates and deletes become ambiguous.

With Entity Integrity:

-   Every row has one clear identity.
-   Relationships remain accurate.
-   Data integrity is preserved.

------------------------------------------------------------------------

# 4. Child-Friendly Analogy

Imagine a school where every student receives a roll number.

``` text
Roll No.

101
102
103
```

Now imagine one student has:

``` text
Roll No. = NULL
```

Teachers cannot identify that student.

A database faces the same problem.

------------------------------------------------------------------------

# 5. Rules of Entity Integrity

A Primary Key:

-   Must be UNIQUE
-   Must NOT be NULL
-   Must identify exactly one row
-   Should remain stable

``` text
Primary Key
      │
Unique + NOT NULL
      │
Valid Entity
```

------------------------------------------------------------------------

# 6. Why Can't a Primary Key Be NULL?

`NULL` means:

> Unknown or Missing

If the identifier itself is unknown, the database cannot uniquely
identify the row.

Example:

``` text
StudentID

NULL
```

This violates Entity Integrity.

------------------------------------------------------------------------

# 7. SQL Implementation

``` sql
CREATE TABLE Student(
    StudentID INT PRIMARY KEY,
    Name VARCHAR(100) NOT NULL,
    Email VARCHAR(100) UNIQUE
);
```

The `PRIMARY KEY` constraint automatically enforces:

-   UNIQUE
-   NOT NULL

------------------------------------------------------------------------

# 8. Valid vs Invalid Data

### Valid

``` text
StudentID

101
102
103
```

### Invalid

``` text
StudentID

101
101
NULL
```

The duplicate and NULL values violate Entity Integrity.

------------------------------------------------------------------------

# 9. Entity Integrity vs Key Constraint

  Entity Integrity                    Key Constraint
  ----------------------------------- --------------------------------
  Applies to the Primary Key          Applies to key uniqueness
  Requires NOT NULL                   Focuses on uniqueness
  Ensures every row has an identity   Prevents duplicate identifiers

------------------------------------------------------------------------

# 10. Real-World Examples

## Banking

``` text
AccountNumber
```

Cannot be NULL.

------------------------------------------------------------------------

## Hospital

``` text
PatientID
```

Must always exist.

------------------------------------------------------------------------

## University

``` text
StudentID
```

Every student must have one.

------------------------------------------------------------------------

## E-commerce

``` text
OrderID
```

Each order requires a unique identifier.

------------------------------------------------------------------------

# 11. Advantages

-   Every row is identifiable.
-   Prevents anonymous records.
-   Supports Foreign Keys.
-   Improves consistency.
-   Simplifies querying and maintenance.

------------------------------------------------------------------------

# 12. Common Mistakes

❌ Allowing NULL values in identifiers.

❌ Using changing business values as Primary Keys.

❌ Assuming UNIQUE alone enforces Entity Integrity.

Remember:

``` text
PRIMARY KEY

=

UNIQUE

+

NOT NULL
```

------------------------------------------------------------------------

# 13. Interview Questions

### Beginner

1.  What is Entity Integrity?
2.  Why can't a Primary Key be NULL?
3.  Does PRIMARY KEY allow duplicates?

### Intermediate

1.  Entity Integrity vs Key Constraint?
2.  How is Entity Integrity enforced?

### Advanced

1.  Can Entity Integrity exist without a Primary Key?
2.  Why is Entity Integrity important for Referential Integrity?

------------------------------------------------------------------------

# 14. Practice Problems

1.  Identify Entity Integrity violations:

``` text
EmployeeID

101
NULL
101
```

2.  Design a Student table satisfying Entity Integrity.

3.  Explain why `UNIQUE` alone is insufficient.

------------------------------------------------------------------------

# Revision Notes

``` text
Entity Integrity
       │
Primary Key
       │
UNIQUE + NOT NULL
       │
Every Row Identifiable
```

## Memory Trick

``` text
E I

Entity

Identity
```

## Key Points

-   Every relation should have a Primary Key.
-   Primary Key values must be UNIQUE.
-   Primary Key values must never be NULL.
-   Entity Integrity guarantees every row has a unique identity.
-   `PRIMARY KEY` automatically enforces Entity Integrity.

------------------------------------------------------------------------

# Final Takeaway

Entity Integrity guarantees that every record in a relational database
has a clear, permanent identity. It is one of the fundamental rules that
makes relational databases reliable. If a row cannot be uniquely
identified, every relationship built on top of it becomes uncertain.
Databases dislike uncertainty even more than developers dislike
mysterious production bugs.
