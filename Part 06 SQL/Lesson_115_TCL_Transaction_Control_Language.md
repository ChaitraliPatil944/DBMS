# Lesson 115 --- TCL (Transaction Control Language)

> **Part 06 --- Structured Query Language (SQL)**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What a transaction is
-   What TCL is
-   Why transactions are important
-   COMMIT
-   ROLLBACK
-   SAVEPOINT
-   Transaction life cycle
-   TCL vs DML
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Imagine transferring ₹10,000 from Account A to Account B.

The process involves:

1.  Deduct ₹10,000 from Account A.
2.  Add ₹10,000 to Account B.

If the system crashes after Step 1 but before Step 2, money disappears.

Transactions prevent this problem.

------------------------------------------------------------------------

# 2. What is a Transaction?

A **transaction** is a sequence of one or more SQL operations treated as
a **single logical unit of work**.

``` text
Transaction
    │
Multiple SQL Statements
    │
Success or Failure Together
```

Either every operation succeeds, or none of them do.

------------------------------------------------------------------------

# 3. What is TCL?

**TCL (Transaction Control Language)** manages transactions.

Major TCL commands:

``` text
TCL
│
├── COMMIT
├── ROLLBACK
└── SAVEPOINT
```

These commands ensure data remains consistent.

------------------------------------------------------------------------

# 4. Why Do We Need TCL?

Without TCL:

``` text
Debit ✔

Credit ✘

↓

Incorrect Balance
```

With TCL:

``` text
Debit ✔
Credit ✘

↓

ROLLBACK

↓

Original Balance Restored
```

------------------------------------------------------------------------

# 5. COMMIT

`COMMIT` permanently saves all changes made during the current
transaction.

``` sql
UPDATE Account
SET Balance = Balance - 1000
WHERE AccountID = 1;

COMMIT;
```

After `COMMIT`, the changes become permanent.

------------------------------------------------------------------------

# 6. ROLLBACK

`ROLLBACK` cancels changes made since the last commit.

``` sql
UPDATE Account
SET Balance = Balance - 1000
WHERE AccountID = 1;

ROLLBACK;
```

The database returns to its previous state.

------------------------------------------------------------------------

# 7. SAVEPOINT

A `SAVEPOINT` creates a checkpoint within a transaction.

``` sql
SAVEPOINT BeforeUpdate;

UPDATE Employee
SET Salary = Salary + 5000;

ROLLBACK TO BeforeUpdate;
```

Only changes made after the savepoint are undone.

------------------------------------------------------------------------

# 8. Transaction Life Cycle

``` text
BEGIN
  │
Execute SQL
  │
SAVEPOINT (Optional)
  │
More SQL
  │
 ┌───────────────┐
 │               │
COMMIT      ROLLBACK
 │               │
Permanent    Undo Changes
```

------------------------------------------------------------------------

# 9. TCL vs DML

  TCL                     DML
  ----------------------- ------------------
  Controls transactions   Manipulates data
  COMMIT                  INSERT
  ROLLBACK                UPDATE
  SAVEPOINT               DELETE
  Ensures consistency     Changes rows

------------------------------------------------------------------------

# 10. Real-World Banking Example

``` text
Account A = ₹50,000

↓

Debit ₹10,000

↓

Credit ₹10,000

↓

COMMIT
```

If the credit fails:

``` text
Debit

↓

ROLLBACK

↓

Balance Restored
```

------------------------------------------------------------------------

# 11. Best Practices

-   Commit only after successful validation.
-   Use transactions for related operations.
-   Create savepoints in long transactions.
-   Avoid leaving transactions open for too long.

------------------------------------------------------------------------

# 12. Common Mistakes

❌ Forgetting to commit.

❌ Committing before verifying all operations.

❌ Assuming every SQL statement automatically commits.

❌ Using rollback after a committed transaction.

------------------------------------------------------------------------

# 13. Interview Questions

### Beginner

1.  What is a transaction?
2.  What is TCL?
3.  What does COMMIT do?

### Intermediate

1.  COMMIT vs ROLLBACK?
2.  What is SAVEPOINT?
3.  Why are transactions important?

### Advanced

1.  Explain the transaction life cycle.
2.  Why is TCL essential in banking systems?

------------------------------------------------------------------------

# 14. Practice Problems

1.  Write a transaction that updates two accounts and commits.
2.  Demonstrate ROLLBACK after an incorrect update.
3.  Use SAVEPOINT in a salary update transaction.
4.  Compare TCL and DML.
5.  Explain why transactions improve consistency.

------------------------------------------------------------------------

# Revision Notes

``` text
Transaction
   │
Execute SQL
   │
SAVEPOINT
   │
COMMIT
or
ROLLBACK
```

## Memory Trick

``` text
TCL

=

Take Control Logically

COMMIT = Save

ROLLBACK = Undo

SAVEPOINT = Checkpoint
```

## Key Points

-   A transaction is a logical unit of work.
-   TCL manages transactions.
-   COMMIT permanently saves changes.
-   ROLLBACK undoes uncommitted changes.
-   SAVEPOINT allows partial rollback.
-   Transactions improve data consistency and reliability.

------------------------------------------------------------------------

# Final Takeaway

Transaction Control Language ensures that databases remain accurate even
when unexpected failures occur. Every banking transfer, online payment,
ticket booking, and inventory update relies on transactions to keep data
consistent. Understanding `COMMIT`, `ROLLBACK`, and `SAVEPOINT` is
essential because reliable systems are built not just on storing data,
but on protecting it when things inevitably go wrong.
