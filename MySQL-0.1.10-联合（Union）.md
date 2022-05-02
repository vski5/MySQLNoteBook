普通的join会联合多张表的列，把某个表的列加到另外一个表里。

想直接加一列，来进行注释，那就在SELECT里面操作。

```sql
USE sql_store;

SELECT 
	o.order_id,
	"active" AS something
FROM orders o
```

这会显示两列，一列o.order_id，另外一列名为something，里面的内容是字符串active

通过鼠标框选，可以限定执行的语句，只执行框选内的语句。

为某些条件赋予标注，就用这个方法。
比如把时间大于2019年的标注为active，小于的标为noactive
```sql
USE sql_store;

SELECT 
	o.order_id,o.order_date,
	"active" AS something
FROM orders o
WHERE o.order_date>='2019-01-01'
;
SELECT 
	o.order_id,o.order_date,
	"NOactive" AS something
FROM orders o
WHERE o.order_date<'2019-01-01'
```
注意两端SELECT之间有个分号。
还有，这里使用WHERE筛选，而不是用ON，ON用在JOIN后面。

此处的输出，只有NOactive这个状态的，也就是在后面的哪个代码整出来的，
用UNION合并两次查询的结果。

```sql
USE sql_store;

SELECT 
	o.order_id,o.order_date,
	"active" AS something
FROM orders o
WHERE o.order_date>='2019-01-01'
UNION 
SELECT 
	o.order_id,o.order_date,
	"NOactive" AS something
FROM orders o
WHERE o.order_date<'2019-01-01'
```

**顺序推荐依次就是**
>SELECT , FROM ,JOIN , ON , WHERE , ORDER BY

顺序不可变，不然会报错。

也可以用到不同表格里面，连接不同表格。就是说FROM后面跟的条件（表格名）可以不一样

这是一个增加行的方法，比如说，在同一个元素不同名字的时候，可以用UNION合并，都是客户名，一个叫客户名1，另外一个表格里叫客户名2，那就可以用UNION连到一起。
在上面的SELECT的名字作为列名。
