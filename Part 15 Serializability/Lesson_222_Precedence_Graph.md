# Lesson 222 --- Precedence Graph (Serialization Graph)

> **Part 15 --- Serializability**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What a Precedence Graph is
-   Why it is used
-   How to construct a graph
-   Detecting Conflict Serializability
-   Cyclic vs Acyclic graphs
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Checking conflict serializability by repeatedly swapping operations is
difficult.

A simpler method is to construct a **Precedence Graph**, also called a
**Serialization Graph**.

------------------------------------------------------------------------

# 2. What is a Precedence Graph?

A **Precedence Graph** is a directed graph that represents dependencies
between transactions.

``` text
Transactions
      │
Conflicting Operations
      │
Directed Graph
      │
Serializable?
```

Each node represents a transaction.

Each edge represents an ordering dependency.

------------------------------------------------------------------------

# 3. Why is it Needed?

A precedence graph helps us determine whether a concurrent schedule is
**conflict serializable** quickly.

Instead of swapping operations, we inspect the graph.

------------------------------------------------------------------------

# 4. Components

## Nodes

Each transaction is represented by a node.

``` text
(T1)

(T2)

(T3)
```

## Edges

Draw an edge:

``` text
T1 ─────► T2
```

when:

-   Operations belong to different transactions.
-   They conflict.
-   T1's operation occurs before T2's operation.

------------------------------------------------------------------------

# 5. Steps to Construct a Precedence Graph

1.  List all transactions.
2.  Create one node per transaction.
3.  Identify all conflicting operations.
4.  Draw directed edges.
5.  Check for cycles.

``` text
Schedule
   │
Find Conflicts
   │
Draw Edges
   │
Cycle?
```

------------------------------------------------------------------------

# 6. Example

Schedule

``` text
R1(A)
W1(A)
R2(A)
W2(A)
```

Conflict:

``` text
W1(A) → R2(A)

↓

T1 ───► T2
```

Graph:

``` text
(T1) ─────► (T2)
```

No cycle.

Therefore:

**Schedule is Conflict Serializable.**

------------------------------------------------------------------------

# 7. Cyclic Graph Example

``` text
T1 ───► T2
▲        │
│        ▼
└────────┘
```

Cycle detected.

Result:

**Not Conflict Serializable.**

------------------------------------------------------------------------

# 8. Acyclic Graph Example

``` text
T1 ───► T2
 │
 ▼
T3
```

No cycle.

Result:

**Conflict Serializable.**

------------------------------------------------------------------------

# 9. Cycle Detection Rule

``` text
Cycle?

Yes
 │
Not Serializable

No
 │
Conflict Serializable
```

This is the most important rule to remember.

------------------------------------------------------------------------

# 10. Real-World Example

### Banking

Transactions updating the same account create dependencies.

The precedence graph checks whether those dependencies still allow a
serial execution order.

------------------------------------------------------------------------

# 11. Advantages

-   Simple visualization
-   Fast conflict serializability testing
-   Widely used in DBMS education
-   Easy to understand

------------------------------------------------------------------------

# 12. Limitations

-   Only tests Conflict Serializability
-   Cannot test View Serializability
-   Requires conflict identification first

------------------------------------------------------------------------

# 13. Best Practices

-   Identify conflicts carefully.
-   Ignore Read-Read pairs.
-   Draw edges only for conflicting operations.
-   Always check for cycles.

------------------------------------------------------------------------

# 14. Common Mistakes

❌ Drawing edges for Read-Read operations.

❌ Forgetting operation order.

❌ Assuming every graph without many edges is serializable.

------------------------------------------------------------------------

# 15. Interview Questions

### Beginner

1.  What is a Precedence Graph?
2.  Why is it used?

### Intermediate

1.  How do you construct a precedence graph?
2.  What does an edge represent?

### Advanced

1.  Why does an acyclic graph imply conflict serializability?
2.  Can a precedence graph test view serializability?

------------------------------------------------------------------------

# 16. Practice Problems

1.  Construct a precedence graph from a schedule.
2.  Identify all conflicting operations.
3.  Detect whether a graph contains a cycle.
4.  Decide whether the schedule is conflict serializable.

------------------------------------------------------------------------

# Revision Notes

``` text
Schedule
   │
Conflicts
   │
Precedence Graph
   │
Cycle?
 │      │
No     Yes
 │       │
Serializable  Not Serializable
```

## Memory Trick

``` text
GRAPH

Find Conflicts

↓

Draw Edges

↓

Find Cycle

↓

Decide
```

## Key Points

-   Nodes represent transactions.
-   Edges represent conflicting dependencies.
-   Acyclic graph ⇒ Conflict Serializable.
-   Cyclic graph ⇒ Not Conflict Serializable.
-   Precedence graphs do not test View Serializability.

------------------------------------------------------------------------

# Final Takeaway

The Precedence Graph is the standard technique for determining Conflict
Serializability. By representing transaction dependencies as a directed
graph and checking for cycles, the DBMS can quickly determine whether a
concurrent schedule is equivalent to a serial schedule. This is one of
the most important and frequently tested concepts in DBMS exams and
technical interviews.
