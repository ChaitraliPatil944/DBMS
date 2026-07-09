# Lesson 245 --- Query Optimization Practice Problems

> **Part 17 --- Query Optimization**

------------------------------------------------------------------------

# Learning Objectives

By completing these exercises, you will:

-   Strengthen your understanding of query optimization
-   Analyze execution plans
-   Select appropriate join algorithms
-   Apply SQL tuning techniques
-   Prepare for university exams and technical interviews

------------------------------------------------------------------------

# Section A --- Fundamentals (1--10)

1.  Define Query Optimization.
2.  Why is Query Optimization important?
3.  Explain the query processing lifecycle.
4.  What is an Execution Plan?
5.  Differentiate Estimated and Actual Execution Plans.
6.  List the goals of query optimization.
7.  What factors affect query performance?
8.  Explain the role of the Query Optimizer.
9.  What is a Rule-Based Optimizer?
10. What is a Cost-Based Optimizer?

------------------------------------------------------------------------

# Section B --- Cost-Based Optimization (11--20)

11. What database statistics are used by a CBO?
12. Define Cardinality.
13. Define Selectivity.
14. Why are statistics important?
15. Compare CBO and RBO.
16. Explain how disk I/O affects cost.
17. Explain CPU cost estimation.
18. How does memory affect execution plans?
19. Why can stale statistics lead to poor plans?
20. Identify the cheapest plan from multiple alternatives.

------------------------------------------------------------------------

# Section C --- Heuristic Optimization (21--30)

21. Define Heuristic Optimization.
22. Explain Predicate Pushdown.
23. Explain Projection Pushdown.
24. Explain Join Reordering.
25. Simplify a redundant WHERE clause.
26. Identify unnecessary operations in a query.
27. Rewrite a query using heuristic rules.
28. Compare Heuristic Optimization and CBO.
29. Why should filtering occur early?
30. Why should only required columns be selected?

------------------------------------------------------------------------

# Section D --- Join Algorithms (31--40)

31. Explain Nested Loop Join.
32. Explain Merge Join.
33. Explain Hash Join.
34. Compare all three join algorithms.
35. When should Nested Loop Join be preferred?
36. When should Merge Join be preferred?
37. When should Hash Join be preferred?
38. Calculate the complexity of Nested Loop Join.
39. Explain the Build and Probe phases of Hash Join.
40. Explain Sort-Merge Join.

------------------------------------------------------------------------

# Section E --- Query Tuning (41--50)

41. Rewrite a query to avoid SELECT \*.
42. Identify missing indexes in a sample query.
43. Explain why a table scan occurs.
44. Suggest improvements for a slow query.
45. Compare Table Scan and Index Seek.
46. Interpret an execution plan.
47. Identify the most expensive operator.
48. Suggest tuning improvements for a join query.
49. Explain the risks of over-indexing.
50. Design a tuning strategy for a large database.

------------------------------------------------------------------------

# Self-Assessment Checklist

``` text
✓ Query Optimization
✓ Execution Plans
✓ CBO
✓ RBO
✓ Cardinality
✓ Selectivity
✓ Predicate Pushdown
✓ Projection Pushdown
✓ Nested Loop Join
✓ Merge Join
✓ Hash Join
✓ Query Tuning
```

------------------------------------------------------------------------

# Bonus Challenge

Given the query:

``` sql
SELECT *
FROM Orders
WHERE CustomerID = 100
ORDER BY OrderDate;
```

Tasks:

-   Identify performance issues.
-   Suggest suitable indexes.
-   Rewrite the query.
-   Predict the execution plan.
-   Explain which optimizer techniques apply.

------------------------------------------------------------------------

# Practice Tips

-   Read execution plans before changing SQL.
-   Measure performance before and after tuning.
-   Filter rows as early as possible.
-   Retrieve only necessary columns.
-   Choose indexes carefully.

------------------------------------------------------------------------

# Final Takeaway

Query optimization is best learned through practice. By analyzing
execution plans, comparing optimizer strategies, selecting suitable join
algorithms, and tuning SQL queries, you develop the practical skills
needed to improve database performance in real-world applications,
university examinations, and technical interviews.
