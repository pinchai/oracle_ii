# Oracle CASE WHEN 
------------------------------------------------------------------------

## 1. Introduction to CASE WHEN

### What is CASE?

CASE is used to implement IF-ELSE logic inside SQL.

### Simple CASE Syntax

- Compares one column/expression
- Uses equality (=) only
- Cleaner when checking fixed values

``` sql
CASE column
   WHEN value1 THEN result1
   WHEN value2 THEN result2
   ELSE result
END
```

``` sql
SELECT
    employee_id,
    department_id,
    CASE department_id
        WHEN 10 THEN 'Administration'
        WHEN 20 THEN 'Marketing'
        ELSE 'Other'
    END AS dept_name
FROM employees;
```

### Searched CASE Syntax
- Uses full conditions
- More flexible
- Can use <, >, BETWEEN, IS NULL, AND, OR

``` sql
CASE
   WHEN condition1 THEN result1
   WHEN condition2 THEN result2
   ELSE result
END
```

``` sql
SELECT
    employee_id,
    salary,
    CASE
        WHEN salary < 3000 THEN 'LOW'
        WHEN salary BETWEEN 3000 AND 8000 THEN 'MEDIUM'
        ELSE 'HIGH'
    END AS salary_level
FROM employees;
```

------------------------------------------------------------------------

## 2. Example 1 -- Salary Level Classification

``` sql
SELECT 
    employee_id,
    first_name,
    salary,
    CASE
        WHEN salary < 3000 THEN 'LOW'
        WHEN salary BETWEEN 3000 AND 8000 THEN 'MEDIUM'
        ELSE 'HIGH'
    END AS salary_level
FROM employees;
```

------------------------------------------------------------------------

## 3. Example 2 -- Commission Status

``` sql
SELECT
    employee_id,
    first_name,
    commission_pct,
    CASE
        WHEN commission_pct IS NULL THEN 'NO COMMISSION'
        ELSE 'HAS COMMISSION'
    END AS commission_status
FROM employees;
```

------------------------------------------------------------------------

## 4. Example 3 -- Department Label

``` sql
SELECT
    employee_id,
    first_name,
    department_id,
    CASE department_id
        WHEN 10 THEN 'Administration'
        WHEN 20 THEN 'Marketing'
        WHEN 50 THEN 'Shipping'
        ELSE 'Other Department'
    END AS department_name
FROM employees;
```

------------------------------------------------------------------------

## 5. Example 4 -- Salary Bonus Calculation

``` sql
SELECT
    employee_id,
    salary,
    CASE
        WHEN salary > 8000 THEN salary * 0.10
        WHEN salary BETWEEN 3000 AND 8000 THEN salary * 0.05
        ELSE salary * 0.02
    END AS bonus
FROM employees;
```

------------------------------------------------------------------------

## 6. Example 5 -- CASE with GROUP BY

``` sql
SELECT
    CASE
        WHEN salary < 3000 THEN 'LOW'
        WHEN salary BETWEEN 3000 AND 8000 THEN 'MEDIUM'
        ELSE 'HIGH'
    END AS salary_level,
    COUNT(*) AS total_employees
FROM employees
GROUP BY
    CASE
        WHEN salary < 3000 THEN 'LOW'
        WHEN salary BETWEEN 3000 AND 8000 THEN 'MEDIUM'
        ELSE 'HIGH'
    END;
```

------------------------------------------------------------------------

# Exercises


Classify salary: - salary \< 2000 → 'UNDERPAID' - 2000 -- 5000 →
'NORMAL' - \> 5000 → 'WELL PAID'

------------------------------------------------------------------------

Categorize by hire year: - Before 2005 → 'SENIOR' - 2005 -- 2010 → 'MID
LEVEL' - After 2010 → 'JUNIOR'

(Hint: Use EXTRACT(YEAR FROM hire_date))

------------------------------------------------------------------------

From JOBS table classify salary range: - MAX_SALARY \< 5000 → 'LOW
RANGE' - 5000 -- 10000 → 'MEDIUM RANGE' - \> 10000 → 'HIGH RANGE'

------------------------------------------------------------------------


Join EMPLOYEES and JOB_GRADES and classify grade using salary BETWEEN
LOWEST_SAL and HIGHEST_SAL.

------------------------------------------------------------------------

Classify income type: - commission_pct IS NOT NULL → 'COMMISSION
BASED' - commission_pct IS NULL AND salary \> 8000 → 'HIGH FIXED' -
Otherwise → 'STANDARD FIXED'

------------------------------------------------------------------------

# Mini Quiz

1.  Difference between Simple CASE and Searched CASE?
2.  Can CASE be used inside WHERE?
