# SQL_HW_3

## :small_blue_diamONd:HW during Vadim Ksendzov course:small_blue_diamONd:
```
1. Вывести всех работников чьи зарплаты есть в базе, вместе с зарплатами.
```
```sql
SELECT employees.employee_name, salary.monthly_salary
FROM employee_salary JOIN employees
ON employee_salary.employee_id = employees.id
JOIN salary
ON employee_salary.salary_id = salary.id
```
```
2. Вывести всех работников у которых ЗП меньше 2000.
```
```sql
SELECT employees.employee_name
FROM employee_salary
JOIN salary ON employee_salary.salary_id = salary.id
JOIN employees ON employee_salary.employee_id = employees.id
WHERE salary.monthly_salary < 2000
```
```
3. Вывести все зарплатные позиции, но работник по ним не назначен. (ЗП есть, но не понятно кто её получает.)
```
```sql
SELECT salary.monthly_salary
FROM employee_salary JOIN employees
ON employee_salary.employee_id = employees.id
RIGHT JOIN salaryORDER BY
ON employee_salary.salary_id = salary.id
WHERE employee_name IS NULL
```
```
4. Вывести все зарплатные позиции меньше 2000 но работник по ним не назначен. (ЗП есть, но не понятно кто её получает.)
```
```sql
SELECT salary.id, salary.monthly_salary, employees.employee_name
FROM salary
LEFT JOIN employee_salary ON employee_salary.salary_id = salary.id
LEFT JOIN employees ON employee_salary.employee_id = employees.id
WHERE employee_name IS NULL AND monthly_salary < 2000;
```
```
5. Найти всех работников кому не начислена ЗП.
```
```sql
SELECT employees.employee_name, employees.id
FROM employee_salary RIGHT JOIN employees
ON employee_salary.employee_id = employees.id
WHERE employee_salary.salary_id IS NULL
```
```
6. Вывести всех работников с названиями их должности.
```
```sql
SELECT employees.employee_name, roles.role_name, employees.id, roles.id
FROM roles_employee JOIN employees
ON roles_employee.employee_id = employees.id
JOIN roles
ON roles_employee.role_id = roles.id
```
```
7. Вывести имена и должность только Java разработчиков.
```
```sql
SELECT employees.employee_name, roles.role_name
FROM roles_employee JOIN employees
ON roles_employee.employee_id = employees.id
JOIN roles
ON roles_employee.role_id = roles.id
WHERE role_name LIKE '%Java developer%'
```
```
8. Вывести имена и должность только Python разработчиков.
```
```sql
SELECT employees.employee_name, roles.role_name
FROM roles_employee JOIN employees
ON roles_employee.employee_id = employees.id
JOIN roles
ON roles_employee.role_id = roles.id
WHERE role_name LIKE '%Python developer%'
```
```
9. Вывести имена и должность всех QA инженеров.
```
```sql
SELECT employees.employee_name, roles.role_name
FROM roles_employee JOIN employees
ON roles_employee.employee_id = employees.id
JOIN roles
ON roles_employee.role_id = roles.id
WHERE role_name LIKE '%QA engineer%'
```
```
10. Вывести имена и должность ручных QA инженеров.
```
```sql
SELECT employees.employee_name, roles.role_name
FROM roles_employee JOIN employees
ON roles_employee.employee_id = employees.id
JOIN roles
ON roles_employee.role_id = roles.id
WHERE role_name LIKE '%Manual QA%'
```
```
11. Вывести имена и должность автоматизаторов QA
```
```sql
SELECT employees.employee_name, roles.role_name
FROM roles_employee JOIN employees
ON roles_employee.employee_id = employees.id
JOIN roles
ON roles_employee.role_id = roles.id
WHERE role_name LIKE '%AutomatiON QA%'
```
```
12. Вывести имена и зарплаты Junior специалистов
```
```sql
SELECT employees.employee_name, salary.monthly_salary
FROM employees JOIN employee_salary
ON employees.id = employee_salary.employee_id
JOIN salary
ON salary.id = employee_salary.salary_id
JOIN roles_employee
ON employees.id = roles_employee.employee_id
JOIN roles
ON roles_employee.role_id = roles.id
WHERE role_name LIKE '%Junior%'
```
```
13. Вывести имена и зарплаты Middle специалистов
```
```sql
SELECT employees.employee_name, salary.monthly_salary, employees.id
FROM employees JOIN employee_salary
ON employees.id = employee_salary.employee_id
JOIN salary
ON salary.id = employee_salary.salary_id
JOIN roles_employee
ON employees.id = roles_employee.employee_id
JOIN roles
ON roles_employee.role_id = roles.id
WHERE role_name LIKE '%Middle%'
```
```
14. Вывести имена и зарплаты Senior специалистов.
```
```sql
SELECT employees.employee_name, salary.monthly_salary, employees.id
FROM employees JOIN employee_salary
ON employees.id = employee_salary.employee_id
JOIN salary
ON salary.id = employee_salary.salary_id
JOIN roles_employee
ON employees.id = roles_employee.employee_id
JOIN roles
ON roles_employee.role_id = roles.id
WHERE role_name LIKE '%Senior%'
```
```
15. Вывести зарплаты Java разработчиков.
```
```sql
SELECT salary.monthly_salary, roles.role_name 
FROM employees JOIN employee_salary
ON employees.id = employee_salary.employee_id
JOIN salary
ON salary.id = employee_salary.salary_id
JOIN roles_employee
ON employees.id = roles_employee.employee_id
JOIN roles
ON roles_employee.role_id = roles.id
WHERE role_name LIKE '%Java %';
```
```
16. Вывести зарплаты Python разработчиков.
```
```sql
SELECT salary.monthly_salary, roles.role_name 
FROM employees JOIN employee_salary
ON employees.id = employee_salary.employee_id
JOIN salary
ON salary.id = employee_salary.salary_id
JOIN roles_employee
ON employees.id = roles_employee.employee_id
JOIN roles
ON roles_employee.role_id = roles.id
WHERE role_name LIKE '%Python%';
```
```
17. Вывести имена и зарплаты Junior Python разработчиков.
```
```sql
SELECT employees.employee_name, salary.monthly_salary, roles.role_name 
FROM employees JOIN employee_salary
ON employees.id = employee_salary.employee_id
JOIN salary
ON salary.id = employee_salary.salary_id
JOIN roles_employee
ON employees.id = roles_employee.employee_id
JOIN roles
ON roles_employee.role_id = roles.id
WHERE role_name LIKE '%Junior Python%';
```
```
18. Вывести имена и зарплаты Middle JS разработчиков.
```
```sql
SELECT employees.employee_name, salary.monthly_salary, roles.role_name 
FROM employees JOIN employee_salary
ON employees.id = employee_salary.employee_id
JOIN salary
ON salary.id = employee_salary.salary_id
JOIN roles_employee
ON employees.id = roles_employee.employee_id
JOIN roles
ON roles_employee.role_id = roles.id
WHERE role_name LIKE '%Middle JavaScript%';
```
```
19. Вывести имена и зарплаты Senior Java разработчиков.
```
```sql
SELECT employees.employee_name, salary.monthly_salary, roles.role_name 
FROM employees LEFT JOIN employee_salary
ON employees.id = employee_salary.employee_id
LEFT JOIN salary
ON salary.id = employee_salary.salary_id
JOIN roles_employee
ON employees.id = roles_employee.employee_id
JOIN roles
ON roles_employee.role_id = roles.id
WHERE role_name LIKE '%Senior Java %';
```
```
20. Вывести зарплаты Junior QA инженеров.
```
```sql
SELECT salary.monthly_salary, roles.role_name 
FROM employees JOIN employee_salary
ON employees.id = employee_salary.employee_id
JOIN salary
ON salary.id = employee_salary.salary_id
JOIN roles_employee
ON employees.id = roles_employee.employee_id
JOIN roles
ON roles_employee.role_id = roles.id
WHERE role_name LIKE '%Junior%QA%';
```
```
21. Вывести среднюю зарплату всех Junior специалистов.
```
```sql
SELECT avg(salary.monthly_salary)
FROM employees JOIN employee_salary
ON employees.id = employee_salary.employee_id
JOIN salary
ON salary.id = employee_salary.salary_id
JOIN roles_employee
ON employees.id = roles_employee.employee_id
JOIN roles
ON roles_employee.role_id = roles.id
WHERE role_name LIKE '%Junior%';
```
```
22. Вывести сумму зарплат JS разработчиков.
```
```sql
SELECT sum(salary.monthly_salary)
FROM employees JOIN employee_salary
ON employees.id = employee_salary.employee_id
JOIN salary
ON salary.id = employee_salary.salary_id
JOIN roles_employee
ON employees.id = roles_employee.employee_id
JOIN roles
ON roles_employee.role_id = roles.id
WHERE role_name LIKE '%JavaScript%';
```
```
23. Вывести минимальную ЗП QA инженеров.
```
```sql
SELECT min(salary.monthly_salary)
FROM employees JOIN employee_salary
ON employees.id = employee_salary.employee_id
JOIN salary
ON salary.id = employee_salary.salary_id
JOIN roles_employee
ON employees.id = roles_employee.employee_id
JOIN roles
ON roles_employee.role_id = roles.id
WHERE role_name LIKE '%QA%';
```
```
24. Вывести максимальную ЗП QA инженеров.
```
```sql
SELECT max(salary.monthly_salary)
FROM employees JOIN employee_salary
ON employees.id = employee_salary.employee_id
JOIN salary
ON salary.id = employee_salary.salary_id
JOIN roles_employee
ON employees.id = roles_employee.employee_id
JOIN roles
ON roles_employee.role_id = roles.id
WHERE role_name LIKE '%QA%';
```
```
25. Вывести количество QA инженеров.
```
```sql
SELECT count(employees.id)
FROM employees JOIN employee_salary
ON employees.id = employee_salary.employee_id
JOIN salary
ON salary.id = employee_salary.salary_id
JOIN roles_employee
ON employees.id = roles_employee.employee_id
JOIN roles
ON roles_employee.role_id = roles.id
WHERE role_name LIKE '%QA%';
```
```
26. Вывести количество Middle специалистов.
```
```sql
SELECT count(employees.id)
FROM employees JOIN employee_salary
ON employees.id = employee_salary.employee_id
JOIN salary
ON salary.id = employee_salary.salary_id
JOIN roles_employee
ON employees.id = roles_employee.employee_id
JOIN roles
ON roles_employee.role_id = roles.id
WHERE role_name LIKE '%Middle%';
```
```
27. Вывести количество разработчиков.
```
```sql
SELECT count(employees.id)
FROM employees JOIN employee_salary
ON employees.id = employee_salary.employee_id
JOIN salary
ON salary.id = employee_salary.salary_id
JOIN roles_employee
ON employees.id = roles_employee.employee_id
JOIN roles
ON roles_employee.role_id = roles.id
WHERE role_name LIKE '%developer%';
```
```
28. Вывести фонд (сумму) зарплаты разработчиков.
```
```sql
SELECT sum(salary.monthly_salary)
FROM employees JOIN employee_salary
ON employees.id = employee_salary.employee_id
JOIN salary
ON salary.id = employee_salary.salary_id
JOIN roles_employee
ON employees.id = roles_employee.employee_id
JOIN roles
ON roles_employee.role_id = roles.id
WHERE role_name LIKE '%developer%';
```
```
29. Вывести имена, должности и ЗП всех специалистов по возрастанию.
```
```sql
SELECT employees.employee_name, roles.role_name, salary.monthly_salary
FROM employees JOIN employee_salary
ON employees.id = employee_salary.employee_id
JOIN salary
ON salary.id = employee_salary.salary_id
JOIN roles_employee
ON employees.id = roles_employee.employee_id
JOIN roles
ON roles_employee.role_id = roles.id
ORDER BY employees.employee_name
```
```
30. Вывести имена, должности и ЗП всех специалистов по возрастанию у специалистов у которых ЗП от 1700 до 2300.
```
```sql
SELECT employees.employee_name, roles.role_name, salary.monthly_salary
FROM employees JOIN employee_salary
ON employees.id = employee_salary.employee_id
JOIN salary
ON salary.id = employee_salary.salary_id
JOIN roles_employee
ON employees.id = roles_employee.employee_id
JOIN roles
ON roles_employee.role_id = roles.id
WHERE salary.monthly_salary > 1700 AND salary.monthly_salary < 2300
ORDER BY salary.monthly_salary
```
```
31. Вывести имена, должности и ЗП всех специалистов по возрастанию у специалистов у которых ЗП меньше 2300.
```
```sql
SELECT employees.employee_name, roles.role_name, salary.monthly_salary
FROM employees JOIN employee_salary
ON employees.id = employee_salary.employee_id
JOIN salary
ON salary.id = employee_salary.salary_id
JOIN roles_employee
ON employees.id = roles_employee.employee_id
JOIN roles
ON roles_employee.role_id = roles.id
WHERE salary.monthly_salary < 2300
ORDER BY salary.monthly_salary
```
```
32. Вывести имена, должности и ЗП всех специалистов по возрастанию у специалистов у которых ЗП равна 1100, 1500, 2000.
```
```sql
SELECT employees.employee_name, roles.role_name, salary.monthly_salary
FROM employees JOIN employee_salary
ON employees.id = employee_salary.employee_id
JOIN salary
ON salary.id = employee_salary.salary_id
JOIN roles_employee
ON employees.id = roles_employee.employee_id
JOIN roles
ON roles_employee.role_id = roles.id
WHERE salary.monthly_salary in (1100, 1500, 2000)
ORDER BY salary.monthly_salary
```