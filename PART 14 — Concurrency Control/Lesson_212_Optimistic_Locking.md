# Lesson 212 --- Optimistic Locking

> **Part 14 --- Concurrency Control**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What Optimistic Locking is
-   Why it is used
-   Phases of Optimistic Concurrency Control (OCC)
-   Validation process
-   Advantages and limitations
-   Real-world examples
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Traditional locking assumes conflicts are common, so transactions
acquire locks before accessing data.

Optimistic Locking takes the opposite approach.

It assumes **conflicts are rare**, allowing transactions to execute
freely and checking for conflicts only before committing.

------------------------------------------------------------------------

# 2. What is Optimistic Locking?

**Optimistic Locking** is a concurrency control technique where
transactions execute **without locking data**. Before committing, the
DBMS validates that no conflicting updates have occurred.

``` text
Execute
   │
Validate
   │
Commit?
 │       │
Yes     No
 │       │
COMMIT ROLLBACK
```

------------------------------------------------------------------------

# 3. Why Use Optimistic Locking?

It works well when:

-   Read operations are much more frequent than writes.
-   Data conflicts are uncommon.
-   High concurrency is required.

Examples include web applications, reporting systems, and analytics.

------------------------------------------------------------------------

# 4. Phases of Optimistic Concurrency Control

### Read Phase

-   Read required data.
-   Make changes in local memory.
-   Do not update the database yet.

### Validation Phase

-   Check whether another transaction modified the same data.
-   Detect conflicts.

### Write Phase

-   If validation succeeds, write changes.
-   Otherwise, abort and retry.

``` text
Read
 │
Validate
 │
Write
```

------------------------------------------------------------------------

# 5. Validation Example

Suppose:

``` text
T1 reads Product Stock = 10

T2 reads Product Stock = 10

T2 commits first

T1 validates

↓

Conflict Found

↓

Rollback T1
```

Only one transaction succeeds.

------------------------------------------------------------------------

# 6. Version Numbers

Many databases implement optimistic locking using **version numbers**.

Example:

``` text
Product

Stock = 10

Version = 5
```

When updating:

``` text
UPDATE Product
SET Stock = 9,
    Version = 6
WHERE ProductID = 101
AND Version = 5;
```

If no row is updated, another transaction already modified the record.

------------------------------------------------------------------------

# 7. Optimistic vs Pessimistic Locking

  Optimistic                        Pessimistic
  --------------------------------- ----------------------------------
  Assumes conflicts are rare        Assumes conflicts are common
  No locks during execution         Locks acquired before access
  Validation before commit          Waiting may occur
  Better for read-heavy workloads   Better for write-heavy workloads

------------------------------------------------------------------------

# 8. Real-World Examples

-   Online shopping carts
-   REST APIs
-   Inventory management
-   Mobile applications
-   Banking dashboards

------------------------------------------------------------------------

# 9. Advantages

-   High concurrency
-   No deadlocks
-   Minimal locking overhead
-   Better performance for read-heavy systems

------------------------------------------------------------------------

# 10. Limitations

-   Transactions may restart frequently
-   Poor choice for heavy write workloads
-   Validation adds processing overhead

------------------------------------------------------------------------

# 11. Best Practices

-   Use version numbers or timestamps.
-   Retry aborted transactions carefully.
-   Prefer OCC for low-conflict systems.
-   Keep transactions short.

------------------------------------------------------------------------

# 12. Common Mistakes

❌ Using optimistic locking in highly conflicting workloads.

❌ Ignoring validation failures.

❌ Assuming optimistic locking never rolls back transactions.

------------------------------------------------------------------------

# 13. Interview Questions

### Beginner

1.  What is Optimistic Locking?
2.  Why is it called "optimistic"?

### Intermediate

1.  Explain the three OCC phases.
2.  Why are version numbers used?

### Advanced

1.  Compare Optimistic and Pessimistic Locking.
2.  When should OCC be preferred?

------------------------------------------------------------------------

# 14. Practice Problems

1.  Draw the OCC workflow.
2.  Explain validation with an example.
3.  Compare OCC and locking.
4.  Explain version-based concurrency control.

------------------------------------------------------------------------

# Revision Notes

``` text
Read
 │
Validate
 │
Conflict?
 │       │
No      Yes
 │        │
Commit Rollback
```

## Memory Trick

``` text
OPTIMISTIC

Read First

↓

Validate

↓

Commit
```

## Key Points

-   Optimistic Locking assumes conflicts are rare.
-   No locks are held during execution.
-   Validation occurs before commit.
-   Version numbers help detect conflicts.
-   Failed validation causes rollback and retry.

------------------------------------------------------------------------

# Final Takeaway

Optimistic Locking is ideal for applications where data conflicts are
infrequent and high concurrency is important. Instead of preventing
conflicts with locks, it detects them during validation and safely
retries failed transactions. This approach eliminates deadlocks and
provides excellent performance for read-heavy systems.
