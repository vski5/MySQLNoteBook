# 自然连接（NATURAL JOIN）
自然连接不必打上列名，MySQL自己看着办，基于共同的列连接
```SQL
USE sql_store;

SELECT 
	
	c.first_name
FROM orders o
NATURAL JOIN customers c
```

# 交叉连接（CROSS JOIN）
用交叉连接 连接 第一和第二个表的每条记录。

```SQL
USE sql_store;

SELECT *
FROM customers c
CROSS JOIN orders o 
```

customers里的每条记录都会和orders里的每条记录相结合，所以没写条件。

假如有个型号表（大中小），颜色表（红黄绿），那么就会出现穷举，列出所有的不重复的组合。

这也可以隐式表达：
`FROM customers c , orders o `

```sql
USE sql_store;

SELECT *
FROM shippers sh
CROSS JOIN products pr

-- FROM shippers sh , products pr
```