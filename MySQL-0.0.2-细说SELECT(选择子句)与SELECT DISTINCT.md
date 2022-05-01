
选择数据库中的某些列，用逗号隔开：`SELECT customer_id,first_name`
选择数据库中的全部列：`SELECT *`

返回的列会按顺序排列，比如`SELECT last_name,first_name，customer_id`排列的顺序就是last_name,first_name，customer_id。

一个对列的操作示例：
```sql
SELECT last_name,first_name，points+10
```
此处的points+10是一个算数表达式，最后输出的都会在原有的数据上+10.

```sql
SELECT last_name,first_name，points , points+10
```

points , points+10是可以在一起被展示出来的。

同理可得，可以展示其他的相同列，用更复杂的计算公式，把每一列的标题当作一个常量。

```sql
USE sql_store;

SELECT 
	last_name,
	first_name,
    points,
    (points+10)*100 AS discount_factor
FROM customers
```

`(points+10)*100 AS discount_factor`让下面输出的表格显示`(points+10)*100` 为` discount_factor` 。

空格一般用下划线代替，实在想用空格就把内容用单/双引号包起来。比如：
```sql
(points+10)*100 AS `discount factor`
(points+10)*100 AS "discount factor"
```

**如何得到某一项的唯一列表**，比如得到所在的州都是VA的唯一列表
可以用关键字DISTINCT。
DISTINCT可以删除重复项。

distinct
adj. 不同的，有区别的；清楚的，明显的；确切的

`SELECT DISTINCT state`
这样所有相同`state`的就会合并，不再有重复

