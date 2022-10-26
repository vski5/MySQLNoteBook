MySQL-1.0.3-事务和锁

1) 事务处理：保证多条SQL语句要么全部执行，要么全部不执行。比如银行转账，出金和入金都要一起执行才行。

    BEGIN 开始一个事务
    COMMIT 事务确认

    ROLLBACK 事务回滚（失败了就手动操作一下）

    例子：
    ```
    begin;
    update 表名 set 列名 = 值 WHERE 条件 = 1 ;
    update 表名 set 列名2 = 值2 WHERE 条件 = 2 ;
    COMMIT;
    ```
    要是失败了，就手动操作一下，ROLLBACK 事务回滚

2) 表级锁:
    1) 读锁,都能读，都不能写入，只有上锁的人能解锁。== 比如抢购的时候，第一个抢到的人将表执行读锁 ==
        ```
        lock table user read;
        unlock tables;
        ```
        ```
        lock table 表名 read;
        unlock tables;
        ```
    2) 写锁,只有上锁的人能读，能写，其他人什么也干不了，只有上锁的人能解锁。
        ```
        lock table user write;
        unlock tables;
        ```
        ```
        lock table 表名 write;
        unlock tables;
        ```
