# Lesson 216 --- Concurrency Control Interview Questions

> **Part 14 --- Concurrency Control**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will:

-   Revise all concurrency control concepts
-   Prepare for DBMS interviews
-   Answer scenario-based questions confidently
-   Differentiate concurrency control techniques

------------------------------------------------------------------------

# 1. Beginner Questions

### Q1. What is concurrency control?

Concurrency control is the process of managing multiple transactions
executing simultaneously while maintaining database consistency.

------------------------------------------------------------------------

### Q2. Why is concurrency control required?

-   Prevent data inconsistency
-   Maintain ACID isolation
-   Avoid conflicting updates
-   Improve multi-user performance

------------------------------------------------------------------------

### Q3. Name common concurrency problems.

-   Lost Update
-   Dirty Read
-   Non-Repeatable Read
-   Phantom Read

------------------------------------------------------------------------

### Q4. What is locking?

Locking is a technique that controls concurrent access by requiring
transactions to acquire locks before reading or writing data.

------------------------------------------------------------------------

### Q5. What are Shared and Exclusive locks?

-   Shared Lock (S-Lock): Allows multiple readers.
-   Exclusive Lock (X-Lock): Allows one writer and blocks conflicting
    access.

------------------------------------------------------------------------

# 2. Deadlock & Starvation

### Q6. What is a deadlock?

A deadlock occurs when two or more transactions wait indefinitely for
each other's resources.

------------------------------------------------------------------------

### Q7. What are the four necessary conditions for deadlock?

-   Mutual Exclusion
-   Hold and Wait
-   No Preemption
-   Circular Wait

------------------------------------------------------------------------

### Q8. What is starvation?

Starvation is indefinite waiting caused by unfair scheduling or repeated
priority given to other transactions.

------------------------------------------------------------------------

### Q9. Deadlock vs Starvation?

  Deadlock                         Starvation
  -------------------------------- ------------------------------------
  Circular waiting                 No circular waiting required
  Multiple blocked transactions    One transaction waits indefinitely
  Solved by detection/prevention   Solved using fairness and aging

------------------------------------------------------------------------

# 3. Timestamp Protocol

### Q10. What is Timestamp Ordering?

Transactions execute according to assigned timestamps.

------------------------------------------------------------------------

### Q11. What are RTS and WTS?

-   RTS: Read Timestamp
-   WTS: Write Timestamp

------------------------------------------------------------------------

### Q12. Why does the Timestamp Protocol avoid deadlocks?

Transactions never wait for locks. They either execute or abort based on
timestamp rules.

------------------------------------------------------------------------

# 4. Locking Techniques

### Q13. What is Optimistic Locking?

Transactions execute without locks and validate for conflicts before
committing.

------------------------------------------------------------------------

### Q14. What is Pessimistic Locking?

Transactions acquire locks before accessing data to prevent conflicts.

------------------------------------------------------------------------

### Q15. When should Optimistic Locking be used?

When conflicts are rare and read operations dominate.

------------------------------------------------------------------------

### Q16. When should Pessimistic Locking be used?

When conflicts are frequent and strong consistency is required.

------------------------------------------------------------------------

# 5. Two-Phase Locking (2PL)

### Q17. What is Two-Phase Locking?

A locking protocol with two phases: Growing and Shrinking.

------------------------------------------------------------------------

### Q18. What is the Lock Point?

The moment a transaction acquires its final lock.

------------------------------------------------------------------------

### Q19. Name the types of 2PL.

-   Basic 2PL
-   Strict 2PL
-   Rigorous 2PL
-   Conservative (Static) 2PL

------------------------------------------------------------------------

### Q20. Which type of 2PL prevents deadlocks?

Conservative (Static) 2PL.

------------------------------------------------------------------------

# 6. MVCC

### Q21. What is MVCC?

A concurrency control technique that maintains multiple versions of data
for consistent reads.

------------------------------------------------------------------------

### Q22. What is Snapshot Isolation?

Each transaction reads a consistent snapshot taken when it begins.

------------------------------------------------------------------------

### Q23. Why is MVCC popular?

It improves read performance and reduces reader-writer blocking.

------------------------------------------------------------------------

# 7. Scenario-Based Questions

### Scenario 1

Two users update the same row simultaneously.

**Answer:** Use locking, 2PL, or MVCC depending on the database
implementation.

------------------------------------------------------------------------

### Scenario 2

Transactions wait forever for each other.

**Answer:** Deadlock.

------------------------------------------------------------------------

### Scenario 3

A transaction waits indefinitely while others continue.

**Answer:** Starvation.

------------------------------------------------------------------------

### Scenario 4

A database requires maximum read concurrency.

**Answer:** MVCC is generally preferred.

------------------------------------------------------------------------

### Scenario 5

A banking system performs frequent updates.

**Answer:** Pessimistic Locking or Strict 2PL is often appropriate.

------------------------------------------------------------------------

# 8. Rapid Fire

1.  What is concurrency control?
2.  Define locking.
3.  S-Lock vs X-Lock.
4.  What is deadlock?
5.  What is starvation?
6.  What is aging?
7.  What is RTS?
8.  What is WTS?
9.  What is 2PL?
10. What is MVCC?

------------------------------------------------------------------------

# 9. Interview Tips

-   Use banking and reservation examples.
-   Draw locking and 2PL diagrams.
-   Clearly differentiate deadlock and starvation.
-   Compare optimistic and pessimistic locking.
-   Explain MVCC with snapshot isolation.

------------------------------------------------------------------------

# Revision Sheet

``` text
Concurrency Control
        │
Locking
        │
Deadlock
        │
Starvation
        │
Timestamp Protocol
        │
Optimistic Locking
        │
Pessimistic Locking
        │
2PL
        │
MVCC
```

------------------------------------------------------------------------

# Final Takeaway

Concurrency control interview questions focus on maintaining consistency
while maximizing parallel execution. A strong understanding of locking,
deadlocks, starvation, timestamp ordering, 2PL, optimistic and
pessimistic locking, and MVCC prepares you for university exams,
placement tests, and technical interviews.
