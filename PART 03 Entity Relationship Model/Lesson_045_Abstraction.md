# Lesson 045 --- Abstraction

> **Part 03 --- Entity Relationship Model**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What Abstraction is
-   Why Abstraction is needed
-   Data Abstraction in DBMS
-   Levels of Abstraction
-   Conceptual Level
-   Logical Level
-   Physical Level
-   Three-Schema Architecture
-   Abstraction in ER Modeling
-   Real-world examples
-   Abstraction vs Generalization vs Specialization vs Aggregation
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

As software systems grow, databases become increasingly complex.

Imagine trying to understand every table, every index, every storage
block, and every disk operation before writing your first SQL query.

That would be overwhelming.

To solve this problem, DBMS uses **Abstraction**.

Abstraction hides unnecessary details and exposes only the information
required for a particular user or task.

------------------------------------------------------------------------

# 2. What is Abstraction?

**Abstraction** is the process of hiding implementation details while
showing only the essential information.

Simply put:

> Show **what is important**, hide **how it is implemented**.

Users interact with the database without worrying about how the data is
physically stored.

------------------------------------------------------------------------

# 3. Why Do We Need Abstraction?

Without abstraction:

    User

    ↓

    Disk Blocks

    Memory Pages

    Indexes

    Pointers

    Storage Files

    Buffers

    Transactions

    Recovery Logs

Every user would need to understand the internal working of a DBMS.

With abstraction:

    User

    ↓

    Database

    ↓

    Results

The DBMS handles the complexity internally.

------------------------------------------------------------------------

# 4. Child-Friendly Analogy

Imagine driving a car.

You use:

-   Steering wheel
-   Brake
-   Accelerator

You do **not** need to understand:

-   Engine timing
-   Fuel injection
-   Gearbox internals
-   ECU programming

The car hides those complexities.

That is abstraction.

Similarly, a DBMS hides internal storage and processing details.

------------------------------------------------------------------------

# 5. Data Abstraction Levels

A DBMS provides **three levels of abstraction**.

              User
                │
                ▼
    External Level
                │
                ▼
    Conceptual (Logical) Level
                │
                ▼
    Internal (Physical) Level

These are also known as the **Three-Schema Architecture**.

------------------------------------------------------------------------

# 6. External Level (View Level)

This is the highest level.

It shows only the information required by a specific user.

Example:

### Student

    Roll No
    Name
    Marks

### Teacher

    Roll No
    Name
    Marks
    Attendance

Both access the same database but see different views.

------------------------------------------------------------------------

# 7. Conceptual (Logical) Level

This describes the **overall structure** of the database.

It includes:

-   Entities
-   Attributes
-   Relationships
-   Constraints

Example:

    Student

    StudentID

    Name

    Department

This is the level where ER diagrams are created.

------------------------------------------------------------------------

# 8. Internal (Physical) Level

This is the lowest level.

It describes:

-   Files
-   Pages
-   Indexes
-   Hashing
-   B+ Trees
-   Storage Blocks

Users never interact with this level directly.

------------------------------------------------------------------------

# 9. Three-Schema Architecture

    +---------------------------+
    | External Schema (Views)   |
    +---------------------------+
                 │
                 ▼
    +---------------------------+
    | Conceptual Schema         |
    +---------------------------+
                 │
                 ▼
    +---------------------------+
    | Internal Schema           |
    +---------------------------+

------------------------------------------------------------------------

# 10. Abstraction in ER Modeling

When designing an ER diagram, we focus only on:

-   Entities
-   Relationships
-   Attributes

We ignore:

-   File organization
-   Indexing
-   Memory layout
-   Query optimization

That itself is an example of abstraction.

------------------------------------------------------------------------

# 11. Real-World Examples

## ATM

User sees:

    Balance

    Withdraw

    Deposit

Hidden:

    Disk storage

    Locks

    Transactions

    Recovery

    Indexes

------------------------------------------------------------------------

## Instagram

User sees:

    Posts

    Likes

    Followers

Hidden:

    Distributed databases

    Caching

    Replication

    Sharding

------------------------------------------------------------------------

## Amazon

User sees:

    Products

    Orders

    Payments

Hidden:

    Storage engine

    Indexes

    Execution plans

    Cloud databases

------------------------------------------------------------------------

# 12. Advantages of Abstraction

-   Simplifies database usage
-   Improves security
-   Reduces complexity
-   Easier maintenance
-   Better scalability
-   Better modularity
-   Allows different user views

------------------------------------------------------------------------

# 13. Abstraction vs Other EER Concepts

  Concept          Focus
  ---------------- ---------------------------------
  Abstraction      Hide unnecessary details
  Generalization   Combine similar entities
  Specialization   Divide into subclasses
  Aggregation      Treat relationship as an entity

Memory Trick

    Abstraction

    Hide Details

    Generalization

    Combine

    Specialization

    Divide

    Aggregation

    Relationship as Entity

------------------------------------------------------------------------

# 14. Common Mistakes

❌ Thinking abstraction means deleting information.

It only hides unnecessary details.

❌ Confusing abstraction with encapsulation.

Encapsulation is an object-oriented programming concept.

Abstraction is a database design concept.

------------------------------------------------------------------------

# 15. Interview Questions

### Beginner

1.  What is abstraction?
2.  Why is abstraction important?
3.  Name the three abstraction levels.

### Intermediate

1.  Explain the Three-Schema Architecture.
2.  What is the difference between External and Conceptual levels?

### Advanced

Explain how abstraction improves:

-   Security
-   Scalability
-   Performance
-   Database maintenance

------------------------------------------------------------------------

# 16. Practice Problems

1.  Identify the abstraction level for:

-   ER Diagram
-   SQL Table
-   B+ Tree Index
-   User View
-   File Storage

2.  Draw the Three-Schema Architecture.

3.  Explain why abstraction is necessary in a Banking System.

------------------------------------------------------------------------

# Revision Notes

    Abstraction

    ↓

    Hide Complexity

    ↓

    Show Essentials

Three Levels

    External

    ↓

    Conceptual

    ↓

    Internal

Quick Comparison

    External

    Who sees What?

    Conceptual

    How Database is Designed?

    Internal

    How Database is Stored?

Key Points

-   Abstraction hides implementation details.
-   It simplifies database interaction.
-   ER modeling mainly works at the Conceptual Level.
-   Three-Schema Architecture is based on abstraction.

**Remember:**

> Abstraction is one of the fundamental ideas of DBMS. It allows users,
> developers, and administrators to work with the same database at
> different levels of detail, making complex systems easier to
> understand, secure, and maintain.
