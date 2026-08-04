# Lesson 228 - RIGHT JOIN

**Part:** Part 8 - Joins

**Difficulty:** Beginner → Advanced  
**Interview Frequency:** ⭐⭐⭐⭐☆  
**Estimated Reading Time:** 40–50 Minutes

---

# Learning Objectives

After completing this lesson, you will be able to:

- Understand the purpose of RIGHT JOIN.
- Differentiate RIGHT JOIN from INNER JOIN and LEFT JOIN.
- Explain how RIGHT JOIN works internally.
- Identify real-world use cases.
- Solve interview-oriented SQL problems involving RIGHT JOIN.

---

# 1. Introduction

A **RIGHT JOIN** returns:

- All rows from the **right table**
- Matching rows from the **left table**
- NULL values for columns from the left table when no match exists.

It is the mirror image of a LEFT JOIN.

---

# 2. Why RIGHT JOIN?

Suppose an online learning platform wants to display **every available course**, even if no student has enrolled.

The Courses table becomes the right table.

RIGHT JOIN ensures every course appears.

---

# 3. Real-World Analogy

Imagine a university.

One register contains students.

Another register contains all available subjects.

The administration wants a report containing **every subject**, even if nobody has registered.

Subjects without students still appear.

---

# 4. Sample Tables

### Students

```text
+-----------+---------+
|StudentID  |Name     |
+-----------+---------+
|1          |Amit     |
|2          |Neha     |
+-----------+---------+
```

### Courses

```text
+----------+--------------+
|CourseID  |CourseName    |
+----------+--------------+
|101       |DBMS          |
|102       |OS            |
|103       |Networks      |
+----------+--------------+
```

### Enrollments

```text
+-----------+----------+
|StudentID  |CourseID  |
+-----------+----------+
|1          |101       |
|2          |102       |
+-----------+----------+
```

---

# 5. Syntax

```sql
SELECT s.Name,
       c.CourseName
FROM Students s
RIGHT JOIN Enrollments e
ON s.StudentID = e.StudentID
RIGHT JOIN Courses c
ON e.CourseID = c.CourseID;
```

---

# 6. Result

```text
+---------+--------------+
|Name     |CourseName    |
+---------+--------------+
|Amit     |DBMS          |
|Neha     |OS            |
|NULL     |Networks      |
+---------+--------------+
```

The Networks course appears even though no student is enrolled.

---

# 7. Internal Working

```text
Read Left Table
      │
Read Right Table
      │
Compare Join Keys
      │
Return Matches
      │
If No Match
      │
Fill Left Columns with NULL
      │
Return Every Right Row
```

---

# 8. Visual Representation

```text
Students
     │
     ├── Match ─────────► Return Data
     │
     └──────────────┐
                    ▼
Courses (All Rows Returned)
```

---

# 9. RIGHT JOIN vs LEFT JOIN

These two queries are logically equivalent.

RIGHT JOIN

```sql
SELECT *
FROM A
RIGHT JOIN B
ON A.ID = B.ID;
```

Equivalent LEFT JOIN

```sql
SELECT *
FROM B
LEFT JOIN A
ON B.ID = A.ID;
```

For readability, many developers prefer LEFT JOIN.

---

# 10. Real Project Examples

## Banking

Display all bank branches, including those without customers.

## Telecom

Display all mobile plans, including plans with no subscribers.

## E-Commerce

Display every product category, even if no products exist.

## Hospital

Display every department, even if no doctors are assigned.

---

# 11. Performance Notes

- Performance is generally similar to LEFT JOIN.
- Index join columns.
- Match data types on join keys.
- Choose LEFT JOIN instead when it improves readability.

---

# 12. Common Mistakes

- Confusing RIGHT JOIN with LEFT JOIN.
- Forgetting which table is preserved.
- Assuming RIGHT JOIN is faster than LEFT JOIN.
- Joining on unrelated columns.

---

# 13. Interview Questions

## Beginner

1. What is RIGHT JOIN?
2. Which table is always preserved?
3. Difference between RIGHT JOIN and INNER JOIN?

## Intermediate

1. Can RIGHT JOIN be rewritten as LEFT JOIN?
2. When should RIGHT JOIN be used?
3. Why do NULL values appear?

## Advanced

1. Does RIGHT JOIN offer any performance advantage?
2. Why do many SQL developers avoid RIGHT JOIN?
3. How does the optimizer process RIGHT JOIN internally?
4. How do indexes affect RIGHT JOIN?

---

# 14. Practice

```sql
-- Courses without students
SELECT c.CourseName
FROM Students s
RIGHT JOIN Enrollments e
ON s.StudentID=e.StudentID
RIGHT JOIN Courses c
ON e.CourseID=c.CourseID
WHERE s.StudentID IS NULL;

-- Departments without employees
SELECT d.DepartmentName
FROM Employee e
RIGHT JOIN Department d
ON e.DepartmentID=d.DepartmentID;

-- Categories without products
SELECT c.CategoryName
FROM Product p
RIGHT JOIN Category c
ON p.CategoryID=c.CategoryID;
```

---

# Revision Notes

- RIGHT JOIN returns every row from the right table.
- Missing matches produce NULL values in left-table columns.
- It is functionally equivalent to reversing the tables in a LEFT JOIN.
- Most production SQL code favors LEFT JOIN for readability.

---

# Memory Trick

**RIGHT = Retain Right Table**

Always remember: every row from the right table survives.

---

# Final Takeaway

RIGHT JOIN behaves exactly like a LEFT JOIN with the table order reversed. Although it is less commonly used in production code, understanding it is important because interviewers often ask candidates to convert RIGHT JOIN queries into equivalent LEFT JOIN queries. Mastering both joins helps build a strong understanding of relational query processing.
