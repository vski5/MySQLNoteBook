# ANY关键字
`IN `
和 
`= ANY`
等效

要带等号。

```sql
SELECT *
FROM clietns
FROM client_id IN(      
    SELECT client_id, count(*)
    FROM invoices
    GROUP BY client_id
    HAVING COUNT(*) >= 2
)
```
和
```sql
SELECT *
FROM clietns
FROM client_id = ANY(      
    SELECT client_id, count(*)
    FROM invoices
    GROUP BY client_id
    HAVING COUNT(*) >= 2
)
```
等效