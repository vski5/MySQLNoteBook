MySQL-1.0.1-数据库表之间的关系-Mysql中的关联查询(内连接，外连接，自连接)

1) 查找文章分类下面的所有文章

		-- SELECT * FROM article where cate_id=1

		-- SELECT * FROM article 

2) 查找文章的时候显示文章的分类  笛卡尔积连接，用逗号和WHERE

-- SELECT article.id as id ,article.title as title ,article.state as state, article_cate.title as cate FROM article,article_cate WHERE article.cate_id=article_cate.id
-- article_cate是被查询的表，最终展示的表的基础
--  笛卡尔积连接是最慢的

3) 查找文章的时候显示文章的分类 内连接  INNER JOIN   ON 

-- SELECT article.id as id ,article.title as title ,article.state as state, article_cate.title as cate FROM article INNER JOIN article_cate ON  article.cate_id=article_cate.id
-- article_cate是被关联的表 ， ON是关联条件 

4） 多对多的关系，使用中间表

5） NAME这种保留字被用作表的列的列名的话，加上重音符号\` ，\`name`

6) 左外连接 LEFT JOIN ， 就是LEFT JOIN后面的表在左边
-- SELECT * FROM student LEFT JOIN lesson_student ON student.id=lesson_student.student_id 
AND
lesson_student.lesson_id=2

7) 右外连接 RIGHT JOIN  ， 就是RIGHT JOIN后面的表在右边
-- SELECT * FROM student RIGHT JOIN lesson_student ON student.id=lesson_student.student_id
AND 
lesson_student.lesson_id=2