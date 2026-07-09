# Lesson 237 --- Execution Plans

> **Part 17 --- Query Optimization**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What an Execution Plan is
-   Why execution plans are important
-   How the optimizer creates execution plans
-   Common execution plan operators
-   Estimated vs Actual execution plans
-   How to read execution plans
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

A SQL query can often be executed in multiple ways.

The **Query Optimizer** evaluates different strategies and chooses the
one with the lowest estimated cost.

The chosen strategy is called the **Execution Plan**.

------------------------------------------------------------------------

# 2. What is an Execution Plan?

An **Execution Plan** is a detailed blueprint describing how the DBMS
will execute a SQL query.

It specifies:

-   Access methods
-   Join algorithms
-   Sorting operations
-   Filtering operations
-   Estimated costs

``` text
SQL Query
    │
Query Optimizer
    │
Execution Plan
    │
Execution Engine
```

------------------------------------------------------------------------

# 3. Why are Execution Plans Important?

Execution plans help developers:

-   Understand query performance
-   Detect bottlenecks
-   Identify missing indexes
-   Compare optimization strategies
-   Tune slow queries

------------------------------------------------------------------------

# 4. How is an Execution Plan Created?

``` text
SQL Query
    │
Parser
    │
Query Optimizer
    │
Generate Candidate Plans
    │
Estimate Cost
    │
Choose Lowest Cost Plan
```

------------------------------------------------------------------------

# 5. Estimated vs Actual Execution Plan

  Estimated Plan               Actual Plan
  ---------------------------- -------------------------------
  Generated before execution   Generated during execution
  Uses statistics              Uses real runtime information
  Predicts cost                Shows actual performance

------------------------------------------------------------------------

# 6. Common Execution Plan Operators

### Table Scan

Reads every row in a table.

``` text
Entire Table
      │
Read Every Row
```

------------------------------------------------------------------------

### Index Scan

Scans an index and may still examine many rows.

------------------------------------------------------------------------

### Index Seek

Directly locates matching rows using an index.

``` text
Index

↓

Matching Rows Only
```

------------------------------------------------------------------------

### Filter

Removes rows that do not satisfy the WHERE condition.

------------------------------------------------------------------------

### Sort

Orders rows using `ORDER BY`.

------------------------------------------------------------------------

### Join Operators

-   Nested Loop Join
-   Merge Join
-   Hash Join

These are discussed in upcoming lessons.

------------------------------------------------------------------------

# 7. Reading an Execution Plan

Typical reading process:

1.  Identify the most expensive operator.
2.  Check whether indexes are used.
3.  Look for table scans.
4.  Examine joins.
5.  Review estimated cost.

------------------------------------------------------------------------

# 8. Example

Query:

``` sql
SELECT Name
FROM Employee
WHERE EmployeeID = 101;
```

Possible execution plan:

``` text
Index Seek

↓

Filter

↓

Return Result
```

Without an index:

``` text
Table Scan

↓

Filter

↓

Return Result
```

------------------------------------------------------------------------

# 9. Advantages

-   Improves SQL performance
-   Helps identify inefficient operations
-   Supports index tuning
-   Reduces execution cost

------------------------------------------------------------------------

# 10. Limitations

-   Estimated plans may differ from actual execution
-   Incorrect statistics produce poor estimates
-   Complex plans require experience to interpret

------------------------------------------------------------------------

# 11. Best Practices

-   Keep statistics updated.
-   Investigate expensive operators.
-   Avoid unnecessary table scans.
-   Create useful indexes.
-   Compare estimated and actual plans.

------------------------------------------------------------------------

# 12. Common Mistakes

❌ Ignoring execution plans for slow queries.

❌ Assuming estimated cost always matches runtime.

❌ Adding indexes without checking the plan.

------------------------------------------------------------------------

# 13. Interview Questions

### Beginner

1.  What is an execution plan?
2.  Why are execution plans important?

### Intermediate

1.  Estimated vs Actual execution plan.
2.  Index Seek vs Table Scan.

### Advanced

1.  How does the optimizer generate execution plans?
2.  Why can estimated and actual plans differ?

------------------------------------------------------------------------

# 14. Practice Problems

1.  Draw the execution plan generation workflow.
2.  Compare Table Scan and Index Seek.
3.  Explain why execution plans are useful.
4.  Identify expensive operators in a sample plan.

------------------------------------------------------------------------

# Revision Notes

``` text
SQL Query
    │
Optimizer
    │
Execution Plan
    │
Operators
    │
Result
```

## Memory Trick

``` text
PLAN

Parse

↓

Optimize

↓

Execute

↓

Analyze
```

## Key Points

-   Execution plans describe how SQL queries are executed.
-   The optimizer selects the lowest-cost plan.
-   Estimated plans use statistics.
-   Actual plans use runtime information.
-   Reading execution plans is essential for SQL tuning.

------------------------------------------------------------------------

# Final Takeaway

Execution Plans reveal exactly how a DBMS processes a SQL query. By
understanding operators such as table scans, index seeks, filters,
sorts, and joins, you can diagnose slow queries, design better indexes,
and improve overall database performance. Execution plans are among the
most valuable tools for SQL optimization and are frequently discussed in
database administration and technical interviews.
