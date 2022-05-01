以一个线上商城为例，当发货状态的识别符放在订单的表单里面，识别符所对应的含义又放在其他的表单里，那就要多表连接。

```sql
USE sql_store;

SELECT *
FROM orders o
JOIN customers c
	ON o.customer_id = c.customer_id
JOIN order_statuses os
	on o.status = os.order_status_id 
```
把orders这张表里的连接到customers和order_statuses这两张表，第一个ON后面的`ON o.customer_id = c.customer_id`是保证用户id一样，第二个ON后面的`o.status = os.order_status_id `是保证发货状态码和解释对应上。

简化一下：
```sql
USE sql_store;

SELECT 
o.order_id,o.order_date,
c.first_name,c.last_name,
os.name AS status
FROM orders o
JOIN customers c
	ON o.customer_id = c.customer_id
JOIN order_statuses os
	on o.status = os.order_status_id 
```

[【中字】SQL进阶教程 | 史上最易懂SQL教程！10小时零基础成长SQL大师！！_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1UE41147KC?p=22&spm_id_from=pageDriver)

P22