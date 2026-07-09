# Lesson 211 --- Timestamp Protocol

> **Part 14 --- Concurrency Control**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What the Timestamp Protocol is
-   Why timestamps are used
-   Timestamp Ordering Protocol (TOP)
-   Read Timestamp (RTS)
-   Write Timestamp (WTS)
-   Basic and Strict Timestamp Ordering
-   Advantages and limitations
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Locking forces transactions to wait.

Timestamp-based concurrency control avoids many waits by assigning every
transaction a unique timestamp and executing operations in that order.

------------------------------------------------------------------------

# 2. What is a Timestamp?

A **timestamp** is a unique number assigned to a transaction when it
begins.

``` text
T1 → TS = 10
T2 → TS = 20
T3 → TS = 30
```

A smaller timestamp means an older transaction.

------------------------------------------------------------------------

# 3. What is the Timestamp Protocol?

The **Timestamp Ordering Protocol (TOP)** ensures that all conflicting
operations execute according to timestamp order.

``` text
Start Transaction
        │
Assign Timestamp
        │
Check Read/Write Rules
        │
Execute or Abort
```

------------------------------------------------------------------------

# 4. Why Use Timestamp Ordering?

Without timestamp ordering:

-   Conflicting updates
-   Dirty reads
-   Inconsistent execution

With timestamp ordering:

-   Serializable execution
-   No deadlocks
-   Predictable ordering

------------------------------------------------------------------------

# 5. Read Timestamp (RTS)

Every data item stores:

``` text
RTS(X)

Highest timestamp of any transaction
that successfully read X
```

------------------------------------------------------------------------

# 6. Write Timestamp (WTS)

Every data item also stores:

``` text
WTS(X)

Highest timestamp of any transaction
that successfully wrote X
```

------------------------------------------------------------------------

# 7. Read Rule

Transaction **Ti** can read item **X** only if:

``` text
TS(Ti) ≥ WTS(X)
```

Otherwise, the read is rejected and the transaction is rolled back.

------------------------------------------------------------------------

# 8. Write Rule

Transaction **Ti** can write item **X** only if:

``` text
TS(Ti) ≥ RTS(X)

AND

TS(Ti) ≥ WTS(X)
```

Otherwise, the write is rejected.

------------------------------------------------------------------------

# 9. Example

``` text
T1 (TS=5)

T2 (TS=10)

X.WTS = 10

↓

T1 tries to write X

↓

Rejected

↓

Rollback T1
```

The older transaction cannot overwrite newer data.

------------------------------------------------------------------------

# 10. Types of Timestamp Protocols

## Basic Timestamp Ordering

-   Executes strictly according to timestamps.
-   May cause cascading rollbacks.

## Strict Timestamp Ordering

-   Delays access to uncommitted writes.
-   Prevents cascading rollbacks.
-   More reliable.

------------------------------------------------------------------------

# 11. Comparison with Locking

  Locking                    Timestamp Protocol
  -------------------------- -----------------------------------------
  Uses locks                 Uses timestamps
  Deadlocks possible         Deadlocks impossible
  Transactions may wait      Transactions abort if order is violated
  Lock management required   Timestamp management required

------------------------------------------------------------------------

# 12. Advantages

-   Deadlock-free
-   Serializable execution
-   Simple ordering
-   Suitable for high concurrency

------------------------------------------------------------------------

# 13. Limitations

-   More transaction rollbacks
-   Possible starvation
-   Timestamp storage overhead

------------------------------------------------------------------------

# 14. Best Practices

-   Use strict timestamp ordering in critical systems.
-   Combine with recovery mechanisms.
-   Keep transactions short.
-   Monitor rollback frequency.

------------------------------------------------------------------------

# 15. Common Mistakes

❌ Confusing timestamps with system clocks.

❌ Assuming timestamp ordering never aborts transactions.

❌ Ignoring RTS and WTS rules.

------------------------------------------------------------------------

# 16. Interview Questions

### Beginner

1.  What is a timestamp?
2.  What is the Timestamp Protocol?

### Intermediate

1.  Explain RTS and WTS.
2.  Why does timestamp ordering prevent deadlocks?

### Advanced

1.  Basic vs Strict Timestamp Ordering.
2.  Compare locking and timestamp protocols.

------------------------------------------------------------------------

# 17. Practice Problems

1.  Assign timestamps to transactions.
2.  Check whether read/write operations are allowed.
3.  Compare locking and timestamp ordering.
4.  Explain why rollbacks occur.

------------------------------------------------------------------------

# Revision Notes

``` text
Transaction
     │
Timestamp
     │
Read / Write Rules
     │
Allowed?

Yes → Execute

No → Abort
```

## Memory Trick

``` text
TIMESTAMP

Older First

↓

Follow Order

↓

No Deadlock
```

## Key Points

-   Every transaction receives a unique timestamp.
-   RTS records the latest successful read.
-   WTS records the latest successful write.
-   Conflicting operations violating timestamp order are aborted.
-   Timestamp ordering avoids deadlocks but may increase rollbacks.

------------------------------------------------------------------------

# Final Takeaway

The Timestamp Ordering Protocol provides concurrency control without
using locks. Instead of making transactions wait, it enforces a global
execution order based on timestamps. This eliminates deadlocks and
guarantees serializable execution, making it an important alternative to
lock-based concurrency control in modern database systems.
