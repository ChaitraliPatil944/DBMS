# Lesson 096 --- CREATE Statement

> **Part 06 --- Structured Query Language (SQL)**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What the `CREATE` statement is
-   Why the `CREATE` statement is used
-   Creating databases
-   Creating tables
-   Creating tables with data types
-   Creating tables with constraints
-   Best practices
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Before storing any data, a database must know **where** the data will be
stored.

The `CREATE` statement builds those database objects.

Think of it as constructing an empty house before moving furniture
inside.

------------------------------------------------------------------------

# 2. What is the CREATE Statement?

The **CREATE** statement is a DDL command used to create new database
objects such as:

-   Databases
-   Tables
-   Views
-   Indexes
-   Schemas

``` text
CREATE
   │
New Database Object
```

------------------------------------------------------------------------

# 3. Why Do We Need CREATE?

Without `CREATE`:

-   No database exists.
-   No tables exist.
-   No columns exist.

Everything in a relational database begins with a `CREATE` statement.

------------------------------------------------------------------------

# 4. CREATE DATABASE

General syntax:

``` sql
CREATE DATABASE CollegeDB;
```

Result:

``` text
CollegeDB
│
(No tables yet)
```

------------------------------------------------------------------------

# 5. CREATE TABLE

General syntax:

``` sql
CREATE TABLE TableName(
    Column1 DataType,
    Column2 DataType
);
```

Example:

``` sql
CREATE TABLE Student(
    StudentID INT,
    Name VARCHAR(100),
    Age INT
);
```

------------------------------------------------------------------------

# 6. CREATE TABLE with Constraints

``` sql
CREATE TABLE Student(
    StudentID INT PRIMARY KEY,
    Name VARCHAR(100) NOT NULL,
    Email VARCHAR(100) UNIQUE,
    Age INT CHECK (Age >= 16),
    Country VARCHAR(50) DEFAULT 'India'
);
```

------------------------------------------------------------------------

# 7. Understanding the Statement

``` text
CREATE TABLE Student
        │
        ├── StudentID → INT → PRIMARY KEY
        ├── Name → VARCHAR → NOT NULL
        ├── Email → UNIQUE
        ├── Age → CHECK
        └── Country → DEFAULT
```

------------------------------------------------------------------------

# 8. Real-World Example

Employee table:

``` sql
CREATE TABLE Employee(
    EmployeeID INT PRIMARY KEY,
    Name VARCHAR(100) NOT NULL,
    Department VARCHAR(50),
    Salary DECIMAL(10,2),
    JoiningDate DATE
);
```

------------------------------------------------------------------------

# 9. Best Practices

-   Use meaningful table names.
-   Choose appropriate data types.
-   Add constraints wherever necessary.
-   Use consistent naming conventions.
-   Keep table designs simple and normalized.

------------------------------------------------------------------------

# 10. Common Mistakes

❌ Forgetting commas.

❌ Missing parentheses.

❌ Choosing incorrect data types.

❌ Creating tables without a PRIMARY KEY.

❌ Ignoring constraints.

------------------------------------------------------------------------

# 11. Interview Questions

### Beginner

1.  What is the CREATE statement?
2.  Is CREATE a DDL or DML command?
3.  What objects can CREATE generate?

### Intermediate

1.  CREATE DATABASE vs CREATE TABLE?
2.  Why should every table have a PRIMARY KEY?

### Advanced

1.  Why is table design important before inserting data?
2.  What factors influence column data type selection?

------------------------------------------------------------------------

# 12. Practice Problems

1.  Create a `Student` table.
2.  Create an `Employee` table with a PRIMARY KEY.
3.  Create a `Product` table using:
    -   PRIMARY KEY
    -   NOT NULL
    -   UNIQUE
    -   CHECK
    -   DEFAULT
4.  Create a database named `LibraryDB`.

------------------------------------------------------------------------

# Revision Notes

``` text
CREATE
│
├── DATABASE
├── TABLE
├── VIEW
├── INDEX
└── SCHEMA
```

## Memory Trick

``` text
CREATE

=

Construct Before Using
```

## Key Points

-   `CREATE` is a DDL command.
-   It creates new database objects.
-   `CREATE TABLE` defines columns, data types, and constraints.
-   Good table design improves performance and maintainability.
-   Constraints should be added during table creation whenever possible.

------------------------------------------------------------------------

# Final Takeaway

The `CREATE` statement is the starting point of every relational
database. It transforms a design into a real database structure by
defining tables, columns, data types, and constraints. A carefully
written `CREATE TABLE` statement saves countless hours of redesign
later, because changing a schema after it contains millions of records
is considerably harder than planning it well from the beginning.
