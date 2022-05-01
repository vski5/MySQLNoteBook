内连接（INNER JOIN）在多张表格中检索数据

INNER JOIN里的INNER关键字可写可不写。

连接有两种：内连接和外连接

选择orders这张表里的一切，然后合并orders表里的列和customers表里的列。
关系型数据库中，每个表格都有一个主键列，要使主键表一样，那么就用到ON短语，

```sql
SELECT *
FROM orders
JOIN customers ON orders.customer_id=customers.customer_id
```
选择orders里的所有列加入customers，在主键表一致（`orders.customer_id=customers.customer_id`这两个数据一一被AS了一样，成为一个评判的标准，作为识别码一样）的条件下。

当多张表格有一样的列，就需要增加表名称作为列的前缀，让他生效。

表名称可以简写，但要先赋值。
`FROM order o`这就是把order这个表赋值为o，下面都以用o作为前缀。

```sql
SELECT *
FROM orders o
JOIN customers c ON o.customer_id=c.customer_id
```
此时把order这个表赋值为o，customers赋值为c

```sql
USE sql_store;

SELECT 
order_items.order_id , 
order_items.product_id,
order_items.quantity,
order_items.unit_price
FROM order_items
JOIN products ON order_items.product_id = products.product_id
ORDER BY order_items.order_id DESC
```

简化一下
```sql
USE sql_store;

SELECT 
o.order_id , 
o.product_id,
o.quantity,
o.unit_price
FROM order_items o
JOIN products p ON o.product_id = p.product_id
ORDER BY o.order_id DESC
```

