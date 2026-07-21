# Lesson 221 - Numeric Functions

**Part:** Part 7 - SQL Functions

**Difficulty:** Beginner → Intermediate  
**Interview Frequency:** ⭐⭐⭐⭐☆  
**Estimated Reading Time:** 25–30 Minutes

---

# Learning Objectives

After this lesson, you will be able to:

- Understand SQL Numeric Functions.
- Perform mathematical calculations inside SQL queries.
- Differentiate between common numeric functions.
- Use numeric functions in real-world projects.
- Answer interview questions confidently.

---

# 1. Introduction

Numeric functions operate on numeric data types such as INT, FLOAT, DECIMAL, and DOUBLE.

They are used for:

- Financial calculations
- Data analysis
- Billing systems
- Reports
- Scientific calculations

Unlike aggregate functions, numeric functions operate on **individual values** and return **one value per row**.

---

# 2. Why Numeric Functions Matter

Imagine an e-commerce application.

The application needs to:

- Round invoice totals
- Calculate discounts
- Find absolute profit/loss
- Generate random coupon numbers

Numeric functions make these tasks simple and efficient.

---

# 3. Common Numeric Functions

| Function | Purpose |
|----------|---------|
| ABS() | Absolute value |
| ROUND() | Round to specified decimals |
| CEIL()/CEILING() | Round upward |
| FLOOR() | Round downward |
| MOD() | Remainder |
| POWER() | Raise to a power |
| SQRT() | Square root |
| RAND() | Random number |

---

# 4. Sample Table

```sql
Product

+----+--------+
|ID  |Price   |
+----+--------+
|1   |99.75   |
|2   |150.40  |
|3   |-75.20  |
+----+--------+
```

---

# 5. ABS()

```sql
SELECT ABS(-75.20);
```

Output

```
75.20
```

Useful for calculating distance, variance, or profit/loss.

---

# 6. ROUND()

```sql
SELECT ROUND(99.756,2);
```

Output

```
99.76
```

---

# 7. CEIL() / CEILING()

```sql
SELECT CEIL(99.10);
```

Output

```
100
```

Always rounds upward.

---

# 8. FLOOR()

```sql
SELECT FLOOR(99.90);
```

Output

```
99
```

Always rounds downward.

---

# 9. MOD()

```sql
SELECT MOD(15,4);
```

Output

```
3
```

Useful for even/odd checks and cyclic operations.

---

# 10. POWER() and SQRT()

```sql
SELECT POWER(5,2);

SELECT SQRT(64);
```

Results

```
25
8
```

---

# 11. RAND()

```sql
SELECT RAND();
```

Returns a pseudo-random decimal value between 0 and 1.

---

# 12. Internal Working

```
Input Number
      │
Read Numeric Value
      │
Apply Mathematical Function
      │
Generate Result
      │
Return Value
```

Numeric functions do not change stored values unless used inside UPDATE statements.

---

# 13. Real Project Examples

## Banking

- Interest calculations
- EMI computation
- Currency rounding

## Telecom

- Recharge calculations
- Data usage billing

## E-Commerce

- Product discounts
- Tax computation
- Invoice generation

## Hospital

- Medicine dosage calculations
- Billing adjustments

---

# 14. Performance Notes

- Numeric functions are generally inexpensive.
- Applying functions to indexed columns inside WHERE clauses can prevent index usage.
- Use DECIMAL for financial calculations to avoid floating-point inaccuracies.

---

# 15. Common Mistakes

- Using FLOAT for currency values.
- Confusing CEIL() with ROUND().
- Ignoring precision and scale.
- Expecting RAND() to generate the same value every execution.

---

# 16. Interview Questions

## Beginner

1. What are numeric functions?
2. Difference between FLOOR() and CEIL()?
3. What does ABS() return?

## Intermediate

1. ROUND() vs TRUNCATE()?
2. Why is DECIMAL preferred over FLOAT for money?
3. Explain MOD() with examples.

## Advanced

1. How do numeric functions affect indexes?
2. Why shouldn't FLOAT be used in banking systems?
3. How are precision and scale stored internally?

---

# 17. Practice

```sql
SELECT ROUND(125.678,2);

SELECT ABS(-250);

SELECT FLOOR(45.98);

SELECT CEIL(45.02);

SELECT MOD(28,5);

SELECT POWER(3,4);

SELECT SQRT(144);
```

---

# Revision Notes

- Numeric functions work on individual numeric values.
- Frequently used: ABS, ROUND, CEIL, FLOOR, MOD, POWER, SQRT, RAND.
- Use DECIMAL for financial applications.
- Avoid functions on indexed columns in filtering conditions.

---

# Memory Trick

**ARCMPSR**

- A → ABS
- R → ROUND
- C → CEIL
- M → MOD
- P → POWER
- S → SQRT
- R → RAND

---

# Final Takeaway

Numeric functions are essential for calculations in SQL. They appear in billing, banking, analytics, and reporting systems. Interviewers often combine them with SQL queries to evaluate both syntax knowledge and problem-solving skills, so understanding when and why to use each function is as important as remembering its syntax.
