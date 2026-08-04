# Lesson 238 --- Cost-Based Optimizer (CBO)

> **Part 17 --- Query Optimization**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What a Cost-Based Optimizer (CBO) is
-   Why CBO is important
-   How CBO estimates query cost
-   Database statistics
-   Cardinality and selectivity
-   Cost factors
-   Advantages and limitations
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

A SQL query can usually be executed in multiple ways.

Modern DBMSs evaluate these alternatives and estimate which one is
cheapest before execution.

This decision-making process is performed by the **Cost-Based Optimizer
(CBO)**.

------------------------------------------------------------------------

# 2. What is a Cost-Based Optimizer?

A **Cost-Based Optimizer (CBO)** estimates the cost of different
execution plans and selects the one with the lowest estimated cost.

``` text
SQL Query
    │
Generate Plans
    │
Estimate Cost
    │
Choose Lowest Cost
    │
Execution
```

------------------------------------------------------------------------

# 3. Why is CBO Needed?

Without CBO:

-   Inefficient execution plans
-   Higher CPU usage
-   More disk I/O
-   Longer response time

With CBO:

-   Faster queries
-   Better scalability
-   Efficient resource utilization

------------------------------------------------------------------------

# 4. How CBO Works

``` text
SQL Query
    │
Collect Statistics
    │
Generate Candidate Plans
    │
Estimate Cost
    │
Select Cheapest Plan
```

------------------------------------------------------------------------

# 5. Statistics Used by CBO

The optimizer relies on database statistics such as:

-   Number of rows
-   Number of pages
-   Index information
-   Data distribution
-   Distinct values
-   Null values

Accurate statistics lead to better execution plans.

------------------------------------------------------------------------

# 6. Cardinality

**Cardinality** is the estimated number of rows produced by an
operation.

Example:

``` text
Employee Table

100,000 Rows

↓

WHERE Department='HR'

↓

Estimated Rows = 800
```

------------------------------------------------------------------------

# 7. Selectivity

**Selectivity** measures how effectively a condition filters rows.

High selectivity:

``` text
100000 Rows

↓

5 Rows Returned
```

Low selectivity:

``` text
100000 Rows

↓

80000 Rows Returned
```

Highly selective conditions often benefit from indexes.

------------------------------------------------------------------------

# 8. Cost Factors

The optimizer estimates cost using:

-   Disk I/O
-   CPU time
-   Memory usage
-   Network transfer (distributed systems)
-   Join algorithm cost
-   Sorting cost

------------------------------------------------------------------------

# 9. Example

``` sql
SELECT *
FROM Orders
WHERE OrderID = 1001;
```

Possible plans:

``` text
Table Scan

Estimated Cost = High
```

``` text
Index Seek

Estimated Cost = Low
```

The optimizer selects the Index Seek.

------------------------------------------------------------------------

# 10. CBO vs Rule-Based Optimizer

  Cost-Based Optimizer   Rule-Based Optimizer
  ---------------------- ----------------------
  Uses statistics        Uses fixed rules
  Dynamic decisions      Static decisions
  Better performance     Simpler
  Widely used today      Mostly obsolete

------------------------------------------------------------------------

# 11. Advantages

-   Better execution plans
-   Efficient index usage
-   Lower resource consumption
-   Improved scalability

------------------------------------------------------------------------

# 12. Limitations

-   Depends on accurate statistics
-   Optimization consumes CPU
-   Stale statistics reduce accuracy

------------------------------------------------------------------------

# 13. Best Practices

-   Update statistics regularly.
-   Create appropriate indexes.
-   Review execution plans.
-   Avoid unnecessary full table scans.

------------------------------------------------------------------------

# 14. Common Mistakes

❌ Ignoring outdated statistics.

❌ Assuming indexes always improve performance.

❌ Confusing cardinality with selectivity.

------------------------------------------------------------------------

# 15. Interview Questions

### Beginner

1.  What is a Cost-Based Optimizer?
2.  Why is CBO important?

### Intermediate

1.  What statistics does CBO use?
2.  Explain cardinality and selectivity.

### Advanced

1.  CBO vs Rule-Based Optimizer.
2.  Why can stale statistics produce poor execution plans?

------------------------------------------------------------------------

# 16. Practice Problems

1.  Draw the CBO workflow.
2.  Explain how statistics affect optimization.
3.  Compare CBO and RBO.
4.  Explain why selectivity influences index usage.

------------------------------------------------------------------------

# Revision Notes

``` text
SQL Query
    │
Statistics
    │
Estimate Cost
    │
Choose Best Plan
```

## Memory Trick

``` text
CBO

Collect Statistics

↓

Estimate Cost

↓

Optimize
```

## Key Points

-   CBO chooses the lowest-cost execution plan.
-   Statistics are essential for accurate optimization.
-   Cardinality estimates row counts.
-   Selectivity measures filtering effectiveness.
-   Modern relational DBMSs rely primarily on CBO.

------------------------------------------------------------------------

# Final Takeaway

The Cost-Based Optimizer is the decision-making engine behind modern SQL
execution. By analyzing statistics, estimating resource usage, and
comparing alternative execution plans, it selects the most efficient
strategy for running a query. Understanding CBO is fundamental for SQL
performance tuning, database administration, and technical interviews.
