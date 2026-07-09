# Lesson 046 --- ER Diagram Symbols

> **Part 03 --- Entity Relationship Model**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What ER Diagram symbols are
-   Why standardized symbols are important
-   Symbols used in ER diagrams
-   Entity symbols
-   Attribute symbols
-   Relationship symbols
-   Cardinality notation
-   Participation notation
-   Weak Entity notation
-   Generalization & Specialization symbols
-   Aggregation notation
-   Complete ER diagram examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Imagine trying to read a road map where every city, highway, and river
had different symbols.

It would be confusing.

Similarly, database designers around the world use **standard ER Diagram
symbols** so everyone can understand a database design.

These symbols act as the universal language of database modeling.

------------------------------------------------------------------------

# 2. Why Are Symbols Important?

ER diagrams are visual representations of databases.

Symbols help us quickly identify:

-   Entities
-   Attributes
-   Relationships
-   Constraints
-   Keys
-   Special structures

Without standard symbols, every ER diagram would look different.

------------------------------------------------------------------------

# 3. Complete Symbol Overview

    Rectangle          → Strong Entity

    Double Rectangle   → Weak Entity

    Oval               → Attribute

    Double Oval        → Multi-Valued Attribute

    Dashed Oval        → Derived Attribute

    Underlined Oval    → Key Attribute

    Diamond            → Relationship

    Double Diamond     → Identifying Relationship

    Single Line        → Partial Participation

    Double Line        → Total Participation

    Triangle           → Generalization / Specialization (IS-A)

    Box Around Relation→ Aggregation

------------------------------------------------------------------------

# 4. Strong Entity

Representation

    +-----------+
    | Student   |
    +-----------+

Meaning

An entity that exists independently.

Examples

-   Student
-   Product
-   Employee
-   Customer

------------------------------------------------------------------------

# 5. Weak Entity

Representation

    +================+
    || Dependent    ||
    +================+

Meaning

Depends on another entity for existence.

Examples

-   Order Item
-   Dependent
-   Room (within Building)

------------------------------------------------------------------------

# 6. Attribute

Representation

          Name
           ○
           |
       Student

Stores information about an entity.

Examples

-   Name
-   Age
-   Salary
-   Price

------------------------------------------------------------------------

# 7. Key Attribute

Representation

    StudentID
    =========
         |
      Student

The attribute uniquely identifies an entity.

Examples

-   Roll Number
-   EmployeeID
-   Passport Number

------------------------------------------------------------------------

# 8. Composite Attribute

              Name
               ○
          /    |    \
     First  Middle  Last

Can be divided into smaller meaningful parts.

------------------------------------------------------------------------

# 9. Multi-Valued Attribute

Representation

    ((Phone))
          |
       Student

One entity can have multiple values.

Examples

-   Phone Numbers
-   Skills
-   Email Addresses

------------------------------------------------------------------------

# 10. Derived Attribute

Representation

    - - Age - -
          |
       Student

Calculated from another attribute.

Example

    Age

    ↓

    Derived from

    ↓

    Date of Birth

------------------------------------------------------------------------

# 11. Relationship

Representation

    +---------+    <Enrolls>    +--------+
    | Student |-----------------| Course |
    +---------+                 +--------+

Represents an association between entities.

------------------------------------------------------------------------

# 12. Identifying Relationship

Representation

    Employee

    <>====<>

    Dependent

Used with Weak Entities.

------------------------------------------------------------------------

# 13. Participation Symbols

Partial Participation

    Student
       |
    Enrolls

Single line

Total Participation

    Dependent
       ||
    Belongs To

Double line

------------------------------------------------------------------------

# 14. Cardinality Symbols

One-to-One

    Person
       |
    Passport

One-to-Many

    Department

     |

    Employees

Many-to-Many

    Student

    <---->

    Course

------------------------------------------------------------------------

# 15. Generalization / Specialization

Representation

             Vehicle
                ▲
          ┌─────┼─────┐
          │     │     │
        Car   Bike  Truck

Represents an IS-A relationship.

------------------------------------------------------------------------

# 16. Aggregation

Representation

    +--------------------------------+
    | Employee -- WorksOn -- Project |
    +--------------------------------+
                    |
              Supervised By
                    |
                 Manager

The relationship behaves like an entity.

------------------------------------------------------------------------

# 17. Complete Example

                    StudentID
                    =========
                        ○
                        |
                 +---------------+
                 |   Student     |
                 +---------------+
                     |
                  <Enrolls>
                     |
                 +---------------+
                 |    Course     |
                 +---------------+
                        |
                     CourseID
                     ========

------------------------------------------------------------------------

# 18. Common Interview Diagram

                     Vehicle
                        ▲
                ----------------
                |      |       |
              Car    Bike    Truck

Superclass with subclasses.

------------------------------------------------------------------------

# 19. Common Mistakes

❌ Drawing weak entities using a single rectangle.

❌ Forgetting to underline key attributes.

❌ Using single ovals for multi-valued attributes.

❌ Forgetting the double line for total participation.

------------------------------------------------------------------------

# 20. Interview Questions

### Beginner

1.  Which symbol represents an entity?
2.  Which symbol represents a relationship?
3.  How is a weak entity shown?

### Intermediate

1.  Difference between a double oval and dashed oval?
2.  Why are key attributes underlined?

### Advanced

Draw a complete ER diagram using all major symbols for:

-   Hospital
-   Banking
-   Library
-   University

------------------------------------------------------------------------

# 21. Practice Problems

Draw ER diagrams with proper symbols for:

1.  Student Management System
2.  Hospital Management System
3.  Library Management System
4.  Railway Reservation System
5.  Online Shopping Platform

Identify every symbol used.

------------------------------------------------------------------------

# Revision Notes

    Rectangle
    ↓

    Entity

    Double Rectangle
    ↓

    Weak Entity

    Oval
    ↓

    Attribute

    Double Oval
    ↓

    Multi-Valued

    Dashed Oval
    ↓

    Derived

    Underline
    ↓

    Key Attribute

    Diamond
    ↓

    Relationship

    Double Diamond
    ↓

    Identifying Relationship

    Triangle
    ↓

    Generalization / Specialization

    Box Around Relationship
    ↓

    Aggregation

Memory Trick

    Rectangle = Thing

    Oval = Information

    Diamond = Connection

    Triangle = Inheritance

    Box = Relationship becomes Entity

**Remember:**

> ER diagram symbols form the visual language of database design. Once
> you recognize these symbols, you can read almost any ER diagram and
> immediately understand how the database is structured, even before
> looking at the SQL implementation.
