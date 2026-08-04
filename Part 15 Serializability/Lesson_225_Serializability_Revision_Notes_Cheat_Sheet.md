# Lesson 225 --- Serializability Revision Notes & Cheat Sheet

> **Part 15 --- Serializability**

------------------------------------------------------------------------

# Quick Definition

**Serializability** ensures that the result of executing concurrent
transactions is the same as executing them one after another in some
serial order.

``` text
Concurrent Schedule
        │
Equivalent to Serial?
        │
Yes
        │
Serializable
```

------------------------------------------------------------------------

# Why Serializability?

-   Ensures correctness
-   Maintains consistency
-   Supports safe concurrency
-   Preserves ACID Isolation

------------------------------------------------------------------------

# Schedule Types

  Schedule     Description
  ------------ -------------------------------------------------------
  Serial       One transaction finishes before the next starts
  Concurrent   Operations from multiple transactions are interleaved

------------------------------------------------------------------------

# Conflict Serializability

A schedule is **conflict serializable** if it can be converted into a
serial schedule by swapping only **non-conflicting operations**.

## Conflicting Operations

  Operation Pair    Conflict?
  ---------------- -----------
  Read - Read         ❌ No
  Read - Write       ✅ Yes
  Write - Read       ✅ Yes
  Write - Write      ✅ Yes

``` text
Different Transactions
        │
Same Data Item
        │
One Operation is WRITE
        │
Conflict
```

------------------------------------------------------------------------

# Conflict Equivalence

Two schedules are conflict equivalent if the order of every conflicting
operation is identical.

------------------------------------------------------------------------

# View Serializability

A schedule is **view serializable** if it is view equivalent to a serial
schedule.

## Three Rules

1.  Initial Read Rule
2.  Read-From Rule
3.  Final Write Rule

``` text
Initial Read
      │
Read-From
      │
Final Write
      │
View Serializable
```

------------------------------------------------------------------------

# Conflict vs View Serializability

  Conflict Serializability   View Serializability
  -------------------------- ------------------------
  Based on conflicts         Based on database view
  Easier to test             Harder to test
  More restrictive           More general
  Uses precedence graph      No simple graph test

> Every **Conflict Serializable** schedule is **View Serializable**, but
> not every **View Serializable** schedule is **Conflict Serializable**.

------------------------------------------------------------------------

# Precedence (Serialization) Graph

## Components

-   **Nodes** → Transactions
-   **Edges** → Conflicting dependencies

``` text
Schedule
    │
Find Conflicts
    │
Draw Graph
    │
Cycle?
```

### Decision Rule

``` text
Cycle Present?
      │
 ┌────┴────┐
 │         │
Yes        No
 │          │
Not      Conflict
Serializable Serializable
```

------------------------------------------------------------------------

# Steps to Construct a Precedence Graph

1.  Identify all transactions.
2.  Create one node for each transaction.
3.  Find conflicting operations.
4.  Draw directed edges.
5.  Check for cycles.

------------------------------------------------------------------------

# Comparison Table

  Concept                    Purpose
  -------------------------- ------------------------------------
  Serial Schedule            Baseline correct execution
  Concurrent Schedule        Improves performance
  Conflict Serializability   Checks correctness using conflicts
  View Serializability       Checks logical equivalence
  Precedence Graph           Detects conflict serializability

------------------------------------------------------------------------

# Common Interview Questions

1.  What is serializability?
2.  Serial vs Concurrent Schedule?
3.  What is Conflict Serializability?
4.  What are conflicting operations?
5.  What is View Serializability?
6.  Explain the three rules of view equivalence.
7.  What is a precedence graph?
8.  What does a cycle indicate?
9.  Conflict vs View Serializability?
10. Why are precedence graphs important?

------------------------------------------------------------------------

# Last-Minute Checklist

``` text
✓ Serializability

✓ Schedule

✓ Serial Schedule

✓ Concurrent Schedule

✓ Conflict Rules

✓ Conflict Equivalence

✓ View Equivalence

✓ Initial Read

✓ Read-From

✓ Final Write

✓ Precedence Graph

✓ Cycle Detection
```

------------------------------------------------------------------------

# Memory Trick

``` text
Schedule

↓

Conflict

↓

View

↓

Graph

↓

Cycle?

↓

Serializable
```

------------------------------------------------------------------------

# Key Points

-   Serial schedules are always serializable.
-   Concurrent schedules must be tested.
-   Read-Read operations never conflict.
-   Conflict serializability is easier to verify.
-   View serializability is more general.
-   Acyclic precedence graph ⇒ Conflict Serializable.
-   Cyclic precedence graph ⇒ Not Conflict Serializable.

------------------------------------------------------------------------

# Final Takeaway

Serializability is the foundation of correct concurrent transaction
execution. Conflict Serializability provides a practical way to verify
correctness using conflicting operations and precedence graphs, while
View Serializability offers a more general theoretical model based on
equivalent database views. Together, these concepts ensure that
concurrent schedules preserve consistency without sacrificing
performance.
