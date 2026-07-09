# Lesson 037 --- Relationships

> **Part 03 --- Entity Relationship Model**

------------------------------------------------------------------------

# Learning Objectives

After completing this lesson, you will understand:

-   What is a Relationship?
-   Why relationships are required
-   Relationship Set
-   Relationship Instance
-   Types of Relationships
-   Unary, Binary, Ternary and N-ary relationships
-   Identifying Relationships
-   Relationship Attributes
-   ER Diagram notation
-   SQL mapping
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

An entity tells us **what exists**.

A relationship tells us **how those entities are connected**.

Without relationships, a database is simply a collection of isolated
tables with no meaning.

------------------------------------------------------------------------

# 2. What is a Relationship?

A **Relationship** is an association between two or more entities.

Example:

    Student -------- Enrolls -------- Course

Here,

-   Student is an entity.
-   Course is an entity.
-   Enrolls is the relationship.

------------------------------------------------------------------------

# 3. Why Do We Need Relationships?

Imagine these tables:

    Student
    --------
    101  Alice

    Course
    -------
    DBMS

How do we know which student studies which course?

We don't.

Relationships solve this problem.

------------------------------------------------------------------------

# 4. Real-Life Analogy

Think of a family.

    Father -------- Parent Of -------- Child

Knowing only the people is not enough.

The relationship tells us how they are connected.

------------------------------------------------------------------------

# 5. ER Diagram Representation

Relationships are represented using a **diamond**.

    +---------+      /-----------\      +--------+
    | Student | ----<  Enrolls   >----- | Course |
    +---------+      \-----------/      +--------+

------------------------------------------------------------------------

# 6. Relationship Set vs Relationship Instance

**Relationship Set**

The collection of all possible relationships.

Example:

    Student ---- Enrolls ---- Course

**Relationship Instance**

One specific occurrence.

    Alice enrolled in DBMS

------------------------------------------------------------------------

# 7. Types of Relationships

Based on the number of participating entities:

    Relationships
    │
    ├── Unary
    ├── Binary
    ├── Ternary
    └── N-ary

------------------------------------------------------------------------

# 8. Unary (Recursive) Relationship

An entity is related to itself.

Example:

    Employee

    Manager Of

    Employee

    Employee
         |
     Manages
         |
    Employee

------------------------------------------------------------------------

# 9. Binary Relationship

The most common type.

Two entities participate.

    Student -------- Enrolls -------- Course

Examples:

-   Customer buys Product
-   Doctor treats Patient
-   Teacher teaches Subject

------------------------------------------------------------------------

# 10. Ternary Relationship

Three entities participate together.

Example:

    Doctor

    Patient

    Medicine

A doctor prescribes a medicine to a patient.

    Doctor
       \
        \
     Prescribes
       /     \
    Patient  Medicine

------------------------------------------------------------------------

# 11. N-ary Relationship

More than three entities participate.

Example:

    Supplier

    Warehouse

    Product

    Transport

    Invoice

These relationships are less common.

------------------------------------------------------------------------

# 12. Identifying Relationship

Used with **Weak Entities**.

Example:

    Employee

    Identifies

    Dependent

Without Employee, Dependent cannot exist.

------------------------------------------------------------------------

# 13. Relationship Attributes

Sometimes a relationship has its own attributes.

Example:

    Student ---- Enrolls ---- Course
                   |
              EnrollmentDate
                   Grade

EnrollmentDate does not belong only to Student or Course.

It belongs to the relationship.

------------------------------------------------------------------------

# 14. SQL Mapping

ER Diagram

    Student ---- Enrolls ---- Course

SQL

``` sql
CREATE TABLE Student(
    StudentID INT PRIMARY KEY,
    Name VARCHAR(100)
);

CREATE TABLE Course(
    CourseID INT PRIMARY KEY,
    CourseName VARCHAR(100)
);

CREATE TABLE Enrollment(
    StudentID INT,
    CourseID INT,
    EnrollmentDate DATE,
    PRIMARY KEY(StudentID, CourseID),
    FOREIGN KEY(StudentID) REFERENCES Student(StudentID),
    FOREIGN KEY(CourseID) REFERENCES Course(CourseID)
);
```

------------------------------------------------------------------------

# 15. Real-World Examples

### Library

    Student ---- Borrows ---- Book

### Banking

    Customer ---- Owns ---- Account

### Hospital

    Doctor ---- Treats ---- Patient

### Online Shopping

    Customer ---- Places ---- Order

------------------------------------------------------------------------

# 16. Common Mistakes

❌ Treating an attribute as a relationship.

    Age

Age is an attribute.

It is not a relationship.

❌ Using relationships where an entity should exist.

For example, **Order** is usually an entity, not simply a relationship.

------------------------------------------------------------------------

# 17. Interview Questions

### Beginner

1.  What is a relationship?
2.  How is a relationship represented in an ER diagram?
3.  What is a binary relationship?

### Intermediate

1.  Difference between relationship set and relationship instance?
2.  What is an identifying relationship?
3.  When do relationship attributes occur?

### Advanced

Design relationships for:

-   Hospital Management
-   Banking System
-   Airline Reservation
-   Food Delivery Application

------------------------------------------------------------------------

# 18. Practice Problems

Draw ER diagrams for:

1.  Customer purchases Product.
2.  Teacher teaches Subject.
3.  Doctor treats Patient.
4.  Student enrolls in Course.
5.  Employee manages Employee.

Identify:

-   Entities
-   Relationships
-   Relationship attributes (if any)

------------------------------------------------------------------------

# Revision Notes

    Entities
        │
    Connected By
        ▼
    Relationship

Types:

    Unary
    Binary
    Ternary
    N-ary

Notation:

    Rectangle = Entity

    Diamond = Relationship

    Oval = Attribute

**Remember**

> Entities describe **things**. Relationships describe **how those
> things interact**. A well-designed database depends on both.
