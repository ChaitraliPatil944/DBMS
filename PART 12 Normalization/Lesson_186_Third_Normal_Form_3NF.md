# Lesson 186 --- Third Normal Form (3NF)

> **Part 12 --- Normalization**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What Third Normal Form (3NF) is
-   Why 3NF is important
-   Transitive Functional Dependency
-   Rules of 3NF
-   Converting a table from 2NF to 3NF
-   Advantages and limitations
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

A table may satisfy **2NF** but still contain redundant data because one
non-key attribute depends on another non-key attribute.

Example:

  StudentID   StudentName   DepartmentID   DepartmentName
  ----------- ------------- -------------- ------------------------
  101         Asha          D01            Computer Science
  102         Rahul         D02            Information Technology

`DepartmentName` depends on `DepartmentID`, not directly on `StudentID`.

This is called a **Transitive Dependency**.

------------------------------------------------------------------------

# 2. What is Third Normal Form?

A table is in **Third Normal Form (3NF)** if:

1.  It is already in **2NF**.
2.  It has **no transitive dependencies**.

``` text
2NF
 │
Remove Transitive Dependency
 │
3NF
```

------------------------------------------------------------------------

# 3. What is Transitive Dependency?

A transitive dependency occurs when:

``` text
A → B
B → C

Therefore

A → C
```

Here:

``` text
StudentID
     │
     ▼
DepartmentID
     │
     ▼
DepartmentName
```

`DepartmentName` depends indirectly on `StudentID`.

------------------------------------------------------------------------

# 4. Why Do We Need 3NF?

Without 3NF:

-   Data redundancy increases.
-   Updating department information requires multiple changes.
-   Inconsistent data may appear.
-   Storage is wasted.

------------------------------------------------------------------------

# 5. Converting 2NF to 3NF

## Before

  StudentID   StudentName   DepartmentID   DepartmentName
  ----------- ------------- -------------- ----------------

## After

### Student

  StudentID   StudentName   DepartmentID
  ----------- ------------- --------------

### Department

  DepartmentID   DepartmentName
  -------------- ----------------

Now each fact is stored only once.

------------------------------------------------------------------------

# 6. Internal Transformation

``` text
2NF Table
     │
Find Transitive Dependency
     │
Separate Dependent Data
     │
3NF Tables
```

------------------------------------------------------------------------

# 7. Real-World Example

Employee Database

Before:

``` text
EmployeeID
EmployeeName
DepartmentID
DepartmentName
ManagerName
```

After:

``` text
Employee
---------
EmployeeID
EmployeeName
DepartmentID

Department
----------
DepartmentID
DepartmentName
ManagerName
```

------------------------------------------------------------------------

# 8. Advantages

-   Removes transitive dependencies
-   Reduces redundancy
-   Improves consistency
-   Easier maintenance
-   Better integrity

------------------------------------------------------------------------

# 9. Limitations

Even after 3NF:

-   Certain anomalies may remain.
-   Some tables still violate BCNF.

BCNF is a stricter version of 3NF.

------------------------------------------------------------------------

# 10. Best Practices

-   Identify all functional dependencies.
-   Separate lookup information into independent tables.
-   Keep relationships simple.
-   Ensure the table is already in 2NF.

------------------------------------------------------------------------

# 11. Common Mistakes

❌ Confusing partial and transitive dependency.

❌ Assuming 2NF automatically satisfies 3NF.

❌ Storing lookup data repeatedly.

------------------------------------------------------------------------

# 12. Interview Questions

### Beginner

1.  What is 3NF?
2.  What is a transitive dependency?

### Intermediate

1.  How does 3NF improve database design?
2.  Differentiate 2NF and 3NF.

### Advanced

1.  Can a table be in 3NF but not BCNF?
2.  Explain transitive dependency using an example.

------------------------------------------------------------------------

# 13. Practice Problems

1.  Identify transitive dependencies.
2.  Convert a 2NF table into 3NF.
3.  Design Student and Department tables.
4.  Compare 2NF and 3NF.

------------------------------------------------------------------------

# Revision Notes

``` text
2NF
 │
Remove Transitive Dependency
 │
3NF
```

## Memory Trick

``` text
3NF

Three Rules

1. Already in 2NF

2. No Transitive Dependency
```

## Key Points

-   3NF builds on 2NF.
-   Removes transitive dependencies.
-   Non-key attributes should depend only on the key.
-   Reduces redundancy and anomalies.
-   BCNF is stricter than 3NF.

------------------------------------------------------------------------

# Final Takeaway

Third Normal Form eliminates transitive dependencies by ensuring non-key
attributes depend directly on the primary key and not on other non-key
attributes. This results in cleaner, more maintainable database designs
and prepares the database for the stricter rules of Boyce-Codd Normal
Form (BCNF).
