
# SELECT子句中的子查询


```sql
USE invoicing
;
SELECT 
	invoice_id,
    invoice_total,
    (SELECT AVG(invoice_total)
		FROM invoices) AS aerage
	
FROM invoices
```
子句里的SELECT可以计算来自另外一个表的东西。

# FROM子句中的子查询
```SQL

USE invoicing
;
SELECT *

FROM (

SELECT 
	invoice_id,
    invoice_total,
    (SELECT AVG(invoice_total)
		FROM invoices) AS aerage
	
	FROM invoices

)

```
FROM可以从自己已经选好范围的部分来选择。