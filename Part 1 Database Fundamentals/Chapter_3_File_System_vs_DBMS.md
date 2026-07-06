
# Chapter 3 – File System vs DBMS

## Learning Objectives
- Understand traditional file systems.
- Identify limitations of file systems.
- Explain why DBMS was introduced.
- Compare File System and DBMS for interviews.

---

# 1. Introduction

Before DBMS, organizations stored data in separate files. As data grew, managing these files became difficult, leading to the development of Database Management Systems (DBMS).

---

# 2. What is a File System?

A file system stores data in individual files managed by the operating system.

Example:
- students.txt
- employees.csv
- salary.xlsx

Each application often maintains its own files.

### Advantages
- Simple to use
- Low cost
- Suitable for small applications

### Disadvantages
- Data redundancy
- Data inconsistency
- Poor security
- Difficult backup and recovery
- Limited data sharing
- No concurrency control

---

# 3. Problems with File Systems

## Data Redundancy
The same data is stored in multiple files.

## Data Inconsistency
Updating one file but not another causes conflicting information.

## Data Isolation
Data is scattered across different files and formats.

## Security Issues
Limited access control makes sensitive data vulnerable.

## Concurrent Access Problems
Multiple users editing the same file may overwrite each other's changes.

## Backup & Recovery
Recovering lost or corrupted files is difficult.

---

# 4. What is DBMS?

A DBMS is software that stores, manages, retrieves, secures, and controls access to data in a centralized database.

Examples:
- MySQL
- PostgreSQL
- Oracle Database
- Microsoft SQL Server

---

# 5. Why DBMS is Better

- Centralized storage
- Reduced redundancy
- Better consistency
- Security and authorization
- Concurrent access
- Backup and recovery
- Data independence
- Powerful querying using SQL

---

# 6. File System vs DBMS

| Feature | File System | DBMS |
|---|---|---|
| Data Storage | Separate files | Centralized database |
| Redundancy | High | Low |
| Consistency | Difficult | Maintained |
| Security | Basic | Advanced |
| Multi-user Support | Limited | Excellent |
| Backup | Manual | Built-in support |
| Query Language | Not available | SQL |
| Relationships | Difficult | Easy using keys |
| Scalability | Low | High |

---

# 7. Real-World Example

## College Without DBMS
Admissions, library, exams, and fees each keep separate files. Student details are duplicated, leading to inconsistent records.

## College With DBMS
All departments access a single database. Updates are reflected everywhere instantly.

---

# 8. Interview Questions

1. What is a file system?
2. Why was DBMS introduced?
3. Explain data redundancy.
4. Differentiate file system and DBMS.
5. What problems does DBMS solve?

---

# 9. MCQs

**1. Which has higher redundancy?**
- A. DBMS
- **B. File System**
- C. Both
- D. Neither

**2. Which uses SQL?**
- A. File System
- **B. DBMS**
- C. Both
- D. None

---

# 10. Practice Exercises

1. Compare file systems and DBMS with five examples.
2. Explain data inconsistency using a banking example.
3. List five advantages of DBMS over file systems.
4. Draw a comparison table from memory.

---

# 11. Memory Trick

**R-S-C-B**
- **R** = Redundancy reduced
- **S** = Security improved
- **C** = Consistency maintained
- **B** = Backup & Recovery

---

# 12. Chapter Summary

- File systems are suitable for simple data storage but struggle with large, shared applications.
- DBMS overcomes redundancy, inconsistency, and security issues.
- Modern software systems rely on DBMS because it supports efficient, secure, and scalable data management.
