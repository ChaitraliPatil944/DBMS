# Lesson 237 - ANY and ALL Operators

**Part:** Part 9 - Subqueries

**Difficulty:** Intermediate → Advanced  
**Interview Frequency:** ⭐⭐⭐⭐☆  
**Estimated Reading Time:** 45–55 Minutes

---

# Learning Objectives

After completing this lesson, you will be able to:

- Understand the ANY and ALL operators.
- Learn how they work with subqueries.
- Compare ANY, ALL, IN, and EXISTS.
- Understand DBMS execution.
- Solve interview-oriented SQL problems.

---

# 1. Introduction

The **ANY** and **ALL** operators compare a value against **multiple values returned by a subquery**.

They are always used with comparison operators such as:

- =
- >
- <
- >=
- <=
- <>

Unlike scalar subqueries, the inner query returns multiple rows.

---

# 2. ANY Operator

**ANY** returns TRUE if **at least one** value satisfies the comparison.

General Syntax

```sql
SELECT *
FROM Employee
WHERE Salary > ANY
(
    SELECT Salary
    FROM Employee
    WHERE DepartmentID = 10
);
```

Meaning:

Return employees whose salary is greater than **at least one** salary in Department 10.

---

# 3. ALL Operator

**ALL** returns TRUE only if **every** value satisfies the comparison.

Syntax

```sql
SELECT *
FROM Employee
WHERE Salary > ALL
(
    SELECT Salary
    FROM Employee
    WHERE DepartmentID = 10
);
```

Meaning:

Return employees whose salary is greater than **every** salary in Department 10.

---

# 4. Sample Data

```text
Employee
+----+-------+--------+--------------+
|ID  |Name   |Salary  |DepartmentID  |
+----+-------+--------+--------------+
|1   |Alice  |50000   |10            |
|2   |Bob    |60000   |10            |
|3   |Carol  |75000   |20            |
|4   |David  |90000   |20            |
+----+-------+--------+--------------+
```

Department 10 salaries:

```
50000
60000
```

Examples:

```
75000 > ANY
TRUE

75000 > ALL
TRUE

55000 > ANY
TRUE

55000 > ALL
FALSE
```

---

# 5. Internal Working

```text
Execute Subquery
       │
Return Multiple Values
       │
Compare Outer Value
       │
ANY → One Match?
ALL → Every Match?
       │
Return TRUE/FALSE
```

---

# 6. ANY vs ALL

| Feature | ANY | ALL |
|---------|-----|-----|
|Needs one matching comparison|✔|✖|
|Needs every comparison|✖|✔|
|Returns TRUE easily|✔|Sometimes|
|Usually more restrictive|✖|✔|

---

# 7. ANY vs IN

| ANY | IN |
|-----|----|
|Works with >, <, >=, <=, = | Primarily equality matching |
|General comparison operator|Membership operator|
|Supports numeric comparisons|Checks whether a value exists in a list|

---

# 8. Real Project Examples

## Banking

Find accounts with balances greater than **any** premium account.

Find accounts with balances greater than **all** student accounts.

## Telecom

Subscribers with usage greater than all users of a specific plan.

## E-Commerce

Products priced higher than any discounted product.

Products priced higher than all products in a category.

## Hospital

Doctors earning more than all doctors in another department.

---

# 9. Performance Notes

- Index columns used by the subquery.
- Compare execution plans with MAX() or MIN() alternatives.
- Optimizers may rewrite ANY and ALL into aggregate comparisons.

Example:

```sql
Salary > ALL (...)
```

may be transformed into

```sql
Salary >
(
SELECT MAX(Salary)
...
)
```

---

# 10. Common Mistakes

- Confusing ANY with ALL.
- Using ANY when every comparison is required.
- Forgetting that the subquery may return many rows.
- Ignoring NULL values in comparison results.

---

# 11. Interview Questions

## Beginner

1. What does ANY mean?
2. What does ALL mean?
3. Can ANY work with > and < ?

## Intermediate

1. ANY vs IN?
2. ALL vs MAX()?
3. When should ALL be used?

## Advanced

1. How does the optimizer execute ANY?
2. Can ALL be rewritten using aggregate functions?
3. How do NULL values affect ANY and ALL?

---

# 12. Practice

```sql
-- Employees earning more than any employee in Department 10
SELECT Name,
       Salary
FROM Employee
WHERE Salary > ANY
(
SELECT Salary
FROM Employee
WHERE DepartmentID = 10
);

-- Employees earning more than all employees in Department 10
SELECT Name,
       Salary
FROM Employee
WHERE Salary > ALL
(
SELECT Salary
FROM Employee
WHERE DepartmentID = 10
);

-- Products priced above all products in Category 1
SELECT ProductName
FROM Product
WHERE Price > ALL
(
SELECT Price
FROM Product
WHERE CategoryID = 1
);
```

---

# Revision Notes

- ANY requires one successful comparison.
- ALL requires every comparison to succeed.
- Used with multi-row subqueries.
- Optimizers may rewrite them internally.

---

# Memory Trick

**ANY = One is Enough**

**ALL = Every One Must Pass**

---

# Final Takeaway

The ANY and ALL operators extend the power of SQL by allowing comparisons against multiple values returned by a subquery. ANY succeeds when at least one comparison is true, while ALL requires every comparison to be true. Although they appear less frequently in everyday SQL, they remain popular interview topics because they test a candidate's understanding of multi-row subqueries, comparison logic, and query optimization techniques.
