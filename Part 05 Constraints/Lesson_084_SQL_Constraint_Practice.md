# Lesson 084 --- SQL Constraint Practice

> **Part 05 --- Constraints**

------------------------------------------------------------------------

# Learning Objectives

Practice writing SQL constraints through progressively difficult
exercises.

You should be able to:

-   Create tables with constraints
-   Modify existing tables
-   Combine multiple constraints
-   Predict SQL execution results
-   Debug common constraint errors

------------------------------------------------------------------------

# SQL Constraint Summary

``` text
PRIMARY KEY  → Unique + NOT NULL

FOREIGN KEY  → Relationship

UNIQUE       → No duplicate values

NOT NULL     → Mandatory value

CHECK        → Business rule

DEFAULT      → Automatic value
```

------------------------------------------------------------------------

# Level 1 --- Basic Practice (1--10)

### 1.

Create a `Student` table with:

-   StudentID (PRIMARY KEY)
-   Name (NOT NULL)
-   Email (UNIQUE)

------------------------------------------------------------------------

### 2.

Create an `Employee` table where:

-   Salary must be greater than 0.

------------------------------------------------------------------------

### 3.

Create a `Product` table where:

-   Quantity defaults to 1.

------------------------------------------------------------------------

### 4.

Create an `Orders` table where:

-   Status defaults to 'Pending'.

------------------------------------------------------------------------

### 5.

Create a `Department` table with DepartmentID as PRIMARY KEY.

------------------------------------------------------------------------

### 6.

Add a NOT NULL constraint to Name using ALTER TABLE.

------------------------------------------------------------------------

### 7.

Add a UNIQUE constraint on Email.

------------------------------------------------------------------------

### 8.

Add a CHECK constraint so Age is between 18 and 60.

------------------------------------------------------------------------

### 9.

Create a `Book` table with ISBN as UNIQUE.

------------------------------------------------------------------------

### 10.

Create a composite PRIMARY KEY using:

``` text
StudentID
CourseID
```

------------------------------------------------------------------------

# Level 2 --- Intermediate (11--25)

11. Create Customer and Orders tables using a FOREIGN KEY.

12. Create Doctor and Appointment tables.

13. Restrict Marks to 0--100.

14. Restrict Semester to 1--8.

15. Restrict Gender to:

``` text
Male
Female
Other
```

16. Restrict OrderStatus to:

``` text
Pending
Packed
Shipped
Delivered
Cancelled
```

17. Create a composite UNIQUE constraint.

18. Use CURRENT_DATE as a DEFAULT.

19. Use CURRENT_TIMESTAMP as a DEFAULT.

20. Make ProductName mandatory.

21. Create an Employee table with Email UNIQUE.

22. Create an Account table with Balance CHECK(Balance\>=0).

23. Create a Library schema with BookID as PRIMARY KEY.

24. Create Enrollment with composite PRIMARY KEY.

25. Add FOREIGN KEY using ALTER TABLE.

------------------------------------------------------------------------

# Level 3 --- Advanced (26--35)

26. Create Customer, Orders and OrderItems with relationships.

27. Design a Hospital schema using constraints.

28. Design a Banking schema.

29. Design an Airline Booking schema.

30. Design a Food Delivery schema.

31. Predict the result of inserting duplicate PRIMARY KEY values.

32. Predict inserting NULL into a NOT NULL column.

33. Predict deleting a parent row using CASCADE.

34. Predict deleting a parent row using RESTRICT.

35. Predict inserting an invalid FOREIGN KEY.

------------------------------------------------------------------------

# Debugging Exercises (36--40)

### 36.

Find the error.

``` sql
CREATE TABLE Student(
StudentID INT PRIMARY KEY,
StudentID INT
);
```

------------------------------------------------------------------------

### 37.

Find the error.

``` sql
Age INT
CHECK(Age<0)
```

------------------------------------------------------------------------

### 38.

Find the error.

``` sql
Email VARCHAR(100)
UNIQUE
UNIQUE
```

------------------------------------------------------------------------

### 39.

Find the error.

``` sql
FOREIGN KEY(DepartmentID)
REFERENCES Department(ID)
```

Assume `ID` is not unique.

------------------------------------------------------------------------

### 40.

Explain why this fails.

``` sql
INSERT INTO Student(StudentID,Name)
VALUES(NULL,'Alice');
```

------------------------------------------------------------------------

# Mini Project

Design a **University Database**.

Include:

-   Student
-   Faculty
-   Course
-   Department
-   Enrollment

Apply:

-   PRIMARY KEY
-   FOREIGN KEY
-   UNIQUE
-   NOT NULL
-   CHECK
-   DEFAULT

------------------------------------------------------------------------

# Interview Challenge

Write SQL for:

-   PRIMARY KEY
-   FOREIGN KEY
-   UNIQUE
-   CHECK
-   DEFAULT
-   NOT NULL

without referring to notes.

------------------------------------------------------------------------

# Self-Evaluation

``` text
□ I can write CREATE TABLE statements.

□ I can use PRIMARY KEY.

□ I can use FOREIGN KEY.

□ I can use UNIQUE.

□ I can use NOT NULL.

□ I can use CHECK.

□ I can use DEFAULT.

□ I can use ALTER TABLE.

□ I can debug constraint errors.

□ I can combine multiple constraints.
```

------------------------------------------------------------------------

# Final Takeaway

Constraints become intuitive only after writing SQL repeatedly. Practice
combining them in realistic schemas rather than memorizing syntax. A
well-designed table almost never relies on a single constraint; it
layers multiple constraints to protect data from different kinds of
mistakes. Fortunately, databases are relentless about enforcing rules
even when humans are having an optimistic day.
