

Tables
- grinch_prank_ideas(prank_id, target_name, prank_description, evilness_score, created_at)

### **CREATE TABLE**

```sql
CREATE TABLE grinch_prank_ideas (
    prank_id INT PRIMARY KEY,
    target_name VARCHAR(100),
    prank_description VARCHAR(255),
    evilness_score INT,
    created_at DATETIME
);
```

### **INSERT DATA**

```sql
INSERT INTO grinch_prank_ideas 
(prank_id, created_at, target_name, evilness_score, prank_description) 
VALUES
(1, '2024-11-01 08:00:00', 'Mayor', 7, 'Replace his toupee with a bird''s nest'),
(2, '2024-11-03 10:30:00', 'Mayor', 9, 'Steal all his ceremonial sashes'),
(3, '2024-11-05 14:20:00', 'Mayor', 5, 'Fill his office with Christmas carolers at 5am'),
(4, '2024-11-02 09:15:00', 'Cindy-Lou', 3, 'Hide all her hair ribbons'),
(5, '2024-11-04 11:00:00', 'Cindy-Lou', 6, 'Replace her hot cocoa with pickle juice'),
(6, '2024-11-01 07:30:00', 'Toy Factory', 10, 'Reverse all the assembly line directions'),
(7, '2024-11-06 16:45:00', 'Toy Factory', 8, 'Replace toy stuffing with onions'),
(8, '2024-11-02 13:20:00', 'Post Office', 9, 'Mix up all the address labels'),
(9, '2024-11-07 10:00:00', 'Post Office', 6, 'Replace stamps with stickers that say ''Bah Humbug'''),
(10, '2024-11-03 18:30:00', 'Town Square', 10, 'Remove all the Christmas lights'),
(11, '2024-11-08 12:15:00', 'Town Square', 10, 'Replace the Christmas tree with a cactus'),
(12, '2024-11-04 06:45:00', 'Bakery', 8, 'Replace sugar with salt in all recipes'),
(13, '2024-11-05 15:30:00', 'Bakery', 7, 'Steal all the gingerbread men'),
(14, '2024-11-09 08:00:00', 'Bakery', 5, 'Paint all the cookies green'),
(15, '2024-11-06 09:30:00', 'Church Choir', 6, 'Replace hymn books with phone books'),
(16, '2024-11-07 14:00:00', 'Church Choir', 9, 'Train Max to howl during performances'),
(17, '2024-11-08 07:15:00', 'School', 4, 'Replace all chalk with soap'),
(18, '2024-11-09 11:45:00', 'School', 7, 'Change all clocks to show wrong time'),
(19, '2024-11-10 13:00:00', 'Mayor', 9, 'Swap his speech with a recipe for roast beast'),
(20, '2024-11-10 16:30:00', 'Cindy-Lou', 10, 'Tell her Santa isn''t real');
```

---

### The Grinch has brainstormed a ton of pranks for Whoville, but he only wants to keep the top prank per target, with the highest evilness score. Return the most evil prank for each target. If two pranks have the same evilness, the more recently brainstormed wins.
```sql
SELECT
    prank_id, target_name, prank_description,
    evilness_score, created_at
FROM (
    SELECT *,
        ROW_NUMBER() OVER (PARTITION BY target_name ORDER BY evilness_score DESC, created_at DESC
        ) AS rn
    FROM grinch_prank_ideas
) t
WHERE rn = 1
ORDER BY evilness_score DESC  ;
```

Output:

| prank_id | target_name  | prank_description                               | evilness_score | created_at           |
|----------|--------------|--------------------------------------------------|----------------|----------------------|
| 20       | Cindy-Lou    | Tell her Santa isn't real                        | 10             | 2024-11-10 16:30:00 |
| 11       | Town Square  | Replace the Christmas tree with a cactus         | 10             | 2024-11-08 12:15:00 |
| 6        | Toy Factory  | Reverse all the assembly line directions         | 10             | 2024-11-01 07:30:00 |
| 16       | Church Choir | Train Max to howl during performances            | 9              | 2024-11-07 14:00:00 |
| 19       | Mayor        | Swap his speech with a recipe for roast beast    | 9              | 2024-11-10 13:00:00 |
| 8        | Post Office  | Mix up all the address labels                    | 9              | 2024-11-02 13:20:00 |
| 12       | Bakery       | Replace sugar with salt in all recipes           | 8              | 2024-11-04 06:45:00 |
| 18       | School       | Change all clocks to show wrong time             | 7              | 2024-11-09 11:45:00 |







