
Tables
- tinsel_colors(tinsel_id, color_name)
- light_colors(light_id, color_name)

## **1. Table: `light_colors`**

```sql
CREATE TABLE light_colors (
    light_id INT PRIMARY KEY,
    color_name VARCHAR(50)
);

INSERT INTO light_colors (light_id, color_name) VALUES
(1, 'Warm White'),
(2, 'Cool White'),
(3, 'Red'),
(4, 'Green'),
(5, 'Blue'),
(6, 'Yellow'),
(7, 'Orange'),
(8, 'Purple'),
(9, 'Pink'),
(10, 'Multicolor');
```

---

## **2. Table: `tinsel_colors`**

```sql
CREATE TABLE tinsel_colors (
    tinsel_id INT PRIMARY KEY,
    color_name VARCHAR(50)
);

INSERT INTO tinsel_colors (tinsel_id, color_name) VALUES
(1, 'Silver'),
(2, 'Gold'),
(3, 'Red'),
(4, 'Blue'),
(5, 'Green'),
(6, 'Pink'),
(7, 'Purple'),
(8, 'Copper'),
(9, 'White'),
(10, 'Rainbow');
```

```sql
SELECT tc.tinsel_id, lc.light_id,
      CONCAT(tc.color_name, '-', lc.color_name) AS Tinsel_lights
FROM tinsel_colors AS tc
CROSS JOIN light_colors AS lc 
```

### The elves are testing new tinsel–light combinations to find the next big holiday trend. Write a query to generate every possible pairing of tinsel colors and light colors, include in your output a column that combines the two values separated with a dash ("-").

```sql
| tinsel_id | light_id | Tinsel_Lights      |
| --------- | -------- | ------------------ |
| 1         | 1        | Silver-Warm White  |
| 1         | 2        | Silver-Cool White  |
| 1         | 3        | Silver-Red         |
| 1         | 4        | Silver-Green       |
| 1         | 5        | Silver-Blue        |
| 1         | 6        | Silver-Yellow      |
| 1         | 7        | Silver-Orange      |
| 1         | 8        | Silver-Purple      |
| 1         | 9        | Silver-Pink        |
| 1         | 10       | Silver-Multicolor  |
| 2         | 1        | Gold-Warm White    |
| 2         | 2        | Gold-Cool White    |
| 2         | 3        | Gold-Red           |
| 2         | 4        | Gold-Green         |
| 2         | 5        | Gold-Blue          |
| 2         | 6        | Gold-Yellow        |
| 2         | 7        | Gold-Orange        |
| 2         | 8        | Gold-Purple        |
| 2         | 9        | Gold-Pink          |
| 2         | 10       | Gold-Multicolor    |
| 3         | 1        | Red-Warm White     |
| 3         | 2        | Red-Cool White     |
| 3         | 3        | Red-Red            |
| 3         | 4        | Red-Green          |
| 3         | 5        | Red-Blue           |
| 3         | 6        | Red-Yellow         |
| 3         | 7        | Red-Orange         |
| 3         | 8        | Red-Purple         |
| 3         | 9        | Red-Pink           |
| 3         | 10       | Red-Multicolor     |
| 4         | 1        | Blue-Warm White    |
| 4         | 2        | Blue-Cool White    |
| 4         | 3        | Blue-Red           |
| 4         | 4        | Blue-Green         |
| 4         | 5        | Blue-Blue          |
| 4         | 6        | Blue-Yellow        |
| 4         | 7        | Blue-Orange        |
| 4         | 8        | Blue-Purple        |
| 4         | 9        | Blue-Pink          |
| 4         | 10       | Blue-Multicolor    |
| 5         | 1        | Green-Warm White   |
| 5         | 2        | Green-Cool White   |
| 5         | 3        | Green-Red          |
| 5         | 4        | Green-Green        |
| 5         | 5        | Green-Blue         |
| 5         | 6        | Green-Yellow       |
| 5         | 7        | Green-Orange       |
| 5         | 8        | Green-Purple       |
| 5         | 9        | Green-Pink         |
| 5         | 10       | Green-Multicolor   |
| 6         | 1        | Pink-Warm White    |
| 6         | 2        | Pink-Cool White    |
| 6         | 3        | Pink-Red           |
| 6         | 4        | Pink-Green         |
| 6         | 5        | Pink-Blue          |
| 6         | 6        | Pink-Yellow        |
| 6         | 7        | Pink-Orange        |
| 6         | 8        | Pink-Purple        |
| 6         | 9        | Pink-Pink          |
| 6         | 10       | Pink-Multicolor    |
| 7         | 1        | Purple-Warm White  |
| 7         | 2        | Purple-Cool White  |
| 7         | 3        | Purple-Red         |
| 7         | 4        | Purple-Green       |
| 7         | 5        | Purple-Blue        |
| 7         | 6        | Purple-Yellow      |
| 7         | 7        | Purple-Orange      |
| 7         | 8        | Purple-Purple      |
| 7         | 9        | Purple-Pink        |
| 7         | 10       | Purple-Multicolor  |
| 8         | 1        | Copper-Warm White  |
| 8         | 2        | Copper-Cool White  |
| 8         | 3        | Copper-Red         |
| 8         | 4        | Copper-Green       |
| 8         | 5        | Copper-Blue        |
| 8         | 6        | Copper-Yellow      |
| 8         | 7        | Copper-Orange      |
| 8         | 8        | Copper-Purple      |
| 8         | 9        | Copper-Pink        |
| 8         | 10       | Copper-Multicolor  |
| 9         | 1        | White-Warm White   |
| 9         | 2        | White-Cool White   |
| 9         | 3        | White-Red          |
| 9         | 4        | White-Green        |
| 9         | 5        | White-Blue         |
| 9         | 6        | White-Yellow       |
| 9         | 7        | White-Orange       |
| 9         | 8        | White-Purple       |
| 9         | 9        | White-Pink         |
| 9         | 10       | White-Multicolor   |
| 10        | 1        | Rainbow-Warm White |
| 10        | 2        | Rainbow-Cool White |
| 10        | 3        | Rainbow-Red        |
| 10        | 4        | Rainbow-Green      |
| 10        | 5        | Rainbow-Blue       |
| 10        | 6        | Rainbow-Yellow     |
| 10        | 7        | Rainbow-Orange     |
| 10        | 8        | Rainbow-Purple     |
| 10        | 9        | Rainbow-Pink       |
| 10        | 10       | Rainbow-Multicolor |
```
