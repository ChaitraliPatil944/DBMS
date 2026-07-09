# Lesson 118 --- SAVEPOINT Statement

> **Part 06 --- Structured Query Language (SQL)**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What `SAVEPOINT` is
-   Why `SAVEPOINT` is needed
-   Creating savepoints
-   Rolling back to a savepoint
-   Releasing savepoints
-   Nested transaction concepts
-   Internal execution flow
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Imagine writing a long report.

You save versions like:

``` text
Draft 1
   │
Draft 2
   │
Draft 3
```

If Draft 3 goes wrong, you restore Draft 2 instead of rewriting
everything.

A **SAVEPOINT** works the same way inside a database transaction.

------------------------------------------------------------------------

# 2. What is SAVEPOINT?

`SAVEPOINT` is a **TCL (Transaction Control Language)** command that
creates a checkpoint inside a transaction.

``` text
Transaction
     │
 SAVEPOINT
     │
Checkpoint Created
```

If something fails later, the transaction can roll back to that
checkpoint instead of the beginning.

------------------------------------------------------------------------

# 3. Why Do We Need SAVEPOINT?

Without SAVEPOINT:

``` text
Transaction
      │
Error
      │
ROLLBACK
      │
Everything Undone
```

With SAVEPOINT:

``` text
Transaction
      │
SAVEPOINT
      │
More SQL
      │
Error
      │
ROLLBACK TO SAVEPOINT
      │
Only Recent Changes Undone
```

------------------------------------------------------------------------

# 4. Basic Syntax

Create a savepoint:

``` sql
SAVEPOINT BeforeUpdate;
```

Rollback to it:

``` sql
ROLLBACK TO BeforeUpdate;
```

------------------------------------------------------------------------

# 5. Example Transaction

``` sql
UPDATE Account
SET Balance = Balance - 500
WHERE AccountID = 1;

SAVEPOINT TransferStarted;

UPDATE Account
SET Balance = Balance + 500
WHERE AccountID = 2;

ROLLBACK TO TransferStarted;
```

Result:

``` text
First Update Retained

Second Update Undone
```

------------------------------------------------------------------------

# 6. Releasing a SAVEPOINT

Some DBMSs support:

``` sql
RELEASE SAVEPOINT TransferStarted;
```

This removes the checkpoint.

**Note:** Support varies between database systems.

------------------------------------------------------------------------

# 7. Internal Working

``` text
BEGIN
  │
SQL Statement
  │
SAVEPOINT
  │
More SQL
  │
Error?
 │      │
No      Yes
 │       │
COMMIT  ROLLBACK TO SAVEPOINT
```

------------------------------------------------------------------------

# 8. SAVEPOINT vs ROLLBACK

  SAVEPOINT                   ROLLBACK
  --------------------------- ----------------------------------------
  Creates checkpoint          Undoes changes
  Partial recovery            Full recovery (unless using savepoint)
  Used within a transaction   Ends work back to previous state

------------------------------------------------------------------------

# 9. Real-World Example

An online order process:

``` text
Create Order
      │
SAVEPOINT
      │
Reserve Inventory
      │
SAVEPOINT
      │
Process Payment
      │
Payment Fails
      │
ROLLBACK TO Inventory Savepoint
```

The order remains while only the failed part is undone.

------------------------------------------------------------------------

# 10. Nested Transaction Concept

Many DBMSs do not support true nested transactions.

Instead, savepoints provide similar behavior.

``` text
Transaction
 │
SAVEPOINT A
 │
SAVEPOINT B
 │
ROLLBACK TO B
 │
Continue Transaction
```

------------------------------------------------------------------------

# 11. Best Practices

-   Create savepoints before risky operations.
-   Use meaningful savepoint names.
-   Avoid excessive savepoints in simple transactions.
-   Commit after successful completion.

------------------------------------------------------------------------

# 12. Common Mistakes

❌ Assuming SAVEPOINT permanently saves data.

❌ Rolling back to a savepoint after COMMIT.

❌ Forgetting that SAVEPOINT exists only inside the current transaction.

❌ Expecting identical support across all DBMSs.

------------------------------------------------------------------------

# 13. Interview Questions

### Beginner

1.  What is a SAVEPOINT?
2.  Why is SAVEPOINT used?
3.  What does `ROLLBACK TO SAVEPOINT` do?

### Intermediate

1.  SAVEPOINT vs ROLLBACK?
2.  Can multiple savepoints exist in one transaction?

### Advanced

1.  Explain how savepoints simulate nested transactions.
2.  Why are savepoints useful in enterprise applications?

------------------------------------------------------------------------

# 14. Practice Problems

1.  Create a transaction with two savepoints.
2.  Roll back to the first savepoint.
3.  Compare COMMIT, ROLLBACK, and SAVEPOINT.
4.  Explain a banking scenario using savepoints.

------------------------------------------------------------------------

# Revision Notes

``` text
BEGIN
 │
SAVEPOINT A
 │
SQL
 │
SAVEPOINT B
 │
SQL
 │
ROLLBACK TO B
 │
COMMIT
```

## Memory Trick

``` text
SAVEPOINT

=

Safe

Checkpoint

Inside

Transaction
```

## Key Points

-   `SAVEPOINT` creates checkpoints.
-   `ROLLBACK TO` restores to a checkpoint.
-   Only uncommitted changes are affected.
-   Savepoints improve flexibility in long transactions.
-   `COMMIT` removes the need for savepoints by ending the transaction.

------------------------------------------------------------------------

# Final Takeaway

`SAVEPOINT` gives fine-grained control over transactions by allowing
partial recovery instead of undoing every change. It is especially
valuable in long business processes where some steps succeed while
others fail. Rather than restarting the entire transaction, a savepoint
lets the database resume from a known good checkpoint, which saves time,
reduces unnecessary work, and keeps complex workflows manageable.
