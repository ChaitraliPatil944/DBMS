# Lesson 048 --- ER to Relational Mapping

> **Part 03 --- Entity Relationship Model**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What ER to Relational Mapping is
-   Why mapping is required
-   Mapping Strong Entities
-   Mapping Weak Entities
-   Mapping Attributes
-   Mapping Relationships (1:1, 1:N, M:N)
-   Mapping Composite, Multi-Valued and Derived Attributes
-   Mapping Generalization & Specialization
-   Mapping Aggregation
-   Complete examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

So far we have learned how to design an **ER Diagram**.

But computers do not store ER diagrams.

Relational Database Management Systems (RDBMS) store information in
**tables**.

Therefore, every ER Diagram must eventually be converted into relational
tables.

This process is called **ER to Relational Mapping**.

------------------------------------------------------------------------

# 2. Why Do We Need Mapping?

Design Process

    Real World
         │
         ▼
    Requirements
         │
         ▼
    ER Diagram
         │
         ▼
    Relational Tables
         │
         ▼
    SQL Database

The ER diagram is only a blueprint.

The relational model is the actual implementation.

------------------------------------------------------------------------

# 3. Mapping Rules Overview

    ER Component
          │
          ▼
    Relational Component

    Entity          → Table

    Attribute       → Column

    Key Attribute   → Primary Key

    Relationship    → Foreign Key / New Table

    Multi-Valued    → Separate Table

    Weak Entity     → Separate Table with Composite Key

------------------------------------------------------------------------

# 4. Rule 1 --- Strong Entity → Table

ER Diagram

    +-----------+
    | Student   |
    +-----------+

Attributes

    StudentID
    Name
    Department

Relational Table

``` sql
CREATE TABLE Student(
    StudentID INT PRIMARY KEY,
    Name VARCHAR(100),
    Department VARCHAR(50)
);
```

Every Strong Entity becomes one table.

------------------------------------------------------------------------

# 5. Rule 2 --- Weak Entity → Table

ER Diagram

    Employee

    ↓

    Dependent

Dependent has a Partial Key.

SQL

``` sql
CREATE TABLE Dependent(
    EmployeeID INT,
    DependentName VARCHAR(100),
    Age INT,
    PRIMARY KEY(EmployeeID, DependentName),
    FOREIGN KEY(EmployeeID)
        REFERENCES Employee(EmployeeID)
);
```

The owner's primary key becomes part of the composite key.

------------------------------------------------------------------------

# 6. Rule 3 --- Simple Attribute → Column

ER

    Student

    ↓

    Name

    Age

SQL

``` sql
Name VARCHAR(100),
Age INT
```

Simple attributes become columns.

------------------------------------------------------------------------

# 7. Rule 4 --- Composite Attribute

ER

    Name

    ↓

    First

    Middle

    Last

SQL

``` sql
FirstName VARCHAR(50),
MiddleName VARCHAR(50),
LastName VARCHAR(50)
```

Composite attributes are split into individual columns.

------------------------------------------------------------------------

# 8. Rule 5 --- Multi-Valued Attribute

ER

    Student

    ↓

    Phone Numbers

Cannot store multiple phone numbers in one column.

Instead create another table.

``` sql
CREATE TABLE StudentPhone(
    StudentID INT,
    Phone VARCHAR(20),
    PRIMARY KEY(StudentID, Phone),
    FOREIGN KEY(StudentID)
        REFERENCES Student(StudentID)
);
```

------------------------------------------------------------------------

# 9. Rule 6 --- Derived Attribute

Example

    DateOfBirth

    ↓

    Age

Age should usually **not** be stored.

Instead:

``` sql
SELECT
TIMESTAMPDIFF(YEAR,DOB,CURDATE())
AS Age
FROM Student;
```

Derived attributes are generally calculated.

------------------------------------------------------------------------

# 10. Rule 7 --- One-to-One Relationship

Example

    Person

    Passport

Implementation

Place the foreign key in either table (based on business rules).

``` sql
Passport(
PassportID,
PersonID UNIQUE
)
```

------------------------------------------------------------------------

# 11. Rule 8 --- One-to-Many Relationship

Example

    Department

    ↓

    Employees

The primary key from the "One" side becomes a foreign key on the "Many"
side.

``` sql
Employee(
EmployeeID,
DepartmentID
)
```

------------------------------------------------------------------------

# 12. Rule 9 --- Many-to-Many Relationship

Example

    Student

    Course

Cannot be represented directly.

Create a junction table.

``` sql
Enrollment(

StudentID,

CourseID,

EnrollmentDate,

PRIMARY KEY(StudentID, CourseID)
)
```

ASCII

    Student

    ↓

    Enrollment

    ↓

    Course

------------------------------------------------------------------------

# 13. Rule 10 --- Generalization

Superclass

    Vehicle

Subclasses

    Car

    Bike

    Truck

SQL

    Vehicle

    VehicleID

    Brand

    Color

    Car

    VehicleID

    Doors

    Bike

    VehicleID

    Carrier

Subclass tables reference the superclass.

------------------------------------------------------------------------

# 14. Rule 11 --- Specialization

Same mapping principle.

Superclass stores common attributes.

Subclass stores specific attributes.

Foreign keys maintain inheritance.

------------------------------------------------------------------------

# 15. Rule 12 --- Aggregation

Example

    Employee

    WorksOn

    Project

↓

    Assignment

↓

    Manager supervises Assignment

SQL

``` sql
Assignment(
EmployeeID,
ProjectID
)

Supervision(
ManagerID,
EmployeeID,
ProjectID
)
```

------------------------------------------------------------------------

# 16. Complete Example

ER Diagram

    Student

    ↓

    Enrolls

    ↓

    Course

Tables

    Student

    StudentID
    Name

    Course

    CourseID
    Title

    Enrollment

    StudentID
    CourseID
    Semester

------------------------------------------------------------------------

# 17. Complete Mapping Summary

  ER Component             Relational Mapping
  ------------------------ -----------------------
  Strong Entity            Table
  Weak Entity              Table
  Attribute                Column
  Composite Attribute      Multiple Columns
  Multi-Valued Attribute   Separate Table
  Derived Attribute        Calculated
  Key Attribute            Primary Key
  1:1                      Foreign Key
  1:N                      Foreign Key
  M:N                      Junction Table
  Generalization           Parent + Child Tables
  Aggregation              Intermediate Table

------------------------------------------------------------------------

# 18. Common Mistakes

❌ Storing multiple phone numbers in one column.

❌ Storing derived attributes unnecessarily.

❌ Implementing M:N without a junction table.

❌ Forgetting foreign keys when mapping relationships.

------------------------------------------------------------------------

# 19. Interview Questions

### Beginner

1.  What is ER to Relational Mapping?
2.  Why is mapping required?

### Intermediate

1.  How do you map a weak entity?
2.  How are multi-valued attributes represented?

### Advanced

Convert the following ER diagram into relational tables:

-   Hospital
-   Banking
-   University
-   Online Shopping

------------------------------------------------------------------------

# 20. Practice Problems

Convert these ER models into relational schemas:

1.  Library Management System
2.  Hospital Management System
3.  Employee Payroll System
4.  Railway Reservation System
5.  Online Food Delivery System

Write the SQL tables with keys and foreign keys.

------------------------------------------------------------------------

# Revision Notes

    Entity
       ↓
    Table

    Attribute
       ↓
    Column

    Relationship
       ↓
    Foreign Key

    M:N
       ↓
    Junction Table

    Weak Entity
       ↓
    Composite Key

    Derived Attribute
       ↓
    Calculated

Memory Trick

    ER Diagram

    ↓

    Mapping Rules

    ↓

    Tables

    ↓

    SQL

Key Points

-   Every Strong Entity becomes a table.
-   Composite attributes become multiple columns.
-   Multi-valued attributes become separate tables.
-   Weak entities use composite primary keys.
-   One-to-Many relationships use foreign keys.
-   Many-to-Many relationships require junction tables.
-   Derived attributes are usually calculated.
-   ER to Relational Mapping is the bridge between conceptual design and
    database implementation.

**Remember:**

> An ER diagram describes *what* the database should represent. ER to
> Relational Mapping describes *how* to build it using tables, primary
> keys, and foreign keys. This is the final step before writing SQL and
> creating the actual database.
