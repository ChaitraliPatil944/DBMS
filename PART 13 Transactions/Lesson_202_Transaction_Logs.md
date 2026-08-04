# Lesson 202 --- Logs (Transaction Logs)

> **Part 13 --- Transactions**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What transaction logs are
-   Why logs are required
-   Structure of a log record
-   Types of log records
-   Write-Ahead Logging (WAL)
-   Logs in crash recovery
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Imagine a bank updates an account balance and then the system crashes
before the data reaches disk.

How does the DBMS know what happened?

It checks the **transaction log**.

The log is the database's history book, recording every important change
before it is permanently stored.

------------------------------------------------------------------------

# 2. What is a Transaction Log?

A **transaction log** is a sequential file that records all database
transactions and modifications.

``` text
Transaction
     │
Log Record Written
     │
Database Updated
```

The log is used for recovery after failures.

------------------------------------------------------------------------

# 3. Why Are Logs Needed?

Without logs:

-   Lost updates
-   Impossible recovery
-   Data inconsistency
-   Corrupted databases

With logs:

-   Crash recovery
-   Rollback support
-   Durability
-   Audit trail

------------------------------------------------------------------------

# 4. Structure of a Log Record

A typical log record contains:

``` text
Transaction ID (TID)
Operation
Table/Page
Old Value
New Value
Timestamp
```

Example:

  TID    Operation   Old Value   New Value
  ------ ----------- ----------- -----------
  T101   UPDATE      10000       5000

------------------------------------------------------------------------

# 5. Types of Log Records

### Begin Transaction

``` text
<START T1>
```

### Update Record

``` text
<T1, Account, 10000, 5000>
```

### Commit Record

``` text
<COMMIT T1>
```

### Abort Record

``` text
<ABORT T1>
```

------------------------------------------------------------------------

# 6. Write-Ahead Logging (WAL)

**Rule:**

> The log record must be written to stable storage **before** the actual
> database page is written.

``` text
Transaction
      │
Write Log
      │
Flush Log
      │
Update Database
```

This guarantees recovery is possible even after a crash.

------------------------------------------------------------------------

# 7. Logs During Crash Recovery

``` text
START T1
UPDATE
UPDATE
COMMIT
CHECKPOINT
START T2
UPDATE
CRASH
```

Recovery Process:

-   Redo committed transactions.
-   Undo incomplete transactions.

------------------------------------------------------------------------

# 8. Relationship Between Logs and Checkpoints

``` text
Transactions
      │
Transaction Logs
      │
Checkpoint
      │
Crash
      │
Recovery
```

-   **Logs** record every change.
-   **Checkpoints** reduce the amount of log that must be processed.

------------------------------------------------------------------------

# 9. Real-World Example

Online Banking:

1.  User transfers ₹2,000.
2.  Log entry is written.
3.  Database balance is updated.
4.  System crashes.
5.  DBMS uses the log to recover the correct balance.

------------------------------------------------------------------------

# 10. Advantages

-   Supports rollback
-   Supports redo
-   Crash recovery
-   Durability
-   Data consistency

------------------------------------------------------------------------

# 11. Limitations

-   Requires additional storage
-   Continuous log writing adds overhead
-   Log management is necessary

------------------------------------------------------------------------

# 12. Best Practices

-   Always use Write-Ahead Logging.
-   Store logs on reliable storage.
-   Combine logs with checkpoints.
-   Archive logs regularly.

------------------------------------------------------------------------

# 13. Common Mistakes

❌ Assuming logs and checkpoints are the same.

❌ Updating data before writing the log.

❌ Deleting logs too early.

------------------------------------------------------------------------

# 14. Interview Questions

### Beginner

1.  What is a transaction log?
2.  Why are logs required?

### Intermediate

1.  What is Write-Ahead Logging (WAL)?
2.  Difference between logs and checkpoints?

### Advanced

1.  Explain log-based recovery.
2.  Why must logs be written before data pages?

------------------------------------------------------------------------

# 15. Practice Problems

1.  Draw the Write-Ahead Logging process.
2.  Explain how logs help in crash recovery.
3.  Compare logs and checkpoints.
4.  Explain redo and undo using logs.

------------------------------------------------------------------------

# Revision Notes

``` text
Transaction
      │
Write Log
      │
Update Database
      │
Commit
      │
Crash?
      │
Recover Using Log
```

## Memory Trick

``` text
LOG

L → Log First

O → Old & New Values

G → Guarantees Recovery
```

## Key Points

-   Transaction logs record every important database change.
-   WAL requires logs to be written before data pages.
-   Logs enable undo and redo operations.
-   Checkpoints complement logs but do not replace them.
-   Logs are essential for recovery and durability.

------------------------------------------------------------------------

# Final Takeaway

Transaction logs are the foundation of database recovery. Every
significant change is recorded before it reaches the database, allowing
the DBMS to undo incomplete transactions and redo committed ones after a
crash. Together with checkpoints and ACID properties, logs ensure that
modern database systems remain reliable, consistent, and fault tolerant.
