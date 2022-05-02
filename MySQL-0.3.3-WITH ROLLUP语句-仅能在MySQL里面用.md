# WITH ROLLUP语句
用于聚合值的列，求和。汇总数据。

仅能在MySQL里面用。

对于group by 后的数据进行筛选。

```MySQL
SELECT
	client_id,
    SUM(invoice_total) AS total_sales
FROM invoice
JOIN clients USING (client_id)
WHERE invoice_date >= '2020-07-01'

GROUP BY client_id WITH ROLLUP

ORDER BY total_sales DESC
```

会在最后一行汇总invoice_total的总和，只有用于SUM()

如果GROUP BY 后面有多个分组依据，就在做个分组一句后面算总和。

比如说：
```sql
USE store ;
SELECT
	state,
    city,
    SUM(points) AS total_points
FROM customers

JOIN orders USING (customer_id)

WHERE points >= 20

GROUP BY state,city WITH ROLLUP

ORDER BY total_points DESC
```

结果是：
![[WITH ROLLUP.png]]


TX里的城市ARLINTON的总和，然后是TX的总和。