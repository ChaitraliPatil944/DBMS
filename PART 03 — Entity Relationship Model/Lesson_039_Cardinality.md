# Lesson 039 --- Cardinality

> **Part 03 --- Entity Relationship Model**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What Cardinality is
-   Why Cardinality is important
-   Minimum vs Maximum Cardinality
-   One-to-One (1:1)
-   One-to-Many (1:N)
-   Many-to-One (N:1)
-   Many-to-Many (M:N)
-   SQL implementation
-   Junction (Bridge) Tables
-   Real-world examples
-   Common mistakes
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

In Lesson 038, we learned the **Degree of Relationship**, which answers:

> How many **entity types** participate?

Cardinality answers a different question:

> How many **instances** of one entity can be associated with another?

------------------------------------------------------------------------

# 2. What is Cardinality?

**Cardinality** defines the number of instances of one entity that can
be related to instances of another entity.

Example:

    Student -------- Course

Questions:

-   Can one student study many courses?
-   Can one course have many students?

The answers define the cardinality.

------------------------------------------------------------------------

# 3. Why is Cardinality Important?

Correct cardinality helps:

-   Build accurate databases
-   Avoid redundancy
-   Create proper foreign keys
-   Design efficient SQL tables

Choosing the wrong cardinality leads to poor database design.

------------------------------------------------------------------------

# 4. Types of Cardinality

    Cardinality
    │
    ├── One-to-One (1:1)
    ├── One-to-Many (1:N)
    ├── Many-to-One (N:1)
    └── Many-to-Many (M:N)

------------------------------------------------------------------------

# 5. One-to-One (1:1)

One record relates to only one record.

    Person -------- Passport

    One Person
          │
          ▼
    One Passport

SQL

``` sql
CREATE TABLE Passport(
    PassportID INT PRIMARY KEY,
    PersonID INT UNIQUE,
    FOREIGN KEY(PersonID)
        REFERENCES Person(PersonID)
);
```

Examples

-   Citizen ↔ Passport
-   Employee ↔ Locker
-   Vehicle ↔ Registration Certificate

------------------------------------------------------------------------

# 6. One-to-Many (1:N)

One record relates to many records.

    Department -------- Employee

    Department

       IT

      / | \
     /  |  \

    Emp1 Emp2 Emp3

SQL

``` sql
CREATE TABLE Employee(
    EmployeeID INT PRIMARY KEY,
    DepartmentID INT,
    FOREIGN KEY(DepartmentID)
        REFERENCES Department(DepartmentID)
);
```

Examples

-   Customer → Orders
-   Teacher → Students
-   Category → Products

------------------------------------------------------------------------

# 7. Many-to-One (N:1)

The reverse of One-to-Many.

    Many Employees

    ↓

    One Department

Every employee belongs to one department.

Many employees can belong to the same department.

------------------------------------------------------------------------

# 8. Many-to-Many (M:N)

Many records relate to many records.

    Student -------- Course

    Student A
        \
         \
          DBMS

    Student B
         /
        /
    Course

One student studies many courses.

One course has many students.

This **cannot** be implemented directly in a relational database.

We need a **Junction Table**.

------------------------------------------------------------------------

# 9. Junction (Bridge) Table

ER Diagram

    Student ---- Enrolls ---- Course

Relational Model

    Student

    StudentID

    Course

    CourseID

    Enrollment

    StudentID
    CourseID
    EnrollmentDate

SQL

``` sql
CREATE TABLE Enrollment(
    StudentID INT,
    CourseID INT,
    EnrollmentDate DATE,
    PRIMARY KEY(StudentID, CourseID),
    FOREIGN KEY(StudentID)
        REFERENCES Student(StudentID),
    FOREIGN KEY(CourseID)
        REFERENCES Course(CourseID)
);
```

------------------------------------------------------------------------

# 10. Minimum vs Maximum Cardinality

Maximum Cardinality

    1

    or

    Many

Minimum Cardinality

    0 = Optional

    1 = Mandatory

Example

    Customer ---- Places ---- Order

    Customer

    0..N Orders

    Order

    Exactly 1 Customer

------------------------------------------------------------------------

# 11. Comparison Table

  Cardinality   Meaning        Example
  ------------- -------------- -----------------------
  1:1           One to One     Person - Passport
  1:N           One to Many    Department - Employee
  N:1           Many to One    Employee - Department
  M:N           Many to Many   Student - Course

------------------------------------------------------------------------

# 12. Degree vs Cardinality

  Degree                   Cardinality
  ------------------------ --------------------------
  Counts entity types      Counts related instances
  Unary, Binary, Ternary   1:1, 1:N, M:N
  Structural concept       Relationship rule

------------------------------------------------------------------------

# 13. Real-World Examples

Library

    Student ---- Borrows ---- Book

    One Student

    ↓

    Many Books

Hospital

    Doctor ---- Patient

    Many Doctors

    ↓

    Many Patients

Requires a junction table.

Online Shopping

    Customer

    ↓

    Many Orders

Bank

    Branch

    ↓

    Many Accounts

------------------------------------------------------------------------

# 14. Common Mistakes

❌ Confusing Degree with Cardinality.

❌ Trying to implement M:N without a junction table.

❌ Using One-to-One when the business rule is actually One-to-Many.

------------------------------------------------------------------------

# 15. Interview Questions

### Beginner

1.  What is Cardinality?
2.  Name the four types of cardinality.
3.  Give an example of One-to-One.

### Intermediate

1.  Difference between Degree and Cardinality?
2.  Why is Many-to-Many difficult to implement?

### Advanced

Design cardinalities for:

-   Hospital
-   Banking
-   University
-   E-commerce

Explain every relationship.

------------------------------------------------------------------------

# 16. Practice Problems

Determine the cardinality.

1.  Customer → Orders
2.  Student → Courses
3.  Employee → Department
4.  Citizen → Passport
5.  Doctor → Patient

Convert the M:N relationship into relational tables.

------------------------------------------------------------------------

# Revision Notes

    Cardinality

    1:1  → One to One

    1:N  → One to Many

    N:1  → Many to One

    M:N  → Many to Many

    M:N

    ↓

    Bridge Table

    ↓

    Two 1:N Relationships

Memory Trick

    Degree
    =
    How many ENTITY TYPES?

    Cardinality
    =
    How many RECORDS relate?

**Remember:**

> Degree tells you **who participates**. Cardinality tells you **how
> many participate**. Correct cardinality is the foundation of good
> database design and directly determines how your SQL tables and
> foreign keys are implemented.
