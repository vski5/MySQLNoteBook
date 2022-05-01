```SQL
USE sql_store;

SELECT *
FROM customers
LIMIT 3
```

LIMIT 3 只返回前三条消息，如果只有两条的话，会得到全部的两个参数。

用这个给网页分页，比如说每一页有LIMIT 3 个，然后第一页有123，第二页有456，巴拉巴拉。

查第三页的时候，就是`LIMIT 6,3`
6为偏移量，3为查询数量，就是说，跳过前六个再查三个。

```sql
USE sql_store;

SELECT *
ORDER BY  points DESC
LIMIT 3
```
查points最高的三个人。
