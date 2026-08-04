# Lesson 056 --- Tuples

> **Part 04 --- Relational Model**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What a Tuple is
-   Why the term "Tuple" is used
-   Tuple vs Row vs Record
-   Mathematical foundation
-   Properties of Tuples
-   Valid vs Invalid Tuples
-   SQL operations on tuples
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

A relation (table) is made up of **rows** and **columns**.

In the Relational Model, a **row** is formally called a **Tuple**.

    Relation (Table)

    +-----+-------+------+
    | ID  | Name  | Dept |
    +-----+-------+------+
    |101  |Alice  |CSE   |  ← Tuple
    |102  |Bob    |IT    |  ← Tuple
    +-----+-------+------+

------------------------------------------------------------------------

# 2. Why is it Called a Tuple?

The term comes from **Mathematics**, where a tuple is an **ordered
collection of values**.

A tuple in a database represents **one complete record**.

------------------------------------------------------------------------

# 3. What is a Tuple?

A **Tuple** is a single row in a relation.

It contains one value for each attribute.

Example

    Student

    (101, Alice, CSE, alice@example.com)

This entire row is one tuple.

------------------------------------------------------------------------

# 4. Tuple vs Row vs Record

  Term     Meaning
  -------- ------------------------
  Tuple    Formal database term
  Row      Common SQL term
  Record   General computing term

In most practical situations, they refer to the same thing.

------------------------------------------------------------------------

# 5. Structure of a Tuple

Relation

    Student

Tuple

    (StudentID, Name, Department)

    ↓

    (101, Alice, CSE)

Each value belongs to its corresponding attribute.

------------------------------------------------------------------------

# 6. Properties of a Tuple

A valid tuple must satisfy:

-   One value for every attribute
-   Values belong to the correct domain
-   Atomic (single) values
-   Follows all constraints
-   Represents one real-world object

------------------------------------------------------------------------

# 7. Valid Tuple

    +-----+-------+------+
    |101  |Alice  |CSE   |
    +-----+-------+------+

Reason:

-   All values are atomic
-   Correct data types
-   Complete record

------------------------------------------------------------------------

# 8. Invalid Tuple

    +-----+----------------+------+
    |101  |Alice,Bob       |CSE   |
    +-----+----------------+------+

Invalid because the Name attribute contains multiple values.

Another invalid example:

    +-----+-------+------+
    |ABC  |Alice  |999   |
    +-----+-------+------+

if `StudentID` should be numeric and `Department` should contain
department names.

------------------------------------------------------------------------

# 9. SQL Operations on Tuples

## Insert a Tuple

``` sql
INSERT INTO Student
VALUES (101,'Alice','CSE');
```

## Update a Tuple

``` sql
UPDATE Student
SET Department='AIML'
WHERE StudentID=101;
```

## Delete a Tuple

``` sql
DELETE FROM Student
WHERE StudentID=101;
```

------------------------------------------------------------------------

# 10. Real-World Examples

Library

    Book

    (BookID, Title, Author)

    ↓

    (201, DBMS, Korth)

Hospital

    Patient

    (301, Rahul, O+)

Bank

    Account

    (5001, Alice, 25000)

------------------------------------------------------------------------

# 11. Tuple and Constraints

Every tuple must satisfy:

-   Primary Key Constraint
-   Domain Constraint
-   NOT NULL Constraint
-   UNIQUE Constraint
-   Foreign Key Constraint (when applicable)

If any constraint is violated, the tuple is rejected.

------------------------------------------------------------------------

# 12. Common Mistakes

❌ Calling a column a tuple.

A tuple is always a **row**.

❌ Thinking a tuple can have missing mandatory values.

Constraints prevent invalid tuples.

❌ Confusing tuple with relation.

Relation = Entire table

Tuple = One row

------------------------------------------------------------------------

# 13. Interview Questions

### Beginner

1.  What is a tuple?
2.  Difference between tuple and relation?
3.  Tuple vs row?

### Intermediate

1.  What properties should a tuple satisfy?
2.  Why are tuples based on set theory?

### Advanced

1.  Can duplicate tuples exist?
2.  How do constraints affect tuples?

------------------------------------------------------------------------

# 14. Practice Problems

1.  Identify the tuples:

```{=html}
<!-- -->
```
    +-----+-------+------+
    |101  |Alice  |CSE   |
    |102  |Bob    |IT    |
    |103  |Neha   |ECE   |
    +-----+-------+------+

2.  Find the number of tuples.

3.  Decide whether each tuple is valid.

4.  Write SQL to insert, update and delete one tuple.

------------------------------------------------------------------------

# Revision Notes

    Relation
        ↓
    Collection of Tuples

    Tuple
        ↓
    One Row

    Attribute
        ↓
    One Column

Memory Trick

    Relation
    =
    Table

    Tuple
    =
    Row

    Attribute
    =
    Column

Quick Comparison

  Concept     Meaning
  ----------- --------------
  Relation    Entire table
  Tuple       One row
  Attribute   One column

**Remember:**

> A **Tuple** represents one complete record in a relation. Every tuple
> follows the rules of the relation, satisfies its constraints, and
> stores one real-world object's data. Individually they're simple.
> Collectively they become the database that spends its life answering
> everyone else's questions.
