## What is a VIEW?
A **VIEW** in Oracle is a **virtual table** created from a SQL `SELECT` statement.

- A VIEW does **not store data**
- It stores **only the SQL query**
- Data is fetched from base tables when the VIEW is queried

**Simple definition:**  
> A VIEW is a saved SELECT query that behaves like a table.

---

## Why Use VIEWs?

### Advantages
- Security (hide sensitive columns)
- Simplifies complex queries
- Reusability
- Logical abstraction
- Cleaner and readable SQL

### Disadvantages
- Performance cost for complex views
- Not all views are updatable

---

## CREATE VIEW Syntax

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

## Types of VIEWs

### Simple VIEW
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

### Complex VIEW
- Uses JOIN, GROUP BY, or functions
- Usually read-only

```sql
CREATE VIEW dept_salary_summary AS
SELECT department_id, AVG(salary) AS avg_salary
FROM employees
GROUP BY department_id;
```

## DROP VIEW

```sql
DROP VIEW emp_public;
```

---

## VIEW vs TABLE

| Feature | TABLE | VIEW |
|------|------|------|
| Stores data | Yes | No |
| Physical storage | Yes | No |
| Based on query | No | Yes |
| Supports JOIN | No | Yes |
| Used for security | Limited | Yes |

---

## Practice Exercises

### Exercise 1
Create a VIEW that shows employees with job_id = 'IT_PROG'

### Exercise 2
Create a VIEW showing total salary per department
