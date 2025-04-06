# 👨‍💼 SQL Problem: Managers with at Least 5 Direct Reports

**LeetCode Problem**: [Managers with at Least 5 Direct Reports](https://leetcode.com/problems/managers-with-at-least-5-direct-reports/)

---

## 📄 Problem Description

### Table: `Employee`

| Column Name | Type    |
|-------------|---------|
| id          | int     |
| name        | varchar |
| department  | varchar |
| managerId   | int     |

- `id` is the primary key.
- Each row represents an employee, including their department and their manager’s ID.
- If `managerId` is `NULL`, then the employee does not have a manager.
- No employee is the manager of themself.

---

## 🎯 Objective

Write an SQL query to **find the names of managers who have at least five direct reports**.

Return the result in **any order**.

---

## 🧪 Example

### Input

#### `Employee` Table:

| id  | name  | department | managerId |
|-----|-------|------------|-----------|
| 101 | John  | A          | null      |
| 102 | Dan   | A          | 101       |
| 103 | James | A          | 101       |
| 104 | Amy   | A          | 101       |
| 105 | Anne  | A          | 101       |
| 106 | Ron   | B          | 101       |

### Output

| name |
|------|
| John |

---

## ✅ SQL Solution

```sql
SELECT 
    e.name AS name
FROM 
    employee emp
JOIN 
    employee e ON emp.managerId = e.id
GROUP BY 
    e.id, e.name
HAVING 
    COUNT(emp.id) >= 5;
```

---

## 🧠 Key Concepts

- **Self join** on the `Employee` table to relate employees to their managers.
- **GROUP BY** to count direct reports per manager.
- **HAVING** clause to filter managers with at least 5 reports.

---

✍️ *Contributed by Deepak Shanmugam K 
📘 *SQL | LeetCode Practice*
