# Lesson 208 --- Locking

> **Part 14 --- Concurrency Control**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What locking is
-   Why locks are required
-   Shared and Exclusive locks
-   Lock compatibility
-   Lock conversion
-   Lock granularity
-   Advantages and disadvantages
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

When multiple transactions access the same data simultaneously,
conflicts may occur.

A DBMS prevents these conflicts using **locks**.

A lock is like reserving a resource. While one transaction is using it,
other transactions may have to wait.

------------------------------------------------------------------------

# 2. What is Locking?

**Locking** is a concurrency control technique in which a transaction
acquires permission before reading or modifying data.

``` text
Transaction
     │
Acquire Lock
     │
Read / Write Data
     │
Release Lock
```

------------------------------------------------------------------------

# 3. Why is Locking Needed?

Without locking:

-   Lost Updates
-   Dirty Reads
-   Data inconsistency
-   Concurrent write conflicts

With locking:

-   Safe concurrent access
-   Correct transaction execution
-   Better consistency

------------------------------------------------------------------------

# 4. Types of Locks

## Shared Lock (S-Lock)

Allows multiple transactions to **read** the same data simultaneously.

``` text
T1 ---- Read
          │
        Shared Lock
          │
T2 ---- Read
```

No transaction can modify the data while a shared lock exists.

------------------------------------------------------------------------

## Exclusive Lock (X-Lock)

Allows one transaction to **read and write** a data item.

``` text
T1
 │
Exclusive Lock
 │
Read + Write

T2
 │
Wait
```

Only one exclusive lock is allowed at a time.

------------------------------------------------------------------------

# 5. Lock Compatibility Matrix

  Existing Lock    Shared Request   Exclusive Request
  --------------- ---------------- -------------------
  Shared             ✅ Allowed      ❌ Not Allowed
  Exclusive        ❌ Not Allowed    ❌ Not Allowed

------------------------------------------------------------------------

# 6. Lock Conversion

Sometimes a transaction first reads data and later updates it.

``` text
Shared Lock
     │
Upgrade
     │
Exclusive Lock
```

This is called **lock upgrade**.

Similarly,

``` text
Exclusive Lock
     │
Downgrade
     │
Shared Lock
```

------------------------------------------------------------------------

# 7. Lock Granularity

Locks can be applied at different levels:

-   Database
-   Table
-   Page
-   Row (Record)

``` text
Database
   │
Table
   │
Page
   │
Row
```

Smaller locks provide higher concurrency but require more management.

------------------------------------------------------------------------

# 8. Locking Workflow

``` text
Start Transaction
        │
Acquire Lock
        │
Execute Query
        │
COMMIT / ROLLBACK
        │
Release Lock
```

------------------------------------------------------------------------

# 9. Real-World Example

### Banking

Customer A transfers money.

While the balance is being updated:

-   Other users may read depending on isolation level.
-   No other transaction should modify the same account balance.

------------------------------------------------------------------------

# 10. Advantages

-   Prevents conflicting updates
-   Preserves consistency
-   Supports ACID Isolation
-   Reliable concurrent execution

------------------------------------------------------------------------

# 11. Limitations

-   Waiting between transactions
-   Deadlocks
-   Starvation
-   Lock management overhead

------------------------------------------------------------------------

# 12. Best Practices

-   Keep transactions short.
-   Release locks quickly.
-   Lock only required data.
-   Use row-level locks when appropriate.

------------------------------------------------------------------------

# 13. Common Mistakes

❌ Holding locks longer than necessary.

❌ Locking entire tables unnecessarily.

❌ Forgetting that locks can cause deadlocks.

------------------------------------------------------------------------

# 14. Interview Questions

### Beginner

1.  What is locking?
2.  Why is locking required?
3.  What is a Shared Lock?

### Intermediate

1.  Shared Lock vs Exclusive Lock.
2.  Explain lock compatibility.

### Advanced

1.  What is lock granularity?
2.  Why can locking lead to deadlocks?

------------------------------------------------------------------------

# 15. Practice Problems

1.  Draw the locking workflow.
2.  Compare Shared and Exclusive locks.
3.  Explain lock conversion.
4.  Explain row-level vs table-level locking.

------------------------------------------------------------------------

# Revision Notes

``` text
Acquire Lock
     │
Read / Write
     │
COMMIT
     │
Release Lock
```

## Memory Trick

``` text
S Lock

=

Share Reading

X Lock

=

Exclusive Writing
```

## Key Points

-   Locking coordinates concurrent transactions.
-   Shared locks allow multiple readers.
-   Exclusive locks allow one writer.
-   Locks protect consistency but may reduce concurrency.
-   Proper lock management prevents many transaction conflicts.

------------------------------------------------------------------------

# Final Takeaway

Locking is the most widely used concurrency control mechanism in
relational databases. By controlling how transactions access shared
data, locks prevent conflicts and maintain consistency. Understanding
shared locks, exclusive locks, compatibility rules, and lock granularity
provides the foundation for advanced topics such as deadlocks,
starvation, and Two-Phase Locking (2PL).
