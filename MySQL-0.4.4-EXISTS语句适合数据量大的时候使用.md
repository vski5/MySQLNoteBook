EXISTS能提高运算效率，适合数据量大的时候使用。

EXISTS反悔的结果会是以一个布尔值。

查找有client_id的客户
一般解法
```sql
SELECT *
FROM clients
WHERE client_id IN  (  

  SELECT DISTINCT client_id       
  FROM invoices
  )
```

EXISTS解法
```SQL
SELECT *
FROM clients c
WHERE EXISTS (         
  SELECT client_id       
  FROM invoices
  WHERE client_id = c.client_id

  )

```
内连接与外连接相关联了。

子查询不给外查询返回结果，避免子查询生成的量表过大。
只返回合` WHERE client_id = c.client_id  `条件的结果。
如果有的话，返回ture，反之false。



