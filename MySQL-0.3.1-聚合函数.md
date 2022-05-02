
聚合函数，一类内置函数。

就类似excle，有`MAX()`之类的
```sql
MAX() --最大值，单起一列来展示
MIN() --最小值，单起一列来展示
AVG() --平均值，单起一列来展示
SUM() --总值，单起一列来展示
COUNT() --数有多少个（就是记数），单起一列来展示
```


不运行空值，COUNT()不计算空值的，返回非空记录数。
要想算进去空值那就要用星号`COUNT(*)`。

WHERE后面接的条件会影响前面SELECT的聚合函数结果，比如WHERE只选出来了一部分行，那AVG(invoice_total)求得就是这样小部分的平均值。

```sql
SELECT
	MAX(invoice_total)  AS highest,
    MIN(invoice_total) AS lowest,
    AVG(invoice_total) AS average,
    SUM(invoice_total*1.1) AS number_of_voice, --这里面也可以做计算
    COUNT(*) AS total_records
    COUNT(DISTINCT clients_id) AS users_numbers
FROM invoice
WHERE 后面接限制条件
```

DISTINCT可以删除重复项，相同的就会合并，不再有重复
`COUNT(DISTINCT clients_id)`就是计算有多少种clients_id