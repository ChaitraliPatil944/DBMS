# Lesson 241 --- Merge Join

> **Part 17 --- Query Optimization**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What a Merge Join is
-   Why Merge Join is used
-   How it works internally
-   Sort-Merge Join process
-   Time complexity
-   Advantages and limitations
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

When two tables are already sorted on the join key, repeatedly comparing
every row is unnecessary.

A **Merge Join** takes advantage of sorted data by scanning both tables
simultaneously, making it one of the fastest join algorithms for large
sorted datasets.

------------------------------------------------------------------------

# 2. What is a Merge Join?

A **Merge Join** is a join algorithm that joins two sorted inputs by
comparing their current rows and advancing through them in order.

``` text
Sorted Table A      Sorted Table B
      │                   │
      └──── Compare ──────┘
               │
          Matching Rows
```

------------------------------------------------------------------------

# 3. Why is Merge Join Needed?

Without sorted inputs, joins may require repeated scans.

Merge Join:

-   Reads each table sequentially
-   Minimizes repeated comparisons
-   Works efficiently for large sorted datasets

------------------------------------------------------------------------

# 4. Working Principle

Suppose:

``` text
Employee
DeptID

Department
DeptID
```

Algorithm:

``` text
Pointer A → First Row

Pointer B → First Row

Compare Keys

Equal?

│
├─ Yes → Output Match → Advance Both
│
├─ A < B → Advance A
│
└─ A > B → Advance B
```

------------------------------------------------------------------------

# 5. Example

``` sql
SELECT e.Name, d.DepartmentName
FROM Employee e
JOIN Department d
ON e.DepartmentID = d.DepartmentID;
```

Sorted inputs:

``` text
Employee:     10 20 30 40
Department:   20 30 40 50

Compare

10 < 20 → Move Employee

20 = 20 → Match

30 = 30 → Match

40 = 40 → Match
```

------------------------------------------------------------------------

# 6. Sort-Merge Join

If tables are not already sorted:

``` text
Table A ─┐
          ├─ Sort ─┐
Table B ─┘         │
                   ▼
              Merge Join
```

Sorting increases the total execution cost.

------------------------------------------------------------------------

# 7. Time Complexity

Already sorted inputs:

``` text
O(N + M)
```

If sorting is required:

``` text
Sorting + Merge

≈ O(N log N + M log M)
```

------------------------------------------------------------------------

# 8. When is Merge Join Used?

-   Both tables are sorted
-   Join columns are indexed and scanned in order
-   Large datasets
-   Range joins
-   Data warehouses (OLAP)

------------------------------------------------------------------------

# 9. Merge Join vs Other Joins

  Join Algorithm   Best For
  ---------------- ------------------------------
  Nested Loop      Small tables / index lookups
  Merge Join       Large sorted tables
  Hash Join        Large unsorted tables

------------------------------------------------------------------------

# 10. Advantages

-   Very efficient for sorted data
-   Sequential disk access
-   Low comparison overhead
-   Excellent for large datasets

------------------------------------------------------------------------

# 11. Limitations

-   Requires sorted inputs
-   Sorting may be expensive
-   Not ideal for highly unsorted data

------------------------------------------------------------------------

# 12. Best Practices

-   Index join columns.
-   Reuse existing sorted order.
-   Filter rows before joining.
-   Review execution plans.

------------------------------------------------------------------------

# 13. Common Mistakes

❌ Ignoring sorting cost.

❌ Assuming Merge Join is always faster.

❌ Joining unsorted tables without considering alternatives.

------------------------------------------------------------------------

# 14. Interview Questions

### Beginner

1.  What is a Merge Join?
2.  Why does it require sorted inputs?

### Intermediate

1.  Explain Sort-Merge Join.
2.  Compare Merge Join and Nested Loop Join.

### Advanced

1.  When does the optimizer choose Merge Join?
2.  Why is Merge Join efficient for large datasets?

------------------------------------------------------------------------

# 15. Practice Problems

1.  Draw the Merge Join workflow.
2.  Compare Merge Join and Hash Join.
3.  Calculate complexity with and without sorting.
4.  Identify situations where Merge Join is preferred.

------------------------------------------------------------------------

# Revision Notes

``` text
Sorted Inputs
      │
Compare Keys
      │
Advance Pointer
      │
Match
```

## Memory Trick

``` text
MERGE

Sort

↓

Compare

↓

Advance

↓

Join
```

## Key Points

-   Merge Join requires sorted inputs.
-   Already sorted data gives O(N + M) complexity.
-   Sort-Merge Join first sorts, then merges.
-   Sequential scanning improves performance.
-   Frequently used for large ordered datasets.

------------------------------------------------------------------------

# Final Takeaway

Merge Join is an efficient physical join algorithm that exploits sorted
data to join tables with minimal comparisons. When suitable ordering
already exists, it can outperform many alternatives by scanning each
input only once. Understanding Merge Join helps explain optimizer
decisions in execution plans and is a core DBMS interview topic.
