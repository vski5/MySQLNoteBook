跨数据库连接

和内连接差不多，但是格式为 库的名称.表单的名称
```sql
USE sql_store;

SELECT *
FROM order_items oi
JOIN sql_inventory.products p
ON oi.product_id = p.product_id
```

假设USE是其他的库，那么就要在order_items前加所在库的前缀。
```sql
USE sql_inventory;

SELECT *
FROM sql_store.order_items oi
JOIN products p
ON oi.product_id = p.product_id
```
这里的products本身就是在sql_inventory里面，就不要加前缀了，不然会报错。