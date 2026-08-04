# Lesson 218 --- Concurrency Control Revision Notes & Cheat Sheet

> **Part 14 --- Concurrency Control**

------------------------------------------------------------------------

# Quick Definition

**Concurrency Control** is the DBMS mechanism that manages multiple
transactions executing simultaneously while maintaining correctness and
consistency.

``` text
Multiple Transactions
        │
Concurrency Control
        │
Consistent Database
```

------------------------------------------------------------------------

# Why Concurrency Control?

-   Prevents conflicting updates
-   Maintains ACID Isolation
-   Ensures consistency
-   Maximizes concurrent execution

------------------------------------------------------------------------

# Common Concurrency Problems

  Problem               Meaning
  --------------------- ---------------------------------
  Lost Update           One update overwrites another
  Dirty Read            Read uncommitted data
  Non-Repeatable Read   Same row gives different values
  Phantom Read          New rows appear between reads

------------------------------------------------------------------------

# Locking

``` text
Acquire Lock
     │
Read / Write
     │
COMMIT
     │
Release Lock
```

## Lock Types

  Lock            Purpose
  --------------- ------------------
  Shared (S)      Multiple readers
  Exclusive (X)   One writer

------------------------------------------------------------------------

# Lock Compatibility

  Existing     Shared   Exclusive
  ----------- -------- -----------
  Shared         ✓          ✗
  Exclusive      ✗          ✗

------------------------------------------------------------------------

# Deadlock

``` text
T1 waits for T2
      ▲      │
      └──────┘
```

Four Conditions:

-   Mutual Exclusion
-   Hold and Wait
-   No Preemption
-   Circular Wait

Solutions:

-   Detection
-   Prevention
-   Avoidance
-   Recovery

------------------------------------------------------------------------

# Starvation

``` text
T1 Waiting...

T2 Runs
T3 Runs
T4 Runs

↓

Aging

↓

T1 Executes
```

Use **Aging** to prevent indefinite waiting.

------------------------------------------------------------------------

# Timestamp Protocol

Every transaction gets a unique timestamp.

``` text
TS(T1)=5

TS(T2)=10

↓

Older executes first
```

Rules:

-   Read: TS ≥ WTS
-   Write: TS ≥ RTS and TS ≥ WTS

------------------------------------------------------------------------

# Optimistic Locking

``` text
Read
 │
Validate
 │
Commit
```

-   Assumes conflicts are rare
-   Validation before commit

------------------------------------------------------------------------

# Pessimistic Locking

``` text
Lock
 │
Read / Write
 │
Commit
 │
Unlock
```

-   Assumes conflicts are common
-   Lock first, work later

------------------------------------------------------------------------

# Two-Phase Locking (2PL)

``` text
Growing
(Acquire)

↓

Lock Point

↓

Shrinking
(Release)
```

Types:

-   Basic
-   Strict
-   Rigorous
-   Conservative

------------------------------------------------------------------------

# MVCC

``` text
Version 1

↓

Version 2

↓

Version 3
```

-   Multiple row versions
-   Snapshot Isolation
-   Readers rarely block writers

------------------------------------------------------------------------

# Comparison Table

  Concept       Purpose
  ------------- ------------------------
  Locking       Prevent conflicts
  Deadlock      Circular waiting
  Starvation    Indefinite waiting
  Timestamp     Order transactions
  Optimistic    Validate later
  Pessimistic   Lock first
  2PL           Serializable schedules
  MVCC          Multiple versions

------------------------------------------------------------------------

# Common Interview Questions

1.  What is concurrency control?
2.  Lost Update vs Dirty Read?
3.  Shared vs Exclusive Lock?
4.  Deadlock vs Starvation?
5.  What is Aging?
6.  Explain Timestamp Ordering.
7.  Optimistic vs Pessimistic Locking.
8.  What is 2PL?
9.  Explain MVCC.
10. MVCC vs Locking.

------------------------------------------------------------------------

# Last-Minute Checklist

``` text
✓ Concurrency Control

✓ Locking

✓ S-Lock & X-Lock

✓ Deadlock

✓ Starvation

✓ Timestamp Protocol

✓ Optimistic Locking

✓ Pessimistic Locking

✓ Two-Phase Locking

✓ MVCC
```

------------------------------------------------------------------------

# Memory Trick

``` text
Concurrency

↓

Lock

↓

Deadlock

↓

Starvation

↓

Timestamp

↓

Optimistic

↓

Pessimistic

↓

2PL

↓

MVCC
```

------------------------------------------------------------------------

# Final Takeaway

Concurrency control enables multiple users to access the same database
safely and efficiently. Locking, timestamp ordering, optimistic and
pessimistic locking, Two-Phase Locking, and MVCC each solve concurrency
problems in different ways. Mastering these concepts provides a strong
foundation for transaction processing, database design, university
examinations, and technical interviews.
