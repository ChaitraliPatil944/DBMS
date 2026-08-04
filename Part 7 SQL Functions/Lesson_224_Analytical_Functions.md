# Lesson 224 - Analytical Functions

**Part:** Part 7 - SQL Functions

**Difficulty:** Intermediate → Advanced  
**Interview Frequency:** ⭐⭐⭐⭐⭐  
**Estimated Reading Time:** 35–45 Minutes

---

# Learning Objectives

After completing this lesson, you will be able to:

- Understand Analytical Functions and their purpose.
- Differentiate Analytical Functions from Aggregate Functions.
- Differentiate Analytical Functions from Window Functions.
- Use ranking and statistical analytical functions.
- Apply analytical functions in business scenarios.
- Answer interview questions confidently.

---

# 1. Introduction

Analytical Functions perform calculations across a group of rows while **preserving every row** in the result set.

They are primarily used for:

- Business Intelligence
- Data Analytics
- Financial Reporting
- Dashboards
- Trend Analysis

Most analytical functions are implemented using the **OVER()** clause.

---

# 2. Aggregate vs Window vs Analytical Functions

| Feature | Aggregate | Window | Analytical |
|---------|-----------|---------|------------|
|Returns one row per group|✔|✖|✖|
|Keeps original rows|✖|✔|✔|
|Uses OVER()|✖|✔|✔|
|Used in analytics|Limited|High|Very High|

Think of analytical functions as specialized window functions designed for reporting and analysis.

---

# 3. Why Analytical Functions?

Consider a telecom company.

Management wants to know:

- Top 5 customers by recharge amount.
- Percentage contribution of each customer.
- Previous month's recharge.
- Monthly growth.

These are difficult using only GROUP BY but straightforward with analytical functions.

---

# 4. Common Analytical Functions

| Function | Purpose |
|----------|---------|
|ROW_NUMBER()|Unique ranking|
|RANK()|Ranking with gaps|
|DENSE_RANK()|Ranking without gaps|
|LAG()|Previous row value|
|LEAD()|Next row value|
|FIRST_VALUE()|First value in window|
|LAST_VALUE()|Last value in window|
|NTILE()|Divide rows into groups|

---

# 5. ROW_NUMBER()

```sql
SELECT Name,
ROW_NUMBER() OVER(ORDER BY Salary DESC)
AS RowNo
FROM Employee;
```

Every row receives a unique sequential number.

---

# 6. RANK()

```sql
SELECT Name,
RANK() OVER(ORDER BY Salary DESC)
FROM Employee;
```

Employees with equal salaries receive the same rank.

The next rank is skipped.

Example

```
1
2
2
4
```

---

# 7. DENSE_RANK()

```sql
SELECT Name,
DENSE_RANK() OVER(ORDER BY Salary DESC)
FROM Employee;
```

Ranks never skip numbers.

Example

```
1
2
2
3
```

---

# 8. LAG() and LEAD()

Previous recharge amount:

```sql
SELECT CustomerID,
RechargeAmount,
LAG(RechargeAmount)
OVER(ORDER BY RechargeDate)
FROM Recharge;
```

Next recharge:

```sql
LEAD(RechargeAmount)
OVER(ORDER BY RechargeDate)
```

Useful for growth and trend analysis.

---

# 9. FIRST_VALUE() and LAST_VALUE()

```sql
FIRST_VALUE(Salary)
OVER(ORDER BY Salary DESC)
```

Returns the first value within the window.

Similarly,

```sql
LAST_VALUE()
```

returns the final value.

---

# 10. NTILE()

```sql
SELECT Name,
NTILE(4)
OVER(ORDER BY Salary DESC)
FROM Employee;
```

Divides employees into four equal groups.

Applications:

- Customer segmentation
- Quartile analysis
- Performance grading

---

# 11. Internal Working

```
Read Rows
    │
Create Window
    │
Partition Data
    │
Sort Rows
    │
Apply Analytical Function
    │
Return Every Row
```

The database never collapses the rows into a single record.

---

# 12. Real Project Examples

## Banking

- Top depositors
- Monthly balance trends
- Fraud analysis

## Telecom

- Highest recharge customers
- Usage trend analysis
- Revenue ranking

## E-Commerce

- Best-selling products
- Customer lifetime value
- Monthly sales growth

## HR

- Salary rankings
- Performance quartiles
- Promotion eligibility

---

# 13. Performance Notes

- Analytical functions require sorting.
- Large partitions increase memory usage.
- Indexes on PARTITION BY and ORDER BY columns improve performance.
- Avoid unnecessary window calculations.

---

# 14. Common Mistakes

- Confusing RANK() with DENSE_RANK().
- Using analytical functions instead of aggregate functions.
- Forgetting OVER().
- Ignoring partitioning requirements.
- Assuming LAST_VALUE() always returns the final table value.

---

# 15. Interview Questions

## Beginner

1. What are analytical functions?
2. Why do they require OVER()?
3. Difference between ROW_NUMBER() and RANK()?

## Intermediate

1. RANK() vs DENSE_RANK()?
2. Explain LAG() and LEAD().
3. When would you use NTILE()?

## Advanced

1. How are analytical functions executed internally?
2. Why are analytical queries expensive?
3. How can indexes optimize analytical queries?
4. Explain a real-world dashboard using analytical functions.

---

# 16. Practice

```sql
SELECT Name,
ROW_NUMBER()
OVER(ORDER BY Salary DESC)
FROM Employee;

SELECT Name,
RANK()
OVER(ORDER BY Salary DESC)
FROM Employee;

SELECT Name,
DENSE_RANK()
OVER(ORDER BY Salary DESC)
FROM Employee;

SELECT Amount,
LAG(Amount)
OVER(ORDER BY OrderDate)
FROM Orders;

SELECT Name,
NTILE(5)
OVER(ORDER BY Salary DESC)
FROM Employee;
```

---

# Revision Notes

- Analytical functions preserve all rows.
- OVER() defines the analysis window.
- Common functions: ROW_NUMBER, RANK, DENSE_RANK, LAG, LEAD, FIRST_VALUE, LAST_VALUE, NTILE.
- Widely used in reporting, dashboards, and business intelligence.

---

# Memory Trick

**RRDLFN**

- R → ROW_NUMBER
- R → RANK
- D → DENSE_RANK
- L → LAG / LEAD
- F → FIRST_VALUE / LAST_VALUE
- N → NTILE

---

# Final Takeaway

Analytical functions are the backbone of modern SQL reporting and analytics. They allow databases to calculate rankings, trends, comparisons, and statistical insights without losing individual rows. Mastering these functions is essential for data engineering, business intelligence, and technical interviews because they demonstrate a deeper understanding of SQL beyond basic querying.
