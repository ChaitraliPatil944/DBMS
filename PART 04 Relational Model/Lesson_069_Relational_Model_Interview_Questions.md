# Lesson 069 --- Relational Model Interview Questions

> **Part 04 --- Relational Model**

------------------------------------------------------------------------

# Purpose

This lesson is a complete interview preparation guide for the
**Relational Model**. It covers beginner to advanced questions commonly
asked in university viva, technical interviews, and placement drives.

------------------------------------------------------------------------

# Section 1 --- Beginner Questions

### 1. What is the Relational Model?

**Answer:**\
The Relational Model is a logical database model proposed by Edgar F.
Codd in 1970 that organizes data into relations (tables) consisting of
rows (tuples) and columns (attributes).

------------------------------------------------------------------------

### 2. What is a Relation?

A relation is a table containing rows (tuples) and columns (attributes).

------------------------------------------------------------------------

### 3. What is a Tuple?

A tuple is a single row in a relation.

------------------------------------------------------------------------

### 4. What is an Attribute?

An attribute is a column that stores one type of information.

------------------------------------------------------------------------

### 5. What is a Domain?

A domain is the set of valid values an attribute can contain.

------------------------------------------------------------------------

### 6. Difference between Relation, Tuple and Attribute?

  Relation   Tuple   Attribute
  ---------- ------- -----------
  Table      Row     Column

------------------------------------------------------------------------

### 7. What is Degree?

Number of columns in a relation.

### 8. What is Cardinality?

Number of rows in a relation.

### 9. What is Relation Schema?

The blueprint or structure of a relation.

### 10. What is Relation Instance?

The actual data stored at a specific time.

------------------------------------------------------------------------

# Section 2 --- Keys

### 11. What is a Super Key?

Any attribute or combination of attributes that uniquely identifies a
row.

### 12. What is a Candidate Key?

A minimal Super Key.

### 13. What is a Primary Key?

The Candidate Key selected to uniquely identify every row.

### 14. What is an Alternate Key?

Candidate Keys that are not selected as the Primary Key.

### 15. What is a Foreign Key?

An attribute that references the Primary Key (or UNIQUE Candidate Key)
of another table.

### 16. What is a Composite Key?

A key formed using two or more attributes.

### 17. What is a Surrogate Key?

An artificial identifier with no business meaning.

------------------------------------------------------------------------

# Section 3 --- Comparison Questions

  -----------------------------------------------------------------------
  Question                    Key Difference
  --------------------------- -------------------------------------------
  Super Key vs Candidate Key  Extra attributes vs Minimal

  Candidate Key vs Primary    Eligible vs Selected
  Key                         

  Primary Key vs Foreign Key  Identifies vs References

  Natural vs Surrogate Key    Business value vs Artificial

  Composite Key vs Candidate  Multiple columns vs Minimal uniqueness
  Key                         

  Degree vs Cardinality       Columns vs Rows

  Schema vs Instance          Structure vs Data
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# Section 4 --- Conceptual Questions

### Why are Primary Keys important?

They uniquely identify rows and prevent duplicates.

### Why can't a Primary Key contain NULL?

Every row must always be identifiable.

### Can a table have multiple Candidate Keys?

Yes.

### Can a table have multiple Primary Keys?

No.

### Can a Foreign Key contain duplicate values?

Yes.

### Can a Foreign Key contain NULL?

Yes, if the business rules and column definition allow it.

------------------------------------------------------------------------

# Section 5 --- Referential Integrity

### What is Referential Integrity?

It ensures every Foreign Key references an existing parent row or is
NULL if permitted.

### What are orphan records?

Child rows that reference a parent row that no longer exists.

### Explain CASCADE.

Changes or deletions in the parent automatically propagate to child
rows.

### Explain RESTRICT / NO ACTION.

Prevent the parent operation while dependent child rows exist.

### Explain SET NULL.

The child Foreign Key becomes NULL after the parent change or deletion.

------------------------------------------------------------------------

# Section 6 --- Relational Algebra

### What is Relational Algebra?

A procedural query language forming the mathematical foundation of
relational databases.

### Difference between Selection and Projection?

  Selection      Projection
  -------------- -----------------
  Filters rows   Chooses columns

### Name the fundamental operators.

-   Selection (σ)
-   Projection (π)
-   Union (∪)
-   Difference (−)
-   Cartesian Product (×)
-   Rename (ρ)

------------------------------------------------------------------------

# Section 7 --- Scenario Questions

### Scenario 1

A student can enroll in many courses and a course has many students.

**Answer:** Use a junction table with a Composite Primary Key:

    (StudentID, CourseID)

------------------------------------------------------------------------

### Scenario 2

Why shouldn't Email be used as a Primary Key?

Because it can change.

Prefer a Surrogate Key and enforce email uniqueness with `UNIQUE`.

------------------------------------------------------------------------

### Scenario 3

Which key is best for Order Details?

    (OrderID, ProductID)

Composite Key.

------------------------------------------------------------------------

# Section 8 --- Tricky Questions

1.  Is every Candidate Key a Super Key? ✔ Yes.
2.  Is every Super Key a Candidate Key? ✘ No.
3.  Can a Composite Key be a Primary Key? ✔ Yes.
4.  Can a Candidate Key contain multiple columns? ✔ Yes.
5.  Is every UNIQUE column an Alternate Key? ✘ Not necessarily.

------------------------------------------------------------------------

# Section 9 --- Rapid Fire

-   Relation = Table
-   Tuple = Row
-   Attribute = Column
-   Domain = Allowed values
-   Degree = Columns
-   Cardinality = Rows
-   Super Key = Unique
-   Candidate Key = Minimal unique
-   Primary Key = Selected Candidate Key
-   Alternate Key = Remaining Candidate Keys
-   Foreign Key = Reference
-   Composite Key = Multiple columns
-   Surrogate Key = Artificial identifier

------------------------------------------------------------------------

# Section 10 --- Common Interview Mistakes

-   Confusing rows with columns.
-   Confusing degree with cardinality.
-   Assuming every UNIQUE column is automatically an Alternate Key.
-   Forgetting that Primary Keys cannot contain NULL values.
-   Confusing Composite Attributes with Composite Keys.

------------------------------------------------------------------------

# Final Interview Checklist

``` text
✓ Relation vs Table

✓ Tuple vs Attribute

✓ Degree vs Cardinality

✓ Schema vs Instance

✓ Domain

✓ Super Key

✓ Candidate Key

✓ Primary Key

✓ Alternate Key

✓ Foreign Key

✓ Composite Key

✓ Surrogate Key

✓ Referential Integrity

✓ Relational Algebra

✓ Selection vs Projection

✓ SQL equivalents
```

# Final Takeaway

If you can confidently explain every topic in this lesson **without
memorizing definitions**, you have built a solid understanding of the
Relational Model. Interviewers are rarely looking for textbook wording.
They want to see that you understand **why** these concepts exist, how
they connect, and where they are applied in real database systems.
