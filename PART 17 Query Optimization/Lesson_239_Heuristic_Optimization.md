# Lesson 239 --- Heuristic Optimization

> **Part 17 --- Query Optimization**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What Heuristic Optimization is
-   Why heuristic optimization is used
-   Common heuristic rules
-   Predicate pushdown
-   Projection pushdown
-   Join reordering
-   Expression simplification
-   Advantages and limitations
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Before estimating query costs, many DBMSs first apply simple
transformation rules that almost always improve performance.

These rules are called **heuristics**.

Unlike Cost-Based Optimization, heuristic optimization does not
calculate execution cost. It rewrites queries into a more efficient form
using proven optimization rules.

------------------------------------------------------------------------

# 2. What is Heuristic Optimization?

**Heuristic Optimization** is a rule-based optimization technique that
transforms a query into an equivalent but more efficient form without
estimating execution costs.

``` text
SQL Query
    │
Apply Rules
    │
Optimized Query
    │
Execution
```

------------------------------------------------------------------------

# 3. Why is Heuristic Optimization Needed?

Without heuristic optimization:

-   More rows processed
-   More disk I/O
-   Larger intermediate results
-   Slower execution

With heuristic optimization:

-   Smaller intermediate tables
-   Less memory usage
-   Faster query execution

------------------------------------------------------------------------

# 4. Common Heuristic Rules

-   Predicate Pushdown
-   Projection Pushdown
-   Join Reordering
-   Expression Simplification
-   Remove Redundant Operations
-   Early Selection

------------------------------------------------------------------------

# 5. Predicate Pushdown

Move filtering conditions (`WHERE`) as close as possible to the data
source.

Before:

``` text
Read All Rows
      │
Join
      │
Filter
```

After:

``` text
Filter
   │
Join
```

This reduces the number of rows participating in joins.

------------------------------------------------------------------------

# 6. Projection Pushdown

Retrieve only required columns instead of all columns.

Before:

``` sql
SELECT *
FROM Employee;
```

Better:

``` sql
SELECT Name, Salary
FROM Employee;
```

Fewer columns mean less memory and I/O.

------------------------------------------------------------------------

# 7. Join Reordering

When multiple joins exist, the optimizer changes their order to reduce
intermediate results.

``` text
A JOIN B JOIN C

↓

(B JOIN C)

↓

JOIN A
```

The final result remains the same, but execution may be much faster.

------------------------------------------------------------------------

# 8. Expression Simplification

Simplify unnecessary expressions.

Example:

``` sql
WHERE Salary > 5000
AND Salary > 3000
```

Simplified:

``` sql
WHERE Salary > 5000
```

------------------------------------------------------------------------

# 9. Removing Redundant Operations

Examples include:

-   Eliminating unnecessary DISTINCT
-   Removing unnecessary ORDER BY
-   Eliminating duplicate predicates

------------------------------------------------------------------------

# 10. Heuristic vs Cost-Based Optimization

  Heuristic Optimization   Cost-Based Optimization
  ------------------------ --------------------------
  Rule-based               Cost-based
  No statistics required   Uses statistics
  Fast optimization        More computation
  Uses predefined rules    Estimates execution cost

------------------------------------------------------------------------

# 11. Real-World Example

``` sql
SELECT Name
FROM Employee
WHERE Department='HR';
```

Instead of scanning and processing all employees first, the optimizer
filters HR employees immediately and then processes only those rows.

------------------------------------------------------------------------

# 12. Advantages

-   Fast optimization
-   Smaller intermediate results
-   Reduced CPU and memory usage
-   Complements Cost-Based Optimization

------------------------------------------------------------------------

# 13. Limitations

-   Does not consider actual execution cost
-   Rules may not always produce the optimal plan
-   Less flexible than CBO

------------------------------------------------------------------------

# 14. Best Practices

-   Filter data as early as possible.
-   Select only required columns.
-   Write simple predicates.
-   Avoid unnecessary sorting.

------------------------------------------------------------------------

# 15. Common Mistakes

❌ Using `SELECT *` when unnecessary.

❌ Applying filters after joins when they can be applied earlier.

❌ Assuming heuristic optimization always produces the best plan.

------------------------------------------------------------------------

# 16. Interview Questions

### Beginner

1.  What is Heuristic Optimization?
2.  Why is it used?

### Intermediate

1.  Explain predicate pushdown.
2.  Explain projection pushdown.

### Advanced

1.  Compare Heuristic Optimization and CBO.
2.  Why does join reordering improve performance?

------------------------------------------------------------------------

# 17. Practice Problems

1.  Draw the heuristic optimization workflow.
2.  Rewrite a query using predicate pushdown.
3.  Compare heuristic optimization and CBO.
4.  Explain why projection pushdown reduces I/O.

------------------------------------------------------------------------

# Revision Notes

``` text
SQL Query
    │
Apply Rules
    │
Reduce Data Early
    │
Execute Faster
```

## Memory Trick

``` text
HEURISTIC

Filter Early

↓

Project Early

↓

Join Smart

↓

Execute Fast
```

## Key Points

-   Heuristic optimization uses predefined rules.
-   Predicate pushdown reduces rows early.
-   Projection pushdown reduces columns.
-   Join reordering minimizes intermediate results.
-   Modern DBMSs combine heuristic and cost-based optimization.

------------------------------------------------------------------------

# Final Takeaway

Heuristic Optimization improves SQL performance by applying proven
transformation rules before query execution. Techniques such as
predicate pushdown, projection pushdown, join reordering, and expression
simplification reduce unnecessary work and complement Cost-Based
Optimization, resulting in faster and more efficient query execution.
