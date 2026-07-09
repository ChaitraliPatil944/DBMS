# Lesson 095 --- DDL (Data Definition Language) Overview

> **Part 06 --- Structured Query Language (SQL)**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What DDL is
-   Why DDL is important
-   Database schema and metadata
-   Major DDL commands
-   DDL vs DML vs DQL
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Imagine constructing a new house.

Before anyone can live in it, you must build:

-   Rooms
-   Doors
-   Windows
-   Walls

Similarly, before storing data, a database needs its structure.

DDL is used to build and manage that structure.

------------------------------------------------------------------------

# 2. What is DDL?

**DDL (Data Definition Language)** is the collection of SQL commands
used to create, modify, rename, truncate, and delete database objects.

DDL mainly works on:

-   Databases
-   Tables
-   Views
-   Indexes
-   Schemas

``` text
DDL
 │
Database Structure
 │
Tables & Objects
```

------------------------------------------------------------------------

# 3. Why Do We Need DDL?

Without DDL:

-   No tables exist.
-   No columns exist.
-   No relationships exist.

DDL allows us to design the blueprint of the database before data is
stored.

------------------------------------------------------------------------

# 4. Child-Friendly Analogy

Think of building a school.

First you construct:

``` text
Classrooms
Library
Laboratory
Office
```

Only after construction can students and teachers use it.

DDL constructs the database in the same way.

------------------------------------------------------------------------

# 5. Database Schema

A **schema** is the logical design of a database.

It defines:

-   Table names
-   Column names
-   Data types
-   Constraints
-   Relationships

``` text
Schema
   │
Tables
   │
Columns
   │
Constraints
```

DDL creates and modifies this schema.

------------------------------------------------------------------------

# 6. What is Metadata?

**Metadata** means **data about data**.

Example:

``` text
Table Name : Student

Columns

StudentID INT
Name VARCHAR(100)
Age INT
```

The actual student records are data.

The table definition is metadata.

------------------------------------------------------------------------

# 7. Major DDL Commands

``` text
DDL
│
├── CREATE
├── ALTER
├── DROP
├── TRUNCATE
└── RENAME
```

Each command has a different purpose.

------------------------------------------------------------------------

# 8. DDL Command Overview

## CREATE

Creates new database objects.

``` sql
CREATE TABLE Student(
    StudentID INT
);
```

------------------------------------------------------------------------

## ALTER

Modifies an existing object.

``` sql
ALTER TABLE Student
ADD Email VARCHAR(100);
```

------------------------------------------------------------------------

## DROP

Deletes an object permanently.

``` sql
DROP TABLE Student;
```

------------------------------------------------------------------------

## TRUNCATE

Deletes all rows while keeping the table structure.

``` sql
TRUNCATE TABLE Student;
```

------------------------------------------------------------------------

## RENAME

Changes an object's name.

``` sql
RENAME TABLE Student TO Students;
```

------------------------------------------------------------------------

# 9. DDL vs DML vs DQL

  DDL                 DML            DQL
  ------------------- -------------- ----------------
  Defines structure   Changes data   Retrieves data
  CREATE              INSERT         SELECT
  ALTER               UPDATE         WHERE
  DROP                DELETE         ORDER BY

------------------------------------------------------------------------

# 10. DDL Characteristics

-   Defines database structure
-   Usually changes metadata
-   Often auto-commits in many DBMSs
-   Does not normally manipulate individual rows
-   Used by developers and DBAs

------------------------------------------------------------------------

# 11. Real-World Example

Creating an Employee table:

``` sql
CREATE TABLE Employee(
    EmployeeID INT PRIMARY KEY,
    Name VARCHAR(100),
    Salary DECIMAL(10,2)
);
```

Flow:

``` text
Developer
    │
DDL Command
    │
DBMS
    │
Creates Table
```

------------------------------------------------------------------------

# 12. Common Mistakes

❌ Confusing DDL with DML.

❌ Thinking TRUNCATE deletes the table.

❌ Using DROP when only the data should be removed.

Remember:

``` text
DROP
=
Deletes table

TRUNCATE
=
Deletes rows only
```

------------------------------------------------------------------------

# 13. Interview Questions

### Beginner

1.  What is DDL?
2.  Name the major DDL commands.
3.  What is a schema?

### Intermediate

1.  What is metadata?
2.  DROP vs TRUNCATE?

### Advanced

1.  Why do many DDL commands auto-commit?
2.  Why is DDL considered structural rather than operational?

------------------------------------------------------------------------

# 14. Practice Problems

1.  List five DDL commands.
2.  Differentiate DDL, DML, and DQL.
3.  Explain schema and metadata.
4.  Identify when to use CREATE, ALTER, DROP, and TRUNCATE.

------------------------------------------------------------------------

# Revision Notes

``` text
DDL
 │
Structure
 │
CREATE
ALTER
DROP
TRUNCATE
RENAME
```

## Memory Trick

``` text
C A D T R

CREATE
ALTER
DROP
TRUNCATE
RENAME
```

## Key Points

-   DDL defines database structure.
-   DDL works on metadata.
-   CREATE builds new objects.
-   ALTER modifies existing objects.
-   DROP removes objects.
-   TRUNCATE removes all rows while preserving structure.
-   RENAME changes object names.

------------------------------------------------------------------------

# Final Takeaway

DDL is the foundation of database design. Before a database can store
meaningful information, its structure must be carefully planned and
created. Every table, column, constraint, and relationship begins with
DDL commands. Good database design starts with a solid blueprint,
because changing the foundation after a building is full of occupants is
rarely anyone's favorite task.
