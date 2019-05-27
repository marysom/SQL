### SQL

Задача 1:
```sql
SELECT model, speed, hd FROM pc WHERE price < 500
```
Задача 2:
```sql
SELECT DISTINCT maker FROM product WHERE type = 'Printer'
```

Задача 3:
```sql
SELECT model, ram, screen FROM laptop WHERE price > 1000
```

Задача 4:
```sql
SELECT * FROM printer WHERE color = 'y'
```

Задача 5:
```sql
SELECT model, speed, hd FROM pc WHERE price < 600 AND (cd = '12x' OR cd = '24x')
```

Задача 6:
```sql
SELECT DISTINCT product.maker AS Meker, laptop.speed AS speed 
  FROM product RIGHT JOIN laptop ON product.model = laptop.model 
  WHERE laptop.hd >= 10  AND product.type = 'Laptop'ORDER BY speed
```

Задача 7:
```sql
SELECT pc.model, pc.price FROM pc INNER JOIN product ON pc.model = product.model WHERE product.maker = 'B'
UNION
SELECT laptop.model, laptop.price FROM laptop INNER JOIN product ON laptop.model = product.model 
  WHERE product.maker = 'B'
UNION
SELECT printer.model, printer.price FROM printer INNER JOIN product ON printer.model = product.model 
  WHERE product.maker = 'B' ORDER BY price
```

Задача 8:
```sql
SELECT DISTINCT maker FROM product 
  WHERE type = 'PC' and maker NOT IN (SELECT maker FROM product WHERE type = 'Laptop')
```


Задача 9:
```sql
SELECT DISTINCT product.maker Maker FROM product INNER JOIN pc ON product.model = pc.model 
  WHERE pc.speed >= 450
```

Задача 10:
```sql
SELECT model, price FROM printer WHERE price  = (SELECT max(price) FROM printer)
```

Задача 11:
```sql
SELECT AVG(speed) FROM pc
```

Задача 12:
```sql
SELECT AVG(speed) FROM laptop WHERE speed IN (SELECT speed FROM laptop WHERE price > 1000)
```

Задача 13:
```sql
SELECT AVG(speed) FROM pc WHERE model IN (SELECT model FROM product 
  WHERE maker = 'A' and type = 'PC')
```

Задача 14:
```sql
SELECT maker, MAX(type) FROM product GROUP BY maker 
  HAVING COUNT(DISTINCT model)>1 AND COUNT(DISTINCT type) = 1
```

Задача 15:
```sql
SELECT hd FROM pc GROUP BY hd HAVING COUNT(hd)>=2
```

Задача 16:
```sql
SELECT DISTINCT a.model, b.model, a.speed, a.ram FROM pc as a, pc as b 
  WHERE a.speed = b.speed AND a.ram = b.ram AND a.model > b.model
```

Задача 17:
```sql
SELECT DISTINCT product.type, laptop.model, laptop.speed FROM product, laptop 
  WHERE laptop.speed < ALL (SELECT speed FROM pc) AND product.type = 'Laptop'
```

Задача 18:
```sql
SELECT DISTINCT product.maker, printer.price FROM product INNER JOIN printer ON product.model = printer.model 
  WHERE printer.color = 'y' AND printer.price IN (SELECT MIN(price) FROM printer WHERE color = 'y')
```

Задача 19:
```sql
SELECT product.maker, AVG(laptop.screen) FROM product INNER JOIN laptop ON product.model = laptop.model 
  GROUP BY product.maker
```

Задача 20:
```sql
SELECT maker, COUNT(model) FROM product WHERE type = 'PC' GROUP BY maker HAVING COUNT(model) >= 3
```

Задача 21:
```sql
SELECT product.maker, MAX(pc.price) FROM product, pc WHERE product.model = pc.model GROUP BY product.maker
```

Задача 22:
```sql
SELECT speed, AVG(price) FROM pc WHERE speed > 600 GROUP BY speed
```

Задача 23:
```sql
SELECT DISTINCT product.maker FROM product INNER JOIN pc ON product.model = pc.model 
  WHERE pc.speed >= 750 AND product.maker IN (SELECT product.maker 
    FROM product INNER JOIN laptop ON product.model = laptop.model WHERE laptop.speed >= 750)
```

Задача 24:
```sql
SELECT model FROM (SELECT model, price FROM pc UNION SELECT model, price 
  FROM laptop UNION SELECT model, price FROM printer) table_first 
  WHERE price = (SELECT MAX(price) FROM (SELECT price FROM pc UNION SELECT price 
  FROM laptop UNION SELECT price FROM printer) table_second)
```

Задача 25:
```sql
SELECT DISTINCT maker FROM product WHERE model IN (
  SELECT model FROM pc WHERE ram = (SELECT MIN(ram) FROM pc) 
  AND speed = (SELECT MAX(speed) FROM pc WHERE ram = (SELECT MIN(ram) FROM pc))) 
  AND maker IN(SELECT maker FROM product WHERE type = 'printer')
```

Задача 26:
```sql
SELECT AVG(price) FROM (
  (SELECT price FROM pc WHERE model IN(SELECT model FROM product WHERE maker = 'A')) 
   UNION ALL
  (SELECT price FROM laptop WHERE model IN(SELECT model FROM product WHERE maker = 'A'))) as t
```

Задача 27:
```sql
SELECT product.maker, AVG(pc.hd) as hdsr FROM product INNER JOIN pc ON product.model = pc.model 
  GROUP BY product.maker HAVING product.maker IN(SELECT maker FROM product WHERE type = 'printer')
```

Задача 28:
```sql
SELECT COUNT(maker) FROM (SELECT maker, COUNT(model) as kol FROM product GROUP BY maker HAVING COUNT(model) = 1) as t
```

Задача 29:
```sql
SELECT income_o.point, income_o.date, income_o.inc, outcome_o.out FROM income_o LEFT JOIN outcome_o ON income_o.point = outcome_o.point AND income_o.date = outcome_o.date
UNION
SELECT outcome_o.point, outcome_o.date, income_o.inc, outcome_o.out FROM income_o RIGHT JOIN outcome_o ON income_o.point = outcome_o.point AND income_o.date = outcome_o.date
```

Задача 30:
```sql
SELECT point, date, SUM(sumout), SUM(suminc) FROM(
  SELECT point, date, SUM(inc) as suminc, null as sumout FROM income GROUP BY point, date 
   UNION 
  SELECT point, date, null as suminc, SUM(out) as sumout FROM outcome GROUP BY point, date ) as t 
    GROUP BY point, date ORDER BY point

```

Задача 31:
```sql
SELECT class, country FROM classes WHERE bore >= 16
```

Задача 32:
```sql
SELECT country, CAST( AVG(0.5*(power(bore,3))) AS NUMERIC(6,2)) 
  FROM (SELECT country, classes.class, bore, name FROM classes LEFT JOIN ships on classes.class=ships.class 
   UNION 
  SELECT DISTINCT country, class, bore, ship FROM classes table1 LEFT JOIN outcomes table2 on table1.class=table2.ship 
    WHERE ship=class and ship NOT IN (SELECT name FROM ships) ) t
    WHERE name IS NOT NULL 
    GROUP BY country

```

Задача 33:
```sql
SELECT ship FROM outcomes WHERE battle = 'North Atlantic' AND result = 'sunk'
```

Задача 34:
```sql
SELECT DISTINCT ships.name  FROM ships, classes 
  WHERE ships.class = classes.class AND (ships.launched >= 1922 AND ships.launched IS NOT NULL )  
  AND classes.displacement > 35000 AND classes.type = 'bb'
```
