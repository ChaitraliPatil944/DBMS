# Lesson 220 - String Functions

**Part:** Part 7 - SQL Functions

**Difficulty:** Beginner → Intermediate  
**Interview Frequency:** ⭐⭐⭐⭐⭐  
**Estimated Reading Time:** 25–30 Minutes

---

# Learning Objectives

After completing this lesson, you will be able to:

- Understand SQL String Functions.
- Manipulate text data efficiently.
- Explain how string functions work internally.
- Apply string functions in real-world projects.
- Answer interview questions related to text processing.

---

# 1. Introduction

String functions operate on character data (CHAR, VARCHAR, TEXT) and return either modified text or numeric information about the text.

They are heavily used for:

- Data Cleaning
- Data Validation
- Reporting
- Searching
- Formatting

---

# 2. Why Are String Functions Important?

Real-world databases often contain inconsistent data.

Example:

```
CHAITRALI
chaitrali
 Chaitrali
```

Using string functions, these values can be standardized before analysis.

---

# 3. Common String Functions

| Function | Purpose |
|----------|---------|
| UPPER() | Converts text to uppercase |
| LOWER() | Converts text to lowercase |
| LENGTH() | Returns string length |
| TRIM() | Removes leading/trailing spaces |
| CONCAT() | Joins strings |
| SUBSTRING() | Extracts part of a string |
| REPLACE() | Replaces text |
| LEFT() | Returns left characters |
| RIGHT() | Returns right characters |

---

# 4. Sample Table

```sql
Employee

+----+------------+
|ID  |Name        |
+----+------------+
|1   | Amit       |
|2   | Neha       |
|3   | Raj Kumar  |
+----+------------+
```

---

# 5. UPPER()

```sql
SELECT UPPER(Name)
FROM Employee;
```

Output

```
AMIT
NEHA
RAJ KUMAR
```

---

# 6. LOWER()

```sql
SELECT LOWER(Name)
FROM Employee;
```

Output

```
amit
neha
raj kumar
```

---

# 7. LENGTH()

```sql
SELECT LENGTH(Name)
FROM Employee;
```

Returns the number of characters in each string.

---

# 8. TRIM()

```sql
SELECT TRIM(Name)
FROM Employee;
```

Removes unnecessary leading and trailing spaces.

---

# 9. CONCAT()

```sql
SELECT CONCAT(FirstName,' ',LastName)
FROM Employee;
```

Output

```
Amit Sharma
Neha Patil
```

---

# 10. SUBSTRING()

```sql
SELECT SUBSTRING(Name,1,3)
FROM Employee;
```

Output

```
Ami
Neh
Raj
```

---

# 11. REPLACE()

```sql
SELECT REPLACE(Name,'Raj','Raja')
FROM Employee;
```

Useful for correcting inconsistent values.

---

# 12. LEFT() and RIGHT()

```sql
SELECT LEFT(Name,3),
       RIGHT(Name,3)
FROM Employee;
```

Extracts characters from the beginning or end.

---

# 13. Internal Working

```
Input String
     │
Read Characters
     │
Apply Function
     │
Generate New String
     │
Return Result
```

String functions generally do not modify stored data unless used in UPDATE statements.

---

# 14. Real Project Examples

## Banking

- Format customer names.
- Mask account numbers.

## Telecom

- Extract country codes.
- Standardize customer records.

## E-Commerce

- Search products regardless of case.
- Build full product names.

## Hospital

- Clean patient names before reporting.

---

# 15. Performance Notes

- Functions on indexed columns may prevent index usage.
- Prefer storing cleaned data when possible.
- Avoid unnecessary string manipulation in large queries.

---

# 16. Common Mistakes

- Confusing LENGTH() with number of words.
- Forgetting that SQL string indexing differs across DBMS.
- Using functions in WHERE on indexed columns.
- Ignoring NULL values while concatenating.

---

# 17. Interview Questions

## Beginner

1. What are string functions?
2. Difference between UPPER() and LOWER()?
3. What does TRIM() do?

## Intermediate

1. CONCAT() vs CONCAT_WS()?
2. Difference between LENGTH() and CHAR_LENGTH()?
3. Why can string functions slow queries?

## Advanced

1. How do string functions affect indexes?
2. Why is searching with LOWER(column) slower?
3. How would you optimize text searches?

---

# 18. Practice

```sql
SELECT UPPER(Name) FROM Employee;

SELECT LOWER(Name) FROM Employee;

SELECT CONCAT(FirstName,' ',LastName)
FROM Employee;

SELECT SUBSTRING(Name,2,4)
FROM Employee;

SELECT REPLACE(Name,'A','X')
FROM Employee;
```

---

# Revision Notes

- String functions manipulate text.
- Common functions: UPPER, LOWER, LENGTH, TRIM, CONCAT, SUBSTRING, REPLACE.
- They are widely used for data cleaning and formatting.
- Excessive use on indexed columns can reduce performance.

---

# Memory Trick

**ULTCSR**

- U → UPPER
- L → LOWER / LENGTH
- T → TRIM
- C → CONCAT
- S → SUBSTRING
- R → REPLACE

---

# Final Takeaway

String functions are essential for preparing, validating, and formatting textual data. In interviews, don't stop at syntax—understand when these functions are useful, how they impact query performance, and how they are applied in real production systems.
