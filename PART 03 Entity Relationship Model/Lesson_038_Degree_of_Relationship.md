# Lesson 038 --- Degree of Relationship

> **Part 03 --- Entity Relationship Model**

------------------------------------------------------------------------

# Learning Objectives

After completing this lesson, you will understand:

-   What is the Degree of a Relationship?
-   Why relationship degree is important
-   Unary (Recursive) Relationship
-   Binary Relationship
-   Ternary Relationship
-   N-ary Relationship
-   Real-world examples
-   ER diagrams
-   SQL implementation ideas
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

In the previous lesson, we learned what a **Relationship** is.

This lesson answers another question:

> **How many entity types participate in a relationship?**

The answer is called the **Degree of Relationship**.

------------------------------------------------------------------------

# 2. What is the Degree of Relationship?

The **Degree of a Relationship** is the **number of entity types
participating** in a relationship.

It is **not** the number of records.

Think of it as counting the different kinds of entities connected by a
relationship.

------------------------------------------------------------------------

# 3. Why Do We Need It?

Suppose we are designing a hospital database.

Should a prescription connect:

-   Doctor and Patient?

or

-   Doctor, Patient, and Medicine?

The answer changes the database design.

Understanding the relationship degree helps us model the real world
correctly.

------------------------------------------------------------------------

# 4. Types of Relationship Degree

    Relationship Degree
    │
    ├── Unary (1 Entity Type)
    ├── Binary (2 Entity Types)
    ├── Ternary (3 Entity Types)
    └── N-ary (More than 3 Entity Types)

------------------------------------------------------------------------

# 5. Unary (Recursive) Relationship

A **Unary Relationship** connects an entity with itself.

Example:

    +-----------+
    | Employee  |
    +-----------+
          ^
          |
      Manages
          |
          v
    +-----------+
    | Employee  |
    +-----------+

Examples:

-   Employee manages Employee
-   Person marries Person
-   Folder contains Folder

SQL Idea:

``` sql
CREATE TABLE Employee (
    EmployeeID INT PRIMARY KEY,
    Name VARCHAR(100),
    ManagerID INT,
    FOREIGN KEY (ManagerID)
        REFERENCES Employee(EmployeeID)
);
```

------------------------------------------------------------------------

# 6. Binary Relationship

A **Binary Relationship** involves **two entity types**.

This is the **most common** relationship in databases.

    +---------+      Enrolls      +--------+
    | Student | ----------------> | Course |
    +---------+                   +--------+

Examples:

-   Customer buys Product
-   Doctor treats Patient
-   Teacher teaches Subject
-   Author writes Book

------------------------------------------------------------------------

# 7. Ternary Relationship

A **Ternary Relationship** connects **three entity types**
simultaneously.

Example:

               Doctor
                  |
                  |
             Prescribes
              /       \
             /         \
     Patient -------- Medicine

Meaning:

A doctor prescribes **a specific medicine** to **a specific patient**.

If we split this into multiple binary relationships, important meaning
may be lost.

------------------------------------------------------------------------

# 8. N-ary Relationship

An **N-ary Relationship** involves **more than three entity types**.

Example:

    Supplier
        \
         \
       Supplies
      /   |    \
     /    |     \
    Product Warehouse Transport
                 \
                Invoice

These are less common and usually appear in large enterprise systems.

------------------------------------------------------------------------

# 9. Comparison Table

  Degree    Entity Types   Example
  --------- -------------- --------------------------------------------------------
  Unary     1              Employee manages Employee
  Binary    2              Student enrolls in Course
  Ternary   3              Doctor prescribes Medicine to Patient
  N-ary     \>3            Supplier supplies Product to Warehouse using Transport

------------------------------------------------------------------------

# 10. How to Identify the Degree?

Ask yourself:

    How many DIFFERENT entity types are involved?

    ↓

    1 → Unary

    2 → Binary

    3 → Ternary

    More than 3 → N-ary

Remember:

Do **not** count duplicate entity names separately.

In a recursive relationship:

    Employee manages Employee

Only one entity type exists.

So the degree is **Unary**.

------------------------------------------------------------------------

# 11. Real-World Examples

## College

    Student ---- Enrolls ---- Course

Binary

------------------------------------------------------------------------

## Organization

    Employee
       |
    Manages
       |
    Employee

Unary

------------------------------------------------------------------------

## Hospital

    Doctor
       \
        \
     Prescribes
       /      \
    Patient  Medicine

Ternary

------------------------------------------------------------------------

## Logistics

    Supplier

    Product

    Warehouse

    Truck

    Driver

N-ary

------------------------------------------------------------------------

# 12. Common Mistakes

❌ Confusing **Degree** with **Cardinality**.

Degree answers:

> How many entity types participate?

Cardinality answers:

> How many instances are related?

These are different concepts.

------------------------------------------------------------------------

# 13. Interview Questions

### Beginner

1.  What is the Degree of a Relationship?
2.  Define Unary Relationship.
3.  Give an example of a Binary Relationship.

### Intermediate

1.  Difference between Binary and Ternary Relationships?
2.  Why are Binary Relationships more common?

### Advanced

Design suitable relationship degrees for:

-   Airline Reservation
-   Online Food Delivery
-   Banking
-   Hospital Management

Explain your choices.

------------------------------------------------------------------------

# 14. Practice Problems

Identify the degree of each relationship.

1.  Student studies Course
2.  Employee supervises Employee
3.  Customer places Order
4.  Doctor prescribes Medicine to Patient
5.  Supplier delivers Product to Warehouse using Vehicle

------------------------------------------------------------------------

# Revision Notes

    Relationship Degree

    1 Entity Type
        ↓
    Unary

    2 Entity Types
        ↓
    Binary

    3 Entity Types
        ↓
    Ternary

    More than 3
        ↓
    N-ary

Quick Memory Trick

    Unary   → One entity type

    Binary  → Two entity types

    Ternary → Three entity types

    N-ary   → Four or more entity types

**Remember:**

> The **degree of a relationship** counts the **different entity types**
> participating in the relationship, not the number of records. The next
> lesson covers **Cardinality**, which explains **how many instances**
> of one entity can be associated with another.
