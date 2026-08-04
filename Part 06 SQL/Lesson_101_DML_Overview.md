# Lesson 101 --- DML (Data Manipulation Language) Overview

> **Part 06 --- Structured Query Language (SQL)**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What DML is
-   Why DML is important
-   Difference between DDL and DML
-   Major DML commands
-   How DML changes data
-   Transactions and DML
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Imagine you have built a brand-new house.

DDL created:

-   Rooms
-   Walls
-   Doors
-   Windows

Now people move in, furniture is added, old furniture is replaced, and
unwanted items are removed.

That is exactly what **DML** does.

It works with the **data inside the tables**, not the table structure.

------------------------------------------------------------------------

# 2. What is DML?

**DML (Data Manipulation Language)** is the collection of SQL commands
used to **insert, update, delete, and merge data** stored in database
tables.

``` text
Database Table
      │
      ▼
 DML Commands
      │
      ▼
Data Changes
```

------------------------------------------------------------------------

# 3. Why Do We Need DML?

Without DML:

-   No records can be added.
-   Existing information cannot be updated.
-   Incorrect data cannot be removed.

A database without DML is simply an empty structure.

------------------------------------------------------------------------

# 4. DML Commands

``` text
DML
│
├── INSERT
├── UPDATE
├── DELETE
└── MERGE
```

Each command manipulates existing data.

------------------------------------------------------------------------

# 5. INSERT

Adds new records.

``` sql
INSERT INTO Student(StudentID, Name)
VALUES (101, 'Alice');
```

Result:

``` text
StudentID   Name
----------------
101         Alice
```

------------------------------------------------------------------------

# 6. UPDATE

Modifies existing records.

``` sql
UPDATE Student
SET Name = 'Alicia'
WHERE StudentID = 101;
```

------------------------------------------------------------------------

# 7. DELETE

Removes records.

``` sql
DELETE FROM Student
WHERE StudentID = 101;
```

Unlike `DROP`, the table still exists.

------------------------------------------------------------------------

# 8. MERGE

Combines INSERT and UPDATE logic.

If a matching record exists:

``` text
Update
```

Otherwise:

``` text
Insert
```

MERGE is commonly used for data synchronization and ETL.

------------------------------------------------------------------------

# 9. DDL vs DML

  DDL                 DML
  ------------------- ------------------
  Defines structure   Manipulates data
  CREATE              INSERT
  ALTER               UPDATE
  DROP                DELETE
  TRUNCATE            MERGE
  Works on metadata   Works on records

------------------------------------------------------------------------

# 10. How DML Works

``` text
Application
      │
SQL DML
      │
DBMS
      │
Table Rows Updated
```

------------------------------------------------------------------------

# 11. Transactions and DML

Most DML operations participate in transactions.

``` text
INSERT
UPDATE
DELETE
      │
COMMIT
or
ROLLBACK
```

This allows changes to be saved or undone.

------------------------------------------------------------------------

# 12. Real-World Example

Online shopping:

``` text
Customer Places Order
        │
INSERT Order

Customer Changes Address
        │
UPDATE Customer

Customer Cancels Order
        │
DELETE Order

Daily Synchronization
        │
MERGE
```

------------------------------------------------------------------------

# 13. Best Practices

-   Always use `WHERE` with `UPDATE` and `DELETE` unless every row
    should change.
-   Validate data before inserting.
-   Use transactions for important operations.
-   Test large updates carefully.

------------------------------------------------------------------------

# 14. Common Mistakes

❌ Updating every row accidentally.

``` sql
UPDATE Employee
SET Salary = 50000;
```

Without a `WHERE` clause, every employee receives the same salary.

❌ Deleting all rows unintentionally.

``` sql
DELETE FROM Employee;
```

------------------------------------------------------------------------

# 15. Interview Questions

### Beginner

1.  What is DML?
2.  Name the DML commands.
3.  Difference between DDL and DML?

### Intermediate

1.  Why is MERGE useful?
2.  INSERT vs UPDATE?
3.  DELETE vs TRUNCATE?

### Advanced

1.  Why do DML statements use transactions?
2.  Why should UPDATE usually include a WHERE clause?

------------------------------------------------------------------------

# 16. Practice Problems

1.  Insert a student record.
2.  Update an employee's salary.
3.  Delete a customer by ID.
4.  Explain a real-world use of MERGE.
5.  Compare DDL and DML.

------------------------------------------------------------------------

# Revision Notes

``` text
DML
│
├── INSERT
├── UPDATE
├── DELETE
└── MERGE
```

## Memory Trick

``` text
I U D M

Insert
Update
Delete
Merge
```

## Key Points

-   DML manipulates table data.
-   INSERT adds rows.
-   UPDATE modifies rows.
-   DELETE removes rows.
-   MERGE synchronizes data.
-   DML commonly works with transactions.

------------------------------------------------------------------------

# Final Takeaway

DDL creates the database structure, while DML brings that structure to
life by storing and modifying actual information. Almost every business
application executes thousands of DML statements every day, making these
commands some of the most frequently used in SQL. Understanding them
well is essential because the database follows your instructions with
impressive speed and absolutely no interest in whether they were a good
idea.
