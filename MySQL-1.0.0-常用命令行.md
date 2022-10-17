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

12) 删除指定的数据

13) 按指定的数据排序

14) 统计数量

15) Limit

16) 删除指定的表

15) 删除指定的数据库
