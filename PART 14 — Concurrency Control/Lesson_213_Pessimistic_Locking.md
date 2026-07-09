# Lesson 213 --- Pessimistic Locking

> **Part 14 --- Concurrency Control**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What Pessimistic Locking is
-   Why it is used
-   How pessimistic locking works
-   Types of pessimistic locks
-   Advantages and limitations
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Some applications cannot afford conflicting updates.

Instead of assuming conflicts are rare, they assume conflicts are
**likely**.

To prevent problems before they occur, the DBMS locks data before it is
accessed.

This approach is called **Pessimistic Locking**.

------------------------------------------------------------------------

# 2. What is Pessimistic Locking?

**Pessimistic Locking** is a concurrency control technique in which a
transaction acquires locks before reading or modifying data.

``` text
Acquire Lock
      │
Read / Write
      │
COMMIT
      │
Release Lock
```

Other conflicting transactions must wait until the lock is released.

------------------------------------------------------------------------

# 3. Why Use Pessimistic Locking?

It is preferred when:

-   Conflicts are common
-   Many users update the same records
-   Data consistency is more important than concurrency

Examples include banking, inventory management, and reservation systems.

------------------------------------------------------------------------

# 4. How Pessimistic Locking Works

``` text
Start Transaction
        │
Acquire Lock
        │
Read / Update Data
        │
COMMIT / ROLLBACK
        │
Release Lock
```

If another transaction requests the same resource:

``` text
Transaction 2

↓

Wait
```

------------------------------------------------------------------------

# 5. Types of Locks

### Shared Lock (S-Lock)

-   Allows multiple readers
-   Prevents conflicting writes

### Exclusive Lock (X-Lock)

-   Allows one writer
-   Blocks all other reads and writes (depending on isolation level)

------------------------------------------------------------------------

# 6. Example

Suppose Product Stock = 10.

``` text
T1 acquires X-Lock

↓

Updates Stock

↓

T2 tries to update

↓

Waits

↓

T1 COMMIT

↓

Lock Released

↓

T2 Continues
```

------------------------------------------------------------------------

# 7. Pessimistic vs Optimistic Locking

  Pessimistic                    Optimistic
  ------------------------------ ----------------------------
  Assumes conflicts are common   Assumes conflicts are rare
  Locks data before access       No locks during execution
  Transactions may wait          Validation before commit
  Fewer rollbacks                More rollbacks possible

------------------------------------------------------------------------

# 8. Real-World Examples

-   Banking transactions
-   Flight seat booking
-   Hotel reservation systems
-   Warehouse inventory updates
-   Stock trading platforms

------------------------------------------------------------------------

# 9. Advantages

-   Prevents conflicting updates
-   Strong data consistency
-   Fewer transaction retries
-   Suitable for write-heavy systems

------------------------------------------------------------------------

# 10. Limitations

-   Waiting between transactions
-   Deadlocks may occur
-   Lower concurrency
-   Lock management overhead

------------------------------------------------------------------------

# 11. Best Practices

-   Keep transactions short.
-   Acquire locks only when necessary.
-   Release locks promptly.
-   Access resources in a consistent order.

------------------------------------------------------------------------

# 12. Common Mistakes

❌ Holding locks for too long.

❌ Locking more data than required.

❌ Ignoring deadlock prevention strategies.

------------------------------------------------------------------------

# 13. Interview Questions

### Beginner

1.  What is Pessimistic Locking?
2.  Why is it called "pessimistic"?

### Intermediate

1.  Compare Optimistic and Pessimistic Locking.
2.  When should Pessimistic Locking be used?

### Advanced

1.  Why can pessimistic locking lead to deadlocks?
2.  Which workloads benefit most from pessimistic locking?

------------------------------------------------------------------------

# 14. Practice Problems

1.  Draw the pessimistic locking workflow.
2.  Explain waiting with a banking example.
3.  Compare optimistic and pessimistic locking.
4.  Explain why pessimistic locking reduces conflicts.

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
PESSIMISTIC

Lock First

↓

Work Later

↓

Safe Updates
```

## Key Points

-   Pessimistic Locking assumes conflicts are common.
-   Locks are acquired before accessing data.
-   Other transactions wait until locks are released.
-   It offers strong consistency but lower concurrency.
-   It is ideal for write-intensive applications.

------------------------------------------------------------------------

# Final Takeaway

Pessimistic Locking prevents data conflicts by locking resources before
they are accessed. Although it can reduce concurrency and introduce
waiting or deadlocks, it provides strong consistency for systems where
conflicting updates are frequent. It remains one of the most widely used
concurrency control techniques in enterprise database applications.
