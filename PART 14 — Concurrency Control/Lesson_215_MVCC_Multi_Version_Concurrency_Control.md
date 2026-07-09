# Lesson 215 --- MVCC (Multi-Version Concurrency Control)

> **Part 14 --- Concurrency Control**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What MVCC is
-   Why MVCC was introduced
-   How MVCC works
-   Snapshots and versioning
-   Advantages and limitations
-   MVCC vs Locking
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Traditional locking often makes readers wait for writers and writers
wait for readers.

Modern databases reduce this waiting by storing **multiple versions** of
the same data.

This technique is called **Multi-Version Concurrency Control (MVCC)**.

------------------------------------------------------------------------

# 2. What is MVCC?

**MVCC** is a concurrency control mechanism where multiple versions of a
data item are maintained so transactions can read consistent snapshots
without blocking each other.

``` text
Record
  │
Version 1
Version 2
Version 3
```

Each transaction reads the appropriate version.

------------------------------------------------------------------------

# 3. Why is MVCC Needed?

Without MVCC:

-   Readers wait for writers.
-   Writers wait for readers.
-   Lower concurrency.
-   Longer response times.

With MVCC:

-   Readers usually do not block writers.
-   Writers usually do not block readers.
-   Higher throughput.

------------------------------------------------------------------------

# 4. How MVCC Works

Each row stores version information.

``` text
Row

Version = 1

↓

UPDATE

↓

Version = 2

↓

UPDATE

↓

Version = 3
```

Older versions remain available until they are no longer needed.

------------------------------------------------------------------------

# 5. Snapshot Isolation

Every transaction sees a **snapshot** of the database taken when the
transaction begins.

``` text
Transaction Starts
        │
Snapshot Created
        │
Reads Snapshot
        │
Other Updates Invisible
```

The transaction sees a consistent view throughout its execution.

------------------------------------------------------------------------

# 6. Example

Suppose balance = ₹10,000.

``` text
T1 starts

↓

Snapshot = 10000

↓

T2 updates balance to 8000
and commits

↓

T1 still reads 10000
```

T1 continues using its original snapshot.

------------------------------------------------------------------------

# 7. MVCC vs Locking

  MVCC                           Traditional Locking
  ------------------------------ ---------------------------
  Multiple versions              Single current version
  Readers rarely block writers   Readers may block writers
  Higher read concurrency        More waiting
  Extra storage required         Fewer versions stored

------------------------------------------------------------------------

# 8. Databases Using MVCC

Many modern databases use MVCC, including:

-   PostgreSQL
-   MySQL (InnoDB)
-   Oracle Database
-   SQLite (limited form)

------------------------------------------------------------------------

# 9. Advantages

-   Excellent read performance
-   Higher concurrency
-   Fewer lock conflicts
-   Reduced waiting
-   Consistent snapshots

------------------------------------------------------------------------

# 10. Limitations

-   More storage for old versions
-   Version cleanup required
-   More complex implementation
-   Long-running transactions retain old versions longer

------------------------------------------------------------------------

# 11. Best Practices

-   Keep transactions short.
-   Remove obsolete row versions regularly.
-   Avoid unnecessarily long snapshot transactions.
-   Use MVCC for read-heavy workloads.

------------------------------------------------------------------------

# 12. Common Mistakes

❌ Assuming MVCC eliminates every lock.

❌ Forgetting that writers can still conflict.

❌ Ignoring version cleanup.

------------------------------------------------------------------------

# 13. Interview Questions

### Beginner

1.  What is MVCC?
2.  Why is MVCC used?

### Intermediate

1.  What is snapshot isolation?
2.  MVCC vs locking?

### Advanced

1.  How does MVCC improve concurrency?
2.  Why does MVCC require additional storage?

------------------------------------------------------------------------

# 14. Practice Problems

1.  Explain MVCC with an example.
2.  Draw the MVCC workflow.
3.  Compare MVCC and locking.
4.  Explain snapshot isolation.

------------------------------------------------------------------------

# Revision Notes

``` text
Transaction
     │
Snapshot
     │
Read Correct Version
     │
Concurrent Updates
     │
No Reader Blocking
```

## Memory Trick

``` text
MVCC

Many

Versions

Concurrent

Consistency
```

## Key Points

-   MVCC stores multiple versions of rows.
-   Transactions read consistent snapshots.
-   Readers rarely block writers.
-   Higher concurrency comes with extra storage cost.
-   MVCC is widely used in modern relational databases.

------------------------------------------------------------------------

# Final Takeaway

Multi-Version Concurrency Control improves database performance by
allowing transactions to read consistent snapshots instead of waiting
for locks. By maintaining multiple row versions, MVCC greatly increases
concurrency for read-heavy workloads while preserving data consistency.
It is one of the defining features of modern enterprise database
systems.
