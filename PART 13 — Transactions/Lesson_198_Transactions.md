# Lesson 198 --- Transactions

> **Part 13 --- Transactions**

------------------------------------------------------------------------

# Learning Objectives

-   What is a transaction?
-   Why transactions are important
-   Transaction lifecycle
-   Transaction operations
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# What is a Transaction?

A **transaction** is a logical unit of work consisting of one or more
database operations that are executed as a single unit.

``` text
START
  │
Execute SQL Statements
  │
Success?
 │        │
Yes      No
 │        │
COMMIT ROLLBACK
```

Either all operations succeed or none of them are permanently applied.

------------------------------------------------------------------------

# Why Are Transactions Needed?

Without transactions:

-   Partial updates
-   Data inconsistency
-   Lost information
-   Difficult recovery

Transactions ensure reliability and data integrity.

------------------------------------------------------------------------

# Banking Example

Transfer ₹5000 from Account A to Account B.

``` sql
BEGIN;

UPDATE Account
SET Balance = Balance - 5000
WHERE AccountID = 101;

UPDATE Account
SET Balance = Balance + 5000
WHERE AccountID = 202;

COMMIT;
```

If an error occurs:

``` sql
ROLLBACK;
```

------------------------------------------------------------------------

# Transaction Lifecycle

``` text
Begin Transaction
        │
Execute Statements
        │
Success?
   │          │
 Yes         No
 │            │
COMMIT    ROLLBACK
```

------------------------------------------------------------------------

# Transaction Operations

-   BEGIN / START TRANSACTION
-   COMMIT
-   ROLLBACK
-   SAVEPOINT

------------------------------------------------------------------------

# Real-World Examples

-   Banking fund transfer
-   ATM withdrawal
-   Online shopping checkout
-   Airline ticket booking

------------------------------------------------------------------------

# Relationship with ACID

Every transaction follows:

-   Atomicity
-   Consistency
-   Isolation
-   Durability

These are covered in the next lesson.

------------------------------------------------------------------------

# Advantages

-   Prevents partial updates
-   Improves consistency
-   Supports recovery
-   Protects data integrity

------------------------------------------------------------------------

# Best Practices

-   Keep transactions short.
-   Commit successful work promptly.
-   Roll back on failures.
-   Group related operations together.

------------------------------------------------------------------------

# Common Mistakes

-   Forgetting COMMIT.
-   Long-running transactions.
-   Updating related tables outside a transaction.

------------------------------------------------------------------------

# Interview Questions

1.  What is a transaction?
2.  Why are transactions important?
3.  COMMIT vs ROLLBACK?
4.  Give a real-world transaction example.

------------------------------------------------------------------------

# Practice Problems

1.  Explain a banking transaction.
2.  Write SQL for a fund transfer.
3.  Compare COMMIT and ROLLBACK.
4.  List applications that require transactions.

------------------------------------------------------------------------

# Revision Notes

``` text
Transaction
     │
Multiple Operations
     │
All Success?
 │           │
Yes         No
 │           │
COMMIT   ROLLBACK
```

## Memory Trick

``` text
Transaction

=

All

Or

Nothing
```

------------------------------------------------------------------------

# Final Takeaway

A transaction ensures that related database operations succeed or fail
together. This guarantees consistency, protects data from partial
updates, and forms the foundation of reliable database systems.
