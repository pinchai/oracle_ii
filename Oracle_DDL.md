# Oracle DDL (Data Definition Language)

## What is DDL?

DDL is used to define and manage database structure (tables, schema,
objects).

------------------------------------------------------------------------

## Main DDL Commands

### 1. CREATE → Create database objects

``` sql
CREATE TABLE employees (
    employee_id NUMBER(6) PRIMARY KEY,
    first_name VARCHAR2(20),
    last_name VARCHAR2(25) NOT NULL,
    email VARCHAR2(25) NOT NULL,
    hire_date DATE NOT NULL,
    job_id VARCHAR2(10) NOT NULL,
    salary NUMBER(8,2),
    department_id NUMBER(4)
);
```

------------------------------------------------------------------------

### 2. ALTER → Modify existing objects

#### Add Column

``` sql
ALTER TABLE employees
ADD phone_number VARCHAR2(20);
```

#### Modify Column

``` sql
ALTER TABLE employees
MODIFY salary NUMBER(10,2);
```

#### Drop Column

``` sql
ALTER TABLE employees
DROP COLUMN phone_number;
```

------------------------------------------------------------------------

### 3. DROP → Delete object permanently

``` sql
DROP TABLE employees;
```

------------------------------------------------------------------------

### 4. TRUNCATE → Remove all data (fast)

``` sql
TRUNCATE TABLE employees;
```

------------------------------------------------------------------------

### 5. RENAME → Rename object

``` sql
RENAME employees TO staff;
```

------------------------------------------------------------------------

### 6. COMMENT → Add description

``` sql
COMMENT ON TABLE employees IS 'Employee information';
```

------------------------------------------------------------------------

## Constraints in DDL

-   PRIMARY KEY
-   NOT NULL
-   UNIQUE
-   FOREIGN KEY
-   CHECK

``` sql
CREATE TABLE departments (
    department_id NUMBER(4) PRIMARY KEY,
    department_name VARCHAR2(30) NOT NULL,
    location_id NUMBER(4)
);
```

------------------------------------------------------------------------

## Foreign Key Example

``` sql
CREATE TABLE employees (
    employee_id NUMBER(6) PRIMARY KEY,
    last_name VARCHAR2(25) NOT NULL,
    department_id NUMBER(4),
    CONSTRAINT fk_dept
        FOREIGN KEY (department_id)
        REFERENCES departments(department_id)
        ON DELETE CASCADE
);
```

------------------------------------------------------------------------

## Key Notes

-   DDL commands auto-commit
-   Cannot rollback after execution
-   Used for structure, not data

------------------------------------------------------------------------

## Lab

1.  Create table jobs
2.  Add column commission_pct
3.  Modify salary
4.  Drop column phone_number
5.  Create foreign key
6.  Rename table
7.  Truncate table

------------------------------------------------------------------------

## Summary

  Command    Purpose
  ---------- ------------------
  - CREATE     Create object
  - ALTER      Modify structure
  - DROP       Delete object
  - TRUNCATE   Remove all data
  - RENAME     Rename object
  - COMMENT    Add description
