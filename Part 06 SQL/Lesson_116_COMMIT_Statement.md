# Lesson 116 --- COMMIT Statement

> **Part 06 --- Structured Query Language (SQL)**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What `COMMIT` is
-   Why `COMMIT` is needed
-   How `COMMIT` works internally
-   Auto-commit vs manual commit
-   Transaction examples
-   Banking and e-commerce use cases
-   Best practices
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Imagine filling an online shopping cart.

Nothing is final until you click **Place Order**.

Similarly, SQL changes are often temporary until you execute:

``` sql
COMMIT;
```

`COMMIT` tells the DBMS to permanently save the transaction.

------------------------------------------------------------------------

# 2. What is COMMIT?

`COMMIT` is a **TCL (Transaction Control Language)** command that
permanently saves all changes made during the current transaction.

``` text
Transaction
     │
  COMMIT
     │
Changes Saved Permanently
```

Once committed, the changes become part of the database.

------------------------------------------------------------------------

# 3. Why Do We Need COMMIT?

During a transaction, changes can still be undone.

After `COMMIT`:

-   Changes become permanent.
-   Other users can reliably see the updated data (depending on the
    isolation level).
-   The transaction ends.

Without `COMMIT`, important work may never be saved.

------------------------------------------------------------------------

# 4. Basic Syntax

``` sql
COMMIT;
```

Usually used after DML statements.

------------------------------------------------------------------------

# 5. Example Transaction

``` sql
UPDATE Account
SET Balance = Balance - 1000
WHERE AccountID = 1;

UPDATE Account
SET Balance = Balance + 1000
WHERE AccountID = 2;

COMMIT;
```

Result:

``` text
Money Debited ✔
Money Credited ✔
Transaction Saved ✔
```

------------------------------------------------------------------------

# 6. How COMMIT Works Internally

``` text
BEGIN TRANSACTION
        │
Execute SQL
        │
Validate Changes
        │
Write to Transaction Log
        │
COMMIT
        │
Changes Become Permanent
```

After the commit, a rollback cannot undo those changes.

------------------------------------------------------------------------

# 7. Auto-Commit vs Manual Commit

  -----------------------------------------------------------------------
  Auto-Commit                      Manual Commit
  -------------------------------- --------------------------------------
  Each statement is committed      User explicitly commits
  automatically                    

  Simpler                          Greater control

  Common in many tools by default  Preferred for multi-step transactions
  -----------------------------------------------------------------------

Example:

``` text
INSERT

↓

Auto Commit

↓

Saved Immediately
```

Manual mode:

``` text
INSERT
UPDATE
DELETE
   │
COMMIT
```

------------------------------------------------------------------------

# 8. Real-World Example

Bank transfer:

``` text
Debit Account A
        │
Credit Account B
        │
Verification
        │
COMMIT
```

If verification fails before commit, a rollback can restore the previous
state.

------------------------------------------------------------------------

# 9. Best Practices

-   Commit only after all validations succeed.
-   Group related operations into one transaction.
-   Avoid unnecessary commits inside a logical transaction.
-   Test business logic before committing in production.

------------------------------------------------------------------------

# 10. Common Mistakes

❌ Committing too early.

❌ Forgetting to commit in manual transaction mode.

❌ Assuming committed changes can be rolled back.

❌ Treating auto-commit and manual commit as identical.

------------------------------------------------------------------------

# 11. Interview Questions

### Beginner

1.  What is `COMMIT`?
2.  Is `COMMIT` a DML or TCL command?
3.  What happens after a commit?

### Intermediate

1.  Auto-commit vs manual commit?
2.  Why should related operations be committed together?

### Advanced

1.  Why can't a committed transaction normally be rolled back?
2.  How does `COMMIT` contribute to database consistency?

------------------------------------------------------------------------

# 12. Practice Problems

1.  Write a transaction that transfers money and commits.
2.  Compare auto-commit and manual commit.
3.  Explain why committing too early can be risky.
4.  Describe the internal flow of a commit operation.

------------------------------------------------------------------------

# Revision Notes

``` text
BEGIN
  │
SQL Statements
  │
COMMIT
  │
Permanent Changes
```

## Memory Trick

``` text
COMMIT

=

Confirm

Operations

Make

Modifications

Irreversible

Today
```

## Key Points

-   `COMMIT` permanently saves a transaction.
-   It is a TCL command.
-   After commit, changes normally cannot be rolled back.
-   Manual commit provides better control than auto-commit.
-   Commit only after successful validation.

------------------------------------------------------------------------

# Final Takeaway

`COMMIT` marks the successful completion of a transaction by making its
changes permanent. It is one of the most important commands in SQL
because it separates temporary work from permanent database updates.
Understanding exactly when to commit is essential for building reliable
applications, since committing too soon can preserve mistakes, while
committing too late can leave important work unfinished.
