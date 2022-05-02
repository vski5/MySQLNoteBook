
# 从内连接到外连接

每次用JOIN都是用内连接，即便省略inner.

当用于筛选的条件为空的时候，就不会被显示（选择）出来。

想显示用来作为连接条件为空的列的时候，就要用外连接

比如说
```sql
USE sql_store;

SELECT *
FROM order_items oi
JOIN order_item_notes oin
	ON oi.order_id = oin.order_id
```
当某些行的order_id值为NULL，那么这些行就不会被显示出来。因为这些行不满足条件，自然不会选出来。

# 外连接：LEFT JOIN 和 RIGTH JOIN

## LEFT HOIN
所有在左边的表的都会被返回(显示出来)。
```sql
SELECT *
FROM order_items oi
LEFT JOIN order_item_notes oin
	ON oi.order_id = oin.order_id
```

此时所有order_items这个表的行就会被列出来。不管符不符合条件。

## RIGHT HOIN
所有在右边的表的都会被返回(显示出来)。
```sql
SELECT *
FROM order_items oi
RIGHT JOIN order_item_notes oin
	ON oi.order_id = oin.order_id
```

此时所有order_item_notes这个表的行就会被列出来。不管符不符合条件。

## 规范
可以写作`LEFT OUTER JOIN `或者`LEFT JOIN `。
右连接同理，一个作用。

`OUTER`这个关键词可有可无，也算是一个提醒。


# 多表外连接
```sql
USE sql_store;

SELECT *
FROM orders o
LEFT JOIN customers c
	ON o.customer_id = c.customer_id
JOIN order_statuses os
	on o.status = os.order_status_id 
```
假设
`ON o.customer_id = c.customer_id`
这个条件有一部分不满足，那么还是只会显示满足的内容，因为这是纯JOIN，但上面的LEFT JOIN 就是外连接，想让满不满足的都显示，那就
```sql
USE sql_store;

SELECT *
FROM orders o
LEFT JOIN customers c
	ON o.customer_id = c.customer_id
LEFT JOIN order_statuses os
	on o.status = os.order_status_id 
```

这个LEFT（或者RIGHT）只解决向左或向右一个保留词内的条件。

尽量只走一个方向的连接，最好是左连接。

通过修改表达，LEFT的保留某些表格的保留策略，可以做到只显示下了单的客户等效果。

比如说
```sql
USE sql_store;

SELECT ord.order_id,ord.order_date,cu.first_name,sh.name
FROM orders ord
JOIN shippers sh
	ON ord.shipper_id = sh.shipper_id
LEFT JOIN customers cu
	on ord.customer_id = cu.customer_id
ORDER BY ord.customer_id
```
输出结果就是只显示有订单状态的客户。


```sql
USE sql_store;

SELECT ord.order_id,ord.order_date,cu.first_name,sh.name
FROM orders ord
LEFT JOIN shippers sh
	ON ord.shipper_id = sh.shipper_id
LEFT JOIN customers cu
	on ord.customer_id = cu.customer_id
ORDER BY ord.customer_id
```
输出结果是无论有没有订单状态，都是输出。



