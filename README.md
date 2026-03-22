# SQL-PROJECT
# 📊 HR Analytics – Employee Attrition Analysis | SQL Project  

## 📌 Overview  
This project focuses on analyzing employee data using **SQL (MySQL)** to identify patterns in employee attrition and workforce behavior.  
The goal is to extract meaningful insights from structured data to support **data-driven HR decision-making**.  

---

## 🎯 Objectives  
- Analyze employee data using SQL queries  
- Identify factors influencing employee attrition  
- Perform attendance and department-level analysis  
- Generate insights to improve employee retention  

---

## 🛠️ Tools & Technologies  
- SQL (MySQL)  
- MySQL Workbench  

---

## 🗂️ Database Structure  

The analysis was performed on a relational database with the following tables:

- employees → Employee details (age, gender, department, experience, attrition)  
- departments → Department information  
- attendance → Employee attendance records  
- projects → Project details  
- employee_projects → Mapping of employees to projects  
- salaries → Employee salary details  

---

## 🔍 Key SQL Analysis  

### 1️⃣ Employee Project Mapping  
Maps employees to their respective projects.

```sql
SELECT e.name, p.project_name
FROM Employees e
JOIN Employee_Projects ep ON e.employee_id = ep.employee_id
JOIN Projects p ON ep.project_id = p.project_id;
```
<p align="center">
  <img src="https://raw.githubusercontent.com/Saikiran-005/SQL-PROJECT/main/Screenshot%202026-03-17%20134651.png" width="600"/>
</p>
### 2️⃣ Employee Attrition Rate

```sql
SELECT 
    COUNT(CASE WHEN attrition = 'Yes' THEN 1 END) * 100.0 / COUNT(*) AS attrition_rate
FROM Employees;
```
<p align="center">
  <img src="https://raw.githubusercontent.com/Saikiran-005/SQL-PROJECT/main/Screenshot%202026-03-17%20134730.png" width="600"/>
</p>
###3️⃣ Department-wise Highest Salary

```sql
SELECT d.department_name, MAX(s.salary) AS highest_salary
FROM Employees e
JOIN Departments d ON e.department_id = d.department_id
JOIN Salaries s ON e.employee_id = s.employee_id
GROUP BY d.department_name;
```
