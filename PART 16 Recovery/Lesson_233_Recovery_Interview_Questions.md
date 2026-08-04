# Lesson 233 --- Recovery Interview Questions

> **Part 16 --- Recovery**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will:

-   Revise database recovery concepts
-   Prepare for DBMS interviews
-   Answer scenario-based recovery questions
-   Differentiate recovery techniques

------------------------------------------------------------------------

# 1. Beginner Questions

### Q1. What is database recovery?

Recovery is the process of restoring a database to a consistent state
after a failure.

------------------------------------------------------------------------

### Q2. Why is recovery required?

-   Prevents data loss
-   Restores consistency
-   Preserves committed transactions
-   Supports ACID properties

------------------------------------------------------------------------

### Q3. What are the major types of failures?

-   Transaction failure
-   System failure
-   Media failure

------------------------------------------------------------------------

### Q4. What is a transaction log?

A transaction log records every important database operation required
for recovery.

------------------------------------------------------------------------

### Q5. What is Write-Ahead Logging (WAL)?

WAL ensures that log records are written to stable storage before the
corresponding database pages.

------------------------------------------------------------------------

# 2. UNDO & REDO

### Q6. What is UNDO?

UNDO restores old values by reversing incomplete or failed transactions.

------------------------------------------------------------------------

### Q7. What is REDO?

REDO reapplies committed changes that were not written to disk before a
crash.

------------------------------------------------------------------------

### Q8. Which ACID properties do UNDO and REDO support?

-   UNDO → Atomicity
-   REDO → Durability

------------------------------------------------------------------------

### Q9. Immediate Update vs Deferred Update?

  Immediate Update            Deferred Update
  --------------------------- ----------------------
  Updates before COMMIT       Updates after COMMIT
  UNDO & REDO may be needed   Mostly REDO required

------------------------------------------------------------------------

# 3. Shadow Paging & Log-Based Recovery

### Q10. What is Shadow Paging?

A recovery technique that maintains shadow and current page tables
instead of transaction logs.

------------------------------------------------------------------------

### Q11. Shadow Paging vs Log-Based Recovery?

  Shadow Paging   Log-Based Recovery
  --------------- --------------------
  No UNDO/REDO    Uses UNDO & REDO
  Page copies     Transaction logs
  Simpler         More scalable

------------------------------------------------------------------------

# 4. ARIES

### Q12. What does ARIES stand for?

Algorithms for Recovery and Isolation Exploiting Semantics.

------------------------------------------------------------------------

### Q13. What are the three phases of ARIES?

1.  Analysis
2.  REDO
3.  UNDO

------------------------------------------------------------------------

### Q14. What is a Compensation Log Record (CLR)?

A log record that records an UNDO operation to support safe repeated
recovery.

------------------------------------------------------------------------

# 5. Crash Recovery

### Q15. What is crash recovery?

The process of restoring the database after an unexpected system
failure.

------------------------------------------------------------------------

### Q16. Why are checkpoints important?

Checkpoints reduce recovery time by limiting how much of the log must be
scanned.

------------------------------------------------------------------------

### Q17. Why are both UNDO and REDO needed?

UNDO removes incomplete changes, while REDO restores committed changes.

------------------------------------------------------------------------

# 6. Scenario-Based Questions

### Scenario 1

A transaction commits, but the system crashes before data reaches disk.

**Answer:** Perform REDO.

------------------------------------------------------------------------

### Scenario 2

A transaction crashes before COMMIT.

**Answer:** Perform UNDO.

------------------------------------------------------------------------

### Scenario 3

A database must recover quickly after a crash.

**Answer:** Use checkpoints with log-based recovery (such as ARIES).

------------------------------------------------------------------------

### Scenario 4

Which recovery method avoids transaction logs?

**Answer:** Shadow Paging.

------------------------------------------------------------------------

# 7. Rapid Fire

1.  What is recovery?
2.  WAL?
3.  UNDO?
4.  REDO?
5.  Shadow Paging?
6.  Checkpoint?
7.  ARIES?
8.  CLR?
9.  Immediate Update?
10. Deferred Update?

------------------------------------------------------------------------

# 8. Interview Tips

-   Relate recovery to ACID properties.
-   Explain WAL before discussing ARIES.
-   Compare UNDO and REDO clearly.
-   Mention checkpoints whenever discussing crash recovery.
-   Use banking examples to explain consistency.

------------------------------------------------------------------------

# Revision Sheet

``` text
Recovery
   │
Logs
   │
WAL
   │
UNDO
   │
REDO
   │
Shadow Paging
   │
ARIES
   │
Crash Recovery
```

------------------------------------------------------------------------

# Final Takeaway

Recovery interview questions focus on maintaining consistency after
failures. A solid understanding of transaction logs, WAL, UNDO, REDO,
Shadow Paging, ARIES, checkpoints, and crash recovery prepares you for
university examinations, placement interviews, and enterprise database
discussions.
