# Lesson 224 --- Serializability Interview Questions

> **Part 15 --- Serializability**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will:

-   Revise serializability concepts
-   Prepare for DBMS interviews
-   Answer scenario-based questions confidently
-   Differentiate conflict and view serializability

------------------------------------------------------------------------

# 1. Beginner Questions

### Q1. What is serializability?

Serializability is the property that ensures a concurrent schedule
produces the same result as some serial schedule.

------------------------------------------------------------------------

### Q2. Why is serializability important?

-   Maintains consistency
-   Ensures correctness
-   Supports safe concurrency
-   Preserves database integrity

------------------------------------------------------------------------

### Q3. What is a schedule?

A schedule is the order in which operations from one or more
transactions are executed.

------------------------------------------------------------------------

### Q4. What is a serial schedule?

A schedule in which one transaction completes before the next begins.

------------------------------------------------------------------------

### Q5. What is a concurrent schedule?

A schedule where operations from multiple transactions are interleaved.

------------------------------------------------------------------------

# 2. Conflict Serializability

### Q6. What is Conflict Serializability?

A schedule is conflict serializable if it can be transformed into a
serial schedule by swapping only non-conflicting operations.

------------------------------------------------------------------------

### Q7. What are conflicting operations?

Operations from different transactions that access the same data item
and at least one is a write.

------------------------------------------------------------------------

### Q8. Which operation pairs conflict?

-   Read-Write
-   Write-Read
-   Write-Write

------------------------------------------------------------------------

### Q9. Which operation pair never conflicts?

Read-Read on the same data item.

------------------------------------------------------------------------

### Q10. What is conflict equivalence?

Two schedules are conflict equivalent if the order of every conflicting
operation pair is identical.

------------------------------------------------------------------------

# 3. View Serializability

### Q11. What is View Serializability?

A schedule is view serializable if it is view equivalent to a serial
schedule.

------------------------------------------------------------------------

### Q12. What are the three rules of view equivalence?

-   Initial Read Rule
-   Read-From Rule
-   Final Write Rule

------------------------------------------------------------------------

### Q13. Why is View Serializability more general?

It accepts some schedules that conflict serializability rejects.

------------------------------------------------------------------------

### Q14. Why is View Serializability difficult to test?

It requires checking read relationships and final writes, making it
computationally expensive.

------------------------------------------------------------------------

# 4. Precedence Graph

### Q15. What is a Precedence Graph?

A directed graph used to determine conflict serializability.

------------------------------------------------------------------------

### Q16. What do nodes represent?

Transactions.

------------------------------------------------------------------------

### Q17. What do edges represent?

Ordering dependencies caused by conflicting operations.

------------------------------------------------------------------------

### Q18. How do you determine serializability using a precedence graph?

-   No cycle → Conflict Serializable
-   Cycle present → Not Conflict Serializable

------------------------------------------------------------------------

# 5. Scenario-Based Questions

### Scenario 1

A schedule contains no cycles in its precedence graph.

**Answer:** The schedule is conflict serializable.

------------------------------------------------------------------------

### Scenario 2

A precedence graph contains a cycle.

**Answer:** The schedule is not conflict serializable.

------------------------------------------------------------------------

### Scenario 3

Two schedules preserve initial reads, read-from relationships, and final
writes.

**Answer:** They are view equivalent.

------------------------------------------------------------------------

### Scenario 4

Can every view serializable schedule be conflict serializable?

**Answer:** No. Every conflict serializable schedule is view
serializable, but not vice versa.

------------------------------------------------------------------------

# 6. Rapid Fire

1.  Define serializability.
2.  Serial vs concurrent schedule?
3.  What is conflict serializability?
4.  What is view serializability?
5.  What is conflict equivalence?
6.  What is view equivalence?
7.  What is a precedence graph?
8.  What does a cycle indicate?
9.  Which operations conflict?
10. Which operations never conflict?

------------------------------------------------------------------------

# 7. Interview Tips

-   Draw schedules neatly.
-   Mark conflicting operations first.
-   Use precedence graphs for conflict serializability.
-   Remember the three rules of view equivalence.
-   Explain with banking examples.

------------------------------------------------------------------------

# Revision Sheet

``` text
Serializability
      │
Schedules
      │
Conflict Serializability
      │
View Serializability
      │
Precedence Graph
      │
Cycle Detection
```

------------------------------------------------------------------------

# Final Takeaway

Serializability questions frequently appear in DBMS interviews because
they test your understanding of transaction correctness under concurrent
execution. Mastering schedules, conflict and view serializability, and
precedence graphs enables you to solve both theoretical and
scenario-based interview questions with confidence.
