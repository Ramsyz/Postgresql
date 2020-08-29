# Postgresql Data Analysis

CREATE TABLE refinery_clients (
 refiner_name TEXT NOT NULL,
 units_sold INT NOT NULL,
 status_sent TEXT NULL,
 sale_id INT NOT NULL
);

INSERT INTO refinery_clients VALUES
 ('Big Refine Co.', 10000,'true', '1001'),
    ('Petrol Maker LLC.', 4500,'false', '1002'),
    ('Gasoline Factory Inc.', 20000,'true', '1003'),
 ('Jackson & Family', 3200,'true', 1004),
 ('Clear Prep LLC.', 13400,'', 1005),
 ('Titanium Refineries Inc.', 50000,'', 1006),
 ('Fake Oil Company', 0,'true', 1007)
;


CREATE TABLE distribution_channels (
 dis_name TEXT NOT NULL,
 status_received TEXT NULL,
 sale_id INT NOT NULL
);

INSERT INTO distribution_channels VALUES
 ('Gas n Go','false', 1002),
    ('Gasoline LLC.','true', 1001),
    ('Quick Gas','true', 1003),
 ('Pit Stop','true', 1004),
 ('Real Energy','', 1005),
 ('Car Station Co.','', 1006);

 DELETE FROM refinery_clients
 WHERE sale_id = 1000

 ALTER TABLE distribution_channels
 RENAME TO dis_channels

 ALTER TABLE dis_channels
ADD location TEXT NULL

UPDATE dis_channels
SET location = 'County A'
WHERE sale_id = 1001 OR sale_id = 1003
OR sale_id = 1004 OR sale_id = 1006;

UPDATE dis_channels
SET location = 'County B'
WHERE sale_id = 1002 OR sale_id = 1005;

SELECT DISTINCT dis_name FROM dis_channels

SELECT refiner_name, units_sold
FROM refinery_clients
WHERE units_sold > 10000

SELECT dis_name, sale_id
FROM dis_channels
WHERE sale_id IN (1001, 1003)

SELECT refiner_name, units_sold
FROM refinery_clients
ORDER BY units_sold DESC;

SELECT dis_name, location
FROM dis_channels
GROUP BY location, dis_name
ORDER BY location

SELECT dis_channels.dis_name,
refinery_clients.units_sold
FROM dis_channels
INNER JOIN refinery_clients ON 
dis_channels.sale_id = refinery_clients.sale_id

SELECT COUNT(dis_name)
FROM dis_channels

SELECT AVG(units_sold)
FROM refinery_clients

SELECT SUM(units_sold)
FROM refinery_clients
WHERE status_sent = 'true'

SELECT MIN(units_sold)
FROM refinery_clients
