# Lesson 209 --- Deadlock

> **Part 14 --- Concurrency Control**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What a deadlock is
-   Why deadlocks occur
-   Necessary conditions for deadlock
-   Deadlock detection, prevention, avoidance, and recovery
-   Wait-For Graph (WFG)
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Locking protects data consistency, but it introduces a new problem.

Sometimes two or more transactions wait forever for each other to
release locks.

This situation is called a **Deadlock**.

------------------------------------------------------------------------

# 2. What is a Deadlock?

A **deadlock** occurs when two or more transactions permanently wait for
resources held by one another.

``` text
T1 waits for T2

T2 waits for T1

↓

Deadlock
```

------------------------------------------------------------------------

# 3. Example

Suppose:

``` text
T1 locks Account A

T2 locks Account B

T1 requests Account B

T2 requests Account A

↓

Both Wait Forever
```

------------------------------------------------------------------------

# 4. Deadlock Conditions

All four conditions must exist simultaneously.

### Mutual Exclusion

Only one transaction can own a resource.

### Hold and Wait

A transaction holds one resource while requesting another.

### No Preemption

Resources cannot be forcibly taken away.

### Circular Wait

Transactions form a waiting cycle.

``` text
T1 → T2 → T3 → T1
```

------------------------------------------------------------------------

# 5. Wait-For Graph (WFG)

A Wait-For Graph represents transactions as nodes.

``` text
T1 ───► T2
▲        │
│        ▼
└────── T3
```

A cycle indicates a deadlock.

------------------------------------------------------------------------

# 6. Deadlock Handling Techniques

## Detection

-   Build a Wait-For Graph.
-   Detect cycles.
-   Abort one transaction.

------------------------------------------------------------------------

## Prevention

Break one of the four deadlock conditions.

Examples:

-   Request all locks together.
-   Allow resource preemption.

------------------------------------------------------------------------

## Avoidance

Grant locks only if the system remains in a safe state.

Example:

-   Banker's Algorithm (general operating systems concept)

------------------------------------------------------------------------

## Recovery

After detecting a deadlock:

-   Roll back one transaction.
-   Release its locks.
-   Allow other transactions to continue.

------------------------------------------------------------------------

# 7. Real-World Example

Two ATMs update the same pair of bank accounts in opposite order.

Without consistent locking order:

``` text
ATM 1 waits

ATM 2 waits

↓

Deadlock
```

------------------------------------------------------------------------

# 8. Advantages of Deadlock Handling

-   Improves system availability
-   Prevents infinite waiting
-   Restores normal execution
-   Maintains database consistency

------------------------------------------------------------------------

# 9. Limitations

-   Detection requires overhead
-   Recovery may roll back work
-   Prevention may reduce concurrency

------------------------------------------------------------------------

# 10. Best Practices

-   Acquire locks in a fixed order.
-   Keep transactions short.
-   Release locks quickly.
-   Detect deadlocks periodically.

------------------------------------------------------------------------

# 11. Common Mistakes

❌ Confusing deadlock with starvation.

❌ Holding locks unnecessarily.

❌ Ignoring circular wait.

------------------------------------------------------------------------

# 12. Interview Questions

### Beginner

1.  What is a deadlock?
2.  Why does a deadlock occur?

### Intermediate

1.  List the four deadlock conditions.
2.  What is a Wait-For Graph?

### Advanced

1.  Compare detection, prevention, avoidance, and recovery.
2.  How does a DBMS recover from a deadlock?

------------------------------------------------------------------------

# 13. Practice Problems

1.  Draw a Wait-For Graph.
2.  Explain the four deadlock conditions.
3.  Compare prevention and avoidance.
4.  Explain deadlock recovery.

------------------------------------------------------------------------

# Revision Notes

``` text
Lock
 │
Wait
 │
Circular Wait
 │
Deadlock
 │
Detect
 │
Recover
```

## Memory Trick

``` text
DEADLOCK

Mutual Exclusion

Hold & Wait

No Preemption

Circular Wait
```

## Key Points

-   Deadlock is permanent waiting among transactions.
-   All four conditions must exist.
-   Wait-For Graph detects cycles.
-   Recovery usually aborts one transaction.
-   Fixed lock ordering helps prevent deadlocks.

------------------------------------------------------------------------

# Final Takeaway

Deadlocks are an unavoidable possibility in lock-based concurrency
control, but modern DBMSs include mechanisms to detect, prevent, avoid,
or recover from them. Understanding deadlocks and their solutions is
essential for designing reliable multi-user database systems and is a
favorite topic in DBMS interviews.
