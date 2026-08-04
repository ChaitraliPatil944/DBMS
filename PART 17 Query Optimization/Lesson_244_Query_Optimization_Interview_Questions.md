# Lesson 244 --- Query Optimization Interview Questions

> **Part 17 --- Query Optimization**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will:

-   Revise query optimization concepts
-   Prepare for DBMS interviews
-   Answer scenario-based optimization questions
-   Understand optimizer decisions confidently

------------------------------------------------------------------------

# 1. Beginner Questions

### Q1. What is Query Optimization?

Query Optimization is the process of selecting the most efficient
execution plan for a SQL query.

------------------------------------------------------------------------

### Q2. Why is Query Optimization important?

-   Improves performance
-   Reduces CPU usage
-   Minimizes disk I/O
-   Enhances scalability

------------------------------------------------------------------------

### Q3. What is an Execution Plan?

A blueprint describing how the DBMS executes a SQL query.

------------------------------------------------------------------------

### Q4. What is the role of the Query Optimizer?

It evaluates multiple execution plans and chooses the one with the
lowest estimated cost.

------------------------------------------------------------------------

### Q5. What is the difference between an Estimated and an Actual Execution Plan?

  Estimated Plan               Actual Plan
  ---------------------------- ----------------------------
  Generated before execution   Generated during execution
  Uses statistics              Uses runtime information

------------------------------------------------------------------------

# 2. Cost-Based Optimization

### Q6. What is a Cost-Based Optimizer (CBO)?

A component that selects the execution plan with the lowest estimated
cost using database statistics.

------------------------------------------------------------------------

### Q7. What statistics does CBO use?

-   Row count
-   Data distribution
-   Distinct values
-   Index information
-   Page count

------------------------------------------------------------------------

### Q8. What is Cardinality?

The estimated number of rows produced by an operation.

------------------------------------------------------------------------

### Q9. What is Selectivity?

The effectiveness of a condition in filtering rows.

------------------------------------------------------------------------

# 3. Heuristic Optimization

### Q10. What is Heuristic Optimization?

A rule-based optimization technique that rewrites queries without
calculating execution cost.

------------------------------------------------------------------------

### Q11. Explain Predicate Pushdown.

Move filtering conditions as close to the data source as possible.

------------------------------------------------------------------------

### Q12. Explain Projection Pushdown.

Retrieve only the required columns instead of all columns.

------------------------------------------------------------------------

# 4. Join Algorithms

### Q13. When is Nested Loop Join preferred?

For small tables or indexed lookups.

------------------------------------------------------------------------

### Q14. When is Merge Join preferred?

When both inputs are sorted.

------------------------------------------------------------------------

### Q15. When is Hash Join preferred?

For large unsorted tables using equality joins.

------------------------------------------------------------------------

### Q16. Compare Nested Loop, Merge, and Hash Join.

  Join          Best Use Case
  ------------- -------------------------------
  Nested Loop   Small tables / indexes
  Merge         Sorted datasets
  Hash          Large unsorted equality joins

------------------------------------------------------------------------

# 5. Query Tuning

### Q17. What is Query Tuning?

Improving SQL performance without changing query results.

------------------------------------------------------------------------

### Q18. Name common causes of slow queries.

-   Missing indexes
-   SELECT \*
-   Table scans
-   Outdated statistics
-   Poor joins

------------------------------------------------------------------------

### Q19. Why should you avoid SELECT \*?

It retrieves unnecessary columns, increasing I/O and memory usage.

------------------------------------------------------------------------

### Q20. What are the risks of over-indexing?

-   Extra storage
-   Slower INSERT, UPDATE, DELETE
-   Increased maintenance cost

------------------------------------------------------------------------

# 6. Scenario-Based Questions

### Scenario 1

A query performs a full table scan on a frequently searched column.

**Answer:** Create an appropriate index if justified by workload.

------------------------------------------------------------------------

### Scenario 2

Execution plans show an expensive sort operation.

**Answer:** Review indexes, ORDER BY requirements, and possible query
rewrites.

------------------------------------------------------------------------

### Scenario 3

The optimizer chooses a Hash Join.

**Answer:** Likely because the inputs are large, unsorted, and joined
using equality.

------------------------------------------------------------------------

### Scenario 4

Estimated and Actual row counts differ significantly.

**Answer:** Statistics may be outdated or data distribution may have
changed.

------------------------------------------------------------------------

# 7. Rapid Fire

1.  Query Optimization?
2.  Execution Plan?
3.  CBO?
4.  Cardinality?
5.  Selectivity?
6.  Predicate Pushdown?
7.  Projection Pushdown?
8.  Nested Loop Join?
9.  Merge Join?
10. Hash Join?

------------------------------------------------------------------------

# 8. Interview Tips

-   Explain concepts with execution plans.
-   Compare join algorithms clearly.
-   Mention statistics when discussing CBO.
-   Relate query tuning to real SQL examples.
-   Focus on reducing I/O before CPU.

------------------------------------------------------------------------

# Revision Sheet

``` text
SQL Query
    │
Optimizer
    │
Execution Plan
    │
CBO + Heuristics
    │
Join Algorithm
    │
Query Tuning
    │
Fast Execution
```

------------------------------------------------------------------------

# Final Takeaway

Query optimization interview questions evaluate your understanding of
how a DBMS executes SQL efficiently. Mastering execution plans,
cost-based optimization, heuristic optimization, join algorithms, and
query tuning enables you to diagnose performance issues and design
efficient SQL solutions in both interviews and real-world systems.
