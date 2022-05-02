# GROUP BY

```SQL
SELECT
	client_id,
    SUM(invoice_total) AS total_sales
FROM invoice
JOIN clients USING (client_id)
WHERE invoice_date >= '2020-07-01'

GROUP BY client_id

ORDER BY total_sales DESC
```
GROUPBY
`GROUP BY client_id`用`client_id`作为分组的一句，上面的`SUM`算的是每一组的数据
![[GROUPBY.png]]

按组计算。

WHERE是在GROUP前执行的

# Having语句Group BY在行分组后 筛选数据
```sql
SELECT
	client_id,
    SUM(invoice_total) AS total_sales
    count(*) AS nunber_of_invoice
FROM invoices
GROUP BY client_id
HAVING total_sales > 500 AND number_of_invoice >5  -- having也可以用复合查询
```

having后的内容，必须要在select中出现过。HAVING用的可以是AS后面的别名。

这也是having和where的区别，where不需要在 select中出现过