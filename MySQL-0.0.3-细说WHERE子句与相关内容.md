可以用where进一步筛选结果，比如说此处筛出来customer_id为1的结果：`WHERE customer_id = 1`

另外的例子：
where
```SQL
USE sql_store;

SELECT 
	name,
    unit_price,
    (unit_price*1.1) AS `new price`
FROM products
WHERE unit_price>2
```

<,>,<=，>=，!=之类的被称为比较运算符。

比较运算符不止是操作数字，还能对元素经行比较，就行go中if后的条件。
比如选出所有state不在 "VA"的
所选的内容外面套一层单引号或者双引号都可以。
一般用单引号。
```SQL
USE sql_store;

SELECT 
	customer_id
    state
FROM customers
WHERE state != `VA`
```

对于日期，一样要套一层引号。
日期的标准格式为：0000-00-00，年月日。
```sql
USE sql_store;

SELECT *
FROM customers
WHERE birth_date>`1990-01-01`
```

