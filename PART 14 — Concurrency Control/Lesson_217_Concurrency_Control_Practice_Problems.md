# Lesson 217 --- Concurrency Control Practice Problems

> **Part 14 --- Concurrency Control**

------------------------------------------------------------------------

# Learning Objectives

By completing these exercises, you will:

-   Strengthen your understanding of concurrency control
-   Apply locking and timestamp protocols
-   Analyze deadlocks and starvation
-   Practice MVCC and 2PL concepts
-   Prepare for exams and technical interviews

------------------------------------------------------------------------

# Section A --- Fundamentals (1--10)

1.  Define concurrency control.
2.  Why is concurrency control necessary?
3.  List the goals of concurrency control.
4.  Explain concurrent transactions.
5.  What problems occur without concurrency control?
6.  Define isolation.
7.  Explain a lost update.
8.  What is a dirty read?
9.  What is a non-repeatable read?
10. What is a phantom read?

------------------------------------------------------------------------

# Section B --- Locking (11--20)

11. Define locking.
12. Differentiate Shared Lock and Exclusive Lock.
13. Draw a lock compatibility matrix.
14. Explain lock granularity.
15. What is lock conversion?
16. Explain lock upgrade.
17. Explain lock downgrade.
18. Draw the locking workflow.
19. Why can locking reduce concurrency?
20. List advantages of locking.

------------------------------------------------------------------------

# Section C --- Deadlock & Starvation (21--30)

21. Define deadlock.
22. Explain the four deadlock conditions.
23. Draw a Wait-For Graph.
24. Explain deadlock detection.
25. Explain deadlock prevention.
26. Explain deadlock avoidance.
27. Explain deadlock recovery.
28. Define starvation.
29. Compare starvation and deadlock.
30. Explain the aging algorithm.

------------------------------------------------------------------------

# Section D --- Timestamp Protocol (31--40)

31. What is a timestamp?
32. Explain Timestamp Ordering Protocol.
33. Define RTS.
34. Define WTS.
35. Explain the read rule.
36. Explain the write rule.
37. Compare Basic and Strict Timestamp Ordering.
38. Compare locking and timestamp ordering.
39. Why are deadlocks impossible in timestamp ordering?
40. Solve a timestamp ordering example.

------------------------------------------------------------------------

# Section E --- Advanced Concurrency (41--50)

41. Explain Optimistic Locking.
42. Explain Pessimistic Locking.
43. Compare Optimistic and Pessimistic Locking.
44. Explain Two-Phase Locking (2PL).
45. List the phases of 2PL.
46. Compare Basic, Strict, Rigorous and Conservative 2PL.
47. Explain MVCC.
48. Explain Snapshot Isolation.
49. Compare MVCC and traditional locking.
50. Design a concurrency strategy for an online banking system.

------------------------------------------------------------------------

# Self-Assessment Checklist

``` text
✓ Concurrency Control
✓ Locking
✓ Shared & Exclusive Locks
✓ Deadlock
✓ Starvation
✓ Timestamp Protocol
✓ Optimistic Locking
✓ Pessimistic Locking
✓ Two-Phase Locking
✓ MVCC
```

------------------------------------------------------------------------

# Bonus Challenge

A banking application supports thousands of users.

Tasks:

-   Identify possible concurrency problems.
-   Choose a suitable locking strategy.
-   Explain how deadlocks can be prevented.
-   Suggest whether MVCC should be used.
-   Draw the complete transaction workflow.

------------------------------------------------------------------------

# Practice Tips

-   Draw diagrams wherever possible.
-   Compare similar concepts in tables.
-   Solve banking and reservation scenarios.
-   Practice explaining concepts aloud as if in an interview.

------------------------------------------------------------------------

# Final Takeaway

Concurrency control is best learned through problem solving. These
exercises reinforce locking, deadlocks, starvation, timestamp ordering,
2PL, optimistic and pessimistic locking, and MVCC, helping you build
confidence for university exams, coding assessments, and technical
interviews.
