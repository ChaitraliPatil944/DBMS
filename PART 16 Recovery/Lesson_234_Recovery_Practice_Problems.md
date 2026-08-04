# Lesson 234 --- Recovery Practice Problems

> **Part 16 --- Recovery**

------------------------------------------------------------------------

# Learning Objectives

By completing these exercises, you will:

-   Strengthen your understanding of database recovery
-   Apply UNDO and REDO concepts
-   Analyze recovery algorithms
-   Practice crash recovery scenarios
-   Prepare for university exams and technical interviews

------------------------------------------------------------------------

# Section A --- Recovery Fundamentals (1--10)

1.  Define database recovery.
2.  Why is recovery necessary?
3.  Explain the objectives of recovery.
4.  List the major types of database failures.
5.  Differentiate transaction, system, and media failures.
6.  Explain the role of the Recovery Manager.
7.  Why are transaction logs important?
8.  How does recovery support ACID properties?
9.  Explain database consistency after failures.
10. Draw the basic recovery workflow.

------------------------------------------------------------------------

# Section B --- UNDO & REDO (11--20)

11. Define UNDO recovery.
12. Define REDO recovery.
13. Compare UNDO and REDO.
14. Which ACID property does UNDO support?
15. Which ACID property does REDO support?
16. Explain UNDO using a transaction log.
17. Explain REDO using a transaction log.
18. Compare Immediate Update and Deferred Update.
19. When are both UNDO and REDO required?
20. Solve a banking recovery example.

------------------------------------------------------------------------

# Section C --- Recovery Techniques (21--30)

21. What is Shadow Paging?
22. Explain the Shadow Paging workflow.
23. Compare Shadow Paging and Log-Based Recovery.
24. Define Write-Ahead Logging (WAL).
25. Why must logs be written before database pages?
26. Explain Deferred Update.
27. Explain Immediate Update.
28. Explain the role of checkpoints.
29. Why do checkpoints reduce recovery time?
30. Draw the WAL workflow.

------------------------------------------------------------------------

# Section D --- ARIES & Crash Recovery (31--40)

31. What does ARIES stand for?
32. Explain the Analysis phase.
33. Explain the REDO phase.
34. Explain the UNDO phase.
35. What are Compensation Log Records (CLRs)?
36. Explain crash recovery using ARIES.
37. Draw the ARIES workflow.
38. Compare ARIES and basic log-based recovery.
39. Explain how checkpoints help ARIES.
40. Why is ARIES widely used?

------------------------------------------------------------------------

# Section E --- Scenario-Based Problems (41--50)

41. A transaction fails before COMMIT. Which recovery action is
    required?
42. A transaction commits but data is not written to disk before a
    crash. What happens?
43. Design a recovery strategy for an online banking system.
44. Explain how WAL prevents inconsistency.
45. Identify whether UNDO or REDO is needed in a given log.
46. Compare log-based recovery and shadow paging for a large enterprise
    database.
47. Explain recovery after a power failure.
48. Explain recovery after a disk crash.
49. Design a checkpoint strategy for a busy database.
50. Explain why recovery is essential for enterprise systems.

------------------------------------------------------------------------

# Self-Assessment Checklist

``` text
✓ Recovery Basics
✓ Transaction Logs
✓ Write-Ahead Logging (WAL)
✓ UNDO
✓ REDO
✓ Immediate Update
✓ Deferred Update
✓ Shadow Paging
✓ Log-Based Recovery
✓ ARIES
✓ Checkpoints
✓ Crash Recovery
```

------------------------------------------------------------------------

# Bonus Challenge

A database log contains:

``` text
START T1
UPDATE A (100 → 80)

START T2
UPDATE B (500 → 450)

COMMIT T1

CRASH
```

Tasks:

-   Identify committed and uncommitted transactions.
-   Decide which transactions require UNDO.
-   Decide which transactions require REDO.
-   Explain the recovery sequence.
-   Draw the recovery workflow.

------------------------------------------------------------------------

# Practice Tips

-   Always identify COMMIT records first.
-   Distinguish committed and incomplete transactions.
-   Remember: UNDO restores old values, REDO restores new values.
-   Use checkpoints to shorten recovery analysis.
-   Draw workflows to reinforce concepts.

------------------------------------------------------------------------

# Final Takeaway

Recovery is best understood through repeated problem solving. Practicing
transaction logs, WAL, UNDO, REDO, Shadow Paging, Log-Based Recovery,
ARIES, and crash recovery scenarios builds the skills needed for DBMS
examinations, placement interviews, and real-world database
administration.
