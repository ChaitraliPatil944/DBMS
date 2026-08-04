# Lesson 195 --- Normalization Interview Questions

> **Part 12 --- Normalization**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will:

-   Revise all normalization concepts
-   Prepare for technical interviews
-   Answer scenario-based questions
-   Differentiate between normal forms confidently

------------------------------------------------------------------------

# 1. Beginner Questions

### Q1. What is normalization?

**Answer:** Normalization is the process of organizing data into
well-structured tables to reduce redundancy and improve data integrity.

------------------------------------------------------------------------

### Q2. Why is normalization required?

-   Reduces duplicate data
-   Eliminates anomalies
-   Improves consistency
-   Simplifies maintenance

------------------------------------------------------------------------

### Q3. What are the different normal forms?

-   1NF
-   2NF
-   3NF
-   BCNF
-   4NF
-   5NF

------------------------------------------------------------------------

### Q4. What are database anomalies?

-   Insert Anomaly
-   Update Anomaly
-   Delete Anomaly

------------------------------------------------------------------------

### Q5. What is data redundancy?

Repeated storage of the same information in multiple places.

------------------------------------------------------------------------

# 2. Intermediate Questions

### Q6. Explain 1NF.

Every column contains atomic values and there are no repeating groups.

------------------------------------------------------------------------

### Q7. Explain 2NF.

A table is in 2NF if:

-   It is already in 1NF.
-   Every non-key attribute depends on the whole primary key.

------------------------------------------------------------------------

### Q8. Explain 3NF.

A table is in 3NF if:

-   It is already in 2NF.
-   It has no transitive dependencies.

------------------------------------------------------------------------

### Q9. What is BCNF?

Every determinant must be a Super Key.

------------------------------------------------------------------------

### Q10. Differentiate 3NF and BCNF.

  -----------------------------------------------------------------------
  3NF                                 BCNF
  ----------------------------------- -----------------------------------
  Removes transitive dependency       Removes determinant anomalies

  Determinants need not always be     Every determinant is a Super Key
  Super Keys                          
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# 3. Advanced Questions

### Q11. What is a Functional Dependency?

A relationship where one attribute uniquely determines another.

------------------------------------------------------------------------

### Q12. What is a Multivalued Dependency?

One attribute determines multiple independent values of another
attribute.

------------------------------------------------------------------------

### Q13. What is Join Dependency?

A relation can be decomposed and reconstructed through lossless joins.

------------------------------------------------------------------------

### Q14. What is Lossless Decomposition?

Joining decomposed tables recreates exactly the original relation.

------------------------------------------------------------------------

### Q15. What is Dependency Preservation?

Functional dependencies remain enforceable after decomposition without
joining all tables.

------------------------------------------------------------------------

# 4. Scenario-Based Questions

### Scenario 1

A table stores multiple phone numbers in one column.

**Question:** Which normal form is violated?

**Answer:** 1NF.

------------------------------------------------------------------------

### Scenario 2

StudentName depends only on StudentID, while the primary key is
(StudentID, CourseID).

**Answer:** Partial Functional Dependency. Violates 2NF.

------------------------------------------------------------------------

### Scenario 3

DepartmentName depends on DepartmentID, which depends on StudentID.

**Answer:** Transitive Dependency. Violates 3NF.

------------------------------------------------------------------------

### Scenario 4

One employee has multiple independent skills and certifications.

**Answer:** Multivalued Dependency. Apply 4NF.

------------------------------------------------------------------------

### Scenario 5

A complex relation must be decomposed into multiple tables and
reconstructed exactly.

**Answer:** 5NF using Join Dependency.

------------------------------------------------------------------------

# 5. Rapid Fire

1.  What does FD stand for?
2.  What does MVD stand for?
3.  Which NF removes partial dependency?
4.  Which NF removes transitive dependency?
5.  Which NF introduces Super Keys?
6.  Which NF removes MVD?
7.  Which NF removes JD?
8.  Define determinant.
9.  Define candidate key.
10. What is a surrogate key?

------------------------------------------------------------------------

# 6. Interview Tips

-   Explain concepts with examples.
-   Draw simple dependency diagrams.
-   Mention why each normal form exists.
-   Compare adjacent normal forms.
-   Discuss trade-offs such as denormalization when appropriate.

------------------------------------------------------------------------

# Revision Sheet

``` text
1NF → Atomic Values

2NF → Remove Partial Dependency

3NF → Remove Transitive Dependency

BCNF → Every Determinant = Super Key

4NF → Remove Multivalued Dependency

5NF → Remove Join Dependency

Goals:
✓ Lossless Decomposition
✓ Dependency Preservation
```

## Final Takeaway

Normalization interview questions focus more on understanding than
memorization. If you can explain **why** each normal form exists,
identify the dependency involved, and demonstrate how a table is
decomposed, you'll be well prepared for technical interviews involving
relational database design.
