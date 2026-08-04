# Lesson 047 --- Designing ER Diagrams

> **Part 03 --- Entity Relationship Model**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will be able to:

-   Convert a problem statement into an ER Diagram
-   Identify entities, attributes and relationships
-   Choose appropriate keys
-   Determine cardinality and participation
-   Avoid common ER design mistakes
-   Design interview-quality ER diagrams
-   Convert an ER model into a relational design

------------------------------------------------------------------------

# 1. Introduction

Learning ER symbols is only the beginning.

The real skill is answering this question:

> **"Given a real-world problem, how do I design an ER Diagram?"**

This lesson teaches a practical workflow used in interviews and
industry.

------------------------------------------------------------------------

# 2. ER Design Workflow

    Requirement Gathering
            │
            ▼
    Identify Entities
            │
            ▼
    Identify Attributes
            │
            ▼
    Choose Keys
            │
            ▼
    Find Relationships
            │
            ▼
    Define Cardinality
            │
            ▼
    Define Participation
            │
            ▼
    Draw ER Diagram
            │
            ▼
    Validate Design

------------------------------------------------------------------------

# 3. Step 1 --- Read the Problem Statement

Example:

    A library stores books.
    Students borrow books.
    Each book belongs to one category.
    A student can borrow many books.

Do **not** draw immediately.

Read twice and underline nouns and verbs.

------------------------------------------------------------------------

# 4. Step 2 --- Identify Entities

A simple trick:

**Most important nouns become entities.**

Problem:

    Student borrows Book from Library.

Entities:

    Student

    Book

    Library

------------------------------------------------------------------------

# 5. Step 3 --- Identify Attributes

Ask:

> What information should we store?

Example

    Student

    StudentID
    Name
    Email
    Phone
    DOB

Book

    BookID
    Title
    Author
    Price

------------------------------------------------------------------------

# 6. Step 4 --- Identify Keys

Every strong entity needs a unique identifier.

    Student
    ---------
    StudentID

    Book
    ------
    BookID

Good keys are:

-   Unique
-   Stable
-   Never NULL

------------------------------------------------------------------------

# 7. Step 5 --- Identify Relationships

Look for verbs.

    Student borrows Book

Relationship

    Borrows

Diagram

    Student ---- Borrows ---- Book

------------------------------------------------------------------------

# 8. Step 6 --- Decide Cardinality

Ask:

    One student

    ↓

    How many books?

    Many

    One book

    ↓

    Can many students borrow?

    Yes (over time)

Result

    Student

    M:N

    Book

------------------------------------------------------------------------

# 9. Step 7 --- Decide Participation

Ask:

    Can a student exist without borrowing?

    YES

    Partial

    Can a borrow record exist without a student?

    NO

    Total

------------------------------------------------------------------------

# 10. Step 8 --- Draw the ER Diagram

              StudentID
              =========
                  ○
                  |
            +-------------+
            |  Student    |
            +-------------+
                  |
              <Borrows>
                  |
            +-------------+
            |    Book     |
            +-------------+
                  |
               BookID
               ======

------------------------------------------------------------------------

# 11. Step 9 --- Validate

Checklist

    ✓ Every entity has a key

    ✓ Relationships make sense

    ✓ Correct cardinality

    ✓ Correct participation

    ✓ No duplicate entities

    ✓ No missing attributes

------------------------------------------------------------------------

# 12. Case Study 1 --- Library

Requirements

-   Students borrow books.
-   Books belong to categories.
-   Librarians issue books.

Entities

    Student
    Book
    Category
    Librarian
    Issue

Relationships

    Student ---- Borrows ---- Book

    Book ---- Belongs To ---- Category

    Librarian ---- Issues ---- Book

------------------------------------------------------------------------

# 13. Case Study 2 --- Hospital

Requirements

-   Doctors treat patients.
-   Patients receive medicines.
-   Appointments are scheduled.

Entities

    Doctor
    Patient
    Medicine
    Appointment

Relationships

    Doctor ---- Treats ---- Patient

    Doctor ---- Schedules ---- Appointment

    Patient ---- Receives ---- Medicine

------------------------------------------------------------------------

# 14. Case Study 3 --- Online Shopping

Entities

    Customer
    Order
    Product
    Payment
    Seller

Relationships

    Customer ---- Places ---- Order

    Order ---- Contains ---- Product

    Customer ---- Makes ---- Payment

    Seller ---- Sells ---- Product

------------------------------------------------------------------------

# 15. Case Study 4 --- University

Entities

    Student
    Course
    Faculty
    Department

Relationships

    Student ---- Enrolls ---- Course

    Faculty ---- Teaches ---- Course

    Department ---- Offers ---- Course

------------------------------------------------------------------------

# 16. Common Mistakes

❌ Turning every noun into an entity.

Example:

    Name
    Phone

These are attributes.

------------------------------------------------------------------------

❌ Ignoring business rules.

Example:

    One passport per citizen

    ≠

    Many passports

------------------------------------------------------------------------

❌ Forgetting keys.

Every strong entity should have one.

------------------------------------------------------------------------

❌ Incorrect cardinality.

Always verify with the client or problem statement.

------------------------------------------------------------------------

# 17. Interview Strategy

Interviewers often give a paragraph like:

> "Design a database for a movie ticket booking system."

Your approach:

1.  Identify entities.
2.  List attributes.
3.  Select keys.
4.  Identify relationships.
5.  Decide cardinality.
6.  Draw the ER diagram.
7.  Explain assumptions.

------------------------------------------------------------------------

# 18. Practice Problems

Design ER diagrams for:

1.  ATM System
2.  Food Delivery App
3.  Hotel Management
4.  Railway Reservation
5.  Movie Ticket Booking
6.  Hospital Management
7.  Online Examination Portal
8.  Employee Payroll System

For each identify:

-   Entities
-   Attributes
-   Keys
-   Relationships
-   Cardinality
-   Participation

------------------------------------------------------------------------

# 19. Mini Design Checklist

    □ Read requirements carefully

    □ Identify nouns

    □ Identify verbs

    □ Find entities

    □ Find attributes

    □ Choose keys

    □ Add relationships

    □ Add cardinality

    □ Add participation

    □ Review diagram

------------------------------------------------------------------------

# Revision Notes

    Requirement
          │
          ▼
    Entities
          │
          ▼
    Attributes
          │
          ▼
    Keys
          │
          ▼
    Relationships
          │
          ▼
    Cardinality
          │
          ▼
    Participation
          │
          ▼
    ER Diagram

Memory Trick

    R E A K R C P D

    Requirements
    Entities
    Attributes
    Keys
    Relationships
    Cardinality
    Participation
    Diagram

**Remember**

> Designing an ER Diagram is a process, not a guessing game. Always
> begin with the business requirements, identify the entities and their
> relationships, then validate the design before thinking about SQL. A
> good ER diagram saves countless hours of redesign later, which is
> fortunate because databases are much less forgiving than whiteboards.
