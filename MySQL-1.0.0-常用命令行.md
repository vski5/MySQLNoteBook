# MySQL-1.0.0-常用命令行.md

**记得--在每个命令行结束 加上 分号 ；**

**记得--MySQL命令没有大小写的区别**

1) 显示当前存在的数据库

    `show databases; `

2) 选择你所需要操作的数据库

    `use 数据库名字 ` 
    这个可以不用加冒号。

3) 查看当前数据库有哪些表

    `show tables;`

4) 查看一张表的所有内容

    `select * from 表的名字; `

5) 数据库设置中文编码

    `  set names utf8; `

6) 创建一个数据库

    ` creat database 数据库名字 ； `

7) 在数据库里创建一张表
```
create table players(
username varchar(20), 
sex int(1), 
status int(1)
); 

```
```
create table 表的名字(
列的名字 列的类型(列的长度/集合), 
username varchar(20), 
sex int(1), 
status int(1)
); 

```
记住--即使在命令行中建表，也是以分号结束。

8) 显示表的结构
`describe 表的名字`

9) 给表插入一条数据
```
insert into players(username,sex,status) values ("namenamename",1,1);
```
```
insert into 表的名字(键key,sex,status) values ("值value",值value,1);
```

10) 根据条件筛选指定的数据
```
SELECT * FROM players WHERE username = 'namenamename' ；
SELECT * FROM 表的名字 WHERE 列的名字 = 列的值 ；
```
11) 修改指定的数据

`UPDATE 表的名字 SET 列名key = 值value WHERE 列名='此列对应的某一行的值';`

`UPDATE players SET status = 990 WHERE username='user111';`

12) 删除指定的数据

` DELETE FROM 表的名字 WHERE 列名='此列对应的某一行的值' ;  `

` DELETE FROM players WHERE username='user111' ;  `

13) 按指定的数据排序

`SELECT * FROM 表的名字 ORDER BY 列名 DESC; --按照 列名 倒叙排序 `

`SELECT * FROM players ORDER BY status DESC; --按照 status 倒叙排序 `

14) 统计数量

`  select count(第几列，能写成 * ) from 表的名字 ;  `

`  select count(1) from players ;  `

15) Limit（限定查表）
```
--select 列名,列名 from 表的名字 limit 查询前几条;
select id,name from nav limit 2;
--select 列名,列名 from 表的名字 limit 跳过几条,查询几条;
select id,name from nav limit 2,2;
```

16) 删除指定的表

`DROP TABLE 表名;`

`DROP TABLE test;`

17) 删除指定的数据库

`DROP DATABASE book; `

`DROP DATABASE 数据库名字; `
