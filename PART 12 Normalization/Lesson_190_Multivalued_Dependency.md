# Lesson 190 --- Multivalued Dependency (MVD)

> **Part 12 --- Normalization**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What a Multivalued Dependency (MVD) is
-   Why MVD occurs
-   MVD notation
-   Difference between Functional Dependency and MVD
-   How MVD affects normalization
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Consider a student who has multiple hobbies and speaks multiple
languages.

  Student   Hobby   Language
  --------- ------- ----------
  Asha      Chess   English
  Asha      Chess   Hindi
  Asha      Music   English
  Asha      Music   Hindi

The hobbies and languages are independent, but every possible
combination is stored.

This is a **Multivalued Dependency (MVD)**.

------------------------------------------------------------------------

# 2. What is a Multivalued Dependency?

A Multivalued Dependency exists when one attribute determines multiple
independent values of another attribute.

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

------------------------------------------------------------------------

# 3. Why Does MVD Occur?

MVD appears when:

-   One entity has multiple independent attributes.
-   Those attributes are unrelated to each other.
-   Every possible combination is stored.

------------------------------------------------------------------------

# 4. Functional Dependency vs Multivalued Dependency

  -----------------------------------------------------------------------
  Functional Dependency               Multivalued Dependency
  ----------------------------------- -----------------------------------
  A → B                               A ↠ B

  One value determines one value      One value determines multiple
                                      independent values

  Used in 2NF/3NF/BCNF                Used in 4NF
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# 5. Why is MVD a Problem?

Without handling MVD:

-   Duplicate combinations
-   Increased storage
-   Update anomalies
-   Insert anomalies
-   Delete anomalies

------------------------------------------------------------------------

# 6. Removing MVD

Before:

  Student   Hobby   Language
  --------- ------- ----------

After:

### StudentHobby

  Student   Hobby
  --------- -------

### StudentLanguage

  Student   Language
  --------- ----------

Independent facts are stored separately.

------------------------------------------------------------------------

# 7. Internal View

``` text
Entity
  │
Multiple Independent Facts
  │
MVD Detected
  │
Split Tables
  │
Reduced Redundancy
```

------------------------------------------------------------------------

# 8. Real-World Example

Employee database:

An employee can have:

-   Multiple skills
-   Multiple certifications

These are independent and should be stored in separate tables.

------------------------------------------------------------------------

# 9. Best Practices

-   Identify independent repeating facts.
-   Separate unrelated multivalued attributes.
-   Apply 4NF when MVD exists.
-   Avoid unnecessary decomposition.

------------------------------------------------------------------------

# 10. Common Mistakes

❌ Confusing MVD with Functional Dependency.

❌ Splitting related attributes unnecessarily.

❌ Ignoring redundant combinations.

------------------------------------------------------------------------

# 11. Interview Questions

### Beginner

1.  What is Multivalued Dependency?
2.  Write the notation for MVD.

### Intermediate

1.  Functional Dependency vs MVD?
2.  Why does MVD create redundancy?

### Advanced

1.  Explain how 4NF removes MVD.
2.  Give a real-world example of MVD.

------------------------------------------------------------------------

# 12. Practice Problems

1.  Identify MVD in a table.
2.  Convert a table with MVD into 4NF.
3.  Compare FD and MVD.
4.  Design separate tables for independent facts.

------------------------------------------------------------------------

# Revision Notes

``` text
Student
  │
↠ Hobby
↠ Language
  │
Independent Facts
  │
Separate Tables
```

## Memory Trick

``` text
MVD

=

Many

Values

Depend
```

## Key Points

-   MVD involves multiple independent values.
-   Notation: A ↠ B.
-   MVD is different from Functional Dependency.
-   4NF removes multivalued dependencies.
-   Splitting independent facts reduces redundancy.

------------------------------------------------------------------------

# Final Takeaway

Multivalued Dependency explains why some tables still contain redundant
combinations even after satisfying BCNF. Whenever one entity has
multiple independent sets of values, storing every combination wastes
space and complicates updates. Recognizing MVD is the key to
understanding Fourth Normal Form and designing cleaner relational
databases.
