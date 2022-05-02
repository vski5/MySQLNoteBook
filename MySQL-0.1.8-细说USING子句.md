
```sql
USE sql_store;

SELECT *
FROM order_items oi
JOIN order_item_notes oin
	ON oi.order_id = oin.order_id
```

假设order_items和order_item_notes这两个表有列的名称是相同的，例如`ON oi.order_id = oin.order_id`，那就可以用USING代替。

写作：
`USING (order_id)`
效果一样。

USING不影响外连接
```sql
USE sql_store;

SELECT 
o.order_id,o.order_date,
c.first_name,c.last_name,
sh.name AS shipper
FROM orders o
JOIN customers c
	USING (customer_id)
LEFT JOIN shippers sh
	USING(shipper_id)
```

多个主键一起才能唯一识别某行的，叫做**复合主键**。

当用复合主键作为识别的时候，
1. 用ON来表示是`ON oi.order_id = oin.order_id AND oi.product_id=oin.product_id`
2. 用USING来表示是`SUING(order_id , product_id)`