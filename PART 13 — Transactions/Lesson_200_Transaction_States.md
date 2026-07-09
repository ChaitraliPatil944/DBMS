# Lesson 200 --- Transaction States

> **Part 13 --- Transactions**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What transaction states are
-   Why transaction states are important
-   Every state in a transaction lifecycle
-   State transitions
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

A transaction does not jump directly from **BEGIN** to **COMMIT**.

It passes through several stages before it either succeeds or fails.

These stages are called **Transaction States**.

------------------------------------------------------------------------

# 2. Why Do We Need Transaction States?

Transaction states help the DBMS:

-   Track transaction progress
-   Detect failures
-   Recover from crashes
-   Maintain database consistency

------------------------------------------------------------------------

# 3. Transaction Lifecycle

``` text
Start
  │
Active
  │
Partially Committed
  │
Committed
  │
Terminated
```

If an error occurs:

``` text
Active
  │
Failed
  │
Aborted
  │
Terminated
```

------------------------------------------------------------------------

# 4. Active State

A transaction enters the **Active** state immediately after it begins.

During this state:

-   SQL statements execute
-   Data is read or modified
-   Resources are allocated

Example:

``` sql
BEGIN;

UPDATE Account
SET Balance = Balance - 5000
WHERE AccountID = 101;
```

------------------------------------------------------------------------

# 5. Partially Committed State

The final SQL statement has executed successfully, but the transaction
has **not yet been permanently saved**.

``` text
SQL Finished
      │
Waiting for COMMIT
```

A crash at this point can still cause rollback.

------------------------------------------------------------------------

# 6. Committed State

The DBMS successfully executes:

``` sql
COMMIT;
```

Changes become permanent.

Even a system crash cannot undo them.

------------------------------------------------------------------------

# 7. Failed State

A transaction enters the **Failed** state when:

-   SQL execution fails
-   Constraint violation occurs
-   Deadlock is detected
-   System crash happens

No further execution continues.

------------------------------------------------------------------------

# 8. Aborted State

The DBMS performs:

``` sql
ROLLBACK;
```

Effects:

-   Undo all changes
-   Restore previous database state
-   Release resources

------------------------------------------------------------------------

# 9. Terminated State

After COMMIT or ROLLBACK:

-   Transaction finishes
-   Memory is released
-   Locks are released
-   Transaction disappears from execution

------------------------------------------------------------------------

# 10. Complete State Diagram

``` text
                Start
                  │
                  ▼
              Active
              /    \
             /      \
            ▼        ▼
Partially Committed  Failed
          │            │
          ▼            ▼
     Committed      Aborted
          │            │
          └──────┬─────┘
                 ▼
            Terminated
```

------------------------------------------------------------------------

# 11. Real-World Example

ATM Withdrawal

``` text
Insert Card
      │
Verify PIN
      │
Deduct Balance
      │
Dispense Cash
      │
COMMIT
      │
Finished
```

If cash dispensing fails:

``` text
Failed
   │
ROLLBACK
   │
Aborted
```

------------------------------------------------------------------------

# 12. Best Practices

-   Keep transactions short.
-   Handle failures gracefully.
-   Always release locks.
-   Roll back failed transactions promptly.

------------------------------------------------------------------------

# 13. Common Mistakes

❌ Confusing Partially Committed with Committed.

❌ Assuming Failed transactions automatically save data.

❌ Forgetting that Aborted transactions restore the previous state.

------------------------------------------------------------------------

# 14. Interview Questions

### Beginner

1.  What are transaction states?
2.  List all transaction states.

### Intermediate

1.  Difference between Failed and Aborted?
2.  Difference between Partially Committed and Committed?

### Advanced

1.  Draw the transaction state diagram.
2.  Explain the complete transaction lifecycle.

------------------------------------------------------------------------

# 15. Practice Problems

1.  Draw the transaction state diagram.
2.  Explain each state with an example.
3.  Compare Failed and Aborted states.
4.  Explain why Partially Committed is necessary.

------------------------------------------------------------------------

# Revision Notes

``` text
Start
 │
Active
 │
Partially Committed
 │
Committed
 │
Terminated

Failure Path

Active
 │
Failed
 │
Aborted
 │
Terminated
```

## Memory Trick

``` text
A

Active

↓

Partial

↓

Commit

↓

Terminate

OR

Fail

↓

Abort

↓

Terminate
```

## Key Points

-   Every transaction begins in the Active state.
-   Partially Committed means execution is complete but not yet
    permanent.
-   Committed makes changes permanent.
-   Failed indicates an error.
-   Aborted restores the previous state.
-   Every transaction ends in the Terminated state.

------------------------------------------------------------------------

# Final Takeaway

Transaction states describe the complete lifecycle of a database
transaction, from execution to successful completion or failure.
Understanding these states helps explain how database systems maintain
consistency, recover from errors, and guarantee reliable transaction
processing. They are a fundamental topic in DBMS exams and interviews.
