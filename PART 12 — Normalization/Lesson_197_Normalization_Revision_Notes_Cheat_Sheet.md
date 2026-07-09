# Lesson 197 --- Normalization Revision Notes & Cheat Sheet

> **Part 12 --- Normalization**

------------------------------------------------------------------------

# Quick Definition

**Normalization** is the process of organizing data into well-structured
tables to reduce redundancy, eliminate anomalies, and improve data
integrity.

------------------------------------------------------------------------

# Why Normalize?

``` text
Repeated Data
      │
Redundancy
      │
Anomalies
      │
Normalization
      │
Better Database Design
```

Goals:

-   Reduce redundancy
-   Eliminate anomalies
-   Improve consistency
-   Maintain integrity
-   Simplify maintenance

------------------------------------------------------------------------

# Database Anomalies

  Anomaly          Description
  ---------------- -----------------------------------------------
  Insert Anomaly   Cannot insert data independently
  Update Anomaly   Same data must be updated in multiple places
  Delete Anomaly   Deleting one row removes valuable information

------------------------------------------------------------------------

# Functional Dependencies

``` text
A → B

A determines B
```

Types:

-   Full Functional Dependency
-   Partial Functional Dependency
-   Transitive Dependency

------------------------------------------------------------------------

# Higher Dependencies

``` text
Functional Dependency (FD)
        │
Multivalued Dependency (MVD)
        │
Join Dependency (JD)
```

------------------------------------------------------------------------

# Complete Normalization Flow

``` text
UNF
 │
1NF
 │
2NF
 │
3NF
 │
BCNF
 │
4NF
 │
5NF
```

------------------------------------------------------------------------

# Normal Forms Summary

  Normal Form   Removes
  ------------- --------------------------------------
  1NF           Repeating groups & non-atomic values
  2NF           Partial Functional Dependency
  3NF           Transitive Dependency
  BCNF          Determinants that are not Super Keys
  4NF           Multivalued Dependency
  5NF           Join Dependency

------------------------------------------------------------------------

# Memory Map

``` text
1NF → Atomic Values

2NF → Full Dependency

3NF → No Transitive Dependency

BCNF → Every Determinant = Super Key

4NF → Remove MVD

5NF → Remove JD
```

------------------------------------------------------------------------

# Dependency Cheat Sheet

``` text
FD

A → B

↓

2NF
3NF
BCNF

-------------------

MVD

A ↠ B

↓

4NF

-------------------

JD

JD(R1,R2,R3)

↓

5NF
```

------------------------------------------------------------------------

# Lossless Decomposition

``` text
Original Relation
      │
Decompose
      │
Join Again
      │
Original Relation Restored

✓ Lossless
```

Condition:

-   Common attribute should be a key in at least one decomposed
    relation.

------------------------------------------------------------------------

# Dependency Preservation

``` text
Original Rules
      │
Decompose
      │
Rules Still Enforced
      │
Dependency Preserved
```

Goal:

-   Preserve functional dependencies without joining all tables.

------------------------------------------------------------------------

# Comparison Table

  Feature                           1NF   2NF   3NF   BCNF   4NF   5NF
  -------------------------------- ----- ----- ----- ------ ----- -----
  Atomic Values                      ✓     ✓     ✓     ✓      ✓     ✓
  No Partial Dependency              ✗     ✓     ✓     ✓      ✓     ✓
  No Transitive Dependency           ✗     ✗     ✓     ✓      ✓     ✓
  Every Determinant is Super Key     ✗     ✗     ✗     ✓      ✓     ✓
  No MVD                             ✗     ✗     ✗     ✗      ✓     ✓
  No JD                              ✗     ✗     ✗     ✗      ✗     ✓

------------------------------------------------------------------------

# Interview Revision

Remember these answers:

-   1NF → Atomic values
-   2NF → Remove Partial Dependency
-   3NF → Remove Transitive Dependency
-   BCNF → Every Determinant is a Super Key
-   4NF → Remove Multivalued Dependency
-   5NF → Remove Join Dependency

------------------------------------------------------------------------

# Common Interview Questions

1.  What is normalization?
2.  Why is normalization important?
3.  Explain 1NF to 5NF.
4.  Difference between 3NF and BCNF.
5.  What is Functional Dependency?
6.  What is MVD?
7.  What is Join Dependency?
8.  What is Lossless Decomposition?
9.  What is Dependency Preservation?
10. When is denormalization used?

------------------------------------------------------------------------

# Last-Minute Checklist

``` text
✓ Understand anomalies

✓ Know FD, MVD and JD

✓ Memorize 1NF–5NF

✓ Explain BCNF

✓ Explain Lossless Decomposition

✓ Explain Dependency Preservation

✓ Solve normalization examples

✓ Compare adjacent normal forms
```

------------------------------------------------------------------------

# Memory Trick

``` text
Normalize Like a Ladder

1 → Atomic

2 → Partial

3 → Transitive

BC → Determinant

4 → MVD

5 → JD
```

------------------------------------------------------------------------

# Final Takeaway

Normalization is a step-by-step refinement process. Each normal form
removes a specific type of redundancy and improves the quality of a
relational database. In practice, **3NF** and **BCNF** are the most
commonly used, while **4NF** and **5NF** are applied for specialized
cases involving multivalued and join dependencies. Mastering the
concepts, dependencies, and decomposition techniques gives you a solid
foundation for database design, university exams, and technical
interviews.
