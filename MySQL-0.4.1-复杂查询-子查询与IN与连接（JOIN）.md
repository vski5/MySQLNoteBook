# 子查询
又不是没学过

```sql
USE sql_invoicing
;
SELECT * FROM invoices
;
UPDATE invoices
SET payment_total = payment_total + 50 , payment_date= NULL
WHERE client_id=(

SELECT number 
FROM invoices
WHERE number = '91-953-3396'

)

```
括号内找的是满足`WHERE number = '91-953-3396'`这个条件的`FROM invoices`这个表格的`client_id` 。


# IN运算符写子查询

IN之前用于多选一满足其可的or类的关系。

比如说 `where client_id IN (1,2,3)`

NOT IN 就是不包括在内的。

例如，给payment_total>20的统统加50：
```sql
USE sql_invoicing
;
SELECT * FROM invoices
;
UPDATE invoices
SET payment_total = payment_total + 50 , payment_date= NULL
WHERE client_id NOT IN (
SELECT number 
FROM invoices
WHERE payment_total<=20
)

```

# 子查询 VS 连接（JOIN）

JOIN和ON配合（还有USING() ）的时候，有筛选作用.
自连接也算一种查询。
各有优劣。