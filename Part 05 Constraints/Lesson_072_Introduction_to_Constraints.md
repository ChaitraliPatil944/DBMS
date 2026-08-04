# Lesson 072 --- Introduction to Constraints

> **Part 05 --- Constraints**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What database constraints are
-   Why constraints were introduced
-   Types of constraints
-   Importance of constraints
-   How constraints improve data quality
-   SQL examples
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Imagine a database that allows this data:

    Age = Banana
    Email = hello
    StudentID = NULL
    Salary = -5000

Technically, data is stored.

Practically, the database has become unreliable.

A DBMS needs rules to prevent invalid data.

These rules are called **Constraints**.

------------------------------------------------------------------------

# 2. What is a Constraint?

A **Constraint** is a rule enforced by the DBMS that restricts the
values allowed in a table.

Its purpose is to ensure that only **valid, meaningful, and consistent**
data is stored.

------------------------------------------------------------------------

# 3. Why Were Constraints Introduced?

Without constraints:

-   Duplicate records appear.
-   Missing values cause problems.
-   Invalid references are created.
-   Business rules are violated.

Constraints protect the integrity of the database automatically.

------------------------------------------------------------------------

# 4. Child-Friendly Analogy

Think of a school exam.

Rules:

    Name        → Mandatory
    Roll Number → Unique
    Marks        → 0–100

A student cannot submit:

    Marks = 250

The rules stop invalid entries.

Constraints work exactly the same way.

------------------------------------------------------------------------

# 5. Why Are Constraints Important?

Constraints help to:

-   Maintain data integrity
-   Prevent invalid data
-   Enforce business rules
-   Improve consistency
-   Reduce application bugs
-   Increase reliability

------------------------------------------------------------------------

# 6. Types of Constraints

``` text
Constraints
│
├── Domain Constraint
├── Key Constraint
├── Entity Integrity
├── Referential Integrity
├── NOT NULL
├── UNIQUE
├── PRIMARY KEY
├── FOREIGN KEY
├── CHECK
└── DEFAULT
```

These will be covered in the next lessons.

------------------------------------------------------------------------

# 7. Where Are Constraints Applied?

Constraints can be applied:

-   During table creation (`CREATE TABLE`)
-   After creation (`ALTER TABLE`)

Example:

``` sql
CREATE TABLE Student(
    StudentID INT PRIMARY KEY,
    Name VARCHAR(100) NOT NULL,
    Age INT CHECK (Age >= 16),
    Email VARCHAR(100) UNIQUE,
    Country VARCHAR(50) DEFAULT 'India'
);
```

------------------------------------------------------------------------

# 8. How Constraints Work

``` text
User Input
     │
     ▼
Constraint Check
     │
 ┌───┴────┐
 │        │
Valid   Invalid
 │        │
 ▼        ▼
Stored  Rejected
```

------------------------------------------------------------------------

# 9. Real-World Examples

## Banking

-   Account number must be unique.
-   Balance cannot violate business rules.

## Hospital

-   PatientID must be unique.
-   Blood group should belong to a valid domain.

## University

-   StudentID cannot be NULL.
-   Department should contain valid values.

## E-commerce

-   OrderID must be unique.
-   Order status should follow allowed values.

------------------------------------------------------------------------

# 10. Advantages

-   Better data quality
-   Automatic validation
-   Reduced redundancy
-   Stronger data integrity
-   Easier maintenance

------------------------------------------------------------------------

# 11. Common Mistakes

❌ Depending only on application code.

❌ Ignoring database-level validation.

❌ Assuming data types alone are enough.

Remember:

``` text
Data Type
=
How data is stored

Constraint
=
What data is allowed
```

------------------------------------------------------------------------

# 12. Interview Questions

### Beginner

1.  What is a database constraint?
2.  Why are constraints needed?
3.  Name different types of constraints.

### Intermediate

1.  Constraint vs Data Type?
2.  Why should validation exist in the database as well as the
    application?

### Advanced

1.  How do constraints improve data integrity?
2.  Can multiple constraints exist on one column? Explain.

------------------------------------------------------------------------

# 13. Practice Problems

1.  Identify suitable constraints for:

    -   Student
    -   Employee
    -   Product
    -   Bank Account

2.  Explain what happens if invalid data is inserted.

3.  Write a table that uses PRIMARY KEY, UNIQUE, NOT NULL, CHECK and
    DEFAULT.

------------------------------------------------------------------------

# Revision Notes

``` text
User Data
     │
Constraints
     │
Valid Database
```

Memory Trick

``` text
C I V

Constraints
Integrity
Validation
```

Key Points

-   Constraints are database rules.
-   They prevent invalid data.
-   They improve consistency and integrity.
-   Constraints are enforced automatically by the DBMS.
-   Multiple constraints can be combined on the same table.

------------------------------------------------------------------------

# Final Takeaway

Constraints are the **guardians of a database**. They ensure that every
row follows the rules defined by the business, not just by the
application. Even if an application contains a bug, well-designed
constraints can stop bad data before it spreads through the system. Good
databases trust rules more than assumptions, and for excellent reasons.
