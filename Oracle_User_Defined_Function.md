
# Oracle User-Defined Functions
---

## Prerequisites
- Oracle SQL basics
- Basic PL/SQL block structure

```sql
DECLARE
BEGIN
END;
```

---

## 1. Introduction to Functions

### What is a Function?
A function is a database object that:
- Accepts input parameters
- Performs logic
- Returns one value

### Built-in vs User-Defined

| Built-in Function | User-Defined Function |
|------------------|----------------------|
| Provided by Oracle | Created by developer |
| UPPER(), NVL() | Custom business logic |
| Cannot be modified | Fully customizable |

### Why Use User-Defined Functions?
- Code reusability
- Cleaner SQL
- Centralized business rules
- Easier maintenance

---

## 2. Basic Syntax of Oracle Function

```sql
CREATE OR REPLACE FUNCTION function_name (
    parameter_name datatype
)
RETURN return_datatype
IS
BEGIN
    RETURN value;
END;
/
```

### Rules
- Must return exactly one value
- Can be used in SELECT, WHERE, ORDER BY
- Cannot use COMMIT or ROLLBACK

---

## 3. Demo 1: Simple Function

### Example: Calculate Bonus

```sql
CREATE OR REPLACE FUNCTION get_bonus (
    p_salary NUMBER
)
RETURN NUMBER
IS
BEGIN
    RETURN p_salary * 0.10;
END;
/
```

### Using the Function

```sql
SELECT employee_id,
       salary,
       get_bonus(salary) AS bonus
FROM employees;
```

---

## 4. Function with Conditional Logic

```sql
CREATE OR REPLACE FUNCTION get_grade (
    p_salary NUMBER
)
RETURN VARCHAR2
IS
BEGIN
    IF p_salary >= 8000 THEN
        RETURN 'A';
    ELSIF p_salary >= 5000 THEN
        RETURN 'B';
    ELSE
        RETURN 'C';
    END IF;
END;
/
```

```sql
SELECT first_name,
       salary,
       get_grade(salary) AS grade
FROM employees;
```

---

## 5. Function with Multiple Parameters

```sql
CREATE OR REPLACE FUNCTION get_fullname (
    p_firstname VARCHAR2,
    p_lastname  VARCHAR2
)
RETURN VARCHAR2
IS
BEGIN
    RETURN p_firstname || ' ' || p_lastname;
END;
/
```

---

## 6. NULL Handling in Functions

```sql
CREATE OR REPLACE FUNCTION safe_salary (
    p_salary NUMBER
)
RETURN NUMBER
IS
BEGIN
    RETURN NVL(p_salary, 0);
END;
/
```

---

## 7. Common Errors & Debugging

### Common Errors
- ORA-06575: Invalid function
- ORA-00904: Function not compiled
- Missing RETURN statement

### Check Errors

```sql
SHOW ERRORS FUNCTION function_name;
```

---
---

## Lab Exercises

### Lab 1 (Beginner)
Create a function that:
- Accepts a number
- Returns EVEN or ODD

### Lab 2 (Intermediate)
Create a function:
- Accepts salary
- Returns tax amount

### Lab 3 (Advanced)
Create a function:
- Accepts employee ID
- Returns employee full name

---

## 10. Assessment
1. Can a function return multiple values?
2. Can a function be used in WHERE clause?
3. What happens if RETURN is missing?
4. Difference between function and procedure?

---
