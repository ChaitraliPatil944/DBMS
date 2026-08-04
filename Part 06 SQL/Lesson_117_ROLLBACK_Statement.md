# Lesson 117 --- ROLLBACK Statement

> **Part 06 --- Structured Query Language (SQL)**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What `ROLLBACK` is
-   Why `ROLLBACK` is important
-   How `ROLLBACK` works internally
-   Undoing transactions
-   Partial rollback using `SAVEPOINT`
-   Banking and real-world examples
-   Best practices
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Imagine transferring money online.

Steps:

1.  Debit Account A
2.  Credit Account B

Suddenly, the server crashes after the debit but before the credit.

Without a recovery mechanism, the money disappears.

`ROLLBACK` prevents this by undoing incomplete transactions.

------------------------------------------------------------------------

# 2. What is ROLLBACK?

`ROLLBACK` is a **TCL (Transaction Control Language)** command that
cancels all uncommitted changes made during the current transaction.

``` text
Transaction
     │
Something Goes Wrong
     │
ROLLBACK
     │
Database Restored
```

The database returns to its previous consistent state.

------------------------------------------------------------------------

# 3. Why Do We Need ROLLBACK?

Mistakes happen:

-   Incorrect updates
-   Wrong deletions
-   Application crashes
-   Power failures
-   Network interruptions

Instead of leaving the database half-updated, `ROLLBACK` restores it.

------------------------------------------------------------------------

# 4. Basic Syntax

``` sql
ROLLBACK;
```

It undoes changes made since the last `COMMIT`.

------------------------------------------------------------------------

# 5. Example Transaction

``` sql
UPDATE Account
SET Balance = Balance - 1000
WHERE AccountID = 1;

UPDATE Account
SET Balance = Balance + 1000
WHERE AccountID = 2;

ROLLBACK;
```

Result:

``` text
Debit ❌ Undone
Credit ❌ Undone

Original Balances Restored
```

------------------------------------------------------------------------

# 6. How ROLLBACK Works Internally

``` text
BEGIN TRANSACTION
        │
Execute SQL
        │
Error Occurs
        │
ROLLBACK
        │
Undo Changes
        │
Restore Previous State
```

The DBMS uses transaction logs to reverse the uncommitted changes.

------------------------------------------------------------------------

# 7. Partial Rollback with SAVEPOINT

Create a checkpoint:

``` sql
SAVEPOINT BeforeSalaryUpdate;

UPDATE Employee
SET Salary = Salary + 5000;

ROLLBACK TO BeforeSalaryUpdate;
```

Only the changes made after the savepoint are undone.

Earlier changes remain.

------------------------------------------------------------------------

# 8. COMMIT vs ROLLBACK

  COMMIT                      ROLLBACK
  --------------------------- -----------------------------
  Saves changes               Undoes changes
  Permanent                   Temporary changes removed
  Ends transaction            Returns to previous state
  Cannot normally be undone   Possible only before commit

------------------------------------------------------------------------

# 9. Real-World Example

Online shopping:

``` text
Reserve Inventory
        │
Create Order
        │
Payment Fails
        │
ROLLBACK
        │
Inventory Restored
```

This prevents incorrect stock information.

------------------------------------------------------------------------

# 10. Best Practices

-   Roll back immediately when critical errors occur.
-   Use transactions for related operations.
-   Create savepoints in long transactions.
-   Validate data before committing.

------------------------------------------------------------------------

# 11. Common Mistakes

❌ Trying to rollback after `COMMIT`.

❌ Assuming every DBMS keeps uncommitted changes forever.

❌ Forgetting to use transactions.

❌ Confusing rollback with deleting data.

------------------------------------------------------------------------

# 12. Interview Questions

### Beginner

1.  What is `ROLLBACK`?
2.  Is `ROLLBACK` a TCL command?
3.  What does it undo?

### Intermediate

1.  `COMMIT` vs `ROLLBACK`?
2.  What is `ROLLBACK TO SAVEPOINT`?

### Advanced

1.  How does a DBMS undo changes?
2.  Why can't committed transactions usually be rolled back?

------------------------------------------------------------------------

# 13. Practice Problems

1.  Write a transaction and roll it back.
2.  Demonstrate partial rollback using a savepoint.
3.  Compare `COMMIT` and `ROLLBACK`.
4.  Explain a banking scenario using rollback.

------------------------------------------------------------------------

# Revision Notes

``` text
BEGIN
  │
SQL Statements
  │
ROLLBACK
  │
Undo Changes
  │
Previous State Restored
```

## Memory Trick

``` text
ROLLBACK

=

Return

Operations

Logically

Leaving

Before

Accidental

Changes

Kept
```

## Key Points

-   `ROLLBACK` undoes uncommitted changes.
-   It is a TCL command.
-   It restores database consistency after failures.
-   `SAVEPOINT` enables partial rollback.
-   A committed transaction generally cannot be rolled back.

------------------------------------------------------------------------

# Final Takeaway

`ROLLBACK` is the safety mechanism that protects databases from
incomplete or incorrect transactions. Whenever an error occurs before a
transaction is committed, `ROLLBACK` allows the database to return to a
consistent state as though the failed operation never happened. Reliable
systems depend on this capability because preventing incorrect data is
almost always easier than repairing it later.
