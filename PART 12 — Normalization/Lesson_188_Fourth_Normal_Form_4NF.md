# Lesson 188 --- Fourth Normal Form (4NF)

> **Part 12 --- Normalization**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What Fourth Normal Form (4NF) is
-   Why 4NF is needed
-   What Multivalued Dependency (MVD) is
-   Rules of 4NF
-   How to convert a table into 4NF
-   Advantages and limitations
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

A table may satisfy BCNF but still contain unnecessary repetition
because one entity has **multiple independent facts**.

Example:

  Student   Hobby   Language
  --------- ------- ----------
  Asha      Chess   English
  Asha      Chess   Hindi
  Asha      Music   English
  Asha      Music   Hindi

Hobbies and languages are unrelated, but every combination is stored.

This redundancy is caused by a **Multivalued Dependency (MVD)**.

------------------------------------------------------------------------

# 2. What is Fourth Normal Form?

A table is in **Fourth Normal Form (4NF)** if:

1.  It is already in **BCNF**.
2.  It contains **no non-trivial multivalued dependencies**.

``` text
BCNF
  │
Remove MVD
  │
4NF
```

------------------------------------------------------------------------

# 3. What is a Multivalued Dependency?

A multivalued dependency exists when one attribute determines **multiple
independent values** of another attribute.

Notation:

``` text
A ↠ B
```

Read as:

> A multivalued determines B.

Example:

``` text
Student ↠ Hobby

Student ↠ Language
```

Hobbies and languages are independent.

------------------------------------------------------------------------

# 4. Why Do We Need 4NF?

Without 4NF:

-   Redundant combinations
-   Extra storage
-   Difficult updates
-   Higher chance of inconsistent data

------------------------------------------------------------------------

# 5. Converting to 4NF

### Before

  Student   Hobby   Language
  --------- ------- ----------

### After

#### StudentHobby

  Student   Hobby
  --------- -------
  Asha      Chess
  Asha      Music

#### StudentLanguage

  Student   Language
  --------- ----------
  Asha      English
  Asha      Hindi

Independent facts are stored separately.

------------------------------------------------------------------------

# 6. Internal Transformation

``` text
BCNF Table
     │
Find MVD
     │
Independent Facts?
   │          │
 No         Yes
  │          │
Keep     Split Tables
              │
             4NF
```

------------------------------------------------------------------------

# 7. 4NF vs BCNF

  -----------------------------------------------------------------------
  BCNF                                   4NF
  -------------------------------------- --------------------------------
  Removes functional dependency          Removes multivalued dependency
  anomalies                              anomalies

  Uses Functional Dependency             Uses Multivalued Dependency

  May still have redundant combinations  Eliminates independent
                                         combinations
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# 8. Real-World Example

Employee database:

One employee can have:

-   Multiple skills
-   Multiple certifications

Skills and certifications are independent.

Store them separately:

``` text
EmployeeSkill

EmployeeCertification
```

------------------------------------------------------------------------

# 9. Advantages

-   Removes redundant combinations
-   Improves consistency
-   Reduces storage waste
-   Simplifies maintenance

------------------------------------------------------------------------

# 10. Limitations

-   More tables
-   More joins
-   MVDs are less common in everyday systems

------------------------------------------------------------------------

# 11. Best Practices

-   Verify BCNF first.
-   Identify independent multivalued attributes.
-   Split unrelated repeating facts.
-   Avoid unnecessary decomposition.

------------------------------------------------------------------------

# 12. Common Mistakes

❌ Confusing Functional Dependency with Multivalued Dependency.

❌ Splitting tables when attributes are actually related.

❌ Assuming every BCNF table is automatically in 4NF.

------------------------------------------------------------------------

# 13. Interview Questions

### Beginner

1.  What is 4NF?
2.  What is a Multivalued Dependency?

### Intermediate

1.  Why is BCNF not always enough?
2.  How do you convert a table into 4NF?

### Advanced

1.  Give a real-world example of MVD.
2.  Differentiate Functional Dependency and Multivalued Dependency.

------------------------------------------------------------------------

# 14. Practice Problems

1.  Identify multivalued dependencies.
2.  Convert a BCNF table into 4NF.
3.  Compare BCNF and 4NF.
4.  Design separate tables for independent facts.

------------------------------------------------------------------------

# Revision Notes

``` text
BCNF
 │
Remove MVD
 │
4NF
```

## Memory Trick

``` text
4NF

Four

No

Multivalued

Facts Together
```

## Key Points

-   4NF builds on BCNF.
-   Removes multivalued dependencies.
-   Independent facts belong in separate tables.
-   Reduces redundant combinations.
-   Uses decomposition to improve consistency.

------------------------------------------------------------------------

# Final Takeaway

Fourth Normal Form addresses redundancy caused by multivalued
dependencies, a problem that BCNF does not solve. Whenever one entity
has multiple independent sets of values, 4NF recommends separating those
facts into different tables. This results in cleaner designs, lower
redundancy, and improved data integrity.
