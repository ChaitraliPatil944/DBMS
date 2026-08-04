# Lesson 229 --- Shadow Paging

> **Part 16 --- Recovery**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What Shadow Paging is
-   Why Shadow Paging was introduced
-   How Shadow Paging works
-   Shadow Page Table and Current Page Table
-   Commit and Recovery process
-   Advantages and limitations
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Traditional recovery techniques rely on transaction logs, UNDO, and
REDO.

An alternative approach is **Shadow Paging**, which avoids using
recovery logs by maintaining two versions of page tables.

------------------------------------------------------------------------

# 2. What is Shadow Paging?

**Shadow Paging** is a recovery technique in which the DBMS keeps two
page tables:

-   Shadow Page Table (original)
-   Current Page Table (modified)

The shadow copy never changes during a transaction.

``` text
Database
    │
Shadow Page Table
Current Page Table
```

------------------------------------------------------------------------

# 3. Why is Shadow Paging Needed?

It provides recovery without processing transaction logs.

Benefits include:

-   No UNDO
-   No REDO
-   Simple crash recovery
-   Fast rollback

------------------------------------------------------------------------

# 4. How Shadow Paging Works

Initially:

``` text
Shadow Table
     │
Page 1
Page 2
Page 3
```

When a transaction updates a page:

``` text
Old Page
     │
Copy
     │
Modify Copy
```

The original page remains unchanged.

------------------------------------------------------------------------

# 5. Shadow Page Table vs Current Page Table

  Shadow Page Table   Current Page Table
  ------------------- -----------------------------
  Original mapping    Updated mapping
  Read-only           Modified during transaction
  Used for recovery   Used during execution

------------------------------------------------------------------------

# 6. Commit Process

``` text
Start Transaction
        │
Copy Page Table
        │
Modify New Pages
        │
COMMIT
        │
Replace Shadow Pointer
```

After commit, the current page table becomes the new shadow page table.

------------------------------------------------------------------------

# 7. Crash Recovery

If a crash occurs before commit:

``` text
Crash
   │
Discard Current Pages
   │
Use Shadow Page Table
   │
Database Restored
```

Since the shadow pages were never modified, the database immediately
returns to the previous consistent state.

------------------------------------------------------------------------

# 8. Example

Suppose Page 5 stores:

``` text
Balance = ₹10,000
```

Transaction updates balance to:

``` text
₹8,000
```

Instead of changing Page 5:

``` text
Old Page 5

↓

Copy Page 5

↓

Modify Copy
```

If the transaction commits, the pointer switches to the new page.

If it crashes, the old page is still valid.

------------------------------------------------------------------------

# 9. Advantages

-   No UNDO required
-   No REDO required
-   Simple recovery
-   Fast rollback
-   Consistent database after crashes

------------------------------------------------------------------------

# 10. Limitations

-   Extra storage for copied pages
-   Page table copying overhead
-   Fragmentation over time
-   Not ideal for very large databases

------------------------------------------------------------------------

# 11. Shadow Paging vs Log-Based Recovery

  Shadow Paging      Log-Based Recovery
  ------------------ --------------------
  No logs            Uses logs
  No UNDO/REDO       Uses UNDO & REDO
  Copies pages       Records changes
  Simpler recovery   More scalable

------------------------------------------------------------------------

# 12. Best Practices

-   Use Shadow Paging for smaller systems.
-   Combine with periodic backups.
-   Reclaim obsolete pages regularly.
-   Monitor storage usage.

------------------------------------------------------------------------

# 13. Common Mistakes

❌ Assuming Shadow Paging uses transaction logs.

❌ Forgetting page copying before modification.

❌ Ignoring storage overhead.

------------------------------------------------------------------------

# 14. Interview Questions

### Beginner

1.  What is Shadow Paging?
2.  Why is it used?

### Intermediate

1.  Explain commit using Shadow Paging.
2.  Shadow Paging vs Log-Based Recovery.

### Advanced

1.  Why does Shadow Paging not require UNDO and REDO?
2.  Why is Shadow Paging uncommon in modern enterprise DBMSs?

------------------------------------------------------------------------

# 15. Practice Problems

1.  Draw the Shadow Paging workflow.
2.  Explain crash recovery using Shadow Paging.
3.  Compare Shadow Paging and Log-Based Recovery.
4.  List the advantages and disadvantages.

------------------------------------------------------------------------

# Revision Notes

``` text
Shadow Table
      │
Copy Pages
      │
Modify Copies
      │
Commit?
   │        │
Yes       No
 │          │
Switch    Use Shadow
Pointer   Table
```

## Memory Trick

``` text
SHADOW

Copy

↓

Modify

↓

Switch Pointer
```

## Key Points

-   Shadow Paging maintains two page tables.
-   Original pages remain unchanged until commit.
-   No UNDO or REDO is required.
-   Recovery simply restores the shadow page table.
-   Storage overhead is the main disadvantage.

------------------------------------------------------------------------

# Final Takeaway

Shadow Paging is a recovery technique that avoids transaction logs by
preserving an unchanged shadow copy of database pages while
modifications are made to separate copies. Recovery after a crash is
simple because the DBMS can immediately revert to the shadow page table.
Although elegant in theory, its storage and maintenance overhead make
log-based recovery more common in modern database systems.
