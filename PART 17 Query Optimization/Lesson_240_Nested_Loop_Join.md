# Lesson 240 --- Nested Loop Join

> **Part 17 --- Query Optimization**

------------------------------------------------------------------------

# Learning Objectives

By the end of this lesson, you will understand:

-   What a Nested Loop Join is
-   Why Nested Loop Join is used
-   How it works internally
-   Variants of Nested Loop Join
-   Time complexity
-   Advantages and limitations
-   Interview questions
-   Practice problems
-   Revision notes

------------------------------------------------------------------------

# 1. Introduction

Joining tables is one of the most expensive database operations.

The simplest join algorithm is the **Nested Loop Join (NLJ)**, where
rows from one table are compared with rows from another table until
matching pairs are found.

Although simple, it remains widely used, especially when one table is
small or an efficient index exists.

------------------------------------------------------------------------

# 2. What is a Nested Loop Join?

A **Nested Loop Join** compares each row of one table (outer table) with
every row of another table (inner table).

``` text
Outer Table
    │
For Each Row
    │
Scan Inner Table
    │
Find Matches
```

------------------------------------------------------------------------

# 3. Working Principle

Suppose:

``` text
Employee
ID  DeptID

Department
DeptID  Name
```

Execution:

``` text
For each Employee

↓

Check every Department

↓

If DeptID matches

↓

Return Joined Row
```

------------------------------------------------------------------------

# 4. Algorithm

``` text
FOR each row in Outer Table

    FOR each row in Inner Table

        IF Join Condition True

            Output Row
```

Pseudo-code:

``` text
for each row O:
    for each row I:
        if O.key == I.key:
            output(O,I)
```

------------------------------------------------------------------------

# 5. Example

Query:

``` sql
SELECT e.Name, d.DepartmentName
FROM Employee e
JOIN Department d
ON e.DepartmentID = d.DepartmentID;
```

Execution:

``` text
Employee 1 → Compare with every Department

Employee 2 → Compare with every Department

Employee 3 → Compare with every Department
```

------------------------------------------------------------------------

# 6. Variants

### Simple Nested Loop Join

Scans the inner table for every outer row.

### Block Nested Loop Join

Processes blocks of rows instead of one row at a time.

### Index Nested Loop Join

Uses an index on the inner table to find matching rows quickly.

``` text
Outer Row
    │
Index Lookup
    │
Matching Inner Row
```

------------------------------------------------------------------------

# 7. Time Complexity

If:

-   Outer table = **N** rows
-   Inner table = **M** rows

Then:

``` text
Time Complexity

O(N × M)
```

With an efficient index, the effective cost is significantly reduced.

------------------------------------------------------------------------

# 8. When is Nested Loop Join Used?

-   One table is very small.
-   Join columns are indexed.
-   Very selective queries.
-   OLTP workloads with point lookups.

------------------------------------------------------------------------

# 9. Nested Loop Join vs Other Joins

  Join Algorithm   Best For
  ---------------- --------------------------------
  Nested Loop      Small tables / indexed lookups
  Merge Join       Sorted inputs
  Hash Join        Large unsorted tables

------------------------------------------------------------------------

# 10. Advantages

-   Simple implementation
-   Works with any join condition
-   Efficient for small datasets
-   Excellent with indexes

------------------------------------------------------------------------

# 11. Limitations

-   Slow for large tables
-   High CPU usage without indexes
-   Many repeated comparisons

------------------------------------------------------------------------

# 12. Best Practices

-   Use indexes on join columns.
-   Choose the smaller table as the outer table.
-   Filter rows before joining.
-   Review execution plans.

------------------------------------------------------------------------

# 13. Common Mistakes

❌ Joining large tables without indexes.

❌ Selecting unnecessary columns.

❌ Ignoring predicate pushdown before joins.

------------------------------------------------------------------------

# 14. Interview Questions

### Beginner

1.  What is a Nested Loop Join?
2.  How does it work?

### Intermediate

1.  Explain Index Nested Loop Join.
2.  When is Nested Loop Join preferred?

### Advanced

1.  Compare Nested Loop, Merge, and Hash Join.
2.  Why does an index improve Nested Loop Join performance?

------------------------------------------------------------------------

# 15. Practice Problems

1.  Draw the Nested Loop Join workflow.
2.  Calculate the complexity for tables with N and M rows.
3.  Explain Block Nested Loop Join.
4.  Identify situations where Nested Loop Join is the best choice.

------------------------------------------------------------------------

# Revision Notes

``` text
Outer Table
     │
For Each Row
     │
Scan Inner Table
     │
Match?
     │
Output
```

## Memory Trick

``` text
NESTED LOOP

Outer Row

↓

Inner Scan

↓

Match

↓

Repeat
```

## Key Points

-   Nested Loop Join compares every outer row with inner rows.
-   Basic complexity is O(N × M).
-   Index Nested Loop Join greatly improves performance.
-   Best suited for small tables or indexed joins.
-   Frequently used in OLTP systems.

------------------------------------------------------------------------

# Final Takeaway

Nested Loop Join is the simplest physical join algorithm and forms the
foundation for understanding more advanced join strategies. While its
basic implementation can be expensive for large datasets, index support
and block processing make it highly effective in many real-world
workloads. Understanding when the optimizer selects a Nested Loop Join
is essential for interpreting execution plans and tuning SQL queries.
