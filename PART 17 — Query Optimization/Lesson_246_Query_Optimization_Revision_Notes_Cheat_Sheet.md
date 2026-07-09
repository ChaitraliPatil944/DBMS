# Lesson 246 --- Query Optimization Revision Notes & Cheat Sheet

> **Part 17 --- Query Optimization**

------------------------------------------------------------------------

# Quick Definition

**Query Optimization** is the process of selecting the most efficient
execution plan for a SQL query to minimize execution time and resource
usage.

``` text
SQL Query
    │
Optimizer
    │
Best Plan
    │
Fast Result
```

------------------------------------------------------------------------

# Why Query Optimization?

-   Faster query execution
-   Lower CPU usage
-   Reduced Disk I/O
-   Better memory utilization
-   Improved scalability

------------------------------------------------------------------------

# Query Processing Lifecycle

``` text
SQL Query
    │
Parser
    │
Optimizer
    │
Execution Plan
    │
Execution Engine
    │
Results
```

------------------------------------------------------------------------

# Execution Plans

## Estimated Plan

-   Generated before execution
-   Uses statistics
-   Predicts cost

## Actual Plan

-   Generated during execution
-   Uses runtime information
-   Shows actual performance

------------------------------------------------------------------------

# Cost-Based Optimizer (CBO)

``` text
SQL Query
    │
Collect Statistics
    │
Generate Plans
    │
Estimate Cost
    │
Choose Cheapest Plan
```

Uses:

-   Row count
-   Cardinality
-   Selectivity
-   Indexes
-   Data distribution
-   Page count

------------------------------------------------------------------------

# Heuristic Optimization

Common rules:

-   Predicate Pushdown
-   Projection Pushdown
-   Join Reordering
-   Expression Simplification
-   Remove Redundant Operations

``` text
Filter Early

↓

Project Early

↓

Join Smart

↓

Execute Fast
```

------------------------------------------------------------------------

# Join Algorithms

  Join          Best For                        Complexity (Typical)
  ------------- ------------------------------- ------------------------
  Nested Loop   Small tables / indexes          O(N × M)
  Merge Join    Large sorted tables             O(N + M) after sorting
  Hash Join     Large unsorted equality joins   O(N + M) average

------------------------------------------------------------------------

# Nested Loop Join

``` text
Outer Table
     │
For Each Row
     │
Scan Inner Table
     │
Output Match
```

Best when: - Small tables - Indexed lookups

------------------------------------------------------------------------

# Merge Join

``` text
Sorted A

↓

Compare

↓

Sorted B

↓

Join
```

Requires sorted inputs.

------------------------------------------------------------------------

# Hash Join

``` text
Small Table

↓

Build Hash Table

↓

Large Table

↓

Probe

↓

Join
```

Best for equality joins.

------------------------------------------------------------------------

# Query Tuning Tips

-   Avoid `SELECT *`
-   Filter rows early
-   Retrieve only needed columns
-   Index frequently searched columns
-   Review execution plans
-   Keep statistics updated
-   Avoid unnecessary sorting
-   Avoid functions on indexed columns where practical

------------------------------------------------------------------------

# Common Performance Problems

-   Missing indexes
-   Table scans
-   Poor join order
-   Outdated statistics
-   Over-indexing
-   Unnecessary DISTINCT
-   Unnecessary ORDER BY

------------------------------------------------------------------------

# Comparison Table

  Concept                  Purpose
  ------------------------ ----------------------------
  Query Optimization       Select best execution plan
  Execution Plan           Blueprint for execution
  CBO                      Chooses lowest-cost plan
  Heuristic Optimization   Rule-based query rewriting
  Nested Loop              Small/indexed joins
  Merge Join               Sorted joins
  Hash Join                Large equality joins
  Query Tuning             Improve SQL performance

------------------------------------------------------------------------

# Common Interview Questions

1.  What is Query Optimization?
2.  Estimated vs Actual Execution Plan?
3.  What is a Cost-Based Optimizer?
4.  Cardinality vs Selectivity?
5.  Predicate Pushdown?
6.  Projection Pushdown?
7.  Nested Loop vs Merge vs Hash Join?
8.  What causes table scans?
9.  How do indexes improve performance?
10. What is Query Tuning?

------------------------------------------------------------------------

# Last-Minute Checklist

``` text
✓ Query Optimization
✓ Execution Plans
✓ CBO
✓ Statistics
✓ Cardinality
✓ Selectivity
✓ Heuristic Rules
✓ Predicate Pushdown
✓ Projection Pushdown
✓ Nested Loop Join
✓ Merge Join
✓ Hash Join
✓ Query Tuning
```

------------------------------------------------------------------------

# Memory Trick

``` text
QUERY

↓

Optimize

↓

Plan

↓

Join

↓

Tune

↓

Fast
```

------------------------------------------------------------------------

# Key Points

-   Optimizers choose the best execution plan.
-   CBO relies on accurate statistics.
-   Heuristic optimization rewrites queries using proven rules.
-   Nested Loop, Merge, and Hash are the three major physical join
    algorithms.
-   Execution plans are essential for diagnosing slow queries.
-   Query tuning combines SQL rewriting, indexing, and plan analysis.

------------------------------------------------------------------------

# Final Takeaway

Query Optimization is the intelligence behind efficient SQL execution.
By understanding execution plans, cost estimation, heuristic rules, join
algorithms, and practical query tuning, you can write high-performance
SQL, interpret optimizer decisions, and solve database performance
problems confidently in both interviews and production systems.
