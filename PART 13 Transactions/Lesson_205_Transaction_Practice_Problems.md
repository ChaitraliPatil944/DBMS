# Lesson 205 --- Transaction Practice Problems

> **Part 13 --- Transactions**

------------------------------------------------------------------------

# Learning Objectives

By completing these exercises, you will:

-   Strengthen your understanding of transactions
-   Apply ACID properties to real scenarios
-   Analyze transaction states
-   Practice recovery concepts
-   Prepare for exams and technical interviews

------------------------------------------------------------------------

# Section A --- Basics (1--10)

1.  Define a transaction.
2.  Why are transactions required?
3.  List the four basic transaction operations.
4.  What is COMMIT?
5.  What is ROLLBACK?
6.  What is SAVEPOINT?
7.  Give two real-world examples of transactions.
8.  Why should transactions be short?
9.  What problems occur without transactions?
10. Explain the transaction lifecycle.

------------------------------------------------------------------------

# Section B --- ACID Properties (11--20)

11. Expand ACID.
12. Explain Atomicity.
13. Explain Consistency.
14. Explain Isolation.
15. Explain Durability.
16. Compare Atomicity and Durability.
17. Compare Consistency and Isolation.
18. Which ACID property prevents partial updates?
19. Which property ensures permanent changes?
20. Explain ACID using a banking example.

------------------------------------------------------------------------

# Section C --- Transaction States (21--30)

21. List all transaction states.
22. Explain the Active state.
23. Explain the Partially Committed state.
24. Explain the Committed state.
25. Explain the Failed state.
26. Explain the Aborted state.
27. Explain the Terminated state.
28. Draw the transaction state diagram.
29. Compare Failed and Aborted.
30. Compare Partially Committed and Committed.

------------------------------------------------------------------------

# Section D --- Recovery (31--40)

31. What is database recovery?
32. Why is recovery necessary?
33. What is a checkpoint?
34. What is a transaction log?
35. Explain Write-Ahead Logging (WAL).
36. What is UNDO?
37. What is REDO?
38. Compare logs and checkpoints.
39. Explain crash recovery using logs.
40. List different types of database failures.

------------------------------------------------------------------------

# Section E --- Scenario-Based Problems (41--50)

41. Design a transaction for fund transfer.
42. Explain recovery after a power failure.
43. Identify the violated ACID property in a partial update.
44. Draw the recovery process after a crash.
45. Explain how checkpoints reduce recovery time.
46. Show when UNDO is required.
47. Show when REDO is required.
48. Explain recovery using logs and checkpoints together.
49. Compare backup and recovery.
50. Design a reliable transaction flow for an online shopping checkout.

------------------------------------------------------------------------

# Self-Assessment Checklist

``` text
✓ Understand Transactions
✓ Explain ACID
✓ Draw Transaction States
✓ Explain Checkpoints
✓ Explain Logs
✓ Understand WAL
✓ Differentiate UNDO and REDO
✓ Explain Recovery
✓ Solve Scenario Questions
```

------------------------------------------------------------------------

# Bonus Challenge

A banking application crashes after deducting money from one account but
before adding it to another.

Tasks:

-   Identify the transaction state.
-   Identify the violated ACID property.
-   Explain recovery using WAL.
-   Explain whether UNDO or REDO is required.
-   Draw the complete recovery flow.

------------------------------------------------------------------------

# Practice Tips

-   Draw diagrams whenever possible.
-   Use banking examples to explain concepts.
-   Practice ACID scenarios.
-   Distinguish COMMIT, ROLLBACK, UNDO and REDO clearly.

------------------------------------------------------------------------

# Final Takeaway

Transaction management is best understood through practical scenarios.
Solving these problems will help you master transaction processing, ACID
properties, recovery techniques, and crash handling, making you well
prepared for university exams, placement tests, and technical
interviews.
