# 📘 Oracle VIEW – Database SQL Lesson

## 🎯 Lesson Objectives
By the end of this lesson, students will be able to:
- Explain what a VIEW is in Oracle
- Understand why and when to use a VIEW
- Create, query, update, and drop a VIEW
- Distinguish between simple and complex views
- Apply VIEWs for security and abstraction

---

## 1️⃣ What is a VIEW?
A **VIEW** in Oracle is a **virtual table** created from a SQL `SELECT` statement.

- A VIEW does **not store data**
- It stores **only the SQL query**
- Data is fetched from base tables when the VIEW is queried

**Simple definition:**  
> A VIEW is a saved SELECT query that behaves like a table.

---

## 2️⃣ Why Use VIEWs?

### ✅ Advantages
- Security (hide sensitive columns)
- Simplifies complex queries
- Reusability
- Logical abstraction
- Cleaner and readable SQL

### ❌ Disadvantages
- Performance cost for complex views
- Not all views are updatable

---

## 3️⃣ CREATE VIEW Syntax

```sql
CREATE VIEW view_name AS
SELECT column1, column2
FROM table_name
WHERE condition;
```

### Example
```sql
CREATE VIEW emp_basic AS
SELECT employee_id, first_name, salary
FROM employees;
```

Querying the VIEW:
```sql
SELECT * FROM emp_basic;
```

---

## 4️⃣ Types of VIEWs

### 🔹 Simple VIEW
- Based on one table
- No GROUP BY, JOIN, or functions
- Can allow INSERT, UPDATE, DELETE

```sql
CREATE VIEW emp_sales AS
SELECT employee_id, first_name, department_id
FROM employees
WHERE department_id = 80;
```

---

### 🔹 Complex VIEW
- Uses JOIN, GROUP BY, or functions
- Usually read-only

```sql
CREATE VIEW dept_salary_summary AS
SELECT department_id, AVG(salary) AS avg_salary
FROM employees
GROUP BY department_id;
```

---

## 5️⃣ Updating Data Through a VIEW

### ✔ Allowed (Simple VIEW)
```sql
UPDATE emp_sales
SET salary = 6000
WHERE employee_id = 101;
```

### ❌ Not Allowed (Complex VIEW)
```sql
UPDATE dept_salary_summary
SET avg_salary = 7000;
-- ERROR
```

---

## 6️⃣ VIEW WITH CHECK OPTION

```sql
CREATE VIEW emp_hr AS
SELECT employee_id, first_name, department_id
FROM employees
WHERE department_id = 40
WITH CHECK OPTION;
```

---

## 7️⃣ VIEW for Security

```sql
CREATE VIEW emp_public AS
SELECT employee_id, first_name
FROM employees;
```

```sql
GRANT SELECT ON emp_public TO user1;
```

---

## 8️⃣ DROP VIEW

```sql
DROP VIEW emp_public;
```

---

## 9️⃣ VIEW vs TABLE

| Feature | TABLE | VIEW |
|------|------|------|
| Stores data | Yes | No |
| Physical storage | Yes | No |
| Based on query | No | Yes |
| Supports JOIN | No | Yes |
| Used for security | Limited | Yes |

---

## 🧪 Practice Exercises

### Exercise 1
Create a VIEW that shows employees with job_id = 'IT_PROG'

### Exercise 2
Create a VIEW showing total salary per department

### Exercise 3
Explain why this VIEW is not updatable:
```sql
CREATE VIEW v1 AS
SELECT department_id, COUNT(*)
FROM employees
GROUP BY department_id;
```
