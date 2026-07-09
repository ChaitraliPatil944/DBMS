# Lesson 032 --- Strong Entity

> **Part 03 --- Entity Relationship Model**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What is a Strong Entity?
-   Why do we need Strong Entities?
-   Characteristics of Strong Entities
-   How to identify a Strong Entity
-   Strong Entity vs Weak Entity
-   Real-world examples
-   ER diagrams
-   SQL mapping
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

In the previous lesson, we learned that an **Entity** is anything about
which we store information.

However, not all entities are the same.

Some entities can exist independently.

Some cannot.

An entity that **can exist on its own** is called a **Strong Entity**.

------------------------------------------------------------------------

# 2. Definition

A **Strong Entity** is an entity that:

-   Exists independently.
-   Has its own Primary Key.
-   Can be uniquely identified without depending on another entity.

Simply put,

> A Strong Entity has its own identity.

------------------------------------------------------------------------

# 3. Why Was the Concept Introduced?

Imagine a college database.

There are:

    Student
    Teacher
    Course
    Department

Each has its own ID.

Even if no relationships exist, these entities still exist.

The ER Model needed a way to distinguish such independent entities from
dependent ones.

Hence, the concept of a **Strong Entity** was introduced.

------------------------------------------------------------------------

# 4. Real-Life Analogy

Imagine a city.

    City

    ├── Person
    ├── Car
    ├── Building

A person exists independently.

A building exists independently.

A car exists independently.

These are Strong Entities.

Now think of a **Parking Ticket**.

A parking ticket cannot exist unless a car exists.

That is **not** a Strong Entity.

------------------------------------------------------------------------

# 5. Characteristics

A Strong Entity:

✔ Exists independently

✔ Has a Primary Key

✔ Can participate in relationships

✔ Owns its own attributes

✔ Can exist even if related entities are deleted

------------------------------------------------------------------------

# 6. Representation in ER Diagram

A Strong Entity is represented by a **single rectangle**.

    +------------+
    |  Student   |
    +------------+

    +------------+
    |  Employee  |
    +------------+

    +------------+
    |  Product   |
    +------------+

------------------------------------------------------------------------

# 7. Example

University Database

    +------------+
    | Student    |
    +------------+
    | StudentID  |
    | Name       |
    | Branch     |
    +------------+

StudentID uniquely identifies every student.

Therefore,

Student is a Strong Entity.

------------------------------------------------------------------------

# 8. Another Example

Hospital Database

    +------------+
    | Doctor     |
    +------------+
    | DoctorID   |
    | Name       |
    | Specialty  |
    +------------+

Doctor has its own identity.

It is a Strong Entity.

------------------------------------------------------------------------

# 9. SQL Representation

ER Diagram

    +------------+
    | Student    |
    +------------+

becomes

``` sql
CREATE TABLE Student
(
    StudentID INT PRIMARY KEY,
    Name VARCHAR(100),
    Department VARCHAR(50)
);
```

The presence of a Primary Key makes it a Strong Entity.

------------------------------------------------------------------------

# 10. Strong Entity vs Weak Entity

  Strong Entity             Weak Entity
  ------------------------- --------------------------------------
  Exists independently      Depends on another entity
  Has its own Primary Key   Does not have a complete Primary Key
  Single rectangle          Double rectangle
  Can exist alone           Cannot exist alone

------------------------------------------------------------------------

# 11. Real-World Examples

## College

    Student

    Teacher

    Course

    Department

All are Strong Entities.

------------------------------------------------------------------------

## Banking

    Customer

    Branch

    Employee

    Account Type

------------------------------------------------------------------------

## E-Commerce

    Customer

    Product

    Seller

    Warehouse

------------------------------------------------------------------------

# 12. Common Mistakes

❌ Thinking every table is automatically a Strong Entity.

Not true.

Example:

    Order Item

Order Item usually depends on Order.

Therefore, it may be a Weak Entity.

------------------------------------------------------------------------

# 13. How to Identify a Strong Entity?

Ask these questions:

    Can it exist alone?

    ↓

    YES

    ↓

    Does it have its own identifier?

    ↓

    YES

    ↓

    Strong Entity

------------------------------------------------------------------------

# 14. Interview Questions

### Basic

1.  What is a Strong Entity?
2.  How is it represented?
3.  Does a Strong Entity require a Primary Key?

### Intermediate

1.  Can a Strong Entity participate in multiple relationships?
2.  Can a Strong Entity become a Weak Entity?

### Advanced

Design Strong Entities for:

-   Railway Reservation
-   Hospital Management
-   Online Shopping

------------------------------------------------------------------------

# 15. Practice Problems

Identify the Strong Entities.

### Library

-   Book
-   Student
-   Fine
-   Borrow Record

### Hospital

-   Patient
-   Doctor
-   Prescription
-   Medicine

### Banking

-   Customer
-   Branch
-   Loan
-   Transaction

Explain your reasoning.

------------------------------------------------------------------------

# 16. Revision Notes

    Strong Entity

    ↓

    Independent

    ↓

    Own Primary Key

    ↓

    Can exist alone

Representation

    +-----------+
    |  Entity   |
    +-----------+

Examples

-   Student
-   Customer
-   Product
-   Employee
-   Book

Remember:

> Every Strong Entity has its own identity and does not depend on
> another entity for existence.
