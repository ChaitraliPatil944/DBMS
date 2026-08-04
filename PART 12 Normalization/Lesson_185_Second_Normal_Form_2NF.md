# Lesson 185 --- Second Normal Form (2NF)

> **Part 12 --- Normalization**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What Second Normal Form (2NF) is
-   Why 2NF is important
-   Partial Functional Dependency
-   Rules of 2NF
-   Converting a table from 1NF to 2NF
-   Advantages and limitations
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

A table can satisfy **First Normal Form (1NF)** and still contain
redundant data.

Consider the following table:

  StudentID   CourseID   StudentName   CourseName
  ----------- ---------- ------------- ------------
  101         C101       Asha          DBMS
  101         C102       Asha          SQL
  102         C101       Rahul         DBMS

The table has atomic values, so it is in **1NF**, but notice that
**StudentName** and **CourseName** are repeated.

This happens because of **Partial Functional Dependency**.

------------------------------------------------------------------------

# 2. What is Second Normal Form?

A table is in **Second Normal Form (2NF)** if:

1.  It is already in **1NF**.
2.  Every non-key attribute is **fully functionally dependent** on the
    **entire primary key**.

``` text
1NF
 │
Remove Partial Dependency
 │
2NF
```

------------------------------------------------------------------------

# 3. What is Partial Functional Dependency?

A **Partial Functional Dependency** occurs when a non-key attribute
depends on only **part of a composite primary key**, instead of the
whole key.

Example:

``` text
(StudentID, CourseID)

↓

StudentID → StudentName

CourseID → CourseName
```

StudentName depends only on StudentID.

CourseName depends only on CourseID.

This violates **2NF**.

------------------------------------------------------------------------

# 4. Why Do We Need 2NF?

Without 2NF:

-   Duplicate information
-   Update anomalies
-   Insert anomalies
-   Delete anomalies

The same student and course information must be stored repeatedly.

------------------------------------------------------------------------

# 5. Converting to 2NF

## Before

  StudentID   CourseID   StudentName   CourseName
  ----------- ---------- ------------- ------------
  101         C101       Asha          DBMS
  101         C102       Asha          SQL

------------------------------------------------------------------------

## After

### Student

  StudentID   StudentName
  ----------- -------------
  101         Asha

------------------------------------------------------------------------

### Course

  CourseID   CourseName
  ---------- ------------
  C101       DBMS
  C102       SQL

------------------------------------------------------------------------

### Enrollment

  StudentID   CourseID
  ----------- ----------
  101         C101
  101         C102

Each fact is stored only once.

------------------------------------------------------------------------

# 6. Internal Transformation

``` text
Large Table
     │
Find Composite Key
     │
Detect Partial Dependency
     │
Split Tables
     │
Second Normal Form
```

------------------------------------------------------------------------

# 7. Advantages

-   Reduces redundancy
-   Removes partial dependencies
-   Improves consistency
-   Simplifies updates
-   Better database design

------------------------------------------------------------------------

# 8. Limitations

Even after 2NF:

-   Transitive dependencies may still exist.
-   Some redundancy can remain.

These are removed in **Third Normal Form (3NF)**.

------------------------------------------------------------------------

# 9. Real-World Example

University database:

Instead of repeating department names for every student,

Create:

``` text
Student

Course

Enrollment
```

Relationships replace duplication.

------------------------------------------------------------------------

# 10. Best Practices

-   Use composite keys only when appropriate.
-   Identify all functional dependencies.
-   Separate attributes that depend on part of a composite key.
-   Verify the table is already in 1NF.

------------------------------------------------------------------------

# 11. Common Mistakes

❌ Assuming every 1NF table is automatically in 2NF.

❌ Ignoring composite primary keys.

❌ Confusing full and partial functional dependency.

------------------------------------------------------------------------

# 12. Interview Questions

### Beginner

1.  What is 2NF?
2.  What is Partial Functional Dependency?

### Intermediate

1.  Why must a table be in 1NF before 2NF?
2.  How do you convert a table to 2NF?

### Advanced

1.  Explain Full vs Partial Functional Dependency.
2.  Can a table without a composite key violate 2NF?

------------------------------------------------------------------------

# 13. Practice Problems

1.  Identify partial dependencies in a table.
2.  Convert a table from 1NF to 2NF.
3.  Explain why StudentName violates 2NF.
4.  Design Student, Course, and Enrollment tables.

------------------------------------------------------------------------

# Revision Notes

``` text
1NF
 │
Remove Partial Dependency
 │
2NF
```

## Memory Trick

``` text
2NF

=

Two Rules

1. Already in 1NF

2. Full Dependency
```

## Key Points

-   2NF builds upon 1NF.
-   It removes partial functional dependencies.
-   Every non-key attribute must depend on the entire primary key.
-   It reduces redundancy and anomalies.
-   Transitive dependencies may still remain.

------------------------------------------------------------------------

# Final Takeaway

Second Normal Form improves database design by ensuring that every
non-key attribute depends on the complete primary key rather than only
part of it. This eliminates partial dependencies, reduces duplication,
and prepares the database for Third Normal Form, where transitive
dependencies are removed.
