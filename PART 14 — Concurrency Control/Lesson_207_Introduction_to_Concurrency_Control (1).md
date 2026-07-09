# Lesson 207 --- Introduction to Concurrency Control

> **Part 14 --- Concurrency Control**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What concurrency control is
-   Why concurrency control is needed
-   Problems caused by concurrent transactions
-   Goals of concurrency control
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Modern databases serve thousands of users simultaneously.

Imagine two users transferring money from the same account at the same
time.

Without proper coordination, the final balance may become incorrect.

The DBMS solves this using **Concurrency Control**.

------------------------------------------------------------------------

# 2. What is Concurrency Control?

**Concurrency Control** is the mechanism used by a DBMS to manage
multiple transactions executing at the same time while preserving data
consistency.

``` text
Multiple Users
      │
Concurrent Transactions
      │
Concurrency Control
      │
Consistent Database
```

------------------------------------------------------------------------

# 3. Why is Concurrency Control Needed?

Without concurrency control:

-   Lost updates
-   Dirty reads
-   Inconsistent data
-   Incorrect reports
-   Unpredictable transaction results

------------------------------------------------------------------------

# 4. Example

Initial Balance = ₹10,000

Transaction T1 withdraws ₹2,000.

Transaction T2 withdraws ₹3,000 simultaneously.

Without synchronization:

``` text
T1 reads 10000
T2 reads 10000
T1 writes 8000
T2 writes 7000
```

Correct balance should be **₹5,000**, but the database stores
**₹7,000**.

This is a **Lost Update**.

------------------------------------------------------------------------

# 5. Goals of Concurrency Control

-   Maintain consistency
-   Prevent conflicts
-   Preserve isolation
-   Maximize parallel execution
-   Improve throughput

------------------------------------------------------------------------

# 6. Common Concurrency Problems

-   Lost Update
-   Dirty Read
-   Non-Repeatable Read
-   Phantom Read

These problems are explained in later lessons.

------------------------------------------------------------------------

# 7. How DBMS Handles Concurrency

``` text
Transactions
      │
Scheduler
      │
Locking / MVCC / Timestamp
      │
Safe Execution
```

------------------------------------------------------------------------

# 8. Real-World Examples

### Banking

-   ATM withdrawals
-   Online transfers

### E-commerce

-   Multiple users buying the last product

### Airline Reservation

-   Multiple users booking the same seat

------------------------------------------------------------------------

# 9. Advantages

-   Correct results
-   Better resource utilization
-   High availability
-   Safe multi-user access

------------------------------------------------------------------------

# 10. Limitations

-   Locking overhead
-   Waiting between transactions
-   Deadlocks may occur
-   More complex DBMS implementation

------------------------------------------------------------------------

# 11. Best Practices

-   Keep transactions short.
-   Access data in a consistent order.
-   Commit quickly.
-   Choose an appropriate isolation level.

------------------------------------------------------------------------

# 12. Common Mistakes

❌ Ignoring concurrent access.

❌ Assuming transactions never overlap.

❌ Holding locks longer than necessary.

------------------------------------------------------------------------

# 13. Interview Questions

### Beginner

1.  What is concurrency control?
2.  Why is it needed?

### Intermediate

1.  What problems occur without concurrency control?
2.  What is a lost update?

### Advanced

1.  How does a DBMS manage concurrent transactions?
2.  Why is concurrency control essential for ACID?

------------------------------------------------------------------------

# 14. Practice Problems

1.  Explain concurrency control with a banking example.
2.  Define lost update.
3.  List the goals of concurrency control.
4.  Draw the concurrency control workflow.

------------------------------------------------------------------------

# Revision Notes

``` text
Users
 │
Transactions
 │
Concurrency Control
 │
Consistent Database
```

## Memory Trick

``` text
CONCURRENCY

Many Users

↓

One Correct Database
```

## Key Points

-   Concurrency control manages simultaneous transactions.
-   It preserves consistency and isolation.
-   It prevents conflicts like lost updates.
-   Modern DBMSs use locking, timestamps, and MVCC.

------------------------------------------------------------------------

# Final Takeaway

Concurrency control enables multiple users to work on the same database
safely and efficiently. By coordinating simultaneous transactions, the
DBMS preserves consistency, prevents conflicts, and ensures reliable
results. It forms the foundation for locking, deadlock handling,
timestamp protocols, and MVCC, which are explored in the following
lessons.
