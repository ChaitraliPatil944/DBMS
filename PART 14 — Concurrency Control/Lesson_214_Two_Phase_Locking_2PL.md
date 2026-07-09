# Lesson 214 --- Two-Phase Locking (2PL)

> **Part 14 --- Concurrency Control**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What Two-Phase Locking (2PL) is
-   Why 2PL is required
-   Growing and Shrinking phases
-   Types of 2PL
-   How 2PL guarantees serializability
-   Advantages and limitations
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Simply using locks is not enough.

If transactions acquire and release locks in an arbitrary order,
inconsistent execution may still occur.

To solve this, DBMSs use the **Two-Phase Locking (2PL)** protocol.

------------------------------------------------------------------------

# 2. What is Two-Phase Locking?

**Two-Phase Locking (2PL)** is a locking protocol in which every
transaction has exactly two phases:

1.  Growing Phase
2.  Shrinking Phase

It guarantees **conflict serializability**.

``` text
Growing Phase
Acquire Locks
      │
Lock Point
      │
Shrinking Phase
Release Locks
```

------------------------------------------------------------------------

# 3. Growing Phase

During this phase:

-   Acquire new locks ✔
-   Release locks ✘

``` text
Acquire Lock A
Acquire Lock B
Acquire Lock C
```

The transaction keeps collecting locks.

------------------------------------------------------------------------

# 4. Lock Point

The **Lock Point** is the moment when the transaction acquires its final
lock.

``` text
Acquire
Acquire
Acquire

↓

Lock Point
```

After this point, no new locks can be acquired.

------------------------------------------------------------------------

# 5. Shrinking Phase

During this phase:

-   Release locks ✔
-   Acquire new locks ✘

``` text
Release Lock C
Release Lock B
Release Lock A
```

------------------------------------------------------------------------

# 6. Complete Workflow

``` text
Start
 │
Growing Phase
(Acquire Locks)
 │
Lock Point
 │
Shrinking Phase
(Release Locks)
 │
Commit
```

------------------------------------------------------------------------

# 7. Types of Two-Phase Locking

## Basic 2PL

-   Follows growing and shrinking phases.
-   Deadlocks are possible.

## Strict 2PL

-   Holds all exclusive locks until COMMIT/ROLLBACK.
-   Prevents cascading rollbacks.
-   Most commonly used.

## Rigorous 2PL

-   Holds both shared and exclusive locks until COMMIT.
-   Provides stronger isolation.

## Conservative (Static) 2PL

-   Acquires all required locks before execution starts.
-   Eliminates deadlocks.
-   May reduce concurrency.

------------------------------------------------------------------------

# 8. Why Does 2PL Guarantee Serializability?

``` text
Transactions

↓

Acquire Locks

↓

No Illegal Conflicts

↓

Conflict Serializable Schedule
```

Lock ordering ensures conflicting operations execute in a consistent
sequence.

------------------------------------------------------------------------

# 9. Real-World Example

### Banking

A fund transfer:

-   Lock source account.
-   Lock destination account.
-   Update balances.
-   Commit.
-   Release locks.

No other transaction can interfere during the critical section.

------------------------------------------------------------------------

# 10. Advantages

-   Guarantees conflict serializability
-   Strong consistency
-   Widely supported
-   Simple to understand

------------------------------------------------------------------------

# 11. Limitations

-   Deadlocks (except Conservative 2PL)
-   Waiting between transactions
-   Lock overhead
-   Reduced concurrency

------------------------------------------------------------------------

# 12. Best Practices

-   Keep transactions short.
-   Lock resources in a fixed order.
-   Prefer Strict 2PL in OLTP systems.
-   Monitor deadlocks.

------------------------------------------------------------------------

# 13. Common Mistakes

❌ Acquiring new locks during the shrinking phase.

❌ Releasing locks too early.

❌ Confusing Strict 2PL with Basic 2PL.

------------------------------------------------------------------------

# 14. Interview Questions

### Beginner

1.  What is Two-Phase Locking?
2.  What are the two phases?

### Intermediate

1.  What is the Lock Point?
2.  Basic vs Strict 2PL?

### Advanced

1.  Explain all types of 2PL.
2.  Why does 2PL guarantee conflict serializability?

------------------------------------------------------------------------

# 15. Practice Problems

1.  Draw the 2PL workflow.
2.  Explain growing and shrinking phases.
3.  Compare Basic, Strict, Rigorous and Conservative 2PL.
4.  Explain why Conservative 2PL avoids deadlocks.

------------------------------------------------------------------------

# Revision Notes

``` text
Growing
(Acquire)

↓

Lock Point

↓

Shrinking
(Release)
```

## Memory Trick

``` text
2PL

Grow

↓

Lock Point

↓

Shrink
```

## Key Points

-   2PL has two phases: Growing and Shrinking.
-   No locks are released during Growing.
-   No new locks are acquired during Shrinking.
-   Strict 2PL is widely used in commercial DBMSs.
-   Conservative 2PL prevents deadlocks.

------------------------------------------------------------------------

# Final Takeaway

Two-Phase Locking is the most influential lock-based concurrency control
protocol. By separating lock acquisition and lock release into distinct
phases, it guarantees conflict serializability and maintains database
consistency. Variants such as Strict and Conservative 2PL address
practical concerns like cascading rollbacks and deadlocks, making 2PL a
cornerstone of modern transaction processing.
