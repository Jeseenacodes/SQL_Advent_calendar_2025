## Tables
- storage_trees(item_name, category)
- storage_lights(item_name, category)

```sql
CREATE TABLE storage_trees (
    item_name VARCHAR(100),
    category  VARCHAR(50)
);

CREATE TABLE storage_lights (
    item_name VARCHAR(100),
    category  VARCHAR(50)
);

INSERT INTO storage_trees (category, item_name) VALUES
('Tree', '7ft Douglas Fir'),
('Tree', '5ft Snowy Pine'),
('Tree', '9ft Grand Noble'),
('Tree', '4ft Tabletop Spruce'),
('Tree', '6ft Slim Alpine'),
('Tree', '8ft Flocked Fraser'),
('Tree', '3ft Miniature Pine'),
('Tree', '7.5ft Prelit Balsam'),
('Tree', '6.5ft Blue Spruce'),
('Tree', '5.5ft White Christmas'),
('Tree', '10ft Commercial Grade'),
('Tree', '4.5ft Pencil Pine'),
('Tree', '6ft Scandinavian Fir'),
('Tree', '8.5ft Majestic Pine'),
('Tree', '2ft Desktop Tree');

INSERT INTO storage_lights (category, item_name) VALUES
('Light', 'Warm White String Lights'),
('Light', 'Multicolor LED Set'),
('Light', 'Icicle Lights - Blue'),
('Light', 'Net Lights for Bushes'),
('Light', 'C9 Vintage Bulbs'),
('Light', 'Rope Light - Red'),
('Light', 'Fairy Lights Battery'),
('Light', 'Curtain Lights Indoor'),
('Light', 'Globe String Lights'),
('Light', 'Smart WiFi LED Strip'),
('Light', 'Candy Cane Path Lights'),
('Light', 'Projector Snowflake Light'),
('Light', 'Solar Powered Outdoor'),
('Light', 'Twinkle Lights Copper Wire'),
('Light', 'C7 Ceramic Multicolor');
```

### Mrs. Claus is organizing the holiday storage room and wants a single list of all decorations — both Christmas trees and light sets. Write a query that combines both tables and includes each item's name and category.

```sql
SELECT item_name, category FROM storage_trees 
UNION ALL
SELECT item_name, category FROM storage_lights;
```
