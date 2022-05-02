隐式连接

FROM选择要连接的两个库，再用WHERE筛选两个库中的连接条件。

例如：正常情况下
```sql
USE sql_store;

SELECT *
FROM order_items oi
JOIN order_item_notes oin
	ON oi.order_id = oin.order_id
```

在隐式连接情况下：
```sql
USE sql_store;

SELECT *

FROM order_items oi , order_item_notes oin

WHERE oi.order_id = oin.order_id
```

一般不建议，不打WHERE来筛选的话就会交叉连接，就寄了。

最好用显示连接，JOIN某表格再ON后面接条件。