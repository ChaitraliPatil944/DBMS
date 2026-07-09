# Lesson 183 --- Functional Dependency

> **Part 12 --- Normalization**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What Functional Dependency (FD) is
-   Why Functional Dependency is important
-   Determinants and dependent attributes
-   Types of Functional Dependencies
-   How FD helps normalization
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Suppose every student has a unique StudentID.

``` text
StudentID  →  StudentName
```

If you know the StudentID, you can determine the StudentName.

This relationship is called a **Functional Dependency**.

------------------------------------------------------------------------

# 2. What is Functional Dependency?

A Functional Dependency (FD) is a relationship where the value of one
attribute uniquely determines the value of another attribute.

Notation:

``` text
A → B
```

Read as:

> A functionally determines B.

Here:

-   **A** = Determinant
-   **B** = Dependent Attribute

------------------------------------------------------------------------

# 3. Why is Functional Dependency Important?

Functional Dependencies help us:

-   Identify redundancy
-   Detect anomalies
-   Find candidate keys
-   Perform normalization
-   Design better databases

Without FD, normalization is impossible.

------------------------------------------------------------------------

# 4. Example

Student Table

  StudentID   StudentName   Department
  ----------- ------------- ------------
  101         Asha          CSE
  102         Rahul         IT

Functional Dependencies:

``` text
StudentID → StudentName

StudentID → Department
```

StudentID uniquely determines the remaining values.

------------------------------------------------------------------------

# 5. Determinant vs Dependent

``` text
StudentID
     │
Determines
     ▼
StudentName
```

The left side is the **determinant**.

The right side is the **dependent**.

------------------------------------------------------------------------

# 6. Types of Functional Dependency

## Full Functional Dependency

The entire key is required.

``` text
(StudentID, CourseID) → Grade
```

Neither attribute alone can determine Grade.

------------------------------------------------------------------------

## Partial Functional Dependency

Only part of a composite key determines an attribute.

``` text
(StudentID, CourseID)

↓

StudentID → StudentName
```

This leads to violations of Second Normal Form (2NF).

------------------------------------------------------------------------

## Transitive Functional Dependency

One non-key attribute determines another.

``` text
StudentID → DepartmentID

DepartmentID → DepartmentName

Therefore

StudentID → DepartmentName
```

This violates Third Normal Form (3NF).

------------------------------------------------------------------------

# 7. Real-World Example

Employee Table

  EmployeeID   EmployeeName   Department
  ------------ -------------- ------------

``` text
EmployeeID → EmployeeName

EmployeeID → Department
```

EmployeeID uniquely identifies each employee.

------------------------------------------------------------------------

# 8. How FD Helps Normalization

``` text
Find Functional Dependencies
           │
Identify Keys
           │
Detect Redundancy
           │
Apply Normal Forms
```

Every normal form is based on analyzing functional dependencies.

------------------------------------------------------------------------

# 9. Best Practices

-   Identify functional dependencies before creating tables.
-   Use stable attributes as determinants.
-   Avoid storing attributes that depend transitively on non-key
    columns.
-   Document important dependencies.

------------------------------------------------------------------------

# 10. Common Mistakes

❌ Confusing correlation with dependency.

❌ Assuming every attribute determines every other attribute.

❌ Ignoring composite keys.

❌ Missing transitive dependencies.

------------------------------------------------------------------------

# 11. Interview Questions

### Beginner

1.  What is Functional Dependency?
2.  What is a determinant?
3.  Write the notation for Functional Dependency.

### Intermediate

1.  Full vs Partial Functional Dependency?
2.  What is Transitive Dependency?

### Advanced

1.  Why is Functional Dependency important for normalization?
2.  How does FD help identify candidate keys?

------------------------------------------------------------------------

# 12. Practice Problems

1.  Identify functional dependencies in a Student table.
2.  Find the determinant in a given dependency.
3.  Classify dependencies as Full, Partial, or Transitive.
4.  Explain why FD is essential for normalization.

------------------------------------------------------------------------

# Revision Notes

``` text
Functional Dependency

A → B

A = Determinant

B = Dependent

↓

Normalization
```

## Memory Trick

``` text
FD

=

Find

Dependencies

↓

Normalize
```

## Key Points

-   Functional Dependency describes attribute relationships.
-   A determinant uniquely identifies dependent attributes.
-   Types include Full, Partial, and Transitive Dependency.
-   Functional Dependencies are the foundation of normalization.
-   They help eliminate redundancy and anomalies.

------------------------------------------------------------------------

# Final Takeaway

Functional Dependency is the backbone of database normalization. Before
a database can be transformed into well-structured normal forms, the
relationships between attributes must be understood. Once you can
identify functional dependencies, understanding 1NF, 2NF, 3NF, and BCNF
becomes much easier because each normal form is built on these
relationships.
