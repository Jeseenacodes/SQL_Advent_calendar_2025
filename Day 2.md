Tables
- toy_production(toy_id, toy_name, production_date)
- toy_delivery(toy_id, child_name, delivery_date)

```sql
INSERT INTO toy_delivery (toy_id, child_name, delivery_date) VALUES
(1, 'Emma Johnson', '2024-12-24'),
(3, 'Olivia Brown', '2024-12-25'),
(5, 'Noah Davis', '2024-12-24'),
(7, 'Ava Wilson', '2024-12-25'),
(8, 'Sophia Martinez', '2024-12-24'),
(10, 'Mason Garcia', '2024-12-25'),
(12, 'Isabella Rodriguez', '2024-12-24');
```

```sql
INSERT INTO toy_production (toy_id, toy_name, production_date) VALUES
(1, 'Robot Dog', '2024-11-01'),
(2, 'Teddy Bear', '2024-11-02'),
(3, 'Building Blocks', '2024-11-03'),
(4, 'Doll House', '2024-11-04'),
(5, 'Race Car', '2024-11-05'),
(6, 'Puzzle Set', '2024-11-06'),
(7, 'Train Set', '2024-11-07'),
(8, 'Action Figure', '2024-11-08'),
(9, 'Board Game', '2024-11-09'),
(10, 'Stuffed Elephant', '2024-11-10'),
(11, 'Remote Control Helicopter', '2024-11-11'),
(12, 'Art Set', '2024-11-12');
```

### Santa wants to analyze which toys that were produced in his workshop have already been delivered to children. You are given two tables on toy production and toy delivery — can you return the toy ID and toy name of the toys that have been delivered?
```sql
SELECT DISTINCT tp.toy_id, tp.toy_name
FROM toy_production AS tp
INNER JOIN toy_delivery as td ON tp.toy_id = td.toy_id 
ORDER BY tp.toy_id
```
Output: 

| toy_id | toy_name         |
|--------|------------------|
| 1      | Robot Dog        |
| 3      | Building Blocks  |
| 5      | Race Car         |
| 7      | Train Set        |
| 8      | Action Figure    |
| 10     | Stuffed Elephant |
| 12     | Art Set          |

### Undelivered toys
```sql
SELECT tp.toy_id, tp.toy_name
FROM toy_production tp
LEFT JOIN toy_delivery td ON tp.toy_id = td.toy_id
WHERE td.toy_id IS NULL;
```

### Counting deliveries
```sql
SELECT 
    tp.toy_id, tp.toy_name,
    COUNT(td.toy_id) AS delivery_count
FROM toy_production tp
LEFT JOIN toy_delivery td ON tp.toy_id = td.toy_id
GROUP BY tp.toy_id, tp.toy_name
ORDER BY delivery_count DESC;
```



