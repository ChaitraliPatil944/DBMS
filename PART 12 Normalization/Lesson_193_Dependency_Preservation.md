# Lesson 193 --- Dependency Preservation

> **Part 12 --- Normalization**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What Dependency Preservation is
-   Why it is important
-   Dependency Preservation vs Lossless Decomposition
-   How to check dependency preservation
-   Relationship with normalization
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

When a large table is decomposed into smaller tables, two goals must be
achieved:

1.  Lossless Decomposition
2.  Dependency Preservation

A good database design should satisfy both whenever possible.

------------------------------------------------------------------------

# 2. What is Dependency Preservation?

A decomposition is **dependency preserving** if all the original
functional dependencies can still be enforced using the decomposed
tables **without joining them back together**.

``` text
Original Relation
        │
Functional Dependencies
        │
Decompose
        │
Dependencies Still Enforced?
     │                 │
    Yes               No
     │                 │
Dependency         Not
Preserved      Preserved
```

------------------------------------------------------------------------

# 3. Why is Dependency Preservation Important?

Without dependency preservation:

-   Constraints become difficult to enforce.
-   Extra joins are needed for validation.
-   Updates become slower.
-   Database maintenance becomes harder.

------------------------------------------------------------------------

# 4. Example

Original relation:

  StudentID   StudentName   DepartmentID
  ----------- ------------- --------------

Functional Dependency:

``` text
StudentID → StudentName
StudentID → DepartmentID
```

After decomposition:

### Student

| StudentID \| StudentName \|

### StudentDepartment

| StudentID \| DepartmentID \|

Both dependencies can still be checked directly.

This decomposition is dependency preserving.

------------------------------------------------------------------------

# 5. Example of Non-Preserved Dependency

Suppose a dependency requires attributes spread across multiple
decomposed tables.

To verify it, the DBMS must first join the tables.

``` text
Dependency
      │
Need JOIN?
   │        │
 No        Yes
 │          │
Preserved  Not Preserved
```

------------------------------------------------------------------------

# 6. Dependency Preservation vs Lossless Decomposition

  Dependency Preservation                   Lossless Decomposition
  ----------------------------------------- ---------------------------
  Preserves functional dependencies         Preserves data
  Avoids unnecessary joins for validation   Avoids information loss
  Focuses on constraints                    Focuses on reconstruction

Both properties are desirable.

------------------------------------------------------------------------

# 7. Relationship with Normalization

``` text
Normalization
      │
Decomposition
      │
 ┌──────────────┬──────────────┐
 │              │
Lossless   Dependency
Decomposition Preservation
```

Good normalization aims for both.

------------------------------------------------------------------------

# 8. Real-World Example

Bank database:

-   Customer
-   Account
-   Branch

If dependencies such as:

``` text
AccountNo → BranchID
```

remain enforceable after decomposition, the design preserves
dependencies.

------------------------------------------------------------------------

# 9. Best Practices

-   Preserve important functional dependencies.
-   Verify dependencies before decomposition.
-   Aim for both dependency preservation and lossless joins.
-   Document business rules clearly.

------------------------------------------------------------------------

# 10. Common Mistakes

❌ Focusing only on lossless decomposition.

❌ Ignoring functional dependencies.

❌ Assuming every decomposition preserves dependencies.

------------------------------------------------------------------------

# 11. Interview Questions

### Beginner

1.  What is Dependency Preservation?
2.  Why is it important?

### Intermediate

1.  Dependency Preservation vs Lossless Decomposition?
2.  Why do joins matter for dependency checking?

### Advanced

1.  Can a decomposition be lossless but not dependency preserving?
2.  Why do designers try to achieve both properties?

------------------------------------------------------------------------

# 12. Practice Problems

1.  Check whether a decomposition preserves dependencies.
2.  Compare dependency preservation and lossless decomposition.
3.  Explain why dependency preservation improves performance.
4.  Give a practical example.

------------------------------------------------------------------------

# Revision Notes

``` text
Normalization
      │
Decompose
      │
Keep Data
(Lossless)
      │
Keep Rules
(Dependency Preservation)
```

## Memory Trick

``` text
DEPENDENCY

Keep

Rules

Without

Joining
```

## Key Points

-   Dependency preservation keeps functional dependencies enforceable.
-   It reduces unnecessary joins.
-   It complements lossless decomposition.
-   Good normalization aims for both properties.
-   It simplifies constraint enforcement.

------------------------------------------------------------------------

# Final Takeaway

Dependency Preservation ensures that after normalization, the database
can still enforce its original business rules without reconstructing the
entire relation. Along with lossless decomposition, it forms one of the
two primary goals of database normalization. Achieving both leads to
databases that are accurate, efficient, and easier to maintain.
