# Lesson 210 --- Starvation

> **Part 14 --- Concurrency Control**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What starvation is
-   Why starvation occurs
-   Difference between starvation and deadlock
-   Causes of starvation
-   Prevention techniques
-   Aging algorithm
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Imagine waiting in a queue where new people are always allowed to go
before you.

You never reach the front.

The same problem can happen in databases.

This situation is called **Starvation**.

------------------------------------------------------------------------

# 2. What is Starvation?

**Starvation** (also called **Indefinite Blocking**) occurs when a
transaction waits for an extremely long time because other transactions
continuously receive priority.

``` text
T1 Waiting

↓

T2 Executes

↓

T3 Executes

↓

T4 Executes

↓

T1 Still Waiting
```

------------------------------------------------------------------------

# 3. Why Does Starvation Occur?

Common causes include:

-   Priority scheduling
-   Unfair lock allocation
-   Continuous arrival of high-priority transactions
-   Repeated deadlock victim selection

------------------------------------------------------------------------

# 4. Example

Suppose:

``` text
High Priority Transactions

T2
T3
T4
T5

↓

Execute First

↓

T1 Never Gets CPU/Lock
```

T1 is not deadlocked, but it never progresses.

------------------------------------------------------------------------

# 5. Starvation vs Deadlock

  -----------------------------------------------------------------------
  Starvation                             Deadlock
  -------------------------------------- --------------------------------
  One transaction waits indefinitely     Two or more transactions wait
                                         for each other

  No circular waiting required           Circular wait exists

  Other transactions continue            None of the involved
                                         transactions progress

  Solved using fairness                  Solved by
                                         detection/prevention/recovery
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# 6. Preventing Starvation

## Fair Scheduling

Serve requests roughly in arrival order.

## Aging

Gradually increase the priority of waiting transactions.

``` text
Waiting Time ↑

↓

Priority ↑

↓

Eventually Executes
```

## Balanced Lock Policies

Avoid giving the same transactions repeated preference.

------------------------------------------------------------------------

# 7. Aging Algorithm

The **Aging Algorithm** increases the priority of a transaction the
longer it waits.

``` text
T1 Priority = 1

Wait...

Priority = 2

Wait...

Priority = 3

↓

Runs
```

This guarantees every transaction eventually executes.

------------------------------------------------------------------------

# 8. Real-World Example

### Online Ticket Booking

Premium customers may receive higher priority.

If normal users are never served because premium requests keep arriving,
starvation occurs.

------------------------------------------------------------------------

# 9. Advantages of Starvation Prevention

-   Fair scheduling
-   Better user experience
-   Predictable execution
-   Higher system reliability

------------------------------------------------------------------------

# 10. Limitations

-   Slight scheduling overhead
-   Aging may delay newer high-priority work
-   Perfect fairness can reduce throughput

------------------------------------------------------------------------

# 11. Best Practices

-   Use aging with priority scheduling.
-   Avoid always selecting the same deadlock victim.
-   Monitor long-waiting transactions.
-   Balance fairness and performance.

------------------------------------------------------------------------

# 12. Common Mistakes

❌ Confusing starvation with deadlock.

❌ Assuming every waiting transaction is deadlocked.

❌ Ignoring unfair scheduling policies.

------------------------------------------------------------------------

# 13. Interview Questions

### Beginner

1.  What is starvation?
2.  Why does starvation occur?

### Intermediate

1.  Difference between starvation and deadlock.
2.  What is aging?

### Advanced

1.  How does aging prevent starvation?
2.  Can starvation occur without deadlock?

------------------------------------------------------------------------

# 14. Practice Problems

1.  Compare starvation and deadlock.
2.  Explain aging with an example.
3.  List starvation causes.
4.  Suggest techniques to prevent starvation.

------------------------------------------------------------------------

# Revision Notes

``` text
Long Wait
    │
Priority Increases
    │
Eventually Executes

↓

No Starvation
```

## Memory Trick

``` text
STARVATION

Wait Too Long

↓

Use Aging

↓

Execute
```

## Key Points

-   Starvation means indefinite waiting.
-   It differs from deadlock.
-   Aging is the most common prevention technique.
-   Fair scheduling reduces starvation.
-   Every transaction should eventually execute.

------------------------------------------------------------------------

# Final Takeaway

Starvation occurs when a transaction is repeatedly denied the resources
it needs because other transactions keep receiving priority. Unlike a
deadlock, the system continues to make progress, but one unlucky
transaction does not. Fair scheduling and aging algorithms ensure that
every transaction eventually gets a chance to execute, keeping the
database both efficient and fair.
