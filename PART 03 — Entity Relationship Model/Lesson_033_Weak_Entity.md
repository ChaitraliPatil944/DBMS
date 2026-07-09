# Lesson 033 --- Weak Entity

> **Part 03 --- Entity Relationship Model**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What a Weak Entity is
-   Why Weak Entities exist
-   Identifying Relationship
-   Partial Key (Discriminator)
-   Total Participation
-   ER Diagram notation
-   Weak Entity vs Strong Entity
-   SQL implementation
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

In the previous lesson, we studied **Strong Entities**, which can exist
independently.

But many real-world objects **cannot exist without another entity**.

These are called **Weak Entities**.

------------------------------------------------------------------------

# 2. Definition

A **Weak Entity** is an entity that **cannot be uniquely identified by
its own attributes** and **depends on a Strong Entity for its
existence**.

It does **not** have a complete Primary Key.

Instead, it is identified using:

-   The Primary Key of its owner (Strong Entity)
-   Its own Partial Key

------------------------------------------------------------------------

# 3. Why Was This Concept Introduced?

Consider an online shopping application.

    Order
    └── Order Item

Can an **Order Item** exist without an Order?

No.

Therefore, Order Item depends on Order.

Representing both as independent entities would be incorrect.

The ER Model introduced **Weak Entities** to model such dependency.

------------------------------------------------------------------------

# 4. Child-Friendly Analogy

Think of a family.

    Family
    │
    ├── Parent
    └── Child

A child has an identity, but in this example imagine a school record
where children are identified within a family.

Without the parent record, the child record is incomplete.

Similarly, a weak entity needs its owner entity.

------------------------------------------------------------------------

# 5. Characteristics

A Weak Entity:

✔ Cannot exist independently

✔ Depends on a Strong Entity

✔ Has a Partial Key

✔ Uses an Identifying Relationship

✔ Has Total Participation

------------------------------------------------------------------------

# 6. Representation

Weak Entity → Double Rectangle

    +================+
    || Dependent    ||
    +================+

Strong Entity → Single Rectangle

    +-------------+
    | Employee    |
    +-------------+

Identifying Relationship → Double Diamond

    +-------------+     <>====<>     +================+
    | Employee    | ---- Identifies --|| Dependent   ||
    +-------------+                   +================+

------------------------------------------------------------------------

# 7. Partial Key

A **Partial Key** (also called a **Discriminator**) uniquely identifies
a weak entity **only within its owner**.

Example:

Employee

    EmployeeID = 101

Dependents

    Aarav
    Anaya
    Riya

The name "Aarav" alone is not unique.

The combination

    EmployeeID + DependentName

becomes unique.

------------------------------------------------------------------------

# 8. Total Participation

Every Weak Entity **must** be related to its owner.

This is called **Total Participation**.

    Employee
          ||
          ||
          ||
    Dependent

Without an Employee, a Dependent cannot exist.

------------------------------------------------------------------------

# 9. Real-World Examples

### Employee and Dependent

    Employee
       |
       | Identifies
       |
    Dependent

### Order and Order Item

    Order
       |
       |
    Order Item

### Student and Marksheet

    Student
       |
    Marksheet

### Building and Room

    Building
       |
    Room

Room numbers are usually unique only inside a building.

------------------------------------------------------------------------

# 10. SQL Mapping

ER Design

    Employee

    Dependent

SQL

``` sql
CREATE TABLE Employee (
    EmployeeID INT PRIMARY KEY,
    Name VARCHAR(100)
);

CREATE TABLE Dependent (
    EmployeeID INT,
    DependentName VARCHAR(100),
    Age INT,
    PRIMARY KEY (EmployeeID, DependentName),
    FOREIGN KEY (EmployeeID)
        REFERENCES Employee(EmployeeID)
);
```

Notice that the Primary Key is **composite**.

------------------------------------------------------------------------

# 11. Strong Entity vs Weak Entity

  Strong Entity            Weak Entity
  ------------------------ ---------------------------
  Exists independently     Depends on another entity
  Complete Primary Key     Partial Key
  Single Rectangle         Double Rectangle
  Optional participation   Total participation
  No owner required        Owner required

------------------------------------------------------------------------

# 12. How to Identify a Weak Entity?

Ask yourself:

    Can it exist without another entity?

    ↓

    NO

    ↓

    Does it need another entity's key?

    ↓

    YES

    ↓

    Weak Entity

------------------------------------------------------------------------

# 13. Common Mistakes

❌ Assuming every child table is weak.

A child table may still have its own independent Primary Key.

Weakness depends on **existence**, not merely foreign keys.

------------------------------------------------------------------------

# 14. Interview Questions

### Basic

1.  What is a Weak Entity?
2.  Why can't it exist independently?
3.  How is it represented?

### Intermediate

1.  What is a Partial Key?
2.  Explain Identifying Relationship.
3.  Why does a Weak Entity have Total Participation?

### Advanced

Design weak entities for:

-   Hospital
-   Railway Reservation
-   Banking
-   E-commerce

------------------------------------------------------------------------

# 15. Practice Problems

Identify the Weak Entity.

1.  Employee → Dependent
2.  Order → Order Item
3.  Building → Room
4.  Student → Marksheet
5.  Customer → Address

Explain why each is weak.

------------------------------------------------------------------------

# 16. Key Takeaways

-   Weak Entities depend on Strong Entities.
-   They have no complete Primary Key.
-   They use a Partial Key.
-   They participate totally in an Identifying Relationship.
-   They are represented using a Double Rectangle.

------------------------------------------------------------------------

# Revision Notes

    Strong Entity
          │
          ▼
    Own Primary Key

          │
          ▼
    Weak Entity
          │
          ▼
    Needs Owner Key
    +
    Partial Key
          │
          ▼
    Composite Primary Key

**Remember**

> A Weak Entity cannot stand alone. Its identity comes from both its
> owner and its partial key.
