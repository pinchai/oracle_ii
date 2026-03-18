# Oracle DML (Data Manipulation Language)

## 1. INSERT

### Syntax

INSERT INTO table_name (column1, column2, ...) VALUES (value1, value2,
...);

### Example

INSERT INTO employees ( employee_id, first_name, last_name, email,
hire_date, job_id, salary, department_id ) VALUES ( 1001, 'John', 'Doe',
'JDOE', SYSDATE, 'IT_PROG', 5000, 60 );

------------------------------------------------------------------------

## 2. UPDATE

### Syntax

UPDATE table_name SET column1 = value1 WHERE condition;

### Example

UPDATE employees SET salary = 6000 WHERE employee_id = 1001;

------------------------------------------------------------------------

## 3. DELETE

### Syntax

DELETE FROM table_name WHERE condition;

### Example

DELETE FROM employees WHERE employee_id = 1001;

------------------------------------------------------------------------

## 4. COMMIT

COMMIT;

------------------------------------------------------------------------

## 5. ROLLBACK

ROLLBACK;

------------------------------------------------------------------------

## 6. SAVEPOINT

SAVEPOINT sp1;

------------------------------------------------------------------------

## 7. ROLLBACK TO

ROLLBACK TO sp1;

------------------------------------------------------------------------

# LAB EXERCISES

## Part 1: INSERT

INSERT INTO employees ( employee_id, first_name, last_name, email,
hire_date, job_id, salary, department_id ) VALUES (2001, 'Alice',
'Smith', 'ASMITH', SYSDATE, 'HR_REP', 4000, 40);

INSERT INTO employees ( employee_id, first_name, last_name, email,
hire_date, job_id, salary, commission_pct, department_id ) VALUES (2002,
'Bob', 'Lee', 'BLEE', SYSDATE, 'SA_REP', 4500, 0.1, 50);

------------------------------------------------------------------------

## Part 2: UPDATE

UPDATE employees SET salary = salary \* 1.10 WHERE employee_id = 2001;

UPDATE employees SET department_id = 60 WHERE employee_id = 2002;

------------------------------------------------------------------------

## Part 3: DELETE

DELETE FROM employees WHERE employee_id = 2002;

------------------------------------------------------------------------

## Part 4: TRANSACTION

INSERT INTO employees ( employee_id, first_name, last_name, email,
hire_date, job_id ) VALUES (3001, 'Test', 'User', 'TUSER', SYSDATE,
'IT_PROG');

ROLLBACK;

INSERT INTO employees ( employee_id, first_name, last_name, email,
hire_date, job_id ) VALUES (3002, 'Commit', 'User', 'CUSER', SYSDATE,
'IT_PROG');

COMMIT;

------------------------------------------------------------------------

## Part 5: SAVEPOINT

INSERT INTO employees VALUES (4001, 'A', 'A', 'A1', NULL, SYSDATE,
'IT_PROG', 3000, NULL, NULL, 60);

SAVEPOINT sp1;

INSERT INTO employees VALUES (4002, 'B', 'B', 'B1', NULL, SYSDATE,
'IT_PROG', 3000, NULL, NULL, 60);

ROLLBACK TO sp1;

------------------------------------------------------------------------

# Lab

### Level 1

-   Insert 3 employees
-   Update salary in department 60
-   Delete salary < 3000

### Level 2

-   Savepoint practice
-   Commit vs Rollback

### Level 3

-   Transfer employee with rollback scenario
