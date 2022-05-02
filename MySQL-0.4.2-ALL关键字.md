# ALL关键字
MySQL中`ALL`和`MAX`差不多。
算子查询里的总和的。

对于求MAX(invoice_total)，复合筛选条件里的最大值。

可以MAX(invoice_total)先在自查询里筛出来。
```sql
SELECT *
FROM invoices
WHERE invoice_total > (
  	SELECT MAX(invoice_total)
  	FROM invoices
  	WHERE client_id = 3
	  )
```

也能在子查询的括号前用ALL代替

```sql
SELECT *
FROM invoices
WHERE invoice_total > ALL( 
	SELECT invoice_total
  	FROM invoices
  	WHERE client_id = 3
)
```

