
用于查每个人的管理人是谁的自连接代码。
```sql
USE sql_hr;

SELECT 
	e.employee_id , e.first_name,
	m.first_name AS manager
FROM employees e
JOIN employees m
ON e.reports_to = m.employee_id
```

这有一个问题，最大的管理人就不会被显示出来。

用外连接解决这个问题，显示所有员工，不管他有没有被管到。
```sql
USE sql_hr;

SELECT 
	e.employee_id , e.first_name,
	m.first_name AS manager
FROM employees e
LEFT JOIN employees m
ON e.reports_to = m.employee_id
```

