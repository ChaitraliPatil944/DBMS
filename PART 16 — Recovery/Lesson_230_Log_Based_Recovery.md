# Lesson 230 --- Log-Based Recovery

> **Part 16 --- Recovery**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What Log-Based Recovery is
-   Why transaction logs are important
-   Write-Ahead Logging (WAL)
-   Deferred and Immediate Update
-   UNDO/REDO recovery
-   Advantages and limitations
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Modern DBMSs rarely rely on Shadow Paging.

Instead, they record every important database modification in a
**transaction log**.

If a crash occurs, the log is used to recover the database.

This technique is called **Log-Based Recovery**.

------------------------------------------------------------------------

# 2. What is Log-Based Recovery?

**Log-Based Recovery** is a recovery mechanism in which every
transaction operation is recorded in a log before database pages are
updated.

``` text
Transaction
      │
Transaction Log
      │
Crash?
      │
UNDO / REDO
      │
Recovered Database
```

------------------------------------------------------------------------

# 3. Why is Log-Based Recovery Needed?

Without logs:

-   Committed data may be lost.
-   Failed transactions may leave partial updates.
-   Recovery becomes unreliable.

Logs preserve both **Atomicity** and **Durability**.

------------------------------------------------------------------------

# 4. Transaction Log

A transaction log stores records such as:

``` text
START T1
UPDATE A
Old Value = 100
New Value = 80
COMMIT T1
```

Typical log record:

``` text
<Transaction ID,
 Data Item,
 Old Value,
 New Value>
```

------------------------------------------------------------------------

# 5. Write-Ahead Logging (WAL)

**Rule:**

> The log record must be written to stable storage **before** the
> corresponding database page is written.

``` text
Update Data
    │
Write Log
    │
Flush Log
    │
Write Database Page
```

WAL is the foundation of log-based recovery.

------------------------------------------------------------------------

# 6. Deferred Update

In deferred update:

-   Changes are recorded in the log.
-   Database pages are updated only after COMMIT.
-   Recovery mainly requires REDO.

``` text
Update
   │
Log
   │
COMMIT
   │
Write Database
```

------------------------------------------------------------------------

# 7. Immediate Update

In immediate update:

-   Database pages may be updated before COMMIT.
-   Both UNDO and REDO may be required.

``` text
Update
   │
Log
   │
Database Updated
   │
COMMIT
```

------------------------------------------------------------------------

# 8. Recovery Process

``` text
Crash
   │
Read Transaction Log
   │
Committed?
 │        │
Yes      No
 │         │
REDO     UNDO
```

------------------------------------------------------------------------

# 9. Example

Transaction:

``` text
START T1

UPDATE Balance

10000 → 8000

COMMIT
```

Crash occurs before the updated page reaches disk.

Recovery:

``` text
Read Log

↓

REDO

↓

Balance = 8000
```

If COMMIT is missing:

``` text
UNDO

↓

Balance = 10000
```

------------------------------------------------------------------------

# 10. Log-Based Recovery vs Shadow Paging

  Log-Based Recovery      Shadow Paging
  ----------------------- ---------------------------
  Uses transaction logs   Uses page copies
  Uses UNDO & REDO        No UNDO/REDO
  Scalable                Simpler but less scalable
  Used in modern DBMSs    Rarely used today

------------------------------------------------------------------------

# 11. Advantages

-   Reliable recovery
-   Supports large databases
-   Guarantees ACID properties
-   Widely adopted
-   Works with checkpoints

------------------------------------------------------------------------

# 12. Limitations

-   Log storage overhead
-   Recovery processing time
-   Log management complexity

------------------------------------------------------------------------

# 13. Best Practices

-   Always enable WAL.
-   Flush logs before COMMIT.
-   Create checkpoints periodically.
-   Archive logs safely.
-   Monitor log growth.

------------------------------------------------------------------------

# 14. Common Mistakes

❌ Writing database pages before log records.

❌ Confusing deferred and immediate update.

❌ Assuming backups replace transaction logs.

------------------------------------------------------------------------

# 15. Interview Questions

### Beginner

1.  What is Log-Based Recovery?
2.  Why are transaction logs important?

### Intermediate

1.  Explain Write-Ahead Logging.
2.  Compare deferred and immediate update.

### Advanced

1.  Why does immediate update require both UNDO and REDO?
2.  Compare Log-Based Recovery and Shadow Paging.

------------------------------------------------------------------------

# 16. Practice Problems

1.  Draw the WAL workflow.
2.  Explain log-based recovery with an example.
3.  Compare deferred and immediate update.
4.  Explain how UNDO and REDO use transaction logs.

------------------------------------------------------------------------

# Revision Notes

``` text
Transaction
     │
Transaction Log
     │
WAL
     │
Crash
     │
UNDO / REDO
     │
Recovery
```

## Memory Trick

``` text
LOG

Write Log

↓

Write Data

↓

Recover
```

## Key Points

-   Transaction logs record every important change.
-   WAL writes logs before database pages.
-   Deferred update mainly needs REDO.
-   Immediate update may need both UNDO and REDO.
-   Log-based recovery is the standard approach in modern DBMSs.

------------------------------------------------------------------------

# Final Takeaway

Log-Based Recovery is the most widely used recovery mechanism in modern
database systems. By combining transaction logs, Write-Ahead Logging,
UNDO, REDO, and checkpoints, it enables reliable recovery from failures
while preserving database consistency and ACID guarantees.
