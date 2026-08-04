# Lesson 204 --- Transactions Interview Questions

> **Part 13 --- Transactions**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will:

-   Revise transaction management concepts
-   Prepare for DBMS interviews
-   Answer scenario-based questions confidently
-   Differentiate key transaction concepts

------------------------------------------------------------------------

# 1. Beginner Questions

### Q1. What is a transaction?

A transaction is a logical unit of work consisting of one or more
database operations executed as a single unit.

------------------------------------------------------------------------

### Q2. Why are transactions needed?

-   Prevent partial updates
-   Maintain consistency
-   Support recovery
-   Protect data integrity

------------------------------------------------------------------------

### Q3. What are the basic transaction operations?

-   BEGIN / START TRANSACTION
-   COMMIT
-   ROLLBACK
-   SAVEPOINT

------------------------------------------------------------------------

### Q4. What does COMMIT do?

It permanently saves all changes made during a transaction.

------------------------------------------------------------------------

### Q5. What does ROLLBACK do?

It undoes all uncommitted changes and restores the previous database
state.

------------------------------------------------------------------------

# 2. ACID Questions

### Q6. What does ACID stand for?

-   Atomicity
-   Consistency
-   Isolation
-   Durability

------------------------------------------------------------------------

### Q7. Explain Atomicity.

Either every operation succeeds or none of them do.

------------------------------------------------------------------------

### Q8. Explain Consistency.

Every transaction moves the database from one valid state to another.

------------------------------------------------------------------------

### Q9. Explain Isolation.

Concurrent transactions should not interfere with one another.

------------------------------------------------------------------------

### Q10. Explain Durability.

Committed changes remain permanent even after a crash.

------------------------------------------------------------------------

# 3. Transaction State Questions

### Q11. List the transaction states.

-   Active
-   Partially Committed
-   Committed
-   Failed
-   Aborted
-   Terminated

------------------------------------------------------------------------

### Q12. Difference between Failed and Aborted?

-   Failed: Error detected.
-   Aborted: Changes have been rolled back.

------------------------------------------------------------------------

### Q13. Difference between Partially Committed and Committed?

-   Partially Committed: Waiting for permanent commit.
-   Committed: Changes are permanent.

------------------------------------------------------------------------

# 4. Recovery Questions

### Q14. What is a checkpoint?

A recovery marker that reduces crash recovery time.

------------------------------------------------------------------------

### Q15. What is a transaction log?

A sequential record of database changes used for recovery.

------------------------------------------------------------------------

### Q16. What is Write-Ahead Logging (WAL)?

The log must be written to stable storage before the corresponding
database page.

------------------------------------------------------------------------

### Q17. What is UNDO?

Reverses incomplete or failed transactions.

------------------------------------------------------------------------

### Q18. What is REDO?

Reapplies committed changes after a crash.

------------------------------------------------------------------------

### Q19. What is database recovery?

The process of restoring the database to a consistent state after
failure.

------------------------------------------------------------------------

# 5. Scenario-Based Questions

### Scenario 1

A power failure occurs after COMMIT but before data reaches disk.

**Answer:** REDO restores the committed changes using transaction logs.

------------------------------------------------------------------------

### Scenario 2

A transfer fails halfway through.

**Answer:** ROLLBACK restores the original state using Atomicity.

------------------------------------------------------------------------

### Scenario 3

Two users update the same record simultaneously.

**Answer:** Isolation prevents inconsistent concurrent updates.

------------------------------------------------------------------------

### Scenario 4

Why use checkpoints?

**Answer:** To reduce the amount of log that must be processed during
recovery.

------------------------------------------------------------------------

# 6. Rapid Fire

1.  What is WAL?
2.  Which ACID property guarantees permanence?
3.  Which command saves changes?
4.  Which command undoes changes?
5.  What is a checkpoint?
6.  What is a log?
7.  What is UNDO?
8.  What is REDO?
9.  Why are transactions important?
10. Why are checkpoints used?

------------------------------------------------------------------------

# 7. Interview Tips

-   Explain with banking examples.
-   Draw transaction state diagrams.
-   Distinguish COMMIT vs ROLLBACK.
-   Connect ACID with real-world applications.
-   Explain recovery step by step.

------------------------------------------------------------------------

# Revision Sheet

``` text
Transaction
   │
ACID
   │
States
   │
Logs
   │
Checkpoints
   │
UNDO / REDO
   │
Recovery
```

## Final Takeaway

Transaction management interview questions focus on reliability,
consistency, and recovery. If you understand the transaction lifecycle,
ACID properties, logs, checkpoints, and UNDO/REDO, you will be well
prepared for DBMS technical interviews and university examinations.
