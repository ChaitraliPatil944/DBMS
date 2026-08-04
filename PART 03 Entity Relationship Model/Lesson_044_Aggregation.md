# Lesson 044 --- Aggregation

> **Part 03 --- Entity Relationship Model**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What Aggregation is
-   Why Aggregation was introduced
-   Relationship between relationships
-   When Aggregation is required
-   ER diagram notation
-   Real-world examples
-   SQL implementation
-   Aggregation vs Generalization vs Specialization
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

In earlier lessons, we learned that:

-   Entities participate in Relationships.
-   Relationships connect Entities.

But what if **another entity needs to interact with an existing
relationship itself?**

A normal ER model cannot directly represent this.

To solve this limitation, the Enhanced ER (EER) Model introduces
**Aggregation**.

------------------------------------------------------------------------

# 2. What is Aggregation?

**Aggregation** is a technique that treats a **relationship set as a
higher-level entity** so that it can participate in another
relationship.

Simply put:

> A relationship behaves like an entity.

------------------------------------------------------------------------

# 3. Why Was Aggregation Introduced?

Consider a company.

    Employee -------- Works On -------- Project

Now suppose:

    Manager supervises
    (Employee Works On Project)

The manager is **not supervising only the employee** or **only the
project**.

The manager supervises the **assignment** of an employee to a project.

This is a relationship acting like an entity.

------------------------------------------------------------------------

# 4. Child-Friendly Analogy

Imagine a school.

    Student ------ Participates ------ Competition

Now a teacher evaluates **that participation**.

The teacher is evaluating:

-   not just the student,
-   not just the competition,

but the **participation** itself.

------------------------------------------------------------------------

# 5. Basic Idea

Without aggregation:

    Employee ---- Works On ---- Project

    Manager ???

    (No direct way to connect Manager to Works On.)

With aggregation:

            +---------------------------+
            | Employee -- WorksOn -- Project |
            +---------------------------+
                        |
                   Supervised By
                        |
                     Manager

The boxed relationship is treated as one object.

------------------------------------------------------------------------

# 6. ER Diagram Notation

Aggregation is represented by drawing a **box around the relationship
and its participating entities**.

    +--------------------------------------+
    | Employee ---- WorksOn ---- Project   |
    +--------------------------------------+
                      |
                Supervised By
                      |
                   Manager

------------------------------------------------------------------------

# 7. Real-World Examples

## Company

    Employee ---- Assigned To ---- Project
                       |
                 Managed By
                       |
                    Manager

------------------------------------------------------------------------

## University

    Student ---- Registers ---- Course
                       |
                 Approved By
                       |
                  HOD

------------------------------------------------------------------------

## Banking

    Customer ---- Applies ---- Loan
                      |
                Verified By
                      |
                   Officer

------------------------------------------------------------------------

## Hospital

    Doctor ---- Performs ---- Surgery
                      |
                 Approved By
                      |
               Medical Director

------------------------------------------------------------------------

# 8. SQL Perspective

Aggregation is usually implemented using an **intermediate table**.

``` sql
CREATE TABLE Assignment(
    EmployeeID INT,
    ProjectID INT,
    PRIMARY KEY(EmployeeID, ProjectID)
);
```

Now reference the assignment:

``` sql
CREATE TABLE Supervision(
    ManagerID INT,
    EmployeeID INT,
    ProjectID INT,
    FOREIGN KEY(EmployeeID, ProjectID)
        REFERENCES Assignment(EmployeeID, ProjectID)
);
```

The Assignment table represents the aggregated relationship.

------------------------------------------------------------------------

# 9. When Should We Use Aggregation?

Use aggregation when:

-   A relationship needs its own relationship.
-   A relationship has its own lifecycle.
-   Business rules apply to the relationship itself.
-   A relationship must be referenced by another entity.

------------------------------------------------------------------------

# 10. Aggregation vs Generalization

  -----------------------------------------------------------------------
  Aggregation                     Generalization
  ------------------------------- ---------------------------------------
  Relationship becomes an entity  Similar entities become one superclass

  Models relationship of          Models inheritance
  relationships                   

  Solves complex interactions     Removes repeated attributes
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# 11. Aggregation vs Specialization

  Aggregation                      Specialization
  -------------------------------- --------------------------------
  Focuses on relationships         Focuses on entities
  Relationship acts like entity    Entity divided into subclasses
  Used for higher-level modeling   Used for inheritance

------------------------------------------------------------------------

# 12. Advantages

-   Represents complex business rules
-   Improves ER diagram clarity
-   Supports relationship-to-relationship modeling
-   Reduces ambiguity
-   Better conceptual design

------------------------------------------------------------------------

# 13. Limitations

-   Increases diagram complexity
-   Rarely needed in small databases
-   May confuse beginners
-   Often implemented using bridge tables in relational databases

------------------------------------------------------------------------

# 14. Common Mistakes

❌ Using aggregation when a normal relationship is sufficient.

❌ Confusing aggregation with generalization.

Remember:

-   Generalization = Entity hierarchy
-   Specialization = Entity hierarchy
-   Aggregation = Relationship hierarchy

------------------------------------------------------------------------

# 15. Interview Questions

### Beginner

1.  What is Aggregation?
2.  Why was Aggregation introduced?
3.  How is Aggregation represented?

### Intermediate

1.  When should Aggregation be used?
2.  Explain "relationship between relationships."

### Advanced

Design an aggregation model for:

-   Company Project Management
-   Hospital
-   University ERP
-   Banking Loan Approval

------------------------------------------------------------------------

# 16. Practice Problems

For each scenario, determine whether Aggregation is needed.

1.  Manager supervises employee assignments.
2.  HOD approves course registrations.
3.  Director reviews surgeries.
4.  Bank officer verifies loan applications.
5.  Teacher grades student submissions.

Draw the ER diagram if aggregation is required.

------------------------------------------------------------------------

# Revision Notes

    Entities
        │
    Relationship
        │
    Aggregation
        │
    Relationship behaves as Entity

Memory Trick

    Entity ↔ Relationship

    Aggregation

    ↓

    Relationship ↔ Relationship

Key Points

-   Treats a relationship as a higher-level entity.
-   Used in Enhanced ER (EER) modeling.
-   Helpful when another entity must interact with an existing
    relationship.
-   Usually implemented with an intermediate table in SQL.

**Remember:**

> Aggregation allows an ER model to represent relationships **about
> other relationships**. It is an advanced modeling technique used when
> business rules cannot be expressed using ordinary entities and
> relationships alone.
