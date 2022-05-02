# 列属性，走扳手🔧那儿进。
最左边一列是列的名称。

然后数据类型，
比如VARCHAR(50)表示可变字符，且最大为50个字符。
比如CHAR(50)，最大为50个字符，但是不够50个的话，剩下的用空格填充，很浪费空间。

PK意为主键，会显示黄色标识，用于唯一识别。

NN，not null，决定是否可以写空值，勾上就不能写。

AI，自动递增，可用于主键记数。

最后的default决定默认值。

![[列属性.png]]

# 插入 INSERT INTO

## 加入完完整整的一行
```sql
INSERT INTO 要插入的表的名称
VALUES (值用逗号隔开依次填入每一列的值)
```

```sql
INSERT INTO customers
VALUES (DEFAULT,'john','smith',NULL,DEFAULT,'ADRESS','CITY','CA',DEFAULT)
```
DEFAULT为默认值。

此处customers是自动递增的，所以就直接默认值让系统生成就完事儿了。

字符串和日期要在引号里面

NN，not null，决定是否可以写空值，勾上就不能写。
所以第三个和第四个可赋值可不赋值。
用NULL来不赋值。
意为默认值标出来了就是NULL，所以可以用默认值DEFAULT，来表示NULL。



## 加入想取赋值的列，不赋值的直接默认值

```SQL
INSERT INTO 
customers(first_name,last_name,birth_date,address,city,state)
VALUES 
(DEFAULT,'john','smith','2000-01-01','ADRESS','CITY','CA')
```

括号内加的是，想去赋值的列的名字，不需要赋值（且有默认值允许不去赋值）的直接不写进去就行。

这就少赋值了几个，没辅值的直接默认值.

按顺序赋值即可，不一定要和表中的顺序一样，比如first_name,last_name颠倒顺序之后，VALUES里面的相对应的数据也要赋值。

## 插入单行的完整操作如下：

```sql
USE sql_store;

INSERT INTO customers
VALUES (DEFAULT,'john','smith',NULL,DEFAULT,'ADRESS','CITY','CA',DEFAULT)
```
然后可以看到表customers多了一行值。

# 插入多行INSERT INTO
以表shippers为例。
```sql
USE sql_store;

INSERT INTO shippers (name)
VALUES ('jack'),('jack2'),('jcak3')
```
括号间用逗号隔开，每个括号内的元素必须完整。

这里有所省略，省略的是会自动增加的主键列，不写就默认生成。

# 插入分层行
用在母子表里面，比如说orders是母表，里面部分应该呈现的内容在子表order_items里面，用`order_items JOIN orders ON 某某=某某 AND 某=某`，来与之对应上。

母表中可能有多个子表，子表也能继续套娃。

下面会用到一个新知识：`LAST_INSERT_ID()` , 字面作用,能返回插入新行时MySQL生成的id。

```sql
USE sql_store;

INSERT INTO orders 
VALUES (DEFAULT,1,'2001-01-01',1,DEFAULT,DEFAULT,DEFAULT)
;
INSERT INTO order_items
VALUES 
	(last_insert_id(),1,1,2.99),
    (last_insert_id(),2,1,3.99)
```
orders存放的是顾客的消息，order_items存放的是订单的消息，此处的两个`LAST_INSERT_ID`是同一个数字。

这段代码的意思是创造一个顾客。（在表orders中）

然后给他（用`LAST_INSERT_ID`）创造一个单号（order_id），单号一样就相当于合并了。（在表order_items中）

# 更新单行 UPDATE SET

```SQL
SELECT * FROM sql_invoicing.invoices;

UPDATE invoices
SET payment_total = 0 , payment_date= 10
WHERE invoice_id =1
```

```SQL
SELECT * FROM sql_invoicing.invoices;

UPDATE 表
SET 列的名字 = 值 , 列的名字 = 值
WHERE 选择条件
```

值可以为NULL和DEFAULT，如果支持的话，这样可以清空错误的数据。
```SQL
SELECT * FROM sql_invoicing.invoices;

UPDATE invoices
SET payment_total = DEFAULT , payment_date= NULL
WHERE invoice_id
```

在设计模式下（🔧）打开表,看允不允许。

值可以为一段算式，可以用列的名字作为某某数字的别名。

# 更新多行
条件更加宽松就行。
但默认的MySQL一次只能更新一行。
改设置，取消safe update就行。
```SQL
USE sql_invoicing
;
SELECT * FROM invoices
;
UPDATE invoices
SET payment_total = DEFAULT , payment_date= NULL
WHERE client_id IN (3,4)

```

给每个payment_total加50，
`payment_total = payment_total + 50`
```SQL
USE sql_invoicing
;
SELECT * FROM invoices
;
UPDATE invoices
SET payment_total = payment_total + 50 , payment_date= NULL
WHERE client_id=3
```

# 在UPDATE中使用子查询
接着上面的例子，假设没有client_id，只有名字，那就要从名字到client_id.

此处从number拿到client_id。
充当参数的选择语句要扩在括号里。

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

这个充当参数的就是子查询。

# 删除行 DELETE

```SQL
DELETE FROM invoices
WHERE client_id=1
```
同样可以加上子查询

# 恢复数据库

把data文件夹里的sql文件再跑一边。
