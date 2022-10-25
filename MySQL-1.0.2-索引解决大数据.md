MySQL-1.0.2-索引解决大数据

1) 索引会提高查询速度，减慢修改速度。

2) 模拟百万条大数据的方法：
    模拟表newtable包含 自增的ID列，用来模拟的fake列。
    INSERT INTO 表名(`用来模拟的fake列的列名，外面用重音符号包裹`) SELECT 用来模拟的fake列的列名 FROM 这个表
    INSERT INTO newtable(`fake`) SELECT fake from newtable

    --SELECT 用来模拟的fake列的列名 FROM 这个表
    --意思是查询这个表里的这一行

3) 创建普通索引
基本语法：
CREATE INDEX indexName ON mytable(username);
create index index_name on class(name);

4) 查看索引
show index from table_name
show index from class

5) 删除索引
drop index index_name on class;

6) 创建唯一索引（主键是一种唯一索引）
create unique index index_name on class(name);

7) 另外的一种创建和删除方式
alter table class add index index_name(name);
alter table class add unique index_name(name);
alter table class drop index index_name