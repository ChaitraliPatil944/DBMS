# Lesson 235 --- Recovery Revision Notes & Cheat Sheet

> **Part 16 --- Recovery**

------------------------------------------------------------------------

# Quick Definition

**Database Recovery** is the process of restoring a database to a
consistent state after a failure while preserving committed transactions
and removing incomplete ones.

``` text
Failure
   │
Recovery
   │
Consistent Database
```

------------------------------------------------------------------------

# Why Recovery?

-   Prevents data loss
-   Restores consistency
-   Supports ACID properties
-   Maintains business continuity

------------------------------------------------------------------------

# Types of Failures

  Failure Type          Description
  --------------------- -------------------------
  Transaction Failure   Error before COMMIT
  System Failure        Power/OS/DBMS crash
  Media Failure         Disk or storage failure

------------------------------------------------------------------------

# Recovery Components

``` text
Transactions
      │
Transaction Log
      │
Checkpoints
      │
Recovery Manager
      │
Recovered Database
```

------------------------------------------------------------------------

# UNDO Recovery

Purpose:

-   Restore **old values**
-   Roll back incomplete transactions
-   Supports **Atomicity**

``` text
Failure
   │
Read Log
   │
UNDO
   │
Old Values Restored
```

------------------------------------------------------------------------

# REDO Recovery

Purpose:

-   Restore **new values**
-   Reapply committed transactions
-   Supports **Durability**

``` text
Failure
   │
Read Log
   │
REDO
   │
Committed Values Restored
```

------------------------------------------------------------------------

# UNDO vs REDO

  UNDO                  REDO
  --------------------- ------------------------
  Old values            New values
  Failed transactions   Committed transactions
  Atomicity             Durability

------------------------------------------------------------------------

# Write-Ahead Logging (WAL)

Rule:

> **Write the log record before writing the corresponding database
> page.**

``` text
Update
   │
Write Log
   │
Flush Log
   │
Write Database Page
```

------------------------------------------------------------------------

# Deferred vs Immediate Update

  Deferred Update       Immediate Update
  --------------------- ----------------------
  Update after COMMIT   Update before COMMIT
  Mainly REDO           UNDO + REDO

------------------------------------------------------------------------

# Shadow Paging

``` text
Shadow Table
      │
Copy Pages
      │
Modify Copies
      │
Commit?
  │         │
Yes        No
 │          │
Switch    Restore Shadow
Pointer   Table
```

-   No transaction logs
-   No UNDO or REDO
-   Higher storage overhead

------------------------------------------------------------------------

# Log-Based Recovery

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

Most commercial DBMSs use this approach.

------------------------------------------------------------------------

# ARIES

Three recovery phases:

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

Core principles:

-   Write-Ahead Logging (WAL)
-   Repeat History During REDO
-   Log UNDO using CLRs

------------------------------------------------------------------------

# Crash Recovery Workflow

``` text
Crash
 │
Restart DBMS
 │
Locate Checkpoint
 │
Read Log
 │
REDO
 │
UNDO
 │
Database Restored
```

------------------------------------------------------------------------

# Comparison Table

  Concept              Purpose
  -------------------- -------------------------------
  Recovery             Restore consistency
  UNDO                 Restore old values
  REDO                 Restore new values
  WAL                  Protect transaction logs
  Shadow Paging        Recovery without logs
  Log-Based Recovery   Recovery using logs
  ARIES                Enterprise recovery algorithm
  Checkpoints          Faster recovery
  Crash Recovery       Restore after system failure

------------------------------------------------------------------------

# Common Interview Questions

1.  What is database recovery?
2.  Types of failures?
3.  UNDO vs REDO?
4.  What is WAL?
5.  Deferred vs Immediate Update?
6.  Shadow Paging vs Log-Based Recovery?
7.  What is ARIES?
8.  Explain the three ARIES phases.
9.  What is a checkpoint?
10. Explain crash recovery.

------------------------------------------------------------------------

# Last-Minute Checklist

``` text
✓ Recovery Basics
✓ Failure Types
✓ Transaction Logs
✓ WAL
✓ UNDO
✓ REDO
✓ Deferred Update
✓ Immediate Update
✓ Shadow Paging
✓ Log-Based Recovery
✓ ARIES
✓ Checkpoints
✓ Crash Recovery
```

------------------------------------------------------------------------

# Memory Trick

``` text
FAILURE

↓

LOG

↓

WAL

↓

UNDO

↓

REDO

↓

ARIES

↓

RECOVER
```

------------------------------------------------------------------------

# Key Points

-   Recovery restores database consistency after failures.
-   UNDO restores old values; REDO restores new values.
-   WAL requires logs before data pages.
-   Shadow Paging avoids transaction logs.
-   Log-Based Recovery is the standard enterprise approach.
-   ARIES uses Analysis, REDO, and UNDO.
-   Checkpoints reduce recovery time.

------------------------------------------------------------------------

# Final Takeaway

Database recovery ensures that failures do not compromise data integrity
or business operations. By combining transaction logs, Write-Ahead
Logging, UNDO, REDO, checkpoints, Shadow Paging, Log-Based Recovery, and
ARIES, modern DBMSs can recover efficiently from crashes while
preserving ACID guarantees and maintaining a consistent database state.
