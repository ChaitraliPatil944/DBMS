# Lesson 067 --- Referential Relationships

> **Part 04 --- Relational Model**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What Referential Relationships are
-   Why they are important
-   Parent and Child tables
-   Referential Integrity
-   Insert, Update and Delete rules
-   Cascading actions
-   SQL implementation
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

A relational database is not just a collection of independent tables.

The real power comes from **relationships** between those tables.

Example:

    Student
       │
       ▼
    Enrollment
       │
       ▼
    Course

These relationships allow data to remain connected and consistent.

------------------------------------------------------------------------

# 2. What is a Referential Relationship?

A **Referential Relationship** is a relationship where a **Foreign Key**
in one table refers to a **Primary Key** (or UNIQUE Candidate Key) in
another table.

It tells the database:

> "This row depends on another row."

------------------------------------------------------------------------

# 3. Why Are Referential Relationships Needed?

Without relationships:

-   Orders could belong to non-existent customers.
-   Employees could belong to departments that don't exist.
-   Students could enroll without being students.

Relationships prevent invalid references.

------------------------------------------------------------------------

# 4. Parent and Child Tables

    Department
    +--------------+
    | DepartmentID |
    +--------------+
    | 10           |
    | 20           |
    +--------------+

            │
            ▼

    Employee
    +------------+--------------+
    | EmployeeID | DepartmentID |
    +------------+--------------+
    | 101        | 10           |
    | 102        | 20           |
    +------------+--------------+

-   Parent Table → Department
-   Child Table → Employee

------------------------------------------------------------------------

# 5. Referential Integrity

**Referential Integrity** means:

Every Foreign Key value must either:

-   Match an existing parent key, or
-   Be NULL (if allowed).

Valid

    DepartmentID = 10 ✔

Invalid

    DepartmentID = 99 ✘

if department 99 does not exist.

------------------------------------------------------------------------

# 6. Insert Rule

Before inserting a child row:

    Employee

    DepartmentID = 10

Department 10 must already exist.

Otherwise:

    Insert ❌

------------------------------------------------------------------------

# 7. Update Rule

Changing a parent key may break child references.

Example

    DepartmentID

    10

    ↓

    99

If child rows still point to 10, the database must decide what to do.

------------------------------------------------------------------------

# 8. Delete Rule

Deleting a parent row may leave orphan records.

Example

    Department 10

    ↓

    Employee references Department 10

Deleting Department 10 without handling Employee records creates
inconsistency.

------------------------------------------------------------------------

# 9. Cascading Actions

## RESTRICT / NO ACTION

Prevent deletion or update.

    Delete Department

    ↓

    Blocked ❌

------------------------------------------------------------------------

## CASCADE

Parent changes automatically propagate.

    Delete Department

    ↓

    Delete Employees

------------------------------------------------------------------------

## SET NULL

    Employee

    DepartmentID

    ↓

    NULL

The child record remains.

------------------------------------------------------------------------

## SET DEFAULT

The Foreign Key becomes its default value.

Supported only by some DBMSs.

------------------------------------------------------------------------

# 10. SQL Example

``` sql
CREATE TABLE Department(
    DepartmentID INT PRIMARY KEY,
    DepartmentName VARCHAR(100)
);

CREATE TABLE Employee(
    EmployeeID INT PRIMARY KEY,
    Name VARCHAR(100),
    DepartmentID INT,
    FOREIGN KEY (DepartmentID)
        REFERENCES Department(DepartmentID)
        ON DELETE CASCADE
        ON UPDATE CASCADE
);
```

------------------------------------------------------------------------

# 11. Real-World Examples

## Banking

    Customer
       │
    Account

A bank account must belong to an existing customer.

------------------------------------------------------------------------

## Hospital

    Doctor
       │
    Appointment

Appointments reference valid doctors.

------------------------------------------------------------------------

## Online Shopping

    Customer
       │
    Order
       │
    OrderItem

Deleting a customer affects related orders depending on business rules.

------------------------------------------------------------------------

## University

    Student
       │
    Enrollment
       │
    Course

Enrollment connects valid students with valid courses.

------------------------------------------------------------------------

# 12. Common Mistakes

❌ Deleting parent rows without checking child rows.

❌ Creating orphan records.

❌ Assuming Foreign Keys guarantee uniqueness.

❌ Forgetting ON DELETE and ON UPDATE behavior.

------------------------------------------------------------------------

# 13. Referential Relationship vs Foreign Key

  Referential Relationship     Foreign Key
  ---------------------------- ---------------------------
  Concept                      Attribute/Constraint
  Describes table connection   Implements the connection
  Maintains consistency        Stores the reference

------------------------------------------------------------------------

# 14. Interview Questions

### Beginner

1.  What is a Referential Relationship?
2.  What is Referential Integrity?
3.  Why are Foreign Keys required?

### Intermediate

1.  Parent table vs Child table?
2.  Explain CASCADE and RESTRICT.

### Advanced

1.  What are orphan records?
2.  When should you use SET NULL instead of CASCADE?

------------------------------------------------------------------------

# 15. Practice Problems

1.  Design Customer and Order tables with proper referential
    relationships.

2.  Create Department and Employee tables.

3.  Predict the result of:

-   Parent delete with CASCADE
-   Parent delete with RESTRICT
-   Parent delete with SET NULL

4.  Identify whether referential integrity is violated.

------------------------------------------------------------------------

# Revision Notes

``` text
Primary Key
      │
Referenced By
      ▼
Foreign Key
      │
Referential Relationship
      │
Maintains
      ▼
Referential Integrity
```

## Memory Trick

``` text
Parent
    │
Reference
    ▼
Child
```

## Key Points

-   Referential Relationships connect related tables.
-   They are implemented using Foreign Keys.
-   Referential Integrity prevents invalid references.
-   Parent rows should not leave orphan child rows.
-   ON DELETE and ON UPDATE define how related data behaves.

**Remember:**

> Referential relationships ensure that related tables remain logically
> connected throughout the lifetime of the database. They protect data
> consistency automatically, sparing developers from manually checking
> every relationship. The database becomes the rule keeper, which is
> usually more reliable than hoping every application remembers every
> business rule forever.
