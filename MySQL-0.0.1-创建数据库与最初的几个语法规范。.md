
SQL规范->SQL的代码适配任意关系型DBSM，包括并不限于Oracle和MySQL.

一定要区分好\`和 '

sys：MySQL内部运行用的数据库。

最开始建数据库的时候，点⚡标 运行文件后点击刷新键，才能显示出来，还是没有的话就关掉重开。
一开始有几个table也没有数据，然后我关了重新开就有了，table旁边有一个更新的标志，我猜一开始打开要加载一段时间，或者说这次没有加载好

SQL语法不区分大小写，但一般命令写大写，被操作的文件用本身的大小写规则。
别用中文的逗号，会报错，还不好看出来。
注释语句前面加双横线和一个空格：`-- `，类似GO里的`//`
 
基础查询的语句：
1. 使用某个数据库：`USE sql_store`
2. 选择数据库中的某些列，用逗号隔开：`SELECT customer_id,first_name`
3. 选择数据库中的全部列：`SELECT *`
4. 明确想要库中查询的表，比如说这里想查customers这个表：`FROM customers`
5. 用分号终止每条语句，比如说上面的1、2条就要用分号隔开，但3、4就不用隔开:  ` ; `
```sql
USE sql_store;

SELECT *
FROM customers

```
执行之后的结果是输出customers这个表里的所有列。

6. 可以用where进一步筛选结果，比如说此处筛出来id为1的结果：`WHERE customer_id = 1`
7. 用ORDER BY给数据排序，比如说用first_name为依据排序：`ORDER BY first_name`
```sql
USE sql_store;

SELECT *
FROM customers
-- WHERE customer_id=1 这里的WHERE变成了注释，如果不删的话下面的ORDER BY 排序就没用了。

ORDER BY first_name
```

`SELECT`，`ORDER BY ` , `WHERE `之类的子句是可选的，且顺序对结果有影响，糟糕的顺序会导致报错。
比如
```sql
USE sql_store;

SELECT *
ORDER BY first_name
FROM customers
```
就会报错。

**本次的顺序推荐依次就是**
>SELECT , FROM , WHERE , ORDER BY

顺序不可变，不然会报错。

```sql
SELECT * FROM customers
```
不必用 ; 隔开的语句可以放一行，但是为了格式美观和复杂编程是不推荐的。


```sql
SELECT last_name,first_name
```
也能表示为
```sql
SELECT 
	last_name,
	first_name
```

sql语句只认分号，tab和空格回车统统不认。

怎么好看怎么写。