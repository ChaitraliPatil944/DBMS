# Lesson 220 --- Conflict Serializability

> **Part 15 --- Serializability**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What Conflict Serializability is
-   Conflicting operations
-   Conflict equivalence
-   Conflict-serializable schedules
-   Swapping non-conflicting operations
-   Relationship with precedence graphs
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Not every concurrent schedule is correct.

The DBMS must determine whether a concurrent schedule behaves exactly
like some serial schedule.

The most widely used method is **Conflict Serializability**.

------------------------------------------------------------------------

# 2. What is Conflict Serializability?

A schedule is **Conflict Serializable** if it can be transformed into an
equivalent serial schedule by swapping only **non-conflicting**
operations.

``` text
Concurrent Schedule
        │
Swap Non-Conflicting Operations
        │
Serial Schedule
        │
Conflict Serializable
```

------------------------------------------------------------------------

# 3. What are Conflicting Operations?

Two operations conflict if they:

-   Belong to different transactions,
-   Access the same data item,
-   And at least one operation is a write.

Conflicts:

-   Read(X) ↔ Write(X)
-   Write(X) ↔ Read(X)
-   Write(X) ↔ Write(X)

Do **not** conflict:

-   Read(X) ↔ Read(X)
-   Operations on different data items.

------------------------------------------------------------------------

# 4. Conflict Equivalence

Two schedules are **conflict equivalent** if the order of every pair of
conflicting operations is the same in both schedules.

------------------------------------------------------------------------

# 5. Swapping Rule

Only **non-conflicting** operations may be interchanged.

Example:

``` text
T1: Read(A)

T2: Read(B)

↓

Swap Allowed
```

But:

``` text
T1: Write(A)

T2: Read(A)

↓

Swap NOT Allowed
```

------------------------------------------------------------------------

# 6. Example

Concurrent Schedule

``` text
T1 : Read(A)

T2 : Read(B)

T1 : Write(A)

T2 : Write(B)
```

Since operations access different items, they can be swapped to form a
serial schedule.

------------------------------------------------------------------------

# 7. When is a Schedule Conflict Serializable?

``` text
Concurrent Schedule
        │
Can Convert to Serial
Using Valid Swaps?
        │
      Yes
        │
Conflict Serializable
```

------------------------------------------------------------------------

# 8. Conflict Serializability vs Serial Schedule

  Serial Schedule   Conflict Serializable
  ----------------- ---------------------------
  Already serial    Concurrent but equivalent
  No overlap        Operations may interleave
  Always correct    Correct after valid swaps

------------------------------------------------------------------------

# 9. Relation with Precedence Graph

Instead of repeatedly swapping operations, DBMS builds a **Precedence
Graph**.

``` text
Schedule
   │
Build Graph
   │
Cycle?
 │      │
No     Yes
 │       │
Serializable  Not Serializable
```

This is covered in Lesson 222.

------------------------------------------------------------------------

# 10. Real-World Example

Two customers update different bank accounts simultaneously.

Since they work on different records, operations can be reordered
without changing the result.

------------------------------------------------------------------------

# 11. Advantages

-   Guarantees correctness
-   Easy to verify using graphs
-   Widely implemented
-   Foundation of concurrency control

------------------------------------------------------------------------

# 12. Limitations

-   More restrictive than View Serializability
-   Some valid schedules are rejected
-   Graph construction adds overhead

------------------------------------------------------------------------

# 13. Best Practices

-   Minimize conflicting operations.
-   Keep transactions short.
-   Access records consistently.
-   Use precedence graphs for verification.

------------------------------------------------------------------------

# 14. Common Mistakes

❌ Treating Read-Read as a conflict.

❌ Swapping conflicting operations.

❌ Confusing conflict equivalence with view equivalence.

------------------------------------------------------------------------

# 15. Interview Questions

### Beginner

1.  What is Conflict Serializability?
2.  What are conflicting operations?

### Intermediate

1.  What is conflict equivalence?
2.  Which operations can be swapped?

### Advanced

1.  Why is Conflict Serializability important?
2.  Why is it more restrictive than View Serializability?

------------------------------------------------------------------------

# 16. Practice Problems

1.  Identify conflicting operations.
2.  Check whether a schedule is conflict serializable.
3.  Convert a schedule into a serial schedule using valid swaps.
4.  Explain why some schedules cannot be converted.

------------------------------------------------------------------------

# Revision Notes

``` text
Concurrent Schedule
      │
Swap Non-Conflicting Operations
      │
Serial Schedule
      │
Conflict Serializable
```

## Memory Trick

``` text
CONFLICT

Different Transactions

↓

Same Data

↓

One Write

↓

Conflict
```

## Key Points

-   Conflicts require same data item and at least one write.
-   Only non-conflicting operations can be swapped.
-   Conflict equivalence preserves conflict order.
-   Conflict serializable schedules behave like serial schedules.
-   Precedence graphs efficiently test conflict serializability.

------------------------------------------------------------------------

# Final Takeaway

Conflict Serializability is the most practical method for verifying
whether concurrent transaction execution is correct. By preserving the
order of conflicting operations and allowing only safe swaps, it
guarantees that a concurrent schedule produces the same result as a
serial schedule. This concept forms the basis for precedence graphs and
many concurrency control algorithms used in modern DBMSs.
