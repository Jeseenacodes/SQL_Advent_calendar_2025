```sql

CREATE TABLE snowfall_log (
    flake_id INT PRIMARY KEY,
    fall_time TIMESTAMP,
    flake_type VARCHAR(50)
);

INSERT INTO snowfall_log (flake_id, fall_time, flake_type) VALUES
(1,  '2025-12-24 08:15:23', 'Stellar Dendrite'),
(2,  '2025-12-24 08:17:45', 'Plate Crystal'),
(3,  '2025-12-24 08:22:11', 'Stellar Dendrite'),
(4,  '2025-12-24 08:28:34', 'Needle'),
(5,  '2025-12-24 08:35:19', 'Column'),
(6,  '2025-12-24 09:12:47', 'Stellar Dendrite'),
(7,  '2025-12-24 09:18:52', 'Sectored Plate'),
(8,  '2025-12-24 09:24:33', 'Plate Crystal'),
(9,  '2025-12-24 09:41:08', 'Capped Column'),
(10, '2025-12-24 10:03:21', 'Needle'),
(11, '2025-12-24 10:17:56', 'Stellar Dendrite'),
(12, '2025-12-24 10:29:44', 'Fernlike Stellar'),
(13, '2025-12-24 11:05:13', 'Column'),
(14, '2025-12-24 11:22:37', 'Plate Crystal'),
(15, '2025-12-24 11:48:29', 'Stellar Dendrite'),
(16, '2025-12-24 12:14:51', 'Rimed Crystal'),
(17, '2025-12-24 12:33:18', 'Sectored Plate'),
(18, '2025-12-24 13:07:42', 'Capped Column'),
(19, '2025-12-24 13:29:15', 'Needle'),
(20, '2025-12-24 14:11:58', 'Stellar Dendrite'),
(21, '2025-12-24 14:38:24', 'Fernlike Stellar'),
(22, '2025-12-24 15:02:49', 'Column'),
(23, '2025-12-24 15:27:33', 'Plate Crystal'),
(24, '2025-12-24 16:13:07', 'Rimed Crystal'),
(25, '2025-12-24 16:45:22', 'Stellar Dendrite'),
(26, '2025-12-24 17:19:51', 'Capped Column'),
(27, '2025-12-24 17:52:14', 'Sectored Plate'),
(28, '2025-12-23 22:34:18', 'Needle'),
(29, '2025-12-23 23:47:29', 'Column'),
(30, '2025-12-25 02:15:37', 'Stellar Dendrite');
```


## Frosty wants to know how many unique snowflake types were recorded on the December 24th, 2025 storm. Can you help him?
```sql
SELECT COUNT(DISTINCT flake_type)
FROM snowfall_log
  WHERE fall_time = '2025-12-24';
```
  
