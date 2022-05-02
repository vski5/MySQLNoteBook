# 多表连接
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

# 复合连接条件

之前的表都是单一列识别，比如说都是customer_id唯一识别。

复合连接条件就是多个列作为识别条件。

例如order_id和product_id这两列作为一个筛选，同时满足的设为某个状态，那么ON后面另外的语句用AND连接，这就是复合连接条件。

```sql
USE sql_store;

SELECT *
FROM order_items oi
JOIN order_item_notes oin
	ON oi.order_id = oin.order_id
	AND oi.product_id = oin.product_id
```
