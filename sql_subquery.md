# SQL Subquery


------------------------------------------------------------------------

## 2. Learning Objectives

After this lesson, students will be able to:

1.  Understand what a subquery is.
2.  Use subqueries inside:
    -   WHERE clause
    -   FROM clause
    -   SELECT clause
3.  Use operators with subqueries:
    -   =
    -   IN
    -   ANY
    -   ALL
    -   EXISTS
4.  Solve real database questions using subqueries.

------------------------------------------------------------------------

## 3. What is a Subquery?

A subquery is a query inside another SQL query.

Structure:

``` sql
SELECT column
FROM table
WHERE column = (
    SELECT column
    FROM table
);
```

Execution order:

1.  Inner query runs first
2.  Outer query uses the result

------------------------------------------------------------------------

## 4. Types of Subqueries

  Type                    Description
  ----------------------- -------------------------
  Single-row subquery     Returns one row
  Multiple-row subquery   Returns multiple rows
  Correlated subquery     Depends on outer query
  Inline view             Subquery in FROM clause

------------------------------------------------------------------------

## 5. Example 1 -- Single Row Subquery

Find employees who earn more than the average salary.

``` sql
SELECT first_name, last_name, salary
FROM employees
WHERE salary > (
    SELECT AVG(salary)
    FROM employees
);
```

------------------------------------------------------------------------

## 6. Example 2 -- Subquery with WHERE

Find employees who work in the IT department.

``` sql
SELECT first_name, last_name
FROM employees
WHERE department_id = (
    SELECT department_id
    FROM departments
    WHERE department_name = 'IT'
);
```

------------------------------------------------------------------------

## 7. Example 3 -- Subquery with IN

Find employees working in departments located in Seattle.

``` sql
SELECT first_name, last_name, department_id
FROM employees
WHERE department_id IN (
    SELECT department_id
    FROM departments
    WHERE location_id IN (
        SELECT location_id
        FROM locations
        WHERE city = 'Seattle'
    )
);
```

------------------------------------------------------------------------

## 8. Example 4 -- Subquery in SELECT

``` sql
SELECT
    first_name,
    salary,
    (SELECT AVG(salary) FROM employees) AS avg_salary
FROM employees;
```

------------------------------------------------------------------------

## 9. Example 5 -- Correlated Subquery

Find employees who earn more than the average salary of their
department.

``` sql
SELECT first_name, salary, department_id
FROM employees e
WHERE salary >
(
    SELECT AVG(salary)
    FROM employees
    WHERE department_id = e.department_id
);
```

------------------------------------------------------------------------

## 10. Example 6 -- EXISTS

Find departments that have employees.

``` sql
SELECT department_name
FROM departments d
WHERE EXISTS (
    SELECT 1
    FROM employees e
    WHERE e.department_id = d.department_id
);
```

------------------------------------------------------------------------

# Practice Exercises

## Easy

1.  Find employees whose salary is greater than the average salary.
2.  Find employees who work in the Sales department.
3.  Find departments that have employees.
4.  Find employees who work in the same department as employee 100.
5.  Find employees whose salary equals the minimum salary.

## Medium

6.  Find employees earning more than the average salary of department
    50.
7.  Find employees who work in departments located in USA.
8.  Find employees whose job title is Programmer.
9.  Find employees whose salary is higher than all employees in
    department 30.
10. Find departments with no employees.

## Hard

11. Find employees earning above the average salary of their department.
12. Find the employee with the highest salary in each department.
13. Find employees whose salary is greater than their manager's salary.
14. Find employees who changed jobs (use JOB_HISTORY).
15. Find departments where the average salary is greater than 8000.
