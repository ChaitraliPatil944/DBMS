# Lesson 227 --- UNDO Recovery

> **Part 16 --- Recovery**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What UNDO recovery is
-   Why UNDO is required
-   How UNDO works
-   UNDO using transaction logs
-   Immediate and deferred update concepts
-   Advantages and limitations
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Not every transaction finishes successfully.

A transaction may fail because of:

-   Power failure
-   Software error
-   Deadlock
-   User cancellation

If a transaction has modified the database but has **not committed**,
those changes must be removed.

This process is called **UNDO**.

------------------------------------------------------------------------

# 2. What is UNDO?

**UNDO** is the recovery process that reverses the effects of incomplete
or failed transactions, restoring the database to its previous
consistent state.

``` text
Start Transaction
        │
Update Data
        │
Failure Before COMMIT
        │
UNDO
        │
Old Values Restored
```

------------------------------------------------------------------------

# 3. Why is UNDO Needed?

Without UNDO:

-   Partial updates remain.
-   Database becomes inconsistent.
-   Atomicity is violated.

UNDO guarantees the **Atomicity** property of ACID.

------------------------------------------------------------------------

# 4. How UNDO Works

Before modifying a data item, the DBMS stores its **old value** in the
transaction log.

Example log:

``` text
START T1
UPDATE A
Old Value = 100
New Value = 80
```

If T1 fails:

``` text
UNDO

A = 100
```

------------------------------------------------------------------------

# 5. UNDO Using Transaction Logs

Typical log record:

``` text
<Transaction ID,
 Data Item,
 Old Value,
 New Value>
```

Recovery manager:

1.  Reads the log.
2.  Finds incomplete transactions.
3.  Restores old values in reverse order.

------------------------------------------------------------------------

# 6. UNDO Workflow

``` text
Crash
  │
Read Log
  │
Incomplete Transaction?
  │
Yes
  │
Restore Old Values
  │
Database Consistent
```

------------------------------------------------------------------------

# 7. Immediate vs Deferred Update

### Immediate Update

-   Database may be updated before COMMIT.
-   UNDO is required if the transaction fails.

### Deferred Update

-   Updates are applied only after COMMIT.
-   UNDO is generally unnecessary because uncommitted changes never
    reach the database.

------------------------------------------------------------------------

# 8. Example

Account Balance = ₹10,000

``` text
T1 Withdraw ₹2,000

↓

Balance = ₹8,000

↓

Crash Before COMMIT

↓

UNDO

↓

Balance = ₹10,000
```

------------------------------------------------------------------------

# 9. Advantages

-   Preserves Atomicity
-   Removes incomplete changes
-   Maintains consistency
-   Works with transaction logs

------------------------------------------------------------------------

# 10. Limitations

-   Requires log storage
-   Recovery time increases with long transactions
-   Log management overhead

------------------------------------------------------------------------

# 11. Best Practices

-   Enable Write-Ahead Logging (WAL).
-   Keep transactions short.
-   Record old values before updates.
-   Test recovery procedures regularly.

------------------------------------------------------------------------

# 12. Common Mistakes

❌ Confusing UNDO with ROLLBACK.

❌ Assuming every crash requires only UNDO.

❌ Forgetting that UNDO restores **old values**.

------------------------------------------------------------------------

# 13. Interview Questions

### Beginner

1.  What is UNDO?
2.  Why is UNDO required?

### Intermediate

1.  Explain UNDO using transaction logs.
2.  Immediate vs Deferred Update.

### Advanced

1.  How does UNDO support ACID?
2.  Why are old values stored in logs?

------------------------------------------------------------------------

# 14. Practice Problems

1.  Draw the UNDO workflow.
2.  Explain UNDO with a banking example.
3.  Compare UNDO and ROLLBACK.
4.  Explain why old values are logged.

------------------------------------------------------------------------

# Revision Notes

``` text
Failure
   │
Read Log
   │
Restore Old Values
   │
UNDO Complete
```

## Memory Trick

``` text
UNDO

Failure

↓

Old Values

↓

Restore
```

## Key Points

-   UNDO reverses incomplete transactions.
-   Old values are stored in logs.
-   UNDO guarantees Atomicity.
-   Immediate update systems require UNDO.
-   Recovery restores consistency.

------------------------------------------------------------------------

# Final Takeaway

UNDO recovery protects the database from incomplete transactions by
restoring the previous values recorded in the transaction log. It is a
fundamental recovery mechanism that ensures atomicity and consistency
after transaction failures, forming the basis for advanced recovery
algorithms used in modern DBMSs.
