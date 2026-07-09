# Lesson 080 --- FOREIGN KEY Constraint

> **Part 05 --- Constraints**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What the FOREIGN KEY constraint is
-   Why FOREIGN KEY constraints are important
-   Parent Table vs Child Table
-   Referential Integrity
-   FOREIGN KEY vs PRIMARY KEY
-   ON DELETE and ON UPDATE actions
-   SQL implementation
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Suppose we have two tables:

``` text
Student
----------------
StudentID
101
102

Enrollment
-------------------------
EnrollmentID  StudentID
1             101
2             999
```

Student **999** does not exist.

The Enrollment table now contains an invalid reference.

The **FOREIGN KEY** constraint prevents this.

------------------------------------------------------------------------

# 2. What is the FOREIGN KEY Constraint?

A **FOREIGN KEY** is a constraint that ensures values in one table
reference valid values in another table.

It creates a relationship between tables.

``` text
Parent Table
      │
Primary Key
      │
      ▼
Foreign Key
      │
Child Table
```

------------------------------------------------------------------------

# 3. Why Do We Need It?

Without a FOREIGN KEY:

-   Invalid references appear.
-   Orphan records are created.
-   Data becomes inconsistent.
-   Reports become unreliable.

With a FOREIGN KEY:

-   Relationships stay valid.
-   Invalid references are rejected.
-   Referential Integrity is maintained.

------------------------------------------------------------------------

# 4. Parent Table vs Child Table

``` text
Department
-----------------
DepartmentID
10
20

        │
        ▼

Employee
----------------------------
EmployeeID  DepartmentID
101         10
102         20
```

-   Department → Parent Table
-   Employee → Child Table

------------------------------------------------------------------------

# 5. Referential Integrity

A FOREIGN KEY ensures that every child row references an existing parent
row.

Valid:

``` text
DepartmentID = 10 ✔
```

Invalid:

``` text
DepartmentID = 99 ✘
```

if department 99 does not exist.

------------------------------------------------------------------------

# 6. SQL Implementation

``` sql
CREATE TABLE Department(
    DepartmentID INT PRIMARY KEY,
    DepartmentName VARCHAR(100)
);

CREATE TABLE Employee(
    EmployeeID INT PRIMARY KEY,
    Name VARCHAR(100),
    DepartmentID INT,
    CONSTRAINT FK_Department
    FOREIGN KEY (DepartmentID)
    REFERENCES Department(DepartmentID)
);
```

------------------------------------------------------------------------

# 7. FOREIGN KEY Validation

``` text
New Child Row
      │
      ▼
Parent Exists?
      │
 ┌────┴────┐
 │         │
Yes       No
 │         │
 ▼         ▼
Store   Reject
```

------------------------------------------------------------------------

# 8. ON DELETE Actions

## CASCADE

Delete parent.

↓

Delete related child rows.

------------------------------------------------------------------------

## RESTRICT

Prevent parent deletion.

------------------------------------------------------------------------

## NO ACTION

Reject deletion if relationships break.

------------------------------------------------------------------------

## SET NULL

Parent deleted.

↓

Child FOREIGN KEY becomes NULL.

------------------------------------------------------------------------

## SET DEFAULT

Child FOREIGN KEY becomes its default value.

(Not supported by every DBMS.)

------------------------------------------------------------------------

# 9. ON UPDATE Actions

If the parent key changes:

-   CASCADE → Child updates automatically.
-   RESTRICT → Update blocked.
-   NO ACTION → Reject invalid update.
-   SET NULL → Child value becomes NULL.

------------------------------------------------------------------------

# 10. FOREIGN KEY vs PRIMARY KEY

  PRIMARY KEY       FOREIGN KEY
  ----------------- --------------------
  Identifies rows   References rows
  Must be unique    Duplicates allowed
  NOT NULL          May allow NULL
  One per table     Multiple allowed

------------------------------------------------------------------------

# 11. Real-World Examples

## Banking

``` text
Customer
    │
Account
```

CustomerID is a FOREIGN KEY in Account.

------------------------------------------------------------------------

## Hospital

``` text
Doctor
    │
Appointment
```

DoctorID links appointments to doctors.

------------------------------------------------------------------------

## University

``` text
Student
    │
Enrollment
```

StudentID connects enrollments to students.

------------------------------------------------------------------------

## E-commerce

``` text
Customer
    │
Orders
    │
OrderItems
```

Relationships are enforced through FOREIGN KEY constraints.

------------------------------------------------------------------------

# 12. Advantages

-   Maintains Referential Integrity
-   Prevents orphan records
-   Improves consistency
-   Supports relational design
-   Reduces data errors

------------------------------------------------------------------------

# 13. Common Mistakes

❌ Referencing a value that does not exist.

❌ Deleting parent rows without considering child rows.

❌ Assuming FOREIGN KEY values must be unique.

❌ Forgetting ON DELETE behavior.

------------------------------------------------------------------------

# 14. Interview Questions

### Beginner

1.  What is a FOREIGN KEY?
2.  Why is it used?
3.  Can a table have multiple FOREIGN KEY constraints?

### Intermediate

1.  FOREIGN KEY vs PRIMARY KEY?
2.  Explain Referential Integrity.

### Advanced

1.  Explain CASCADE, RESTRICT, SET NULL, and NO ACTION.
2.  Can a FOREIGN KEY reference a UNIQUE Candidate Key?

------------------------------------------------------------------------

# 15. Practice Problems

1.  Create Customer and Orders tables using a FOREIGN KEY.
2.  Create Student and Enrollment tables.
3.  Predict the result of:
    -   ON DELETE CASCADE
    -   ON DELETE RESTRICT
    -   ON DELETE SET NULL
4.  Identify Referential Integrity violations.

------------------------------------------------------------------------

# Revision Notes

``` text
Parent Table
      │
Primary Key
      │
      ▼
FOREIGN KEY
      │
Child Table
      │
Referential Integrity
```

## Memory Trick

``` text
FOREIGN

=

Reference
```

## Key Points

-   FOREIGN KEY connects related tables.
-   It references a PRIMARY KEY or UNIQUE Candidate Key.
-   It enforces Referential Integrity.
-   Multiple FOREIGN KEY constraints can exist in one table.
-   ON DELETE and ON UPDATE define relationship behavior.

------------------------------------------------------------------------

# Final Takeaway

The **FOREIGN KEY** constraint is what transforms independent tables
into a true relational database. It guarantees that every relationship
stored in the database is valid and consistent. By enforcing Referential
Integrity automatically, the DBMS prevents broken references and keeps
related data synchronized throughout the lifetime of the application.
