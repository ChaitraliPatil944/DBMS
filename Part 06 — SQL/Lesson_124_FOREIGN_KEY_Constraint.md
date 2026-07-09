# Lesson 124 --- FOREIGN KEY Constraint

> **Part 06 --- Structured Query Language (SQL)**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What a FOREIGN KEY is
-   Why FOREIGN KEY is important
-   Parent and Child tables
-   Referential Integrity
-   Creating FOREIGN KEY constraints
-   ON DELETE and ON UPDATE actions
-   Best practices
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Imagine an online store.

Every order belongs to a customer.

``` text
Customer
   │
Places
   │
Order
```

An order cannot belong to a customer that does not exist.

A **FOREIGN KEY** enforces this rule.

------------------------------------------------------------------------

# 2. What is a FOREIGN KEY?

A **FOREIGN KEY** is a constraint that creates a relationship between
two tables.

It references the PRIMARY KEY (or UNIQUE key) of another table.

``` text
Parent Table
PRIMARY KEY
     │
FOREIGN KEY
     │
Child Table
```

------------------------------------------------------------------------

# 3. Why Do We Need FOREIGN KEY?

Without a FOREIGN KEY:

``` text
OrderID  CustomerID
-------------------
101      9999
```

If Customer 9999 does not exist, the order becomes invalid.

A FOREIGN KEY prevents such inconsistent data.

------------------------------------------------------------------------

# 4. Parent and Child Tables

``` text
Customer
---------
CustomerID (PK)

        │

        ▼

Orders
-------
OrderID
CustomerID (FK)
```

-   Parent table contains the referenced key.
-   Child table stores the foreign key.

------------------------------------------------------------------------

# 5. Referential Integrity

**Referential Integrity** means relationships between tables remain
valid.

Rules:

-   A foreign key value must match an existing parent key (or be NULL if
    allowed).
-   Parent records cannot usually be deleted while child records still
    reference them, unless a configured action allows it.

------------------------------------------------------------------------

# 6. Creating a FOREIGN KEY

``` sql
CREATE TABLE Customer
(
    CustomerID INT PRIMARY KEY,
    Name VARCHAR(100)
);

CREATE TABLE Orders
(
    OrderID INT PRIMARY KEY,
    CustomerID INT,
    CONSTRAINT FK_Customer
    FOREIGN KEY (CustomerID)
    REFERENCES Customer(CustomerID)
);
```

------------------------------------------------------------------------

# 7. ON DELETE Actions

## RESTRICT / NO ACTION

Prevent deletion of the parent row if related child rows exist.

## CASCADE

Deleting the parent automatically deletes related child rows.

``` text
Customer Deleted
      │
CASCADE
      │
Orders Deleted
```

## SET NULL

The child foreign key becomes `NULL` (if the column allows NULL).

------------------------------------------------------------------------

# 8. ON UPDATE Actions

If a parent key changes:

-   CASCADE → Child keys update automatically.
-   RESTRICT / NO ACTION → Prevent the update.
-   SET NULL → Child key becomes NULL (DBMS dependent).

------------------------------------------------------------------------

# 9. Internal Working

``` text
INSERT / UPDATE
      │
Check Parent Key
      │
Exists?
 ┌────┴────┐
 │         │
Yes        No
 │         │
Stored   Error
```

------------------------------------------------------------------------

# 10. FOREIGN KEY vs PRIMARY KEY

  PRIMARY KEY                FOREIGN KEY
  -------------------------- --------------------------
  Uniquely identifies rows   References another table
  One per table              Multiple allowed
  Cannot be NULL             May allow NULL
  Parent identifier          Relationship link

------------------------------------------------------------------------

# 11. Real-World Example

``` text
Student
--------
StudentID (PK)

Enrollment
----------
EnrollmentID (PK)
StudentID (FK)
```

Every enrollment must belong to an existing student.

------------------------------------------------------------------------

# 12. Best Practices

-   Always define meaningful relationships.
-   Index foreign key columns for faster joins.
-   Choose ON DELETE actions carefully.
-   Avoid orphan records.

------------------------------------------------------------------------

# 13. Common Mistakes

❌ Inserting child rows before parent rows.

❌ Deleting parent rows without considering child records.

❌ Ignoring referential integrity.

❌ Using CASCADE without understanding its impact.

------------------------------------------------------------------------

# 14. Interview Questions

### Beginner

1.  What is a FOREIGN KEY?
2.  What is referential integrity?
3.  Parent table vs child table?

### Intermediate

1.  PRIMARY KEY vs FOREIGN KEY?
2.  Explain CASCADE and RESTRICT.

### Advanced

1.  Why are foreign keys important in normalization?
2.  Why are foreign key columns often indexed?

------------------------------------------------------------------------

# 15. Practice Problems

1.  Create Customer and Orders tables with a FOREIGN KEY.
2.  Demonstrate ON DELETE CASCADE.
3.  Compare PRIMARY KEY and FOREIGN KEY.
4.  Explain referential integrity with an example.

------------------------------------------------------------------------

# Revision Notes

``` text
Parent Table
    │
PRIMARY KEY
    │
FOREIGN KEY
    │
Child Table
```

## Memory Trick

``` text
FOREIGN KEY

=

Forms

Organized

Relationships

Ensuring

Integrity

Globally

Now
```

## Key Points

-   FOREIGN KEY connects related tables.
-   It references a PRIMARY KEY or UNIQUE key.
-   It enforces referential integrity.
-   Parent and child tables remain consistent.
-   ON DELETE and ON UPDATE define relationship behavior.

------------------------------------------------------------------------

# Final Takeaway

The FOREIGN KEY is what transforms separate tables into a relational
database. It protects relationships by ensuring that child records
always point to valid parent records. Features such as `CASCADE`,
`RESTRICT`, and `SET NULL` allow you to control how those relationships
behave when data changes, making FOREIGN KEY constraints one of the most
important tools for maintaining consistent and reliable databases.
