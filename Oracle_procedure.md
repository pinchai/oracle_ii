# Oracle Procedure

An Oracle Procedure is a stored PL/SQL block that performs a specific task.  
It is stored inside the database and can be executed whenever needed.

---

# Basic Syntax

```sql
CREATE OR REPLACE PROCEDURE procedure_name
(
    parameter_name datatype
)
IS
BEGIN
    -- SQL statements
END;
/
```

---

# Example 1: Simple Procedure

```sql
CREATE OR REPLACE PROCEDURE hello_world
IS
BEGIN
    DBMS_OUTPUT.PUT_LINE('Hello Oracle Procedure');
END;
/
```

Execute:

```sql
BEGIN
    hello_world;
END;
/
```

---

# Example 2: Procedure With Parameters

```sql
CREATE OR REPLACE PROCEDURE increase_salary
(
    p_employee_id IN NUMBER,
    p_amount IN NUMBER
)
IS
BEGIN
    UPDATE employees
    SET salary = salary + p_amount
    WHERE employee_id = p_employee_id;

    COMMIT;
END;
/
```

Execute:

```sql
BEGIN
    increase_salary(100, 500);
END;
/
```

---

# Example 3: Procedure Using OUT Parameter

```sql
CREATE OR REPLACE PROCEDURE get_salary
(
    p_employee_id IN NUMBER,
    p_salary OUT NUMBER
)
IS
BEGIN
    SELECT salary
    INTO p_salary
    FROM employees
    WHERE employee_id = p_employee_id;
END;
/
```

Execute:

```sql
DECLARE
    v_salary NUMBER;
BEGIN
    get_salary(100, v_salary);

    DBMS_OUTPUT.PUT_LINE('Salary: ' || v_salary);
END;
/
```

---

# Parameter Modes

| Mode | Description |
|---|---|
| IN | Input value |
| OUT | Return value |
| IN OUT | Input and output |

---

# Procedure With Exception Handling

```sql
CREATE OR REPLACE PROCEDURE delete_employee
(
    p_employee_id IN NUMBER
)
IS
BEGIN
    DELETE FROM employees
    WHERE employee_id = p_employee_id;

    COMMIT;

EXCEPTION
    WHEN NO_DATA_FOUND THEN
        DBMS_OUTPUT.PUT_LINE('Employee not found');

    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE(SQLERRM);
END;
/
```

---

# View Procedures

```sql
SELECT object_name
FROM user_objects
WHERE object_type = 'PROCEDURE';
```

---

# Drop Procedure

```sql
DROP PROCEDURE procedure_name;
```

---

# Advantages of Procedures

- Reusable code
- Better performance
- Improved security
- Easier maintenance
- Centralized business logic

---

# Exercises

## Exercise 1: Create a Simple Procedure

Create a procedure named `show_message` that displays:

```text
Welcome to Oracle PL/SQL
```

---

## Exercise 2: Employee Salary Update

Create a procedure named `update_employee_salary`.

Requirements:

- Accept employee ID
- Accept salary increase amount
- Update employee salary

---

## Exercise 3: Find Employee Salary

Create a procedure named `find_salary`.

Requirements:

- Accept employee ID
- Return employee salary using OUT parameter

---

## Exercise 4: Delete Employee

Create a procedure named `remove_employee`.

Requirements:

- Accept employee ID
- Delete employee record
- Commit the transaction

---

## Exercise 5: Procedure With IN OUT Parameter

Create a procedure that:

- Accepts a number using IN OUT parameter
- Adds 100 to the value
- Returns the updated value

---

## Exercise 6: Count Employees

Create a procedure named `count_employees`.

Requirements:

- Count all employees from employees table
- Display total employees using DBMS_OUTPUT

---

## Exercise 7: Display Employee Information

Create a procedure named `employee_info`.

Requirements:

- Accept employee ID
- Display:
  - First name
  - Last name
  - Salary

---

## Exercise 8: Procedure With Exception Handling

Create a procedure that:

- Accepts employee ID
- Displays salary
- Handles NO_DATA_FOUND exception

---

## Exercise 9: Department Employee Count

Create a procedure named `department_employee_count`.

Requirements:

- Accept department ID
- Display total employees in the department

---

## Exercise 10: Bonus Calculation

Create a procedure named `calculate_bonus`.

Requirements:

- Accept employee ID
- Accept bonus percentage
- Update employee salary with bonus

Example:

If salary = 5000  
Bonus = 10%  
New salary = 5500

---
