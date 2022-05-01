自连接，把一张表跟自己连接起来。
要用不同的别名对待同一张表。

```sql
USE sql_hr;

SELECT *
FROM employees e
JOIN employees m
ON e.reports_to = m.employee_id
```
这个就是把所有的都连过去了，很多重复项。但是第一张表（FROM employees e）的reports_to和第二张表（JOIN employees m）的employee_id对齐了，这样就可以快速找出来谁管理谁。

简化一下：
```sql
USE sql_hr;

SELECT 
	e.employee_id , e.first_name,
	m.first_name AS manager
FROM employees e
JOIN employees m
ON e.reports_to = m.employee_id
```

