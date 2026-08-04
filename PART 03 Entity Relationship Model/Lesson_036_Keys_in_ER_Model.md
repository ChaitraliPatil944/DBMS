# Lesson 036 --- Keys in ER Model

> **Part 03 --- Entity Relationship Model**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson you will understand:

-   Why keys are needed
-   What a key is
-   Key Attribute
-   Super Key
-   Candidate Key
-   Primary Key
-   Alternate Key
-   Composite Key
-   Foreign Key
-   Partial Key
-   Choosing the right key
-   ER notation
-   SQL examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Why Do We Need Keys?

Imagine a college database:

    Student
    ---------------------
    Name
    Department
    Age

There are three students named **Rahul**.

How do we identify the correct one?

We cannot.

A database needs a way to uniquely identify every record.

That is why **Keys** exist.

------------------------------------------------------------------------

# 2. What is a Key?

A **Key** is an attribute or a combination of attributes that helps
identify a record or establish relationships between entities.

Think of a key as an **ID card**.

Just as every citizen has a unique ID, every entity should have a unique
identifier.

------------------------------------------------------------------------

# 3. Types of Keys

    Keys
    │
    ├── Key Attribute
    ├── Super Key
    ├── Candidate Key
    ├── Primary Key
    ├── Alternate Key
    ├── Composite Key
    ├── Foreign Key
    └── Partial Key

------------------------------------------------------------------------

# 4. Key Attribute

A **Key Attribute** uniquely identifies an entity in an ER diagram.

ER notation:

          StudentID
          =========
              |
          +---------+
          | Student |
          +---------+

Underlining indicates a key attribute.

------------------------------------------------------------------------

# 5. Super Key

A **Super Key** is any set of attributes that uniquely identifies an
entity.

Example:

    StudentID
    StudentID + Name
    StudentID + Email
    StudentID + Phone

All uniquely identify the student.

------------------------------------------------------------------------

# 6. Candidate Key

A **Candidate Key** is the **smallest possible Super Key**.

Example:

    StudentID

    Email

Both are unique.

Both are Candidate Keys.

------------------------------------------------------------------------

# 7. Primary Key

A **Primary Key** is the Candidate Key selected to identify every
record.

Example:

    Candidate Keys

    StudentID

    Email

    ↓

    Choose StudentID

    ↓

    Primary Key

Rules:

-   Unique
-   Never NULL
-   Stable
-   Minimal

SQL

``` sql
CREATE TABLE Student(
    StudentID INT PRIMARY KEY,
    Name VARCHAR(100),
    Email VARCHAR(100)
);
```

------------------------------------------------------------------------

# 8. Alternate Key

Candidate Keys that are **not chosen** become Alternate Keys.

Example

    Candidate Keys

    StudentID
    Email

    ↓

    Primary Key

    StudentID

    ↓

    Alternate Key

    Email

------------------------------------------------------------------------

# 9. Composite Key

A **Composite Key** uses two or more attributes together.

Example

    Enrollment

    StudentID

    CourseID

Neither alone is unique.

Together they are.

SQL

``` sql
PRIMARY KEY(StudentID, CourseID)
```

------------------------------------------------------------------------

# 10. Foreign Key

A **Foreign Key** links two entities.

    Student

    StudentID

    Enrollment

    StudentID
    CourseID

StudentID inside Enrollment is a Foreign Key.

Relationship:

    Student
        |
        | StudentID
        |
    Enrollment

SQL

``` sql
FOREIGN KEY(StudentID)
REFERENCES Student(StudentID);
```

------------------------------------------------------------------------

# 11. Partial Key

Used only with **Weak Entities**.

Example

    Employee

    EmployeeID

    Dependent

    DependentName

DependentName alone is not unique.

Together:

    EmployeeID + DependentName

becomes unique.

------------------------------------------------------------------------

# 12. Comparison Table

  Key             Purpose
  --------------- -----------------------------------------------
  Key Attribute   Identifies entity
  Super Key       Unique identifier (may have extra attributes)
  Candidate Key   Minimal Super Key
  Primary Key     Selected Candidate Key
  Alternate Key   Unselected Candidate Key
  Composite Key   Combination of attributes
  Foreign Key     Links entities
  Partial Key     Identifies Weak Entity with owner

------------------------------------------------------------------------

# 13. Real-World Example

    Student
    -------------------------
    StudentID
    Email
    Phone

-   Super Keys:
    -   StudentID
    -   StudentID + Phone
    -   Email
    -   Email + Name
-   Candidate Keys:
    -   StudentID
    -   Email
-   Primary Key:
    -   StudentID
-   Alternate Key:
    -   Email

------------------------------------------------------------------------

# 14. Common Mistakes

❌ Every unique attribute is **not** the Primary Key.

❌ A Foreign Key does not have to be unique.

❌ A Composite Key is not the same as multiple Primary Keys.

------------------------------------------------------------------------

# 15. Interview Questions

### Beginner

1.  What is a key?
2.  Why are keys important?
3.  Difference between Candidate and Primary Key?

### Intermediate

1.  Super Key vs Candidate Key?
2.  Composite Key vs Foreign Key?
3.  Why should a Primary Key never be NULL?

### Advanced

Design keys for:

-   Railway Reservation
-   Hospital
-   E-commerce
-   Banking

------------------------------------------------------------------------

# 16. Practice Problems

For each system identify all possible keys.

1.  Student Management
2.  Library
3.  Online Shopping
4.  Airline Reservation
5.  Hospital

Also identify:

-   Candidate Keys
-   Primary Key
-   Alternate Keys
-   Foreign Keys

------------------------------------------------------------------------

# Revision Notes

    Super Key
         │
    Minimal
         ▼
    Candidate Key
         │
    Chosen
         ▼
    Primary Key

    Remaining Candidate Keys
         ▼
    Alternate Keys

    Composite Key
    =
    Two or More Attributes

    Foreign Key
    =
    Relationship Between Tables

    Partial Key
    =
    Weak Entity Identifier

**Remember**

> Every Primary Key is a Candidate Key.
>
> Every Candidate Key is a Super Key.
>
> But the reverse is **not** true.
