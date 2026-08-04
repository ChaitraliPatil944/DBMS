# Lesson 076 --- Referential Integrity Constraint

> **Part 05 --- Constraints**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What Referential Integrity is
-   Why Referential Integrity is needed
-   Parent Table vs Child Table
-   Primary Key and Foreign Key relationship
-   Orphan records
-   ON DELETE and ON UPDATE actions
-   SQL implementation
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Consider these tables:

``` text
Student
----------------
StudentID
101
102
103

Enrollment
-------------------------
EnrollmentID  StudentID
1             101
2             999
```

Student **999** does not exist.

The Enrollment table now contains invalid data.

This is prevented by **Referential Integrity**.

------------------------------------------------------------------------

# 2. What is Referential Integrity?

**Referential Integrity** is a rule that ensures every **Foreign Key**
value either:

-   References an existing Primary Key (or UNIQUE Candidate Key), or
-   Is `NULL` (if NULL values are allowed).

It keeps relationships between tables valid.

------------------------------------------------------------------------

# 3. Why Do We Need Referential Integrity?

Without it:

-   Orphan records appear.
-   Relationships become invalid.
-   Reports become inaccurate.
-   Applications return incorrect results.

With it:

-   Relationships remain consistent.
-   Invalid references are rejected.
-   Data quality improves.

------------------------------------------------------------------------

# 4. Parent Table vs Child Table

``` text
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
```

-   **Department** → Parent Table
-   **Employee** → Child Table
-   `DepartmentID` in Employee is a Foreign Key.

------------------------------------------------------------------------

# 5. How Referential Integrity Works

``` text
Parent Row Exists?
        │
   ┌────┴────┐
   │         │
  Yes       No
   │         │
   ▼         ▼
Insert    Reject
```

The DBMS validates every Foreign Key before storing the row.

------------------------------------------------------------------------

# 6. Orphan Records

An **orphan record** is a child row whose parent no longer exists.

Example:

``` text
Department
----------------
10

Employee
----------------
101  10
```

Delete Department 10 without handling Employee.

Result:

``` text
Employee
101  10
```

The employee now points to nothing.

This violates Referential Integrity.

------------------------------------------------------------------------

# 7. ON DELETE Actions

## CASCADE

Delete parent.

↓

Delete related child rows automatically.

------------------------------------------------------------------------

## RESTRICT

Prevent parent deletion while child rows exist.

------------------------------------------------------------------------

## NO ACTION

Reject the operation if it violates integrity.

------------------------------------------------------------------------

## SET NULL

Delete parent.

↓

Foreign Key becomes `NULL`.

Requires the Foreign Key column to allow NULL values.

------------------------------------------------------------------------

## SET DEFAULT

Foreign Key becomes its default value.

Supported only in some DBMSs.

------------------------------------------------------------------------

# 8. ON UPDATE Actions

If the Primary Key changes:

-   CASCADE → Update child rows
-   RESTRICT → Prevent update
-   SET NULL → Child becomes NULL
-   NO ACTION → Reject operation

------------------------------------------------------------------------

# 9. SQL Implementation

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

# 10. Referential Integrity vs Entity Integrity

  Entity Integrity    Referential Integrity
  ------------------- --------------------------------
  Identifies rows     Connects rows
  Primary Key         Foreign Key
  PK cannot be NULL   FK must reference valid parent

------------------------------------------------------------------------

# 11. Real-World Examples

### Banking

Customer → Account

Only existing customers can own accounts.

### Hospital

Doctor → Appointment

Appointments must reference valid doctors.

### University

Student → Enrollment

Only registered students can enroll.

### E-commerce

Customer → Orders

Every order belongs to an existing customer.

------------------------------------------------------------------------

# 12. Advantages

-   Prevents orphan records
-   Protects relationships
-   Improves consistency
-   Maintains data integrity
-   Reduces application errors

------------------------------------------------------------------------

# 13. Common Mistakes

❌ Deleting parent rows without considering children.

❌ Inserting invalid Foreign Key values.

❌ Assuming Foreign Keys automatically become unique.

------------------------------------------------------------------------

# 14. Interview Questions

### Beginner

1.  What is Referential Integrity?
2.  Why is it important?
3.  What is an orphan record?

### Intermediate

1.  Parent table vs Child table?
2.  Explain CASCADE and RESTRICT.

### Advanced

1.  When should SET NULL be used?
2.  Difference between Entity Integrity and Referential Integrity?

------------------------------------------------------------------------

# 15. Practice Problems

1.  Design Customer and Order tables with Referential Integrity.

2.  Predict the result of:

-   ON DELETE CASCADE
-   ON DELETE RESTRICT
-   ON DELETE SET NULL

3.  Identify violations in the following schema.

------------------------------------------------------------------------

# Revision Notes

``` text
Parent Table
      │
Primary Key
      │
      ▼
Foreign Key
      │
Child Table
      │
Referential Integrity
```

## Memory Trick

``` text
Reference

↓

Relationship

↓

Reliability
```

## Key Points

-   Referential Integrity protects relationships between tables.
-   It is enforced using Foreign Keys.
-   Child rows cannot reference missing parent rows.
-   ON DELETE and ON UPDATE define how related data behaves.
-   It prevents orphan records.

------------------------------------------------------------------------

# Final Takeaway

Referential Integrity is the rule that keeps related tables synchronized
and trustworthy. It ensures that every relationship stored in the
database points to something real. Without it, a relational database
quickly turns into a collection of disconnected records with broken
references. Databases are very good at remembering relationships,
provided we give them rules worth following.
