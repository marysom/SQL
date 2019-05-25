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
