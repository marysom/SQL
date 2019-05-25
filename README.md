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
