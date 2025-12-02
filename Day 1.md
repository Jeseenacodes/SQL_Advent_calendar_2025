## Tables
- reindeer_run_results(number, name, rank, color)

```sql
CREATE TABLE reindeer (
    name   VARCHAR(50) NOT NULL,
    rank   INT NOT NULL,
    color  VARCHAR(50),
    number INT NOT NULL,
    PRIMARY KEY (rank)
);
```

```sql
INSERT INTO reindeer (name, rank, color, number) VALUES
('Dasher', 1, 'Brown', 1),
('Dancer', 2, 'Tan', 2),
('Prancer', 3, 'White', 3),
('Vixen', 4, 'Grey', 4),
('Comet', 5, 'Golden', 5),
('Cupid', 6, 'Beige', 6),
('Donner', 7, 'Chestnut', 7),
('Blitzen', 8, 'Dark Brown', 8),
('Rudolph', 9, 'Red', 9),
('Olive', 10, 'Olive', 10),
('Fireball', 11, 'Orange', 11),
('Clarice', 12, 'Cream', 12),
('Jingle', 13, 'Silver', 13),
('Jangle', 14, 'Copper', 14),
('Snowflake', 15, 'White', 15),
('Frostbite', 16, 'Ice Blue', 16),
('Twinkle', 17, 'Sparkle White', 17),
('Sparkle', 18, 'Glitter Gold', 18),
('Candy Cane', 19, 'Red and White', 19),
('Gingerbread', 20, 'Ginger Brown', 20),
('Mistletoe', 21, 'Green', 21),
('Holly', 22, 'Deep Green', 22),
('Nutcracker', 23, 'Walnut Brown', 23),
('Tinsel', 24, 'Metallic Silver', 24),
('Evergreen', 25, 'Pine Green', 25),
('Starlight', 26, 'Yellow', 26),
('Moonbeam', 27, 'Pale Silver', 27),
('Sugarplum', 28, 'Purple', 28),
('Peppermint', 29, 'Mint Green', 29),
('Eggnog', 30, 'Cream Yellow', 30);
```


### Every year, the city of Whoville conducts a Reindeer Run to find the best reindeers for Santa's Sleigh. Write a query to return the name and rank of the top 7 reindeers in this race.

```sql
  SELECT name, rank FROM reindeer_run_results
    ORDER BY rank
    LIMIT 7;
```


Output:

| name   | rank |
|--------|------|
| Dasher | 1    |
| Dancer | 2    |
| Prancer | 3   |
| Vixen  | 4    |
| Comet  | 5    |
| Cupid  | 6    |
| Donner | 7    |

