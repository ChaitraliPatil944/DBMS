# Lesson 097 --- ALTER Statement

> **Part 06 --- Structured Query Language (SQL)**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What the `ALTER` statement is
-   Why `ALTER` is required
-   Adding columns
-   Modifying columns
-   Dropping columns
-   Renaming columns
-   Adding and dropping constraints
-   Best practices
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Imagine a school database.

Initially:

``` text
Student
---------
ID
Name
Age
```

Later the school decides to store:

``` text
Email
```

Should we recreate the entire table?

No.

We modify the existing table using **ALTER**.

------------------------------------------------------------------------

# 2. What is ALTER?

`ALTER` is a **DDL (Data Definition Language)** command used to modify
the structure of an existing database object.

It can:

-   Add columns
-   Modify columns
-   Drop columns
-   Rename columns
-   Add constraints
-   Remove constraints

``` text
Existing Table
      │
    ALTER
      │
Modified Table
```

------------------------------------------------------------------------

# 3. Why Do We Need ALTER?

Business requirements change.

Examples:

-   New employee fields
-   Additional customer details
-   Updated business rules
-   New constraints

Instead of recreating tables, we alter them.

------------------------------------------------------------------------

# 4. ALTER TABLE Syntax

``` sql
ALTER TABLE table_name
action;
```

------------------------------------------------------------------------

# 5. Adding a Column

``` sql
ALTER TABLE Student
ADD Email VARCHAR(100);
```

Before:

``` text
StudentID
Name
Age
```

After:

``` text
StudentID
Name
Age
Email
```

------------------------------------------------------------------------

# 6. Modifying a Column

Change the data type or properties.

Example (syntax varies by DBMS):

``` sql
ALTER TABLE Student
MODIFY Name VARCHAR(150);
```

SQL Server uses:

``` sql
ALTER TABLE Student
ALTER COLUMN Name VARCHAR(150);
```

------------------------------------------------------------------------

# 7. Dropping a Column

``` sql
ALTER TABLE Student
DROP COLUMN Age;
```

After execution:

``` text
StudentID
Name
Email
```

------------------------------------------------------------------------

# 8. Renaming a Column

Different DBMSs use different syntax.

Example:

``` sql
ALTER TABLE Student
RENAME COLUMN Name TO FullName;
```

(Some systems use `sp_rename` or other syntax.)

------------------------------------------------------------------------

# 9. Adding Constraints

``` sql
ALTER TABLE Student
ADD CONSTRAINT PK_Student
PRIMARY KEY(StudentID);
```

Add a CHECK constraint:

``` sql
ALTER TABLE Student
ADD CONSTRAINT CHK_Age
CHECK (Age >= 18);
```

------------------------------------------------------------------------

# 10. Dropping Constraints

Example:

``` sql
ALTER TABLE Student
DROP CONSTRAINT PK_Student;
```

Constraint removal syntax differs slightly across DBMSs.

------------------------------------------------------------------------

# 11. Real-World Example

Employee table initially:

``` text
EmployeeID
Name
Salary
```

Company later requires:

-   Email
-   Department
-   Salary must be positive

SQL:

``` sql
ALTER TABLE Employee
ADD Email VARCHAR(100);

ALTER TABLE Employee
ADD Department VARCHAR(50);

ALTER TABLE Employee
ADD CONSTRAINT CHK_Salary
CHECK (Salary >= 0);
```

------------------------------------------------------------------------

# 12. Best Practices

-   Back up important databases before structural changes.
-   Test ALTER statements in development first.
-   Use meaningful constraint names.
-   Avoid unnecessary schema changes in production.
-   Schedule major alterations during low-traffic periods.

------------------------------------------------------------------------

# 13. Common Mistakes

❌ Dropping a column without checking dependencies.

❌ Reducing column size and causing data loss.

❌ Forgetting that syntax differs among DBMSs.

❌ Altering production databases without backups.

------------------------------------------------------------------------

# 14. Interview Questions

### Beginner

1.  What is the ALTER statement?
2.  Is ALTER a DDL or DML command?
3.  What operations can ALTER perform?

### Intermediate

1.  ADD vs MODIFY?
2.  MODIFY vs ALTER COLUMN?
3.  Why is ALTER preferred over recreating a table?

### Advanced

1.  What precautions should be taken before altering production tables?
2.  Why does ALTER syntax differ between DBMSs?

------------------------------------------------------------------------

# 15. Practice Problems

1.  Add a PhoneNumber column to Student.
2.  Increase Name length to 200 characters.
3.  Remove the Address column.
4.  Add a CHECK constraint for Salary.
5.  Rename Name to FullName.

------------------------------------------------------------------------

# Revision Notes

``` text
ALTER
│
├── ADD
├── MODIFY / ALTER COLUMN
├── DROP COLUMN
├── RENAME COLUMN
├── ADD CONSTRAINT
└── DROP CONSTRAINT
```

## Memory Trick

``` text
A M D R C

Add
Modify
Drop
Rename
Constraints
```

## Key Points

-   `ALTER` modifies existing database objects.
-   It is a DDL command.
-   It supports structural changes without recreating tables.
-   Syntax differs slightly between database systems.
-   Always evaluate the impact of schema changes before applying them.

------------------------------------------------------------------------

# Final Takeaway

The `ALTER` statement gives a database the flexibility to evolve as
business requirements change. Few real-world systems remain unchanged
for long, so knowing how to safely modify an existing schema is an
essential SQL skill. A well-planned alteration is far less disruptive
than rebuilding an entire database simply because one new column became
necessary.
