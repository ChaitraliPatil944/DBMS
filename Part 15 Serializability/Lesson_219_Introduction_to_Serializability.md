# Lesson 219 --- Introduction to Serializability

> **Part 15 --- Serializability**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What serializability is
-   Why serializability is needed
-   Serial vs Concurrent schedules
-   Serializability in DBMS
-   Types of serializability
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Modern databases execute many transactions at the same time.

Running transactions concurrently improves performance, but it can also
produce incorrect results if operations interfere with each other.

To guarantee correctness, the DBMS uses **Serializability**.

------------------------------------------------------------------------

# 2. What is Serializability?

**Serializability** is the property of a schedule that ensures the final
result of concurrent execution is the same as some serial execution of
those transactions.

In simple words:

> Concurrent execution should produce the same result as executing one
> transaction completely before the next.

------------------------------------------------------------------------

# 3. Why is Serializability Needed?

Without serializability:

-   Incorrect balances
-   Lost updates
-   Dirty reads
-   Data inconsistency
-   Unpredictable results

With serializability:

-   Correct execution
-   Data consistency
-   Safe concurrency
-   Reliable transactions

------------------------------------------------------------------------

# 4. What is a Schedule?

A **schedule** is the order in which operations from one or more
transactions are executed.

Example:

``` text
T1 : Read(A)
T1 : Write(A)
T2 : Read(B)
T2 : Write(B)
```

------------------------------------------------------------------------

# 5. Serial Schedule

A **Serial Schedule** executes one complete transaction before starting
another.

``` text
T1

Read(A)
Write(A)

↓

T2

Read(B)
Write(B)
```

Characteristics:

-   No overlap
-   No conflicts
-   Always correct
-   Lower performance

------------------------------------------------------------------------

# 6. Concurrent Schedule

A **Concurrent Schedule** interleaves operations from multiple
transactions.

``` text
Read(A)  T1

Read(B)  T2

Write(A) T1

Write(B) T2
```

Characteristics:

-   Higher throughput
-   Better resource utilization
-   May cause conflicts

------------------------------------------------------------------------

# 7. Serial vs Concurrent Schedule

  Serial                      Concurrent
  --------------------------- -------------------------------
  One transaction at a time   Multiple transactions overlap
  Simple                      Complex
  Lower performance           Higher performance
  Always serializable         Must be checked

------------------------------------------------------------------------

# 8. What Makes a Concurrent Schedule Correct?

A concurrent schedule is considered correct if it is **equivalent** to
some serial schedule.

``` text
Concurrent Schedule

↓

Equivalent?

↓

Yes

↓

Serializable
```

------------------------------------------------------------------------

# 9. Types of Serializability

There are two major types:

1.  Conflict Serializability
2.  View Serializability

These are covered in the next lessons.

------------------------------------------------------------------------

# 10. Real-World Example

### Banking

Two customers transfer money simultaneously.

Even if both transactions execute together, the final account balances
should match the result of executing them one after another.

------------------------------------------------------------------------

# 11. Advantages

-   Ensures correctness
-   Preserves consistency
-   Supports safe concurrency
-   Foundation of transaction scheduling

------------------------------------------------------------------------

# 12. Limitations

-   Checking serializability adds overhead.
-   Some concurrent schedules must be rejected.
-   Advanced algorithms are required.

------------------------------------------------------------------------

# 13. Best Practices

-   Use proven concurrency control protocols.
-   Keep transactions short.
-   Avoid unnecessary conflicts.
-   Verify schedule correctness.

------------------------------------------------------------------------

# 14. Common Mistakes

❌ Assuming every concurrent schedule is serializable.

❌ Confusing serial execution with serializability.

❌ Ignoring operation order.

------------------------------------------------------------------------

# 15. Interview Questions

### Beginner

1.  What is serializability?
2.  Why is serializability important?
3.  What is a schedule?

### Intermediate

1.  Serial vs Concurrent schedule.
2.  What makes a schedule serializable?

### Advanced

1.  Explain serial equivalence.
2.  Why is serializability essential in DBMS?

------------------------------------------------------------------------

# 16. Practice Problems

1.  Define serializability.
2.  Compare serial and concurrent schedules.
3.  Explain why serializability is required.
4.  Draw a serial and a concurrent schedule.

------------------------------------------------------------------------

# Revision Notes

``` text
Transactions
      │
Schedule
      │
Equivalent to Serial?
      │
Yes
      │
Serializable
```

## Memory Trick

``` text
SERIALIZABILITY

Concurrent

↓

Same Result

↓

As Serial
```

## Key Points

-   Serializability guarantees correct concurrent execution.
-   A schedule defines the order of operations.
-   Serial schedules are always correct.
-   Concurrent schedules must be tested for equivalence.
-   Conflict and View Serializability are the two main types.

------------------------------------------------------------------------

# Final Takeaway

Serializability is the gold standard for correctness in concurrent
transaction processing. It allows multiple transactions to execute
simultaneously while ensuring that the final outcome is identical to
some serial execution. Understanding serializability is essential for
mastering transaction scheduling, concurrency control, and database
consistency.
