# Lesson 063 --- Foreign Key

> **Part 04 --- Relational Model**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What a Foreign Key is
-   Why Foreign Keys are needed
-   Parent Table and Child Table
-   Referential Integrity
-   Foreign Key vs Primary Key
-   ON DELETE and ON UPDATE actions
-   SQL implementation
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Imagine a university database.

There are two tables:

    Student
    Course

A student enrolls in a course.

How does the database know **which student belongs to which course?**

The answer is a **Foreign Key**.

------------------------------------------------------------------------

# 2. Why Were Foreign Keys Introduced?

Without Foreign Keys:

-   Tables become isolated.
-   Invalid references can be stored.
-   Data consistency is lost.

Foreign Keys connect tables while preserving data integrity.

------------------------------------------------------------------------

# 3. What is a Foreign Key?

A **Foreign Key (FK)** is an attribute (or group of attributes) in one
table that refers to the **Primary Key** of another table.

It creates a relationship between two tables.

------------------------------------------------------------------------

# 4. Parent and Child Tables

    Student
    +-----------+------+
    |StudentID  |Name  |
    +-----------+------+

    Enrollment
    +-----------+----------+
    |EnrollID   |StudentID |
    +-----------+----------+

-   **Student** = Parent Table
-   **Enrollment** = Child Table
-   `Student.StudentID` = Primary Key
-   `Enrollment.StudentID` = Foreign Key

------------------------------------------------------------------------

# 5. How It Works

    Parent Table
    -------------------
    StudentID
    101
    102
    103

            │
            ▼

    Child Table
    -------------------
    EnrollID  StudentID
    1         101
    2         102

The child table can only reference existing parent values.

------------------------------------------------------------------------

# 6. Child-Friendly Analogy

Think of a school.

Every student has a **Roll Number**.

The attendance register stores only the roll number.

    Student Table

    Roll No = 15

    ↓

    Attendance Table

    Roll No = 15

The attendance record refers back to the student.

------------------------------------------------------------------------

# 7. SQL Example

``` sql
CREATE TABLE Student(
    StudentID INT PRIMARY KEY,
    Name VARCHAR(100)
);

CREATE TABLE Enrollment(
    EnrollmentID INT PRIMARY KEY,
    StudentID INT,
    CourseName VARCHAR(100),
    FOREIGN KEY(StudentID)
        REFERENCES Student(StudentID)
);
```

------------------------------------------------------------------------

# 8. Referential Integrity

**Referential Integrity** ensures that every Foreign Key value matches a
valid Primary Key value in the parent table.

Valid

    StudentID = 101 ✔

Invalid

    StudentID = 999 ✘

if 999 does not exist in the Student table.

------------------------------------------------------------------------

# 9. ON DELETE Actions

## RESTRICT / NO ACTION

Prevent deletion if child records exist.

    Student
       │
    Enrollment

    Delete Student ❌

------------------------------------------------------------------------

## CASCADE

Deleting the parent automatically deletes related child rows.

    Delete Student

    ↓

    Delete Enrollment

------------------------------------------------------------------------

## SET NULL

Parent deleted.

Foreign Key becomes NULL.

    Enrollment

    StudentID = NULL

Requires the Foreign Key column to allow NULL values.

------------------------------------------------------------------------

## SET DEFAULT

Foreign Key becomes its default value.

(Only supported by some database systems.)

------------------------------------------------------------------------

# 10. ON UPDATE Actions

If the parent Primary Key changes:

-   CASCADE → Update child values automatically
-   RESTRICT → Prevent update
-   SET NULL → Child Foreign Key becomes NULL

------------------------------------------------------------------------

# 11. Foreign Key vs Primary Key

  Primary Key                Foreign Key
  -------------------------- -----------------------------------------
  Uniquely identifies rows   References another table
  One per table              Many can exist
  Cannot be NULL             May be NULL (business rules permitting)
  Must be unique             Duplicates allowed

------------------------------------------------------------------------

# 12. Real-World Examples

## Banking

    Customer
       │
    Account

CustomerID is a Foreign Key in Account.

------------------------------------------------------------------------

## Hospital

    Doctor
       │
    Appointment

DoctorID is a Foreign Key.

------------------------------------------------------------------------

## Library

    Book
       │
    Issue

BookID is a Foreign Key.

------------------------------------------------------------------------

## Online Shopping

    Customer
       │
    Order

CustomerID connects orders to customers.

------------------------------------------------------------------------

# 13. Common Mistakes

❌ Referencing a non-existent Primary Key.

❌ Deleting parent rows without considering child rows.

❌ Assuming Foreign Keys must be unique.

❌ Confusing Parent and Child tables.

------------------------------------------------------------------------

# 14. Interview Questions

### Beginner

1.  What is a Foreign Key?
2.  Why is it used?
3.  Can a table have multiple Foreign Keys?

### Intermediate

1.  Foreign Key vs Primary Key?
2.  What is Referential Integrity?

### Advanced

1.  Explain CASCADE, RESTRICT, SET NULL and NO ACTION.
2.  Can a Foreign Key reference a UNIQUE Candidate Key?

------------------------------------------------------------------------

# 15. Practice Problems

1.  Design Student and Enrollment tables using a Foreign Key.
2.  Create Customer and Order tables.
3.  Predict what happens when a parent row is deleted using:
    -   CASCADE
    -   RESTRICT
    -   SET NULL

------------------------------------------------------------------------

# Revision Notes

    Parent Table
          │
    Primary Key
          │
          ▼
    Foreign Key
          │
    Child Table

Memory Trick

    Primary Key

    =

    Identity

    Foreign Key

    =

    Reference

Key Points

-   A Foreign Key connects two tables.
-   It references a Primary Key (or another unique key).
-   It enforces Referential Integrity.
-   Multiple Foreign Keys can exist in one table.
-   ON DELETE and ON UPDATE rules control how related data behaves.

**Remember:**

> A Foreign Key is the glue that holds relational databases together.
> Individual tables store data, but Foreign Keys create meaningful
> relationships between them. Without them, a database is just a
> collection of disconnected tables pretending to cooperate.
