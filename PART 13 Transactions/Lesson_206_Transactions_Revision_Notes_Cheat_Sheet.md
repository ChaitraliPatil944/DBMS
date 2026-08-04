# Lesson 206 --- Transactions Revision Notes & Cheat Sheet

> **Part 13 --- Transactions**

------------------------------------------------------------------------

# Quick Definition

A **transaction** is a logical unit of work that executes one or more
database operations as a single unit.

``` text
All Success
     │
 COMMIT

OR

Any Failure
     │
ROLLBACK
```

------------------------------------------------------------------------

# Why Transactions?

-   Prevent partial updates
-   Maintain consistency
-   Support recovery
-   Protect data integrity

------------------------------------------------------------------------

# Transaction Operations

  Operation                   Purpose
  --------------------------- ----------------------------------------
  BEGIN / START TRANSACTION   Starts a transaction
  COMMIT                      Permanently saves changes
  ROLLBACK                    Undoes uncommitted changes
  SAVEPOINT                   Creates an intermediate rollback point

------------------------------------------------------------------------

# ACID Properties

``` text
A → Atomicity

C → Consistency

I → Isolation

D → Durability
```

  Property      Meaning
  ------------- -------------------------------------
  Atomicity     All or Nothing
  Consistency   Valid State → Valid State
  Isolation     Independent Concurrent Transactions
  Durability    Committed Changes are Permanent

------------------------------------------------------------------------

# Transaction States

``` text
Start
 │
Active
 │
Partially Committed
 │
Committed
 │
Terminated

Failure Path

Active
 │
Failed
 │
Aborted
 │
Terminated
```

------------------------------------------------------------------------

# Checkpoints

Purpose:

-   Reduce recovery time
-   Mark recovery points
-   Reduce log scanning

``` text
Transactions
      │
Checkpoint
      │
Crash
      │
Recover From Checkpoint
```

------------------------------------------------------------------------

# Transaction Logs

Logs record every important database modification.

Typical Log Record

``` text
TID
Operation
Old Value
New Value
Timestamp
```

------------------------------------------------------------------------

# Write-Ahead Logging (WAL)

``` text
Write Log
     │
Flush Log
     │
Update Database
```

Rule:

> Log first, database later.

------------------------------------------------------------------------

# Recovery Basics

``` text
Crash
  │
Read Logs
  │
Find Checkpoint
  │
UNDO
  │
REDO
  │
Recovered Database
```

------------------------------------------------------------------------

# UNDO vs REDO

  UNDO                               REDO
  ---------------------------------- ----------------------------------
  Reverses incomplete transactions   Reapplies committed transactions
  Used after failures                Used after crashes
  Restores old values                Restores committed values

------------------------------------------------------------------------

# Common Failures

-   Transaction Failure
-   System Failure
-   Media Failure

------------------------------------------------------------------------

# Complete Flow

``` text
Transaction
     │
ACID
     │
States
     │
Logs
     │
Checkpoint
     │
Crash
     │
UNDO / REDO
     │
Recovery
```

------------------------------------------------------------------------

# Comparison Table

  Concept       Purpose
  ------------- -------------------------
  Transaction   Logical unit of work
  ACID          Reliability guarantees
  Checkpoint    Faster recovery
  Log           Records changes
  WAL           Log before data
  UNDO          Reverse incomplete work
  REDO          Reapply committed work
  Recovery      Restore consistency

------------------------------------------------------------------------

# Common Interview Questions

1.  What is a transaction?
2.  Explain ACID properties.
3.  COMMIT vs ROLLBACK.
4.  What are transaction states?
5.  What is a checkpoint?
6.  What is WAL?
7.  What is a transaction log?
8.  UNDO vs REDO.
9.  Explain database recovery.
10. How do logs and checkpoints work together?

------------------------------------------------------------------------

# Last-Minute Checklist

``` text
✓ Transactions

✓ ACID

✓ COMMIT & ROLLBACK

✓ Transaction States

✓ Checkpoints

✓ Logs

✓ WAL

✓ UNDO

✓ REDO

✓ Recovery Process
```

------------------------------------------------------------------------

# Memory Trick

``` text
Transaction

↓

ACID

↓

States

↓

Checkpoint

↓

Logs

↓

UNDO

↓

REDO

↓

Recovery
```

------------------------------------------------------------------------

# Final Takeaway

Transactions provide reliable execution of database operations, while
ACID properties guarantee correctness. Transaction states track
execution, logs and checkpoints support recovery, and UNDO/REDO restore
consistency after failures. Together, these concepts form the backbone
of transaction management in modern database systems and are among the
most important topics for DBMS exams and interviews.
