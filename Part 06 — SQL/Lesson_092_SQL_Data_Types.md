# Lesson 092 --- SQL Data Types

> **Part 06 --- Structured Query Language (SQL)**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What SQL data types are
-   Why data types are important
-   Categories of SQL data types
-   Numeric, character, date/time, boolean and binary types
-   CHAR vs VARCHAR
-   DATE vs DATETIME vs TIMESTAMP
-   Real-world usage
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Why Do We Need Data Types?

Imagine storing these values:

``` text
Age = Twenty
Name = 12345
BirthDate = Apple
```

The database cannot correctly process meaningless values.

A **data type** tells the DBMS what kind of data a column can store.

------------------------------------------------------------------------

# 2. What is a Data Type?

A **data type** defines:

-   The kind of value allowed
-   Storage requirements
-   Valid operations

``` text
Column
   │
Data Type
   │
Valid Data
```

------------------------------------------------------------------------

# 3. Categories of SQL Data Types

``` text
SQL Data Types
│
├── Numeric
├── Character
├── Date & Time
├── Boolean
└── Binary / Large Objects
```

------------------------------------------------------------------------

# 4. Numeric Data Types

  Data Type      Purpose                         Example
  -------------- ------------------------------- ------------
  INT            Whole numbers                   25
  BIGINT         Very large integers             9876543210
  SMALLINT       Small integers                  120
  DECIMAL(p,s)   Exact decimal values            1234.56
  FLOAT          Approximate decimal             3.14159
  DOUBLE         High precision floating point   99.999999

Example:

``` sql
Salary DECIMAL(10,2),
Age INT
```

------------------------------------------------------------------------

# 5. Character Data Types

  Type         Description
  ------------ ----------------------
  CHAR(n)      Fixed-length text
  VARCHAR(n)   Variable-length text
  TEXT         Large text

Example:

``` sql
Name VARCHAR(100),
Country CHAR(2)
```

------------------------------------------------------------------------

# 6. CHAR vs VARCHAR

  CHAR                           VARCHAR
  ------------------------------ --------------------------------
  Fixed length                   Variable length
  Pads unused spaces             Stores only entered characters
  Faster for fixed-size values   Saves storage

Example:

``` text
CHAR(10)

ABC_______

VARCHAR(10)

ABC
```

------------------------------------------------------------------------

# 7. Date & Time Data Types

  Type        Stores
  ----------- ---------------------------------------------------
  DATE        Date only
  TIME        Time only
  DATETIME    Date + Time
  TIMESTAMP   Date + Time with automatic tracking in many DBMSs

Example:

``` sql
BirthDate DATE,
CreatedAt TIMESTAMP
```

------------------------------------------------------------------------

# 8. DATE vs DATETIME vs TIMESTAMP

  DATE        DATETIME        TIMESTAMP
  ----------- --------------- ----------------------------------------
  Date only   Date and time   Date and time, often used for auditing

------------------------------------------------------------------------

# 9. Boolean Data Type

Stores logical values.

``` text
TRUE
FALSE
```

Example:

``` sql
IsActive BOOLEAN
```

(Some DBMSs implement this internally as 0 and 1.)

------------------------------------------------------------------------

# 10. Binary Data Types

Used for files and binary content.

Examples:

-   Images
-   PDFs
-   Videos
-   Audio

Common types:

``` text
BLOB
BYTEA
VARBINARY
```

------------------------------------------------------------------------

# 11. Real-World Example

``` sql
CREATE TABLE Employee(
    EmployeeID INT,
    Name VARCHAR(100),
    Salary DECIMAL(10,2),
    JoiningDate DATE,
    IsActive BOOLEAN
);
```

------------------------------------------------------------------------

# 12. Choosing the Right Data Type

``` text
Whole Number?
     │
    INT

Money?
     │
 DECIMAL

Name?
     │
VARCHAR

Date?
     │
 DATE

True/False?
     │
BOOLEAN
```

------------------------------------------------------------------------

# 13. Common Mistakes

❌ Using `VARCHAR` for numeric calculations.

❌ Using `FLOAT` for money.

❌ Using `CHAR` for long variable-length text.

❌ Choosing unnecessarily large data types.

------------------------------------------------------------------------

# 14. Interview Questions

### Beginner

1.  What is a data type?
2.  Why are data types important?
3.  Name the major categories.

### Intermediate

1.  CHAR vs VARCHAR?
2.  INT vs DECIMAL?
3.  DATE vs TIMESTAMP?

### Advanced

1.  Why shouldn't money be stored as FLOAT?
2.  How do data types affect storage and performance?

------------------------------------------------------------------------

# 15. Practice Problems

1.  Choose suitable data types for:

    -   Student Name
    -   Age
    -   Salary
    -   Date of Birth
    -   Email
    -   Product Image

2.  Write a CREATE TABLE statement using at least five different data
    types.

3.  Explain why VARCHAR is preferred over CHAR for names.

------------------------------------------------------------------------

# Revision Notes

``` text
Numeric
│
INT
DECIMAL

Character
│
CHAR
VARCHAR
TEXT

Date & Time
│
DATE
TIME
DATETIME
TIMESTAMP

Boolean
│
TRUE/FALSE

Binary
│
BLOB
```

## Memory Trick

``` text
N C D B B

Numeric
Character
Date
Boolean
Binary
```

## Key Points

-   Data types define what values a column can store.
-   Choosing the correct data type improves storage efficiency and
    performance.
-   Use DECIMAL for money.
-   Use VARCHAR for variable-length text.
-   Use DATE or TIMESTAMP depending on the requirement.

------------------------------------------------------------------------

# Final Takeaway

Choosing the right data type is one of the first and most important
decisions in database design. It affects storage, validation,
performance, and future scalability. A well-designed schema starts with
columns that accurately represent the real-world data they hold, because
fixing a poor data type choice after millions of rows exist is
considerably less enjoyable than getting it right the first time.
