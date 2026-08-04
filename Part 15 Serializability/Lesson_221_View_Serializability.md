# Lesson 221 --- View Serializability

> **Part 15 --- Serializability**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What View Serializability is
-   View equivalence
-   Read-from relationship
-   Final write rule
-   Difference between Conflict and View Serializability
-   Advantages and limitations
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Conflict Serializability rejects some schedules that are actually
correct.

To accept more valid schedules, DBMS theory introduces **View
Serializability**.

It checks whether two schedules produce the same logical view of the
database.

------------------------------------------------------------------------

# 2. What is View Serializability?

A schedule is **View Serializable** if it is **view equivalent** to a
serial schedule.

``` text
Concurrent Schedule
        │
View Equivalent?
        │
      Yes
        │
View Serializable
```

------------------------------------------------------------------------

# 3. What is View Equivalence?

Two schedules are **view equivalent** if all three conditions hold:

1.  Initial Read Rule
2.  Read-From Rule
3.  Final Write Rule

------------------------------------------------------------------------

# 4. Initial Read Rule

If a transaction reads the **initial value** of a data item in one
schedule, it must also read the initial value in the other schedule.

``` text
Initial Value of A

↓

T1 Reads A
```

------------------------------------------------------------------------

# 5. Read-From Rule

If transaction **T2** reads a value written by **T1** in one schedule,
it must read the value written by **T1** in the other schedule.

``` text
T1 : Write(A)

↓

T2 : Read(A)
```

The read relationship must remain unchanged.

------------------------------------------------------------------------

# 6. Final Write Rule

The transaction performing the **last write** on a data item must be the
same in both schedules.

``` text
T1 : Write(A)

T2 : Write(A)

↓

Final Writer = T2
```

------------------------------------------------------------------------

# 7. Example

Schedule:

``` text
T1 : Read(A)

T2 : Read(A)

T1 : Write(A)

T2 : Write(A)
```

To check view serializability:

-   Who reads the initial value?
-   Who reads whose write?
-   Who performs the final write?

If all match a serial schedule, it is view serializable.

------------------------------------------------------------------------

# 8. Conflict vs View Serializability

  Conflict Serializability          View Serializability
  --------------------------------- ------------------------
  Based on conflicting operations   Based on database view
  Easier to test                    Harder to test
  More restrictive                  More general
  Uses precedence graph             No simple graph test

Every conflict serializable schedule is view serializable, but not every
view serializable schedule is conflict serializable.

------------------------------------------------------------------------

# 9. Why is View Serializability Important?

It accepts some schedules rejected by conflict serializability,
increasing possible concurrency while preserving correctness.

------------------------------------------------------------------------

# 10. Real-World Example

Two transactions update customer records.

Even if the operation order differs, the schedule is acceptable if the
same transaction performs the final update and every transaction reads
the same values.

------------------------------------------------------------------------

# 11. Advantages

-   More flexible
-   Accepts more valid schedules
-   Preserves logical correctness

------------------------------------------------------------------------

# 12. Limitations

-   Difficult to test
-   Computationally expensive
-   Rarely checked directly in practical DBMSs

------------------------------------------------------------------------

# 13. Best Practices

-   Understand read-from relationships.
-   Track final writes carefully.
-   Use conflict serializability in practice when possible.

------------------------------------------------------------------------

# 14. Common Mistakes

❌ Confusing view equivalence with conflict equivalence.

❌ Ignoring the final writer.

❌ Forgetting initial reads.

------------------------------------------------------------------------

# 15. Interview Questions

### Beginner

1.  What is View Serializability?
2.  What is view equivalence?

### Intermediate

1.  Explain the three conditions of view equivalence.
2.  Conflict vs View Serializability.

### Advanced

1.  Why is View Serializability more general?
2.  Why is it difficult to test?

------------------------------------------------------------------------

# 16. Practice Problems

1.  Check whether two schedules are view equivalent.
2.  Identify the final writer.
3.  Identify read-from relationships.
4.  Compare conflict and view serializability.

------------------------------------------------------------------------

# Revision Notes

``` text
Concurrent Schedule
        │
Initial Read
        │
Read-From
        │
Final Write
        │
View Serializable
```

## Memory Trick

``` text
VIEW

Initial Read

↓

Read-From

↓

Final Write
```

## Key Points

-   View serializability is based on view equivalence.
-   Three rules: Initial Read, Read-From, Final Write.
-   It is more general than conflict serializability.
-   Every conflict serializable schedule is also view serializable.
-   Practical DBMSs usually prefer conflict serializability because it
    is easier to test.

------------------------------------------------------------------------

# Final Takeaway

View Serializability provides a broader definition of correct concurrent
execution by preserving the logical view of database operations instead
of only preserving conflicting operation order. Although it is more
powerful than conflict serializability, its complexity makes it less
practical for direct implementation in commercial database systems.
