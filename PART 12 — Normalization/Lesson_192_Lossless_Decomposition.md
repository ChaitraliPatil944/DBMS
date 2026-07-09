# Lesson 192 --- Lossless Decomposition

> **Part 12 --- Normalization**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What Lossless Decomposition is
-   Why decomposition is required
-   Lossless vs Lossy decomposition
-   Conditions for a lossless decomposition
-   Relationship with normalization
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Normalization often splits one large table into multiple smaller tables.

A question naturally arises:

> Can we reconstruct the original table correctly?

If the answer is **yes**, the decomposition is **lossless**.

------------------------------------------------------------------------

# 2. What is Decomposition?

**Decomposition** is the process of breaking a relation into two or more
smaller relations.

``` text
Large Table
     │
 Split
     │
Smaller Tables
```

The goal is to reduce redundancy while preserving information.

------------------------------------------------------------------------

# 3. What is Lossless Decomposition?

A decomposition is **lossless** if joining the decomposed tables
recreates **exactly** the original relation.

``` text
Original Table
      │
 Decompose
      │
Join Tables
      │
Original Table Again
```

No rows are lost. No extra rows are created.

------------------------------------------------------------------------

# 4. What is Lossy Decomposition?

A decomposition is **lossy** if joining the tables does **not** recreate
the original relation.

Problems include:

-   Missing rows
-   Extra (spurious) rows
-   Incorrect relationships

------------------------------------------------------------------------

# 5. Example of Lossless Decomposition

Original table:

  StudentID   StudentName   DepartmentID
  ----------- ------------- --------------
  101         Asha          D01
  102         Rahul         D02

Decompose into:

### Student

  StudentID   StudentName
  ----------- -------------

### StudentDepartment

  StudentID   DepartmentID
  ----------- --------------

Joining on `StudentID` restores the original table.

------------------------------------------------------------------------

# 6. Example of Lossy Decomposition

Improper decomposition:

### Student

| StudentID \| StudentName \|

### Department

| DepartmentID \| DepartmentName \|

There is no relationship connecting students to departments.

Joining these tables may produce incorrect combinations.

------------------------------------------------------------------------

# 7. Condition for Lossless Decomposition

A decomposition is lossless when the common attribute(s) form a key in
at least one of the decomposed relations.

``` text
Relation R

↓

R1
  ∩
R2

↓

Common Attribute

↓

Key?

 │        │
Yes      No
 │        │
Lossless Lossy
```

------------------------------------------------------------------------

# 8. Why is Lossless Decomposition Important?

-   Preserves all information
-   Prevents spurious tuples
-   Supports correct joins
-   Maintains database integrity

------------------------------------------------------------------------

# 9. Lossless vs Lossy

  Lossless                     Lossy
  ---------------------------- ------------------------------------
  Original table recovered     Original table not fully recovered
  No extra rows                Spurious rows may appear
  Preferred in normalization   Should be avoided

------------------------------------------------------------------------

# 10. Real-World Example

Hospital database:

Instead of storing patient, doctor, and department information in one
large table, split them into related tables while ensuring they can
always be joined back correctly.

------------------------------------------------------------------------

# 11. Best Practices

-   Verify every decomposition is lossless.
-   Preserve keys during decomposition.
-   Test joins after normalization.
-   Avoid unnecessary decomposition.

------------------------------------------------------------------------

# 12. Common Mistakes

❌ Breaking relationships between tables.

❌ Ignoring common key attributes.

❌ Assuming every decomposition is lossless.

------------------------------------------------------------------------

# 13. Interview Questions

### Beginner

1.  What is decomposition?
2.  What is a lossless decomposition?

### Intermediate

1.  Differentiate lossless and lossy decomposition.
2.  Why is lossless decomposition important?

### Advanced

1.  State the condition for a lossless decomposition.
2.  What are spurious tuples?

------------------------------------------------------------------------

# 14. Practice Problems

1.  Identify whether a decomposition is lossless.
2.  Convert a relation into two lossless relations.
3.  Explain why lossy decomposition is dangerous.
4.  Compare lossless and lossy decomposition.

------------------------------------------------------------------------

# Revision Notes

``` text
Original Relation
      │
Decompose
      │
Join Back
      │
Same Data?
 │        │
Yes      No
 │        │
Lossless Lossy
```

## Memory Trick

``` text
LOSSLESS

Lose

Nothing

After

Joining
```

## Key Points

-   Decomposition splits a relation into smaller relations.
-   Lossless decomposition preserves all information.
-   Lossy decomposition creates incorrect or missing data.
-   Keys play a critical role in achieving lossless joins.
-   Good normalization always aims for lossless decomposition.

------------------------------------------------------------------------

# Final Takeaway

Lossless decomposition is one of the most important goals of
normalization. Every time a table is split into smaller tables, the
database designer must ensure that the original information can be
reconstructed perfectly using joins. A normalized design is only
successful when decomposition removes redundancy **without losing
information or creating incorrect relationships**.
