# Lesson 203 --- Recovery Basics

> **Part 13 --- Transactions**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What database recovery is
-   Why recovery is necessary
-   Types of database failures
-   Recovery techniques
-   UNDO and REDO operations
-   Recovery using logs and checkpoints
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

No computer system is immune to failure.

A database may crash because of:

-   Power failure
-   Hardware failure
-   Software bugs
-   Operating system crash
-   Human error

The DBMS must restore the database to a correct state.

This process is called **Recovery**.

------------------------------------------------------------------------

# 2. What is Database Recovery?

**Database Recovery** is the process of restoring the database to a
consistent state after a failure.

``` text
Normal Execution
       │
    Failure
       │
 Recovery
       │
Consistent Database
```

------------------------------------------------------------------------

# 3. Why is Recovery Needed?

Without recovery:

-   Data may be lost
-   Transactions may remain incomplete
-   Database becomes inconsistent
-   Business operations may stop

Recovery ensures reliability and continuity.

------------------------------------------------------------------------

# 4. Types of Failures

### Transaction Failure

-   Invalid input
-   Constraint violation
-   Deadlock
-   Application error

### System Failure

-   Power outage
-   Operating system crash
-   Memory failure

### Media Failure

-   Disk crash
-   Storage corruption
-   Hardware damage

------------------------------------------------------------------------

# 5. Recovery Components

A DBMS relies on:

``` text
Transactions
      │
Transaction Logs
      │
Checkpoints
      │
Recovery Manager
```

These work together to restore the database.

------------------------------------------------------------------------

# 6. UNDO Operation

UNDO reverses the effects of incomplete transactions.

Example:

``` text
Balance = 10000

↓

Deduct 2000

↓

Crash Before COMMIT

↓

UNDO

↓

Balance = 10000
```

Used for:

-   Failed transactions
-   Aborted transactions

------------------------------------------------------------------------

# 7. REDO Operation

REDO reapplies committed changes that were not written to disk before
the crash.

Example:

``` text
Balance = 10000

↓

Transfer Completed

↓

COMMIT

↓

Crash Before Disk Update

↓

REDO

↓

Balance Restored
```

------------------------------------------------------------------------

# 8. Recovery Process

``` text
System Crash
      │
Read Log
      │
Find Checkpoint
      │
UNDO Incomplete Transactions
      │
REDO Committed Transactions
      │
Database Restored
```

------------------------------------------------------------------------

# 9. Recovery Example

Transaction Log

``` text
START T1
UPDATE
COMMIT

START T2
UPDATE

CHECKPOINT

START T3
UPDATE

CRASH
```

Recovery:

-   REDO T1
-   UNDO T2 (if incomplete)
-   UNDO T3

------------------------------------------------------------------------

# 10. Recovery Techniques

-   Log-Based Recovery
-   Checkpoint Recovery
-   Shadow Paging (overview)
-   ARIES (advanced algorithm)

The detailed techniques are covered later in the handbook.

------------------------------------------------------------------------

# 11. Real-World Example

ATM Transaction

``` text
Withdraw ₹5000
      │
Log Written
      │
Cash Dispensed
      │
Crash
      │
Recovery Uses Log
```

The customer balance remains correct.

------------------------------------------------------------------------

# 12. Best Practices

-   Enable transaction logging.
-   Create periodic checkpoints.
-   Follow Write-Ahead Logging (WAL).
-   Test recovery procedures regularly.
-   Keep reliable backups.

------------------------------------------------------------------------

# 13. Common Mistakes

❌ Believing backups alone provide recovery.

❌ Ignoring transaction logs.

❌ Confusing UNDO with REDO.

❌ Skipping checkpoint configuration.

------------------------------------------------------------------------

# 14. Interview Questions

### Beginner

1.  What is database recovery?
2.  Why is recovery necessary?

### Intermediate

1.  Explain UNDO and REDO.
2.  What role do checkpoints play?

### Advanced

1.  Describe the complete recovery process.
2.  How do logs and checkpoints work together?

------------------------------------------------------------------------

# 15. Practice Problems

1.  Draw the recovery process.
2.  Compare UNDO and REDO.
3.  Explain recovery after a system crash.
4.  Identify recovery components in a DBMS.

------------------------------------------------------------------------

# Revision Notes

``` text
Failure
   │
Logs
   │
Checkpoint
   │
UNDO
   │
REDO
   │
Recovered Database
```

## Memory Trick

``` text
RECOVERY

Remember Logs

↓

UNDO Failed

↓

REDO Committed
```

## Key Points

-   Recovery restores database consistency.
-   Transaction logs record changes.
-   Checkpoints reduce recovery time.
-   UNDO reverses incomplete transactions.
-   REDO reapplies committed transactions.

------------------------------------------------------------------------

# Final Takeaway

Database recovery is the safety mechanism that protects information
after failures. By combining transaction logs, checkpoints, UNDO, and
REDO operations, a DBMS can restore the database to a consistent and
reliable state with minimal data loss. Recovery is one of the core
reasons modern database systems are trusted for banking, healthcare,
e-commerce, and other mission-critical applications.
