# Lesson 228 --- REDO Recovery

> **Part 16 --- Recovery**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What REDO recovery is
-   Why REDO is required
-   How REDO works
-   REDO using transaction logs
-   Immediate and deferred update concepts
-   Advantages and limitations
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Sometimes a transaction **commits successfully**, but the updated data
is not written to disk before a system crash.

Without recovery, the committed changes would be lost.

To restore these committed updates, the DBMS performs **REDO**.

------------------------------------------------------------------------

# 2. What is REDO?

**REDO** is the recovery process that reapplies the changes of committed
transactions to ensure their updates are permanently reflected in the
database.

``` text
Start Transaction
        │
Update Data
        │
COMMIT
        │
Crash Before Disk Write
        │
REDO
        │
Committed Values Restored
```

------------------------------------------------------------------------

# 3. Why is REDO Needed?

Without REDO:

-   Committed updates may disappear.
-   Durability is violated.
-   The database may contain outdated values.

REDO guarantees the **Durability** property of ACID.

------------------------------------------------------------------------

# 4. How REDO Works

Before a transaction commits, its updates are recorded in the
transaction log.

Example log:

``` text
START T1
UPDATE A
Old Value = 100
New Value = 80
COMMIT
```

After a crash:

``` text
REDO

A = 80
```

The committed value is restored.

------------------------------------------------------------------------

# 5. REDO Using Transaction Logs

Typical log record:

``` text
<Transaction ID,
 Data Item,
 Old Value,
 New Value>
```

Recovery manager:

1.  Reads the log.
2.  Finds committed transactions.
3.  Reapplies new values if necessary.

------------------------------------------------------------------------

# 6. REDO Workflow

``` text
Crash
  │
Read Log
  │
Committed Transaction?
  │
Yes
  │
Restore New Values
  │
Database Consistent
```

------------------------------------------------------------------------

# 7. Immediate vs Deferred Update

### Immediate Update

-   Changes may reach the database before COMMIT.
-   Both UNDO and REDO may be required.

### Deferred Update

-   Database is updated only after COMMIT.
-   Usually requires REDO after a crash.

------------------------------------------------------------------------

# 8. Example

Account Balance = ₹10,000

``` text
T1 Deposits ₹2,000

↓

Balance = ₹12,000

↓

COMMIT

↓

Crash Before Disk Write

↓

REDO

↓

Balance = ₹12,000
```

------------------------------------------------------------------------

# 9. UNDO vs REDO

  UNDO                  REDO
  --------------------- ------------------------
  Restores old values   Restores new values
  Failed transactions   Committed transactions
  Supports Atomicity    Supports Durability

------------------------------------------------------------------------

# 10. Advantages

-   Preserves committed work
-   Guarantees durability
-   Restores consistency
-   Uses transaction logs efficiently

------------------------------------------------------------------------

# 11. Limitations

-   Requires log storage
-   Recovery takes time
-   Log processing overhead

------------------------------------------------------------------------

# 12. Best Practices

-   Enable Write-Ahead Logging (WAL).
-   Flush logs before COMMIT.
-   Configure checkpoints.
-   Test crash recovery regularly.

------------------------------------------------------------------------

# 13. Common Mistakes

❌ Confusing REDO with UNDO.

❌ Assuming every committed change is already on disk.

❌ Forgetting REDO restores **new values**.

------------------------------------------------------------------------

# 14. Interview Questions

### Beginner

1.  What is REDO?
2.  Why is REDO required?

### Intermediate

1.  Explain REDO using transaction logs.
2.  Compare UNDO and REDO.

### Advanced

1.  How does REDO support ACID?
2.  Why are new values stored in logs?

------------------------------------------------------------------------

# 15. Practice Problems

1.  Draw the REDO workflow.
2.  Explain REDO with a banking example.
3.  Compare REDO and UNDO.
4.  Explain why committed changes may need REDO.

------------------------------------------------------------------------

# Revision Notes

``` text
Crash
   │
Read Log
   │
Restore New Values
   │
REDO Complete
```

## Memory Trick

``` text
REDO

Committed

↓

New Values

↓

Restore
```

## Key Points

-   REDO reapplies committed transactions.
-   New values are restored from logs.
-   REDO guarantees Durability.
-   Immediate update may require both UNDO and REDO.
-   Checkpoints reduce REDO time.

------------------------------------------------------------------------

# Final Takeaway

REDO recovery ensures that committed transactions are never lost, even
if a system crashes before updated pages reach disk. By replaying
committed changes from the transaction log, REDO guarantees durability
and keeps the database consistent. Together with UNDO, it forms the
foundation of modern database recovery mechanisms.
