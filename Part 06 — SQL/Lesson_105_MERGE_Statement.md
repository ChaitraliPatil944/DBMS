# Lesson 105 --- MERGE Statement

> **Part 06 --- Structured Query Language (SQL)**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What the `MERGE` statement is
-   Why `MERGE` is used
-   MERGE syntax
-   `WHEN MATCHED`
-   `WHEN NOT MATCHED`
-   UPSERT operations
-   Data synchronization
-   ETL use cases
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Imagine two employee lists.

``` text
HR Database
Employee 101
Employee 102

New HR File
Employee 101 (updated)
Employee 103 (new)
```

You need to:

-   Update Employee 101
-   Insert Employee 103

Instead of writing separate `UPDATE` and `INSERT` statements, SQL
provides **MERGE**.

------------------------------------------------------------------------

# 2. What is MERGE?

`MERGE` is a **DML** command that combines **INSERT**, **UPDATE**, and
(optionally) **DELETE** into a single statement.

``` text
Source Data
     │
   MERGE
     │
┌────┴────┐
│         │
Match   No Match
│         │
Update  Insert
```

------------------------------------------------------------------------

# 3. Why Do We Need MERGE?

Without MERGE:

``` text
UPDATE

then

INSERT
```

With MERGE:

``` text
One Statement
```

This reduces code and simplifies synchronization.

------------------------------------------------------------------------

# 4. General Syntax

``` sql
MERGE INTO TargetTable AS T
USING SourceTable AS S
ON (T.ID = S.ID)

WHEN MATCHED THEN
UPDATE SET T.Name = S.Name

WHEN NOT MATCHED THEN
INSERT (ID, Name)
VALUES (S.ID, S.Name);
```

------------------------------------------------------------------------

# 5. WHEN MATCHED

Executed when matching rows already exist.

``` text
Target
101 Alice

Source
101 Alicia

↓

UPDATE
```

------------------------------------------------------------------------

# 6. WHEN NOT MATCHED

Executed when no matching row exists.

``` text
Target
101 Alice

Source
102 Bob

↓

INSERT
```

------------------------------------------------------------------------

# 7. UPSERT

MERGE is often called an **UPSERT**.

``` text
Update

or

Insert
```

depending on whether a matching row exists.

------------------------------------------------------------------------

# 8. MERGE Workflow

``` text
Read Source
      │
Compare Target
      │
 ┌────┴────┐
 │         │
Match   No Match
 │         │
Update  Insert
```

Some DBMSs also support deleting unmatched rows.

------------------------------------------------------------------------

# 9. Real-World Example

Synchronize customer records:

``` sql
MERGE INTO Customer AS C
USING NewCustomer AS N
ON (C.CustomerID = N.CustomerID)

WHEN MATCHED THEN
UPDATE SET C.City = N.City

WHEN NOT MATCHED THEN
INSERT(CustomerID, Name, City)
VALUES(N.CustomerID, N.Name, N.City);
```

------------------------------------------------------------------------

# 10. ETL & Data Warehousing

MERGE is widely used in:

-   Data Warehouses
-   ETL pipelines
-   Nightly data synchronization
-   Master Data Management
-   Cloud data integration

------------------------------------------------------------------------

# 11. Advantages

-   Single statement
-   Cleaner code
-   Faster synchronization
-   Reduces duplicate logic
-   Easier maintenance

------------------------------------------------------------------------

# 12. Common Mistakes

❌ Incorrect matching condition.

❌ Updating wrong columns.

❌ Assuming all DBMSs support identical MERGE syntax.

❌ Forgetting unique keys.

------------------------------------------------------------------------

# 13. Interview Questions

### Beginner

1.  What is MERGE?
2.  Why is it used?

### Intermediate

1.  Explain `WHEN MATCHED`.
2.  Explain `WHEN NOT MATCHED`.
3.  What is an UPSERT?

### Advanced

1.  Why is MERGE popular in ETL?
2.  Compare MERGE with separate INSERT and UPDATE statements.

------------------------------------------------------------------------

# 14. Practice Problems

1.  Synchronize Student and StudentBackup.
2.  Write a MERGE statement for Employee records.
3.  Explain a real-world UPSERT scenario.
4.  Compare MERGE and UPDATE.

------------------------------------------------------------------------

# Revision Notes

``` text
MERGE
  │
Source + Target
  │
Match?
│       │
Yes     No
│       │
Update  Insert
```

## Memory Trick

``` text
MERGE

=

Match

Else

Register

Generate Entry
```

## Key Points

-   `MERGE` combines INSERT and UPDATE.
-   Uses `WHEN MATCHED` and `WHEN NOT MATCHED`.
-   Ideal for synchronization.
-   Commonly used in ETL and data warehouses.
-   Syntax varies slightly across DBMSs.

------------------------------------------------------------------------

# Final Takeaway

The `MERGE` statement is designed for situations where data must be
synchronized efficiently. Instead of checking manually whether each row
should be inserted or updated, the DBMS performs that decision
automatically based on the matching condition. In enterprise systems
that process millions of records, this saves time, reduces code
complexity, and keeps multiple datasets consistent.
