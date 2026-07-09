# Lesson 232 --- Crash Recovery

> **Part 16 --- Recovery**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What crash recovery is
-   Causes of database crashes
-   Crash recovery workflow
-   Role of logs and checkpoints
-   UNDO and REDO during recovery
-   ARIES-based crash recovery
-   Advantages and limitations
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

A database crash can occur unexpectedly due to hardware failures,
software bugs, power outages, or operating system failures.

The goal of **Crash Recovery** is to restore the database to a
consistent state without losing committed transactions.

------------------------------------------------------------------------

# 2. What is Crash Recovery?

**Crash Recovery** is the process of restoring a database after an
unexpected system failure using transaction logs, checkpoints, and
recovery algorithms.

``` text
Database Running
       │
    Crash
       │
 Restart DBMS
       │
 Recovery Process
       │
Consistent Database
```

------------------------------------------------------------------------

# 3. Common Causes of Crashes

-   Power failure
-   Operating system crash
-   DBMS software failure
-   Hardware malfunction
-   Memory failure

------------------------------------------------------------------------

# 4. Components Used

``` text
Transaction Log
       │
 Checkpoints
       │
 WAL
       │
UNDO & REDO
       │
Recovery Manager
```

------------------------------------------------------------------------

# 5. Crash Recovery Workflow

``` text
Crash
  │
Restart DBMS
  │
Locate Last Checkpoint
  │
Read Transaction Log
  │
REDO Committed Transactions
  │
UNDO Incomplete Transactions
  │
Database Restored
```

------------------------------------------------------------------------

# 6. Recovery Using Logs

The recovery manager scans the log.

For each transaction:

-   **Committed** → REDO if required.
-   **Uncommitted** → UNDO.

Example:

``` text
START T1
UPDATE A
COMMIT T1

START T2
UPDATE B

CRASH
```

Recovery:

``` text
REDO T1

UNDO T2
```

------------------------------------------------------------------------

# 7. Role of Checkpoints

Checkpoints reduce recovery time.

Instead of scanning the entire log, recovery starts from the most recent
checkpoint.

``` text
Log
 │
Checkpoint
 │
Crash
 │
Recover From Here
```

------------------------------------------------------------------------

# 8. Crash Recovery with ARIES

ARIES performs recovery in three phases:

``` text
Crash
 │
Analysis
 │
REDO
 │
UNDO
 │
Recovered Database
```

-   **Analysis** identifies active transactions and dirty pages.
-   **REDO** repeats necessary updates.
-   **UNDO** rolls back incomplete transactions.

------------------------------------------------------------------------

# 9. Real-World Example

An online banking system processes fund transfers.

A crash occurs after one transfer commits and another is still in
progress.

Recovery:

-   Restore committed transfer (REDO).
-   Cancel incomplete transfer (UNDO).

The final balances remain correct.

------------------------------------------------------------------------

# 10. Advantages

-   Prevents loss of committed data
-   Restores consistency
-   Supports ACID Durability
-   Enables reliable enterprise systems

------------------------------------------------------------------------

# 11. Limitations

-   Recovery consumes time
-   Logs require storage
-   Recovery logic is complex

------------------------------------------------------------------------

# 12. Best Practices

-   Enable Write-Ahead Logging (WAL).
-   Configure periodic checkpoints.
-   Keep reliable backups.
-   Test recovery plans regularly.
-   Monitor transaction log size.

------------------------------------------------------------------------

# 13. Common Mistakes

❌ Assuming backups alone provide crash recovery.

❌ Ignoring checkpoints.

❌ Confusing crash recovery with media recovery.

------------------------------------------------------------------------

# 14. Interview Questions

### Beginner

1.  What is crash recovery?
2.  Why is crash recovery important?

### Intermediate

1.  Explain the crash recovery workflow.
2.  What is the role of checkpoints?

### Advanced

1.  Explain crash recovery using ARIES.
2.  Why are both UNDO and REDO needed?

------------------------------------------------------------------------

# 15. Practice Problems

1.  Draw the crash recovery workflow.
2.  Explain recovery using transaction logs.
3.  Compare crash recovery and media recovery.
4.  Explain how checkpoints reduce recovery time.

------------------------------------------------------------------------

# Revision Notes

``` text
Crash
 │
Checkpoint
 │
Read Log
 │
REDO
 │
UNDO
 │
Recovered Database
```

## Memory Trick

``` text
CRASH

Checkpoint

↓

Logs

↓

Redo

↓

Undo

↓

Recover
```

## Key Points

-   Crash recovery restores consistency after system failures.
-   Logs, WAL, and checkpoints are essential.
-   REDO restores committed transactions.
-   UNDO removes incomplete transactions.
-   ARIES is the standard crash recovery algorithm.

------------------------------------------------------------------------

# Final Takeaway

Crash Recovery combines transaction logs, checkpoints, Write-Ahead
Logging, UNDO, REDO, and ARIES to restore a database after unexpected
failures. It ensures committed work is preserved, incomplete work is
removed, and the database returns to a consistent state with minimal
downtime.
