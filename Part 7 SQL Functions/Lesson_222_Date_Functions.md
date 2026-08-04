# Lesson 222 - Date Functions

**Part:** Part 7 - SQL Functions

**Difficulty:** Beginner → Intermediate  
**Interview Frequency:** ⭐⭐⭐⭐⭐  
**Estimated Reading Time:** 30–35 Minutes

---

# Learning Objectives

After this lesson, you will be able to:

- Understand SQL Date and Time functions.
- Perform date calculations efficiently.
- Work with timestamps and intervals.
- Solve real-world business problems using date functions.
- Answer interview questions related to date handling.

---

# 1. Introduction

Date functions are used to manipulate and analyze date and time values.

Almost every production database stores date information such as:

- Customer registration date
- Order date
- Login time
- Transaction timestamp
- Subscription expiry
- Employee joining date

SQL date functions simplify operations on this data.

---

# 2. Why Date Functions Matter

Imagine an online shopping platform.

The business needs to know:

- Orders placed today
- Customers inactive for 90 days
- Products shipped this month
- Membership expiry dates

Without date functions, these calculations would be difficult and inefficient.

---

# 3. Common Date Functions

| Function | Purpose |
|----------|---------|
| CURDATE() | Current date |
| CURRENT_DATE | Current date |
| NOW() | Current date & time |
| CURRENT_TIMESTAMP | Current timestamp |
| DATE() | Extract date |
| YEAR() | Extract year |
| MONTH() | Extract month |
| DAY() | Extract day |
| DATEDIFF() | Difference between dates |
| DATE_ADD() | Add interval |
| DATE_SUB() | Subtract interval |
| EXTRACT() | Extract date component |

---

# 4. Sample Table

```sql
Orders

+----+------------+
|ID  |OrderDate   |
+----+------------+
|1   |2026-07-15  |
|2   |2026-07-18  |
|3   |2026-07-21  |
+----+------------+
```

---

# 5. CURDATE()

```sql
SELECT CURDATE();
```

Example Output

```
2026-07-21
```

Returns the current system date.

---

# 6. NOW()

```sql
SELECT NOW();
```

Example Output

```
2026-07-21 18:45:30
```

Returns both date and time.

---

# 7. YEAR(), MONTH(), DAY()

```sql
SELECT YEAR(OrderDate),
       MONTH(OrderDate),
       DAY(OrderDate)
FROM Orders;
```

Useful for reports grouped by year or month.

---

# 8. DATEDIFF()

```sql
SELECT DATEDIFF('2026-07-21',
                '2026-07-15');
```

Output

```
6
```

Calculates the difference in days.

---

# 9. DATE_ADD()

```sql
SELECT DATE_ADD(CURDATE(),
INTERVAL 30 DAY);
```

Used for subscription renewal and due dates.

---

# 10. DATE_SUB()

```sql
SELECT DATE_SUB(CURDATE(),
INTERVAL 7 DAY);
```

Useful for finding records from the previous week.

---

# 11. EXTRACT()

```sql
SELECT EXTRACT(MONTH FROM OrderDate)
FROM Orders;
```

Extracts a specific component from a date.

---

# 12. Internal Working

```
Read Date Value
       │
Parse Date
       │
Apply Date Function
       │
Calculate Result
       │
Return Date / Number
```

The DBMS stores dates in an internal format, allowing efficient arithmetic without manually handling months or leap years.

---

# 13. Real Project Examples

## Banking

- Loan maturity dates
- Interest calculation periods
- EMI due dates

## Telecom

- Recharge expiry
- Billing cycle generation
- Daily usage reports

## E-Commerce

- Order delivery estimation
- Return window calculation
- Flash sale duration

## Hospital

- Appointment scheduling
- Follow-up reminders
- Patient admission duration

---

# 14. Performance Notes

- Date columns should be indexed when frequently filtered.
- Avoid wrapping indexed date columns with functions inside WHERE clauses.
- Store dates using proper DATE, TIME, or TIMESTAMP data types instead of strings.

---

# 15. Common Mistakes

- Storing dates as VARCHAR.
- Confusing DATE and DATETIME.
- Ignoring time zones.
- Applying functions to indexed columns in WHERE conditions.
- Assuming all DBMS products support identical date syntax.

---

# 16. Interview Questions

## Beginner

1. Difference between CURDATE() and NOW()?
2. What does DATEDIFF() return?
3. Why use DATE_ADD()?

## Intermediate

1. DATE vs DATETIME vs TIMESTAMP?
2. How do you calculate customer age?
3. How would you retrieve records from the last 30 days?

## Advanced

1. Why do date functions sometimes disable index usage?
2. How are timestamps stored internally?
3. How would you optimize date-based reporting queries?

---

# 17. Practice

```sql
SELECT CURDATE();

SELECT NOW();

SELECT DATE_ADD(CURDATE(),INTERVAL 15 DAY);

SELECT DATE_SUB(CURDATE(),INTERVAL 1 MONTH);

SELECT DATEDIFF(CURDATE(),'2026-01-01');

SELECT YEAR(OrderDate),
       MONTH(OrderDate)
FROM Orders;
```

---

# Revision Notes

- Date functions simplify date and time calculations.
- Common functions include CURDATE, NOW, YEAR, MONTH, DAY, DATEDIFF, DATE_ADD, DATE_SUB, and EXTRACT.
- Use proper date data types.
- Avoid unnecessary functions on indexed date columns.

---

# Memory Trick

**CYMDDE**

- C → CURDATE
- Y → YEAR
- M → MONTH
- D → DAY
- D → DATEDIFF
- E → DATE_ADD / DATE_SUB / EXTRACT

---

# Final Takeaway

Date functions are among the most frequently used SQL features in production systems. Whether building banking software, telecom billing platforms, hospital management systems, or e-commerce applications, working with dates is unavoidable. Interviewers often ask scenario-based questions involving date calculations, making this topic essential for both conceptual understanding and practical SQL development.
