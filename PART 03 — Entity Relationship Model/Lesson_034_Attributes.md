# Lesson 034 --- Attributes

> **Part 03 --- Entity Relationship Model**

------------------------------------------------------------------------

# Learning Objectives

After completing this lesson, you will understand:

-   What an Attribute is
-   Why attributes are needed
-   Characteristics of attributes
-   Attributes in ER diagrams
-   Entity vs Attribute
-   Attribute naming rules
-   Real-world examples
-   SQL mapping
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

An **Entity** tells us **what** we are storing information about.

An **Attribute** tells us **what information** we store about that
entity.

Think of an entity as a person and attributes as the facts that describe
that person.

------------------------------------------------------------------------

# 2. What is an Attribute?

An **Attribute** is a property or characteristic of an entity.

Example:

    Student

    Name
    Age
    Roll Number
    Email
    Department

Here, **Student** is the entity.

Everything else is an attribute.

------------------------------------------------------------------------

# 3. Why Do We Need Attributes?

Suppose a college stores only this:

    Student

Can we identify the student?

No.

We need details like:

    Student
    │
    ├── StudentID
    ├── Name
    ├── Age
    ├── Department
    └── Phone

Attributes make stored data meaningful.

------------------------------------------------------------------------

# 4. Child-Friendly Analogy

Imagine your school ID card.

    +----------------------+
    | Name      : Chaitrali|
    | Roll No   : 101      |
    | Class     : CSE      |
    | Blood Grp : B+       |
    +----------------------+

The student is the **entity**.

The details on the card are **attributes**.

------------------------------------------------------------------------

# 5. Representation in an ER Diagram

Attributes are represented using **ovals (ellipses)**.

               (Name)
                  |
    (Student)----(Age)
                  |
             (Department)

ASCII representation:

              Name
               ○
               |
    Age ○--- Student ---○ Department
               |
             ○ Roll No

------------------------------------------------------------------------

# 6. Real-World Examples

## Employee

    Employee

    EmployeeID
    Name
    Salary
    Joining Date
    Designation

## Product

    Product

    ProductID
    Price
    Brand
    Category
    Stock

## Book

    Book

    ISBN
    Title
    Author
    Publisher
    Price

------------------------------------------------------------------------

# 7. Characteristics of Attributes

A good attribute should be:

-   Relevant
-   Meaningful
-   Easy to understand
-   Easy to store
-   Consistent
-   Atomic (when possible)

------------------------------------------------------------------------

# 8. Entity vs Attribute

  Entity                 Attribute
  ---------------------- ----------------------
  Represents an object   Describes the object
  Student                Name
  Employee               Salary
  Product                Price
  Book                   ISBN

Example:

    Student

    ├── Name
    ├── Age
    └── Roll Number

Student is the entity.

The rest are attributes.

------------------------------------------------------------------------

# 9. Naming Rules

Use clear names such as:

-   StudentID
-   EmployeeName
-   DateOfBirth
-   Email
-   Price

Avoid:

-   Data1
-   Field2
-   Temp
-   Info

------------------------------------------------------------------------

# 10. ER Diagram Example

                 StudentID
                     ○
                     |
    Name ○------ Student ------○ Department
                     |
                  ○ Email
                     |
                  ○ Phone

------------------------------------------------------------------------

# 11. SQL Mapping

ER Diagram

    Student

    StudentID
    Name
    Department
    Email

SQL Table

``` sql
CREATE TABLE Student
(
    StudentID INT PRIMARY KEY,
    Name VARCHAR(100),
    Department VARCHAR(50),
    Email VARCHAR(100)
);
```

Every attribute usually becomes a column.

------------------------------------------------------------------------

# 12. Common Mistakes

❌ Treating relationships as attributes.

Example:

    Student

    Studies

"Studies" is a relationship, not an attribute.

❌ Treating entities as attributes.

    Department

If the department has its own data (HOD, building, phone), it should be
an entity.

------------------------------------------------------------------------

# 13. Looking Ahead

Not all attributes are the same.

Some are:

-   Simple
-   Composite
-   Multi-valued
-   Derived
-   Key attributes

These are covered in **Lesson 035**.

------------------------------------------------------------------------

# 14. Interview Questions

### Beginner

1.  What is an attribute?
2.  How is an attribute represented in an ER diagram?
3.  Give five examples.

### Intermediate

1.  Can an attribute uniquely identify an entity?
2.  What makes a good attribute?

### Advanced

Design suitable attributes for:

-   ATM System
-   Railway Reservation
-   Hospital Management
-   Food Delivery App

------------------------------------------------------------------------

# 15. Practice Problems

Identify suitable attributes for:

### Customer

### Product

### Movie

### Flight

### Bank Account

Explain why each attribute is useful.

------------------------------------------------------------------------

# Revision Notes

    Entity
       │
       ▼
    Stores Information About
       │
       ▼
    Attributes

Representation

          Name
           ○
           |
        Student

Remember:

-   Entity = "What?"
-   Attribute = "Details about What?"

In the next lesson, we'll explore the different **types of attributes**
with detailed diagrams and examples.
