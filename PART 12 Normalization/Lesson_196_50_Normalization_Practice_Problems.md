# Lesson 196 --- 50 Normalization Practice Problems

> **Part 12 --- Normalization**

------------------------------------------------------------------------

# Learning Objectives

By completing these exercises, you will:

-   Strengthen your understanding of normalization
-   Identify different types of dependencies
-   Practice converting tables into normal forms
-   Prepare for university exams and technical interviews

------------------------------------------------------------------------

# Section A --- Basic Concepts (1--10)

1.  Define normalization.
2.  Why is normalization needed?
3.  What is data redundancy?
4.  Explain update anomaly.
5.  Explain insert anomaly.
6.  Explain delete anomaly.
7.  What is an atomic value?
8.  What is a repeating group?
9.  List all normal forms.
10. Why is normalization important?

------------------------------------------------------------------------

# Section B --- Functional Dependencies (11--20)

11. Define Functional Dependency.
12. Identify the determinant in `StudentID → StudentName`.
13. What is a dependent attribute?
14. Explain Full Functional Dependency.
15. Explain Partial Functional Dependency.
16. Explain Transitive Dependency.
17. Give one example of each dependency.
18. Differentiate Full and Partial Dependency.
19. Differentiate Partial and Transitive Dependency.
20. Explain why Functional Dependency is the foundation of
    normalization.

------------------------------------------------------------------------

# Section C --- Normal Forms (21--35)

21. Convert a table with repeating groups into 1NF.
22. Identify whether a table is in 1NF.
23. Convert a 1NF table into 2NF.
24. Find partial dependencies.
25. Convert a 2NF table into 3NF.
26. Find transitive dependencies.
27. Explain BCNF with an example.
28. Identify BCNF violations.
29. Explain 4NF.
30. Identify Multivalued Dependencies.
31. Convert a table into 4NF.
32. Explain 5NF.
33. Identify Join Dependencies.
34. Convert a table into 5NF.
35. Compare 1NF, 2NF, 3NF, BCNF, 4NF and 5NF.

------------------------------------------------------------------------

# Section D --- Decomposition (36--42)

36. Define decomposition.
37. Explain lossless decomposition.
38. Explain lossy decomposition.
39. State the condition for a lossless decomposition.
40. Explain dependency preservation.
41. Compare lossless decomposition and dependency preservation.
42. Why are both important?

------------------------------------------------------------------------

# Section E --- Real-World Scenarios (43--50)

43. Normalize a student-course database to 3NF.
44. Normalize an employee-department database.
45. Design a normalized hospital database.
46. Design a normalized banking database.
47. Identify anomalies in an order management system.
48. Explain when BCNF is preferred over 3NF.
49. Explain when denormalization may be useful.
50. Draw the complete normalization flow from UNF to 5NF.

------------------------------------------------------------------------

# Self-Assessment Checklist

After solving all problems, you should be able to:

``` text
✓ Explain normalization

✓ Identify redundancy

✓ Detect anomalies

✓ Find Functional Dependencies

✓ Identify Partial Dependencies

✓ Identify Transitive Dependencies

✓ Explain BCNF

✓ Detect MVD

✓ Detect Join Dependency

✓ Perform Lossless Decomposition

✓ Preserve Dependencies

✓ Normalize databases up to 5NF
```

------------------------------------------------------------------------

# Bonus Challenge

Normalize the following relation completely:

``` text
OrderID
CustomerName
CustomerPhone
Product
Supplier
SupplierPhone
DeliveryAgent
VehicleNumber
```

Tasks:

-   Identify Functional Dependencies.
-   Identify anomalies.
-   Convert to 1NF.
-   Convert to 2NF.
-   Convert to 3NF.
-   Check BCNF.
-   Identify MVD or JD if applicable.
-   Produce the final normalized schema.

------------------------------------------------------------------------

# Practice Tips

-   Solve every question without looking at previous lessons.
-   Draw dependency diagrams before decomposing tables.
-   Always verify:
    -   Lossless Decomposition
    -   Dependency Preservation
-   Compare adjacent normal forms to understand why each exists.

------------------------------------------------------------------------

# Final Takeaway

Normalization is best learned through practice. The more tables you
analyze and decompose, the easier it becomes to recognize redundancy,
dependencies, and anomalies. Completing these 50 problems will build the
confidence needed for exams, interviews, and real-world database design.
