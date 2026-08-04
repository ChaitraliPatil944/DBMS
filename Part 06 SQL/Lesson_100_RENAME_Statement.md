# Lesson 100 --- RENAME Statement

> **Part 06 --- Structured Query Language (SQL)**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What the `RENAME` statement is
-   Why renaming database objects is important
-   Renaming tables
-   Renaming columns
-   Renaming databases (DBMS-specific)
-   DBMS syntax differences
-   Best practices
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Imagine a school changes the name of a department from:

``` text
Computer Science

↓

Computer Science & Engineering
```

The department is the same.

Only its name changes.

The `RENAME` statement works in the same way.

------------------------------------------------------------------------

# 2. What is the RENAME Statement?

`RENAME` is a DDL command used to change the name of an existing
database object without changing its data.

It can rename:

-   Tables
-   Columns
-   Views
-   Indexes
-   Constraints (DBMS dependent)

``` text
Old Name
   │
RENAME
   │
New Name
```

------------------------------------------------------------------------

# 3. Why Do We Need RENAME?

Business requirements evolve.

Examples:

-   Better naming conventions
-   Correct spelling mistakes
-   Reflect new business terminology
-   Improve readability

Instead of recreating an object, we rename it.

------------------------------------------------------------------------

# 4. Renaming a Table

General syntax (varies by DBMS):

``` sql
RENAME TABLE Student TO Students;
```

PostgreSQL:

``` sql
ALTER TABLE Student
RENAME TO Students;
```

------------------------------------------------------------------------

# 5. Renaming a Column

Example:

``` sql
ALTER TABLE Student
RENAME COLUMN Name TO FullName;
```

SQL Server commonly uses:

``` sql
EXEC sp_rename
'Student.Name',
'FullName',
'COLUMN';
```

------------------------------------------------------------------------

# 6. Renaming a Database

Support differs between DBMSs.

Example (SQL Server):

``` sql
ALTER DATABASE CollegeDB
MODIFY NAME = UniversityDB;
```

Many production systems avoid database renaming because applications may
depend on the original name.

------------------------------------------------------------------------

# 7. Before and After

Before:

``` text
Student
--------
StudentID
Name
Age
```

Rename column:

``` text
Student
--------
StudentID
FullName
Age
```

Rename table:

``` text
Students
---------
StudentID
FullName
Age
```

------------------------------------------------------------------------

# 8. DBMS Syntax Differences

  ----------------------------------------------------------------------------
  DBMS         Table Rename                  Column Rename
  ------------ ----------------------------- ---------------------------------
  MySQL        `RENAME TABLE`                `ALTER TABLE`

  PostgreSQL   `ALTER TABLE ... RENAME TO`   `ALTER TABLE ... RENAME COLUMN`

  SQL Server   `sp_rename` / `ALTER`         `sp_rename`

  Oracle       `RENAME`                      `ALTER TABLE`
  ----------------------------------------------------------------------------

Always consult your DBMS documentation.

------------------------------------------------------------------------

# 9. Real-World Example

A company decides that `Customer` should become `Client`.

``` sql
ALTER TABLE Customer
RENAME TO Client;
```

The data remains unchanged.

Applications should be updated to use the new name.

------------------------------------------------------------------------

# 10. Best Practices

-   Use meaningful names.
-   Follow consistent naming conventions.
-   Rename during maintenance windows.
-   Update application code and documentation.
-   Test after renaming.

------------------------------------------------------------------------

# 11. Common Mistakes

❌ Assuming every DBMS uses identical syntax.

❌ Forgetting to update stored procedures, views, or application code.

❌ Renaming objects without checking dependencies.

------------------------------------------------------------------------

# 12. Interview Questions

### Beginner

1.  What is the `RENAME` statement?
2.  Does renaming affect stored data?
3.  Can tables and columns be renamed?

### Intermediate

1.  Why does syntax differ among DBMSs?
2.  Why is renaming safer than recreating a table?

### Advanced

1.  What problems can occur after renaming a table?
2.  How would you safely rename a production table?

------------------------------------------------------------------------

# 13. Practice Problems

1.  Rename `Student` to `Students`.
2.  Rename `Name` to `FullName`.
3.  Research the rename syntax for your preferred DBMS.
4.  List objects that may break after a table rename.

------------------------------------------------------------------------

# Revision Notes

``` text
RENAME
│
├── TABLE
├── COLUMN
├── VIEW
├── INDEX
└── DATABASE (DBMS specific)
```

## Memory Trick

``` text
RENAME

=

Same Object

New Name
```

## Key Points

-   `RENAME` changes an object's name, not its data.
-   Syntax differs across DBMSs.
-   Renaming can affect dependent applications and database objects.
-   Plan and test renames carefully.

------------------------------------------------------------------------

# Final Takeaway

The `RENAME` statement improves clarity without rebuilding database
objects. Good names make schemas easier to understand and maintain, but
renaming should always be planned because other parts of the system may
depend on the original names. A database remembers relationships
faithfully, but applications are less forgiving when the object they
expect suddenly answers to a different name.
