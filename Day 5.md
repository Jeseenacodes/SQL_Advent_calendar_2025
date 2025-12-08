```sql
CREATE TABLE elves (
    elf_id INT PRIMARY KEY,
    elf_name VARCHAR(50)
);

INSERT INTO elves (elf_id, elf_name) VALUES
(1, 'Jinglebell'),
(2, 'Sparkle'),
(3, 'Tinsel'),
(4, 'Snowflake'),
(5, 'Mistletoe'),
(6, 'Gingerbread'),
(7, 'Peppermint'),
(8, 'Frosty'),
(9, 'Cocoa'),
(10, 'Cinnamon'),
(11, 'Holly'),
(12, 'Evergreen'),
(13, 'Starlight'),
(14, 'Sugarplum'),
(15, 'Nutmeg'),
(16, 'Twinkle'),
(17, 'Ginger'),
(18, 'Candy'),
(19, 'Merry'),
(20, 'Jolly'),
(21, 'Blitzen'),
(22, 'Chestnut'),
(23, 'Cookie'),
(24, 'Clove'),
(25, 'Ribbon');
```

```sql
CREATE TABLE vacations (
    elf_id INT,
    start_date DATE,
    return_date DATE,
    FOREIGN KEY (elf_id) REFERENCES elves(elf_id)
);

INSERT INTO vacations (elf_id, start_date, return_date) VALUES
(1,  '2024-12-26', '2025-01-05'),
(2,  '2024-12-27', '2025-01-08'),
(3,  '2024-12-26', NULL),
(5,  '2024-12-28', '2025-01-03'),
(6,  '2024-12-26', NULL),
(7,  '2024-12-29', '2025-01-10'),
(9,  '2024-12-27', NULL),
(10, '2024-12-26', '2025-01-02'),
(12, '2024-12-30', '2025-01-06'),
(13, '2024-12-26', NULL),
(14, '2024-12-28', '2025-01-04'),
(16, '2024-12-27', NULL),
(17, '2024-12-26', '2025-01-07'),
(19, '2024-12-29', NULL),
(20, '2024-12-26', '2025-01-09'),
(22, '2024-12-31', NULL),
(23, '2024-12-27', '2025-01-05'),
(25, '2024-12-26', NULL);
```

## Some elves took time off after the holiday rush, but not everyone has returned to work. List all elves by name, showing their return date. If they have not returned from vacation, list their return date as "Still resting".



```sql
SELECT e.elf_name, 
  CASE WHEN return_date IS NULL THEN 'Still resting'
    ELSE CAST(v.return_date AS VARCHAR) 
      END AS return_status
  FROM elves AS e 
 LEFT JOIN vacations AS v ON e.elf_id = v.elf_id;
```

```sql

SELECT 
    e.elf_name,
    COALESCE(CAST(v.return_date AS VARCHAR), 'Still resting') AS return_status
FROM elves e
LEFT JOIN vacations v ON e.elf_id = v.elf_id;
```

```sql
WITH elf_vacation AS (
    SELECT 
        e.elf_name,
        v.return_date
    FROM elves e
    LEFT JOIN vacations v ON e.elf_id = v.elf_id
)
SELECT
    elf_name,
    COALESCE(CAST(return_date AS VARCHAR), 'Still resting') AS return_status
FROM elf_vacation;
```

Output:

| elf_name     | return_status |
|--------------|---------------|
| Jinglebell   | 2025-01-05    |
| Sparkle      | 2025-01-08    |
| Tinsel       | Still resting |
| Snowflake    | Still resting |
| Mistletoe    | 2025-01-03    |
| Gingerbread  | Still resting |
| Peppermint   | 2025-01-10    |
| Frosty       | Still resting |
| Cocoa        | Still resting |
| Cinnamon     | 2025-01-02    |
| Holly        | Still resting |
| Evergreen    | 2025-01-06    |
| Starlight    | Still resting |
| Sugarplum    | 2025-01-04    |
| Nutmeg       | Still resting |
| Twinkle      | Still resting |
| Ginger       | 2025-01-07    |
| Candy        | Still resting |
| Merry        | Still resting |
| Jolly        | 2025-01-09    |
| Blitzen      | Still resting |
| Chestnut     | Still resting |
| Cookie       | 2025-01-05    |
| Clove        | Still resting |
| Ribbon       | Still resting |



