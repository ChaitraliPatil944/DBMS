# Lesson 242 --- Hash Join

> **Part 17 --- Query Optimization**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What a Hash Join is
-   Why Hash Join is used
-   Build and Probe phases
-   Internal working
-   Time complexity
-   Advantages and limitations
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Large joins on unsorted tables can be expensive.

Instead of sorting the data or comparing every row, many DBMSs use a
**Hash Join**, which uses a hash table to find matching rows
efficiently.

Hash Join is one of the fastest join algorithms for large, unsorted
datasets with equality conditions.

------------------------------------------------------------------------

# 2. What is a Hash Join?

A **Hash Join** is a join algorithm that builds a hash table on one
input and probes it using rows from the other input.

``` text
Table A
   │
Build Hash Table
   │
Table B
   │
Probe Hash Table
   │
Matching Rows
```

------------------------------------------------------------------------

# 3. Why is Hash Join Needed?

Without hashing:

-   Many row comparisons
-   High CPU usage
-   Slow joins on large tables

With hashing:

-   Fast lookups
-   Reduced comparisons
-   Efficient equality joins

------------------------------------------------------------------------

# 4. Working Principle

Hash Join has two phases:

## Phase 1 --- Build

The smaller table is read first.

``` text
Small Table
     │
Compute Hash(Key)
     │
Store in Hash Table
```

## Phase 2 --- Probe

The larger table is scanned.

``` text
Large Table
     │
Compute Hash(Key)
     │
Search Hash Table
     │
Return Matches
```

------------------------------------------------------------------------

# 5. Example

``` sql
SELECT e.Name, d.DepartmentName
FROM Employee e
JOIN Department d
ON e.DepartmentID = d.DepartmentID;
```

Execution:

``` text
Department
      │
Build Hash Table

Employee
      │
Probe Hash Table

↓

Matching Rows
```

------------------------------------------------------------------------

# 6. Hash Function

A hash function converts the join key into a bucket.

``` text
DeptID = 20

↓

Hash(20)

↓

Bucket 5
```

Rows with the same join key map to the same bucket.

------------------------------------------------------------------------

# 7. Time Complexity

Average case:

``` text
Build  : O(N)

Probe  : O(M)

Total  : O(N + M)
```

Worst case (many hash collisions):

``` text
O(N × M)
```

------------------------------------------------------------------------

# 8. When is Hash Join Used?

-   Large unsorted tables
-   Equality joins (`=`)
-   No useful ordering exists
-   Data warehouse (OLAP) workloads

------------------------------------------------------------------------

# 9. Hash Join vs Other Joins

  Join Algorithm   Best For
  ---------------- --------------------------------
  Nested Loop      Small tables / indexed lookups
  Merge Join       Sorted tables
  Hash Join        Large unsorted tables

------------------------------------------------------------------------

# 10. Advantages

-   Excellent for large datasets
-   No sorting required
-   Fast equality joins
-   Linear average complexity

------------------------------------------------------------------------

# 11. Limitations

-   Extra memory for hash table
-   Not suitable for range joins
-   Performance drops with many collisions

------------------------------------------------------------------------

# 12. Best Practices

-   Build the hash table on the smaller input.
-   Ensure sufficient memory.
-   Use equality join conditions.
-   Filter rows before joining.

------------------------------------------------------------------------

# 13. Common Mistakes

❌ Building the hash table on the larger table.

❌ Using Hash Join for range joins.

❌ Ignoring memory limitations.

------------------------------------------------------------------------

# 14. Interview Questions

### Beginner

1.  What is a Hash Join?
2.  What are the Build and Probe phases?

### Intermediate

1.  Why is Hash Join efficient?
2.  When does the optimizer choose Hash Join?

### Advanced

1.  Compare Hash Join, Merge Join, and Nested Loop Join.
2.  How do hash collisions affect performance?

------------------------------------------------------------------------

# 15. Practice Problems

1.  Draw the Hash Join workflow.
2.  Explain Build and Probe with an example.
3.  Compare Hash Join and Merge Join.
4.  Identify situations where Hash Join is preferred.

------------------------------------------------------------------------

# Revision Notes

``` text
Small Table
    │
Build Hash Table
    │
Large Table
    │
Probe
    │
Join Result
```

## Memory Trick

``` text
HASH

Build

↓

Hash

↓

Probe

↓

Match
```

## Key Points

-   Hash Join uses hashing instead of sorting.
-   Build on the smaller table.
-   Probe using the larger table.
-   Average complexity is O(N + M).
-   Best for equality joins on large unsorted tables.

------------------------------------------------------------------------

# Final Takeaway

Hash Join is one of the most efficient physical join algorithms for
equality-based joins on large unsorted datasets. By building an
in-memory hash table for one input and probing it with the other, it
minimizes comparisons and avoids sorting, making it a preferred strategy
in many modern database systems and execution plans.
