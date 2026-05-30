# Oracle User Controll

---

## Learning Objectives
By the end of this lesson, students will be able to:
- Explain what a database user is
- Create and manage users in Oracle
- Understand system and object privileges
- Use roles to manage permissions efficiently
- Control data access using views
- Revoke privileges and manage user accounts

---

## Lesson Outline

### 1. Introduction to User Controlling
**Key Concepts**
- What is user controlling?
- Why access control is important
- Real-world examples (Admin, HR, Manager, Intern)

**Discussion**
- What could happen if everyone has full access?

---

### 2. Oracle Database Users
**Explanation**
- Definition of a database user
- Authentication and ownership of objects

**Demo**
```sql
CREATE USER hr_user IDENTIFIED BY hr123;
GRANT CREATE SESSION TO hr_user;
```
---

### 3. Privileges in Oracle

#### 3.1 System Privileges
**Examples**
- CREATE TABLE
- CREATE VIEW
- CREATE PROCEDURE

```sql
GRANT CREATE TABLE, CREATE VIEW TO hr_user;
```

#### 3.2 Object Privileges
**Examples**
- SELECT, INSERT, UPDATE, DELETE

```sql
GRANT SELECT, INSERT ON employees TO hr_user;
```

**Discussion**
- Difference between system and object privileges

---

### 4. Roles
**Explanation**
- What is a role?
- Why roles are best practice

**Demo**
```sql
CREATE ROLE hr_role;
GRANT SELECT, INSERT, UPDATE ON employees TO hr_role;
GRANT hr_role TO hr_user;
```
---

### 5. Controlling Access with Views
**Explanation**
- Why use views instead of tables
- Data security and column-level control

**Demo**
```sql
CREATE VIEW v_emp_public AS
SELECT employee_id, first_name, last_name, department_id
FROM employees;

GRANT SELECT ON v_emp_public TO hr_user;
```

**Activity**
- Create a view without salary column

---

### 6. Revoking Privileges and Roles
**Explanation**
- Removing access is part of security

```sql
REVOKE INSERT ON employees FROM hr_user;
REVOKE hr_role FROM hr_user;
```

---

### 7. User Account Control
**Lock / Unlock User**
```sql
ALTER USER hr_user ACCOUNT LOCK;
ALTER USER hr_user ACCOUNT UNLOCK;
```

**Drop User**
```sql
DROP USER hr_user CASCADE;
```

---

## Lab
1. Create a user called `staff_user`
2. Create a role called `staff_role`
3. Grant SELECT on EMPLOYEES and DEPARTMENTS
4. Assign the role to the user
5. Create a view hiding SALARY
6. Grant view access only
---
