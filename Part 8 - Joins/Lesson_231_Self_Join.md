# Lesson 231 - SELF JOIN

**Part:** Part 8 - Joins

**Difficulty:** Intermediate  
**Interview Frequency:** ⭐⭐⭐⭐⭐  
**Estimated Reading Time:** 40–50 Minutes

---

# Learning Objectives

After completing this lesson, you will be able to:

- Understand the concept of a SELF JOIN.
- Learn why aliases are required.
- Solve hierarchical data problems.
- Explain how a DBMS processes SELF JOIN.
- Apply SELF JOIN in real-world scenarios.
- Answer interview questions confidently.

---

# 1. Introduction

A **SELF JOIN** is a join in which a table is joined with **itself**.

Although only one table exists, SQL treats it as two logical tables by using **aliases**.

There is no separate `SELF JOIN` keyword.

---

# 2. Why SELF JOIN?

Many databases store hierarchical relationships in the same table.

Examples:

- Employee → Manager
- Student → Mentor
- Product → Parent Product
- Category → Parent Category

A SELF JOIN connects related rows within the same table.

---

# 3. Sample Table

### Employee

```text
+------------+--------+-----------+
|EmployeeID  |Name    |ManagerID  |
+------------+--------+-----------+
|1           |Alice   |NULL       |
|2           |Bob     |1          |
|3           |Carol   |1          |
|4           |David   |2          |
+------------+--------+-----------+
```

---

# 4. Syntax

```sql
SELECT e.Name AS Employee,
       m.Name AS Manager
FROM Employee e
LEFT JOIN Employee m
ON e.ManagerID = m.EmployeeID;
```

Aliases:

- `e` → Employee
- `m` → Manager

---

# 5. Result

```text
+----------+---------+
|Employee  |Manager  |
+----------+---------+
|Alice     |NULL     |
|Bob       |Alice    |
|Carol     |Alice    |
|David     |Bob      |
+----------+---------+
```

---

# 6. Internal Working

```text
Employee Table
      │
Logical Copy Using Alias
      │
Compare ManagerID
      │
Match EmployeeID
      │
Return Related Rows
```

The DBMS does **not** duplicate the table physically. Aliases create separate logical references during query execution.

---

# 7. Real-World Examples

## Corporate HR

Employee → Manager hierarchy.

## Banking

Branch → Parent Branch.

## Telecom

Distributor → Master Distributor.

## E-Commerce

Category → Parent Category.

---

# 8. Performance Notes

- Index the parent key (`ManagerID`).
- Use LEFT JOIN to include top-level records.
- Avoid unnecessary repeated SELF JOINs on very large tables.
- Recursive hierarchies are often better handled with Recursive CTEs (where supported).

---

# 9. Common Mistakes

- Forgetting aliases.
- Joining on the wrong columns.
- Using INNER JOIN when root records must also appear.
- Creating circular relationships in the data.

---

# 10. SELF JOIN vs INNER JOIN

| Feature | INNER JOIN | SELF JOIN |
|---------|------------|-----------|
|Tables involved|Two different tables|Same table twice|
|Needs aliases|Optional|Required|
|Typical use|Related entities|Hierarchical data|

---

# 11. Interview Questions

## Beginner

1. What is a SELF JOIN?
2. Why are aliases required?
3. Is SELF JOIN a separate SQL keyword?

## Intermediate

1. Explain employee-manager relationships using SELF JOIN.
2. INNER SELF JOIN vs LEFT SELF JOIN?
3. When should SELF JOIN be used?

## Advanced

1. How does the optimizer process a SELF JOIN?
2. When should Recursive CTEs replace SELF JOIN?
3. What indexes improve SELF JOIN performance?

---

# 12. Practice

```sql
-- Employee and Manager
SELECT e.Name,
       m.Name AS Manager
FROM Employee e
LEFT JOIN Employee m
ON e.ManagerID = m.EmployeeID;

-- Category hierarchy
SELECT c.CategoryName,
       p.CategoryName AS ParentCategory
FROM Category c
LEFT JOIN Category p
ON c.ParentCategoryID = p.CategoryID;
```

---

# Revision Notes

- SELF JOIN joins a table with itself.
- Aliases distinguish logical copies.
- Commonly used for hierarchical relationships.
- No dedicated SELF JOIN keyword exists.

---

# Memory Trick

**SELF JOIN = Same Table, Two Roles**

One table acts as both parent and child.

---

# Final Takeaway

SELF JOIN is a powerful technique for querying hierarchical and recursive relationships stored within a single table. While the table is referenced twice, the database uses aliases rather than creating physical copies. In interviews, SELF JOIN questions almost always involve employee-manager or category-parent hierarchies, making this pattern essential to master.
