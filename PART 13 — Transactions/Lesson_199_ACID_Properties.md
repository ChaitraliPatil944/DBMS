# Lesson 199 --- ACID Properties

> **Part 13 --- Transactions**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What ACID properties are
-   Why ACID is important
-   Atomicity, Consistency, Isolation, and Durability
-   Real-world examples
-   ACID in banking systems
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

A transaction must keep the database correct even if:

-   The system crashes
-   Multiple users access data simultaneously
-   Power fails
-   Hardware fails

The four guarantees that make this possible are called **ACID
Properties**.

------------------------------------------------------------------------

# 2. What is ACID?

``` text
A → Atomicity
C → Consistency
I → Isolation
D → Durability
```

These properties ensure every transaction is reliable.

------------------------------------------------------------------------

# 3. Atomicity

**Definition**

Atomicity means **all operations of a transaction happen completely or
none happen at all**.

``` text
Transfer Money

Deduct ₹5000
      │
Add ₹5000

Both succeed
OR
Both fail
```

If one step fails:

``` sql
ROLLBACK;
```

------------------------------------------------------------------------

# 4. Consistency

Consistency ensures that a transaction moves the database from **one
valid state to another valid state**.

Example:

Before Transfer

``` text
A = 10000
B = 5000

Total = 15000
```

After Transfer

``` text
A = 5000
B = 10000

Total = 15000
```

Business rules remain valid.

------------------------------------------------------------------------

# 5. Isolation

Isolation ensures that **multiple transactions do not interfere with
each other**.

``` text
Transaction A
       │
Runs Independently
       │
Transaction B
```

Users should not see incomplete work from other transactions.

------------------------------------------------------------------------

# 6. Durability

Durability means that **once a transaction is committed, its changes are
permanent**, even after a crash.

``` text
COMMIT
   │
Disk Storage
   │
System Crash
   │
Data Still Exists
```

------------------------------------------------------------------------

# 7. Complete ACID Flow

``` text
Begin Transaction
        │
Atomicity
        │
Consistency
        │
Isolation
        │
COMMIT
        │
Durability
```

------------------------------------------------------------------------

# 8. Real-World Example

## ATM Withdrawal

1.  Verify account
2.  Deduct balance
3.  Dispense cash
4.  Commit transaction

If cash cannot be dispensed, the deduction is rolled back.

------------------------------------------------------------------------

# 9. Advantages of ACID

-   Reliable transactions
-   No partial updates
-   Prevents inconsistent data
-   Safe concurrent access
-   Crash recovery support

------------------------------------------------------------------------

# 10. Common Mistakes

❌ Thinking COMMIT alone guarantees ACID.

❌ Confusing Atomicity with Durability.

❌ Ignoring Isolation in concurrent systems.

------------------------------------------------------------------------

# 11. Best Practices

-   Use transactions for related operations.
-   Commit only after successful execution.
-   Roll back failed transactions.
-   Keep transactions short.
-   Design with concurrency in mind.

------------------------------------------------------------------------

# 12. Interview Questions

### Beginner

1.  What does ACID stand for?
2.  What is Atomicity?

### Intermediate

1.  Atomicity vs Durability.
2.  Why is Isolation important?

### Advanced

1.  Explain all four ACID properties using a banking example.
2.  How does ACID improve database reliability?

------------------------------------------------------------------------

# 13. Practice Problems

1.  Explain ACID using an ATM example.
2.  Compare Atomicity and Consistency.
3.  Compare Isolation and Durability.
4.  Identify which ACID property is violated in different scenarios.

------------------------------------------------------------------------

# Revision Notes

``` text
A → Atomicity → All or Nothing

C → Consistency → Valid State

I → Isolation → Independent Transactions

D → Durability → Permanent Changes
```

## Memory Trick

``` text
ACID

A = All or Nothing

C = Correct Database

I = Independent Transactions

D = Data Stays Forever
```

## Key Points

-   ACID makes transactions reliable.
-   Atomicity prevents partial execution.
-   Consistency preserves rules.
-   Isolation handles concurrent users.
-   Durability protects committed data.

------------------------------------------------------------------------

# Final Takeaway

ACID properties are the foundation of reliable database systems. Every
successful transaction should execute completely, preserve database
correctness, remain isolated from other transactions, and survive system
failures after being committed. Understanding ACID is essential for
database design, enterprise applications, and technical interviews.
