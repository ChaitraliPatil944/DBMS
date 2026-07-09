# Lesson 071 --- Relational Model Revision Notes & Cheat Sheet

> **Part 04 --- Relational Model**

------------------------------------------------------------------------

# Purpose

This lesson is a **last-minute revision guide** for the entire
Relational Model chapter.

If you have only **20--30 minutes** before an exam or interview, revise
this lesson.

------------------------------------------------------------------------

# 1. Relational Model Flow

``` text
Real World
    │
ER Model
    │
Relational Model
    │
Relations (Tables)
    │
Tuples (Rows)
    │
Attributes (Columns)
    │
Domains
    │
Keys
    │
Relationships
    │
Relational Algebra
```

------------------------------------------------------------------------

# 2. Core Terminology

  Concept     Meaning
  ----------- -------------------------
  Relation    Table
  Tuple       Row
  Attribute   Column
  Domain      Allowed values
  Schema      Structure of a table
  Instance    Current data in a table

------------------------------------------------------------------------

# 3. Degree vs Cardinality

  Degree              Cardinality
  ------------------- -------------------
  Number of columns   Number of rows
  Usually fixed       Changes with data

**Memory Trick**

``` text
Degree  → Columns
Cardinality → Rows
```

------------------------------------------------------------------------

# 4. Properties of a Relation

-   Every relation has a unique name.
-   Every attribute has a unique name.
-   Attribute values are atomic.
-   Duplicate tuples are not allowed.
-   Order of rows does not matter.
-   Order of columns does not change the meaning.
-   Values in an attribute belong to the same domain.

------------------------------------------------------------------------

# 5. Domain Cheat Sheet

``` text
Domain
   │
Allowed Values
   │
Valid Data
```

Examples:

-   Age → 0--150
-   Semester → 1--8
-   Blood Group → {A+, A-, B+, B-, AB+, AB-, O+, O-}

------------------------------------------------------------------------

# 6. Complete Key Hierarchy

``` text
                Super Key
                    │
      Remove unnecessary attributes
                    ▼
             Candidate Key(s)
              ┌────────────┐
              ▼            ▼
      Primary Key    Alternate Key(s)

Composite Key
= Multiple attributes together

Foreign Key
= Reference to another table

Surrogate Key
= Artificial identifier

Natural Key
= Business identifier
```

------------------------------------------------------------------------

# 7. Key Comparison Table

  Key             Purpose
  --------------- ---------------------------------
  Super Key       Any unique combination
  Candidate Key   Minimal unique combination
  Primary Key     Selected Candidate Key
  Alternate Key   Remaining Candidate Keys
  Foreign Key     References another table
  Composite Key   Multiple columns identify a row
  Surrogate Key   Artificial identifier
  Natural Key     Business identifier

------------------------------------------------------------------------

# 8. Primary Key vs Foreign Key

  Primary Key        Foreign Key
  ------------------ --------------------------
  Identifies a row   References another row
  Unique             Duplicates allowed
  NOT NULL           May be NULL (if allowed)
  One per table      Many possible

------------------------------------------------------------------------

# 9. Referential Integrity

``` text
Parent Table
     │
Primary Key
     │
     ▼
Foreign Key
     │
Child Table
```

Rules:

-   Parent must exist first.
-   Child cannot reference a missing parent.
-   Prevent orphan records.

------------------------------------------------------------------------

# 10. ON DELETE Summary

  Action        Result
  ------------- --------------------------
  CASCADE       Delete child rows
  RESTRICT      Prevent delete
  NO ACTION     Reject invalid operation
  SET NULL      Child FK becomes NULL
  SET DEFAULT   Child FK becomes default

------------------------------------------------------------------------

# 11. Relational Algebra

## Fundamental Operators

  Symbol   Operation           Works On
  -------- ------------------- ----------------------
  σ        Selection           Rows
  π        Projection          Columns
  ∪        Union               Compatible relations
  −        Difference          Sets
  ×        Cartesian Product   Every combination
  ρ        Rename              Names

### Derived Operators

-   Join (⨝)
-   Intersection (∩)
-   Division (÷)

------------------------------------------------------------------------

# 12. Relational Algebra vs SQL

  Relational Algebra      SQL
  ----------------------- ---------------------
  Procedural              Declarative
  Mathematical notation   English-like syntax
  Foundation              Practical language

------------------------------------------------------------------------

# 13. Frequently Confused Concepts

  -----------------------------------------------------------------------
  Concept 1               Concept 2               Difference
  ----------------------- ----------------------- -----------------------
  Relation                Relationship            Table vs Association

  Tuple                   Attribute               Row vs Column

  Schema                  Instance                Structure vs Data

  Degree                  Cardinality             Columns vs Rows

  Composite Attribute     Composite Key           Attribute split vs
                                                  Multiple-key columns

  Candidate Key           Primary Key             Eligible vs Selected
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# 14. 30 Rapid-Fire Questions

1.  What is a relation?
2.  What is a tuple?
3.  What is an attribute?
4.  What is a domain?
5.  Define schema.
6.  Define instance.
7.  What is degree?
8.  What is cardinality?
9.  Define Super Key.
10. Define Candidate Key.
11. Define Primary Key.
12. Define Alternate Key.
13. Define Foreign Key.
14. Define Composite Key.
15. Define Surrogate Key.
16. What is a Natural Key?
17. What is Referential Integrity?
18. Parent vs Child table?
19. What is CASCADE?
20. What is RESTRICT?
21. What is SET NULL?
22. What is Selection?
23. What is Projection?
24. What is Union?
25. What is Difference?
26. What is Cartesian Product?
27. What is Rename?
28. SQL vs Relational Algebra?
29. Degree vs Cardinality?
30. Schema vs Instance?

------------------------------------------------------------------------

# 15. Exam-Day Checklist

``` text
✓ Relation, Tuple, Attribute

✓ Domain

✓ Degree & Cardinality

✓ Relation Schema & Instance

✓ Super Key

✓ Candidate Key

✓ Primary Key

✓ Alternate Key

✓ Foreign Key

✓ Composite Key

✓ Surrogate Key

✓ Referential Integrity

✓ ON DELETE actions

✓ Relational Algebra Operators

✓ SQL Equivalents
```

------------------------------------------------------------------------

# 16. Memory Map

``` text
Relational Model
│
├── Relation
├── Tuple
├── Attribute
├── Domain
├── Keys
│   ├── Super
│   ├── Candidate
│   ├── Primary
│   ├── Alternate
│   ├── Foreign
│   ├── Composite
│   └── Surrogate
├── Referential Integrity
└── Relational Algebra
```

------------------------------------------------------------------------

# Final Chapter Summary

🎉 Congratulations!

You have completed **Part 04 --- Relational Model**.

You now understand:

-   Relations, tuples, attributes, and domains
-   Every major database key
-   Referential integrity and relationships
-   Relational Algebra fundamentals
-   SQL concepts built upon the Relational Model
-   Interview-ready comparisons and terminology

The next chapter, **Part 05 --- Constraints**, builds directly on this
knowledge. You'll learn how databases enforce business rules using
**PRIMARY KEY, FOREIGN KEY, UNIQUE, NOT NULL, CHECK, DEFAULT**, and
other constraints. Designing tables is only half the battle. Constraints
ensure those tables continue behaving sensibly long after real users
start inserting wonderfully creative data.
