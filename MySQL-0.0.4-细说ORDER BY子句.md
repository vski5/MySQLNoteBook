如何为数据排序

用ORDER BY给数据排序，比如说用first_name为依据排序：`ORDER BY first_name`

点击表单的🔧扳手符号，可以增删查改，其中黄色标志就是表但的主键列，默认以其排序。

关系型数据库中，每个表格都有一个主键列。

主键列必须唯一识别表中的记录，相当于身份证号不能重复。

用first_name为依据排序：`ORDER BY first_name`
想降序排序就要用到`DESC`
例子为`ORDER BY first_name DESC`

可以用state排序，然后在每个state里面用first_name为依据排序。
`ORDER BY state,first_name`

可以用state降序排序，然后在每个state里面用first_name为依据排序。
`ORDER BY state DESC,first_name`

MySQL里面，无论数据在不在SLECT里面都能用ORDER BY 来排序。


下面的2指的是SELECT里的第二个元素，可以用AS制造出来的别名来排序。
SELECT可以选择不存在的值，但要用别名AS，这结合一些复杂的算式有妙用。比如说把数量乘以单价AS为一个别名，再用这个别名排序
```SQL
USE sql_store;

SELECT 
	name,
    unit_price,
    (unit_price*1.1) AS `new price`
    100 AS points
FROM products
ORDER BY `new price`,2 DESC,points
```

```sql
USE sql_store;

SELECT 
order_id,product_id,quantity,unit_price,
quantity*unit_price AS total_price

FROM order_items
WHERE order_id = 2
ORDER BY total_price DESC
```

