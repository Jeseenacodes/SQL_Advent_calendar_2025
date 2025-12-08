
Tables
- resort_monthly_snowfall(resort_id, resort_name, snow_month, snowfall_inches)


```sql
CREATE TABLE resort_monthly_snowfall (
    resort_id INT,
    resort_name VARCHAR(100),
    snow_month INT,
    snowfall_inches DECIMAL(6,2)
);

INSERT INTO resort_monthly_snowfall (resort_id, snow_month, resort_name, snowfall_inches) VALUES
(1, 11, 'Alpine Peaks', 18.5),
(1, 12, 'Alpine Peaks', 42.3),
(1, 1, 'Alpine Peaks', 55.7),
(1, 2, 'Alpine Peaks', 48.2),
(1, 3, 'Alpine Peaks', 38.9),

(2, 11, 'Snowbird Summit', 22.1),
(2, 12, 'Snowbird Summit', 51.4),
(2, 1, 'Snowbird Summit', 62.8),
(2, 2, 'Snowbird Summit', 58.3),
(2, 3, 'Snowbird Summit', 44.6),

(3, 11, 'Powder Paradise', 15.2),
(3, 12, 'Powder Paradise', 38.7),
(3, 1, 'Powder Paradise', 45.9),
(3, 2, 'Powder Paradise', 41.5),
(3, 3, 'Powder Paradise', 32.3),

(4, 11, 'Crystal Mountain', 12.8),
(4, 12, 'Crystal Mountain', 35.2),
(4, 1, 'Crystal Mountain', 48.6),
(4, 2, 'Crystal Mountain', 43.1),
(4, 3, 'Crystal Mountain', 35.7),

(5, 11, 'Frostbite Ridge', 25.3),
(5, 12, 'Frostbite Ridge', 58.9),
(5, 1, 'Frostbite Ridge', 71.2),
(5, 2, 'Frostbite Ridge', 65.4),
(5, 3, 'Frostbite Ridge', 52.8),

(6, 11, 'Winter Haven', 8.4),
(6, 12, 'Winter Haven', 28.6),
(6, 1, 'Winter Haven', 36.9),
(6, 2, 'Winter Haven', 32.7),
(6, 3, 'Winter Haven', 25.1),

(7, 11, 'Mammoth Heights', 19.7),
(7, 12, 'Mammoth Heights', 46.8),
(7, 1, 'Mammoth Heights', 59.3),
(7, 2, 'Mammoth Heights', 54.6),
(7, 3, 'Mammoth Heights', 42.4),

(8, 11, 'Blizzard Bay', 10.3),
(8, 12, 'Blizzard Bay', 31.5),
(8, 1, 'Blizzard Bay', 40.2),
(8, 2, 'Blizzard Bay', 37.8),
(8, 3, 'Blizzard Bay', 28.9),

(9, 11, 'Everest Valley', 28.9),
(9, 12, 'Everest Valley', 64.3),
(9, 1, 'Everest Valley', 78.5),
(9, 2, 'Everest Valley', 72.1),
(9, 3, 'Everest Valley', 58.7),

(10, 11, 'Iceberg Lodge', 5.6),
(10, 12, 'Iceberg Lodge', 21.4),
(10, 1, 'Iceberg Lodge', 29.8),
(10, 2, 'Iceberg Lodge', 26.3),
(10, 3, 'Iceberg Lodge', 19.7),

(11, 11, 'Thunder Ridge', 16.4),
(11, 12, 'Thunder Ridge', 40.1),
(11, 1, 'Thunder Ridge', 52.3),
(11, 2, 'Thunder Ridge', 47.9),
(11, 3, 'Thunder Ridge', 37.2),

(12, 11, 'Glacier Point', 31.2),
(12, 12, 'Glacier Point', 68.5),
(12, 1, 'Glacier Point', 82.7),
(12, 2, 'Glacier Point', 76.3),
(12, 3, 'Glacier Point', 61.9),

(13, 11, 'Silver Slopes', 7.8),
(13, 12, 'Silver Slopes', 26.3),
(13, 1, 'Silver Slopes', 34.5),
(13, 2, 'Silver Slopes', 30.8),
(13, 3, 'Silver Slopes', 23.4),

(14, 11, 'Aurora Basin', 20.6),
(14, 12, 'Aurora Basin', 49.2),
(14, 1, 'Aurora Basin', 61.4),
(14, 2, 'Aurora Basin', 56.7),
(14, 3, 'Aurora Basin', 44.1),

(15, 11, 'Summit Station', 14.1),
(15, 12, 'Summit Station', 37.9),
(15, 1, 'Summit Station', 49.7),
(15, 2, 'Summit Station', 45.3),
(15, 3, 'Summit Station', 35.8),

(16, 11, 'Whiteout Peak', 33.7),
(16, 12, 'Whiteout Peak', 72.4),
(16, 1, 'Whiteout Peak', 87.9),
(16, 2, 'Whiteout Peak', 81.2),
(16, 3, 'Whiteout Peak', 65.6),

(17, 11, 'Diamond Run', 11.9),
(17, 12, 'Diamond Run', 33.8),
(17, 1, 'Diamond Run', 44.2),
(17, 2, 'Diamond Run', 39.6),
(17, 3, 'Diamond Run', 30.9),

(18, 11, 'Avalanche Alley', 24.8),
(18, 12, 'Avalanche Alley', 56.7),
(18, 1, 'Avalanche Alley', 69.8),
(18, 2, 'Avalanche Alley', 63.9),
(18, 3, 'Avalanche Alley', 51.2),

(19, 11, 'Frozen Falls', 9.2),
(19, 12, 'Frozen Falls', 29.7),
(19, 1, 'Frozen Falls', 38.4),
(19, 2, 'Frozen Falls', 34.2),
(19, 3, 'Frozen Falls', 26.5),

(20, 11, 'Timber Ridge', 17.3),
(20, 12, 'Timber Ridge', 43.6),
(20, 1, 'Timber Ridge', 57.1),
(20, 2, 'Timber Ridge', 52.4),
(20, 3, 'Timber Ridge', 40.8);
```

## Buddy is planning a winter getaway and wants to rank ski resorts by annual snowfall. Can you help him bucket these ski resorts into quartiles?
```sql
WITH annual_snowfall AS (
    SELECT
        resort_id,
        resort_name,
        ROUND(SUM(snowfall_inches),2) AS total_snowfall
    FROM resort_monthly_snowfall
    GROUP BY resort_id, resort_name
)
SELECT *,
        NTILE(4) OVER (ORDER BY total_snowfall DESC) AS snowfall_quartile
FROM annual_snowfall
ORDER BY snowfall_quartile, total_snowfall DESC;
```

```sql
SELECT 
    *,
    NTILE(4) OVER (ORDER BY total_snowfall DESC) AS snowfall_quartile
FROM (
    SELECT 
        resort_id,
        resort_name,
        ROUND(SUM(snowfall_inches),2) AS total_snowfall
    FROM resort_monthly_snowfall
    GROUP BY resort_id, resort_name
) s
ORDER BY snowfall_quartile, total_snowfall DESC;
```

Output:

| resort_id | resort_name        | total_snowfall | snowfall_quartile |
|-----------|---------------------|----------------|--------------------|
| 16        | Whiteout Peak       | 340.8          | 1                  |
| 12        | Glacier Point       | 320.6          | 1                  |
| 9         | Everest Valley      | 302.5          | 1                  |
| 5         | Frostbite Ridge     | 273.6          | 1                  |
| 18        | Avalanche Alley     | 266.4          | 1                  |
| 2         | Snowbird Summit     | 239.2          | 2                  |
| 14        | Aurora Basin        | 232            | 2                  |
| 7         | Mammoth Heights     | 222.8          | 2                  |
| 20        | Timber Ridge        | 211.2          | 2                  |
| 1         | Alpine Peaks        | 203.6          | 2                  |
| 11        | Thunder Ridge       | 193.9          | 3                  |
| 15        | Summit Station      | 182.8          | 3                  |
| 4         | Crystal Mountain    | 175.4          | 3                  |
| 3         | Powder Paradise     | 173.6          | 3                  |
| 17        | Diamond Run         | 160.4          | 3                  |
| 8         | Blizzard Bay        | 148.7          | 4                  |
| 19        | Frozen Falls        | 138            | 4                  |
| 6         | Winter Haven        | 131.7          | 4                  |
| 13        | Silver Slopes       | 122.8          | 4                  |
| 10        | Iceberg Lodge       | 102.8          | 4                  |


