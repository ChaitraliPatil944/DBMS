# Lesson 123 --- PRIMARY KEY Constraint

> **Part 06 --- Structured Query Language (SQL)**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What a PRIMARY KEY is
-   Why PRIMARY KEY is important
-   Characteristics of a PRIMARY KEY
-   Creating primary keys
-   Single vs Composite Primary Keys
-   Internal indexing concepts
-   PRIMARY KEY vs UNIQUE
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Imagine a college with thousands of students.

Many students may have the same:

-   Name
-   Age
-   Department

How can we uniquely identify one student?

Using a unique **StudentID**.

That unique identifier is the role of a **PRIMARY KEY**.

------------------------------------------------------------------------

# 2. What is a PRIMARY KEY?

A **PRIMARY KEY** is a constraint that uniquely identifies every row in
a table.

Rules:

-   No duplicate values
-   No NULL values

``` text
Table
 │
PRIMARY KEY
 │
Unique Row
```

------------------------------------------------------------------------

# 3. Why Do We Need a PRIMARY KEY?

Without a primary key:

``` text
Name      Age
------------
Rahul     20
Rahul     20
Rahul     20
```

Which Rahul should be updated?

Impossible to know reliably.

With a primary key:

``` text
ID   Name
------------
101  Rahul
102  Rahul
103  Rahul
```

Each row is uniquely identifiable.

------------------------------------------------------------------------

# 4. Characteristics

A PRIMARY KEY:

-   Must be unique
-   Cannot contain NULL
-   One PRIMARY KEY per table
-   May consist of one or more columns
-   Is commonly indexed automatically by the DBMS

------------------------------------------------------------------------

# 5. Creating a PRIMARY KEY

Inline syntax:

``` sql
CREATE TABLE Student
(
    StudentID INT PRIMARY KEY,
    Name VARCHAR(100)
);
```

Table-level syntax:

``` sql
CREATE TABLE Student
(
    StudentID INT,
    Name VARCHAR(100),
    CONSTRAINT PK_Student
    PRIMARY KEY(StudentID)
);
```

------------------------------------------------------------------------

# 6. Composite PRIMARY KEY

A composite key uses multiple columns.

``` sql
CREATE TABLE Enrollment
(
    StudentID INT,
    CourseID INT,
    PRIMARY KEY(StudentID, CourseID)
);
```

``` text
StudentID + CourseID
        │
Unique Combination
```

------------------------------------------------------------------------

# 7. Internal Working

``` text
INSERT
   │
Check NULL?
   │
Check Duplicate?
   │
 ┌──────┴──────┐
 │             │
Valid       Invalid
 │             │
Stored      Error
```

The DBMS validates the key before inserting data.

------------------------------------------------------------------------

# 8. PRIMARY KEY vs UNIQUE

  PRIMARY KEY           UNIQUE
  --------------------- -------------------------------
  Only one per table    Multiple allowed
  No NULL values        NULL handling depends on DBMS
  Identifies each row   Enforces uniqueness only

------------------------------------------------------------------------

# 9. Real-World Example

Employee table:

``` sql
CREATE TABLE Employee
(
    EmployeeID INT PRIMARY KEY,
    Name VARCHAR(100),
    Department VARCHAR(50)
);
```

EmployeeID uniquely identifies every employee.

------------------------------------------------------------------------

# 10. Best Practices

-   Use stable values as primary keys.
-   Avoid meaningful values that may change.
-   Keep keys short.
-   Every table should normally have a PRIMARY KEY.

------------------------------------------------------------------------

# 11. Common Mistakes

❌ Using duplicate values.

❌ Allowing business data that changes frequently to be the primary key.

❌ Forgetting to define a PRIMARY KEY.

------------------------------------------------------------------------

# 12. Interview Questions

### Beginner

1.  What is a PRIMARY KEY?
2.  Can a PRIMARY KEY contain NULL?
3.  How many PRIMARY KEY constraints can a table have?

### Intermediate

1.  PRIMARY KEY vs UNIQUE?
2.  What is a composite PRIMARY KEY?

### Advanced

1.  Why are PRIMARY KEY columns often indexed?
2.  How do surrogate keys differ from natural keys?

------------------------------------------------------------------------

# 13. Practice Problems

1.  Create a Student table with StudentID as PRIMARY KEY.
2.  Create a composite PRIMARY KEY for Enrollment.
3.  Compare PRIMARY KEY and UNIQUE.
4.  Explain why every table should have a primary key.

------------------------------------------------------------------------

# Revision Notes

``` text
PRIMARY KEY
 │
Unique
 │
NOT NULL
 │
Identifies Every Row
```

## Memory Trick

``` text
PRIMARY KEY

=

Permanent

Row

Identifier

Making

All

Records

Yield

Uniqueness
```

## Key Points

-   PRIMARY KEY uniquely identifies each row.
-   It cannot contain NULL values.
-   Only one PRIMARY KEY exists per table.
-   Composite keys use multiple columns.
-   PRIMARY KEY improves integrity and efficient row identification.

------------------------------------------------------------------------

# Final Takeaway

The PRIMARY KEY is the identity of a table. It guarantees that every row
can be uniquely located, updated, or related to other tables. Nearly
every relational database design begins by deciding what the primary key
should be, because without a reliable identity, relationships and data
integrity quickly become difficult to maintain.
