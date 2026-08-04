# Lesson 243 --- Query Tuning

> **Part 17 --- Query Optimization**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What Query Tuning is
-   Why query tuning is important
-   Common causes of slow SQL queries
-   Practical query tuning techniques
-   Index tuning
-   Execution plan analysis
-   Best practices
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Even when a query is correct, it may still perform poorly.

**Query Tuning** is the process of improving SQL query performance by
reducing execution time and resource consumption without changing the
query's result.

------------------------------------------------------------------------

# 2. What is Query Tuning?

Query Tuning is the process of rewriting SQL queries, improving indexes,
and analyzing execution plans to make queries execute faster.

``` text
Slow Query
     │
Analyze
     │
Optimize
     │
Fast Query
```

------------------------------------------------------------------------

# 3. Why is Query Tuning Needed?

Without tuning:

-   Slow response time
-   High CPU usage
-   Excessive disk I/O
-   Poor scalability
-   Blocking and lock contention

With tuning:

-   Faster execution
-   Better throughput
-   Efficient resource utilization
-   Improved user experience

------------------------------------------------------------------------

# 4. Query Tuning Workflow

``` text
Slow Query
     │
Collect Execution Plan
     │
Identify Bottleneck
     │
Optimize Query
     │
Test Performance
     │
Deploy
```

------------------------------------------------------------------------

# 5. Common Causes of Slow Queries

-   Missing indexes
-   Using `SELECT *`
-   Unnecessary joins
-   Functions on indexed columns
-   Large table scans
-   Outdated statistics
-   Poor join order

------------------------------------------------------------------------

# 6. Query Tuning Techniques

## Use Appropriate Indexes

``` sql
CREATE INDEX idx_employee_dept
ON Employee(DepartmentID);
```

Indexes reduce search time.

------------------------------------------------------------------------

## Avoid `SELECT *`

Bad:

``` sql
SELECT *
FROM Employee;
```

Better:

``` sql
SELECT Name, Salary
FROM Employee;
```

------------------------------------------------------------------------

## Filter Early

``` sql
SELECT Name
FROM Employee
WHERE Department='HR';
```

Reduce rows before joins and sorting.

------------------------------------------------------------------------

## Optimize Joins

-   Join indexed columns.
-   Filter before joining.
-   Use the most suitable join algorithm.

------------------------------------------------------------------------

## Avoid Functions on Indexed Columns

Less efficient:

``` sql
WHERE UPPER(Name)='JOHN'
```

Prefer storing/searching data in a form that allows index usage where
practical.

------------------------------------------------------------------------

## Keep Statistics Updated

Accurate statistics help the optimizer choose better execution plans.

------------------------------------------------------------------------

# 7. Analyze Execution Plans

Check for:

-   Table Scans
-   Expensive Sorts
-   Missing Indexes
-   Costly Join Operators
-   High estimated cost

------------------------------------------------------------------------

# 8. Before vs After Tuning

Before:

``` text
Table Scan

↓

Sort

↓

Result
```

After:

``` text
Index Seek

↓

Filter

↓

Result
```

------------------------------------------------------------------------

# 9. Real-World Example

``` sql
SELECT *
FROM Orders
WHERE CustomerID = 100;
```

Improved version:

``` sql
SELECT OrderID, OrderDate
FROM Orders
WHERE CustomerID = 100;
```

Combined with an index on `CustomerID`, execution is much faster.

------------------------------------------------------------------------

# 10. Advantages

-   Faster SQL execution
-   Lower CPU usage
-   Reduced I/O
-   Better scalability
-   Improved application performance

------------------------------------------------------------------------

# 11. Limitations

-   Requires performance analysis
-   Extra indexes consume storage
-   Over-indexing slows INSERT, UPDATE, and DELETE operations

------------------------------------------------------------------------

# 12. Best Practices

-   Examine execution plans regularly.
-   Create indexes only where beneficial.
-   Retrieve only required columns.
-   Keep statistics current.
-   Test performance after every optimization.

------------------------------------------------------------------------

# 13. Common Mistakes

❌ Adding indexes to every column.

❌ Ignoring execution plans.

❌ Using `SELECT *` in production queries.

❌ Optimizing without measuring performance.

------------------------------------------------------------------------

# 14. Interview Questions

### Beginner

1.  What is Query Tuning?
2.  Why is it important?

### Intermediate

1.  How do execution plans help query tuning?
2.  Name common causes of slow queries.

### Advanced

1.  How can indexes improve performance?
2.  What are the risks of over-indexing?

------------------------------------------------------------------------

# 15. Practice Problems

1.  Rewrite a query to avoid `SELECT *`.
2.  Identify tuning opportunities in an execution plan.
3.  Explain how indexes reduce execution time.
4.  Compare a table scan with an index seek.

------------------------------------------------------------------------

# Revision Notes

``` text
Slow Query
     │
Execution Plan
     │
Find Bottleneck
     │
Tune Query
     │
Fast Query
```

## Memory Trick

``` text
TUNE

Trace

↓

Understand

↓

Normalize Query

↓

Evaluate
```

## Key Points

-   Query tuning improves performance without changing results.
-   Execution plans reveal bottlenecks.
-   Indexes are powerful but should be used wisely.
-   Filter early and retrieve only necessary columns.
-   Measure performance before and after tuning.

------------------------------------------------------------------------

# Final Takeaway

Query Tuning is the practical application of query optimization. By
analyzing execution plans, creating appropriate indexes, rewriting
inefficient SQL, and maintaining accurate statistics, database
professionals can dramatically improve performance while reducing CPU,
memory, and disk I/O. Query tuning is an essential skill for DBAs,
backend developers, data engineers, and technical interviews.
