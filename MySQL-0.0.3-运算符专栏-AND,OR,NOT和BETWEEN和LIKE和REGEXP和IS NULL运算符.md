一定要区分好\`和 '
# AND,OR,NOT
```sql
USE sql_store;

SELECT *
FROM customers
WHERE birth_date>'1990-01-01' AND points>100
```
就跟医学统计学里面差不多。
和、或、否。
AND 二者都要满足才行。
OR 满足其一就行。
NOT 不能满足才行。

AND被优先评价，类似四则运算，，也能用括号提高优先级。

同类也必须写出来从哪一列出来的，比如
`WHERE STATE='VA' AND STATE='GA'`

简化手段为用IN和括号：
```sql
WHERE STATE IN ('VA','GA')
```

# BETWEEN运算符
```sql
WHERE points>100 AND points<1100
```
可以写作
```sql
WHERE points BETWEEN 100 AND 1100
```
BETWEEN 100 AND 1100，很口语了，从100到1100之间。

用在日期上
```sql
USE sql_store;

SELECT *
FROM customers
WHERE birth_date BETWEEN '1990-01-01' AND '2000-01-01'
```

# LIKE运算符
取特定字符串开头的数据。

**用%表示任意字符数，可以摆在任意位置，不止是末尾。**

比如取b开头的名字，就用：
`WHERE last_name LIKE "b%"  `

比如取bru开头的名字，就用：
`WHERE last_name LIKE "bru%"  `

比如取b开头且为ld结尾的名字，就用：
`WHERE last_name LIKE "b%ld"  `

比如取名字里有b的名字，就用：
`WHERE last_name LIKE "%b%"  `

**用_表示一个字符数，可以摆在任意位置，不止是末尾。**

比如取brushfield这个名字，可以忽略某一个字符，就用：
`WHERE last_name LIKE "brush_ield"  `

比如取名字里开头b，结尾y，中间有四个字母的名字，就用：
`WHERE last_name LIKE "b____y  `

# REGEXP 正则表达式
比如取名字里有b的名字，就用：
`WHERE last_name LIKE "%b%"  `
在REGEXP里面就是
`WHERE last_name REGEXP "b"`

用`^`表示文件开头，比如取bru开头的名字，就用：
`WHERE last_name REGEXP "^bru"  `

用$表示文件结尾，比如取ld结尾的名字，就用：
`WHERE last_name REGEXP "ld$"  `

用 | 添加or类的条件，比如取包含mac或者rose或者以ld结尾的名字，就用：
`WHERE last_name REGEXP "ma|rose|ld$"  `

用方括号[]表示其一更准确地说是表达一个范围，比如搜索字母e前面有g或者i或者m的三者之一：`WHERE last_name REGEXP "[gim]e"  `
这会去搜索包含ge、ie、me的名字。
在搜索[abcde]e的时候，可以直接写成
`WHERE last_name REGEXP "[a-e]e"  `
这和`WHERE last_name REGEXP "[abcde]e"  `是等价的。

# IS NULL 运算符
搜索缺失了熟悉的记录。

比如搜所有在phone这一栏缺失的customer
```sql
USE sql_store;

SELECT * 
FROM sql_store.customers
WHERE phone IS NULL
```

## 可以结合NOT使用: IS NOT NULL
比如搜所有在phone这一栏**没有**缺失的customer
那就直接`WHERE phone IS NOT NULL`

```sql
USE sql_store;

SELECT * 
FROM sql_store.customers
WHERE phone IS NOT NULL
```