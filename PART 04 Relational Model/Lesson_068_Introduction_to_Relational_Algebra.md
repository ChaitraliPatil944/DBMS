# Lesson 068 --- Introduction to Relational Algebra

> **Part 04 --- Relational Model**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What Relational Algebra is
-   Why it was invented
-   History of Relational Algebra
-   Procedural query language
-   Relation between Relational Algebra and SQL
-   Fundamental operators
-   Derived operators overview
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Imagine a library containing millions of books.

A user asks:

> "Show all books written by Codd."

How does the database know **how** to retrieve the answer?

Before SQL became popular, databases used a mathematical language called
**Relational Algebra** to describe database operations.

------------------------------------------------------------------------

# 2. History

In 1970, **Edgar F. Codd** introduced the Relational Model.

Along with it, he proposed **Relational Algebra**, a formal mathematical
language for manipulating relations (tables).

SQL was later developed using many of these ideas.

------------------------------------------------------------------------

# 3. What is Relational Algebra?

**Relational Algebra** is a **procedural query language**.

Procedural means:

> You specify **what** data you want **and how** to obtain it.

Input:

    Relation(s)

Output:

    Another Relation

Every operation produces a new relation.

------------------------------------------------------------------------

# 4. Why Do We Need It?

Relational Algebra provides:

-   Mathematical foundation for SQL
-   Query optimization
-   Logical query processing
-   Formal database theory

Database optimizers internally transform SQL into algebra-like
operations.

------------------------------------------------------------------------

# 5. Child-Friendly Analogy

Think of a basket of fruits.

    Apple
    Banana
    Orange
    Mango

Operations:

    Pick Apples
    Remove Bananas
    Combine Two Baskets

Relational Algebra performs similar operations on database tables.

------------------------------------------------------------------------

# 6. Fundamental Operators

    Relational Algebra

    ├── Selection (σ)
    ├── Projection (π)
    ├── Union (∪)
    ├── Set Difference (−)
    ├── Cartesian Product (×)
    └── Rename (ρ)

These are the basic building blocks.

------------------------------------------------------------------------

# 7. Selection (σ)

Selects **rows** satisfying a condition.

    σ Department='CSE' (Student)

SQL Equivalent

``` sql
SELECT *
FROM Student
WHERE Department='CSE';
```

------------------------------------------------------------------------

# 8. Projection (π)

Selects specific **columns**.

    π Name, Department (Student)

SQL

``` sql
SELECT Name, Department
FROM Student;
```

------------------------------------------------------------------------

# 9. Union (∪)

Combines rows from two compatible relations.

    Student2025
          ∪
    Student2026

Equivalent to SQL `UNION`.

------------------------------------------------------------------------

# 10. Set Difference (−)

Returns rows present in one relation but not the other.

    Student
    −
    PlacedStudents

------------------------------------------------------------------------

# 11. Cartesian Product (×)

Combines every row of one relation with every row of another.

    Student × Course

If Student has 3 rows and Course has 4 rows:

    3 × 4 = 12 rows

------------------------------------------------------------------------

# 12. Rename (ρ)

Renames a relation or its attributes.

    ρ S(Student)

Useful for self-joins and readability.

------------------------------------------------------------------------

# 13. Derived Operators (Overview)

Built using fundamental operators.

-   Join (⨝)
-   Intersection (∩)
-   Division (÷)

These will be covered in later lessons.

------------------------------------------------------------------------

# 14. Relational Algebra vs SQL

  Relational Algebra      SQL
  ----------------------- ---------------------
  Procedural              Declarative
  Mathematical notation   English-like syntax
  Used in theory          Used in practice

------------------------------------------------------------------------

# 15. Real-World Example

Relation:

    Student

    ID  Name   Dept
    101 Alice  CSE
    102 Bob    IT
    103 Neha   CSE

Find CSE students.

Relational Algebra

    σ Dept='CSE'(Student)

SQL

``` sql
SELECT *
FROM Student
WHERE Dept='CSE';
```

------------------------------------------------------------------------

# 16. Why Is It Important?

Although developers write SQL, the database optimizer often converts
queries into algebraic operations before execution.

Understanding Relational Algebra helps explain:

-   Query execution
-   Optimization
-   Execution plans

------------------------------------------------------------------------

# 17. Common Mistakes

❌ Thinking Relational Algebra is obsolete.

❌ Confusing Selection with Projection.

Remember:

    Selection

    ↓

    Rows

    Projection

    ↓

    Columns

------------------------------------------------------------------------

# 18. Interview Questions

### Beginner

1.  What is Relational Algebra?
2.  Why is it procedural?
3.  Difference between Selection and Projection?

### Intermediate

1.  Relational Algebra vs SQL.
2.  Why is Relational Algebra important?

### Advanced

1.  Why do database optimizers use algebraic transformations?
2.  Explain Cartesian Product with an example.

------------------------------------------------------------------------

# 19. Practice Problems

1.  Write Relational Algebra expressions for:

    -   Students in CSE
    -   Only student names
    -   Students not placed

2.  Convert each expression into SQL.

3.  Predict the size of a Cartesian Product.

------------------------------------------------------------------------

# Revision Notes

``` text
Relations
    │
Operators
    ▼
New Relation
```

Fundamental Operators

``` text
σ  Selection   → Rows
π  Projection  → Columns
∪  Union
−  Difference
×  Cartesian Product
ρ  Rename
```

Memory Trick

``` text
S P U D C R

Selection
Projection
Union
Difference
Cartesian
Rename
```

## Key Points

-   Relational Algebra is the mathematical foundation of SQL.
-   It is procedural.
-   Every operation returns another relation.
-   Fundamental operators build more complex operations.
-   Understanding it improves query optimization knowledge.

**Remember:**

> Relational Algebra is the language databases think in, even if
> developers speak SQL. Learning it reveals what happens beneath every
> query and why some queries run in milliseconds while others seem
> determined to benchmark your patience.
