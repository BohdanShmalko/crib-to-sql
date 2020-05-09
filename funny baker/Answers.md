## FUNNY BAKER

### Бази данних

<img src = "./images/data1.PNG"/></br>
<img src = "./images/data2.PNG"/></br>

### Завдання
1. Отримати звіт про кількість поставок по кожному з постачальників
```sql
SELECT producer.name AS 'Постачальник',
COUNT(producer.name) AS 'Кількість поставок за звітний період'
FROM
producer, product, delivery
WHERE
producer.id = product.producer AND
product.id = delivery.product
GROUP BY producer.name
ORDER BY COUNT(producer.name) DESC;
```
АБО
```sql
SELECT producer.name AS 'Постачальник',
COUNT(producer.name) AS 'Кількість поставок за звітний період'
FROM delivery
INNER JOIN product ON
delivery.product=product.id
INNER JOIN producer ON
product.producer=producer.id
GROUP BY producer.name
ORDER BY COUNT(producer.name) DESC;
```
<img src = "./images/answ1.PNG"/></br>

2. Отримати звіт по товарам з найвищою ціною поставки в діапазоні 50..100 грн
```sql
SELECT product.name AS 'Товар',
delivery.price AS 'Ціна поставки (50..100 грн)'
FROM delivery, product
WHERE delivery.product = product.id
AND delivery.price BETWEEN 50 AND 100
ORDER BY delivery.price DESC
LIMIT 1;
```
АБО
```sql
SELECT product.name AS 'Товар',
delivery.price AS 'Ціна поставки (50..100 грн)'
FROM delivery
INNER JOIN product ON
product.id = delivery.product
WHERE delivery.price BETWEEN 50 AND 100
ORDER BY delivery.price DESC
LIMIT 1;
```
<img src = "./images/answ2.PNG"/></br>

3. Отримати звіт по постачальникам та загальній кількості проданих одиниць товару
```sql
SELECT producer.name AS 'Постачальник',
SUM(sale.quantity) AS ' Кількість одиниць проданого товару'
FROM sale, product, producer
WHERE sale.product = product.id
AND product.producer = producer.id
GROUP BY producer.name
ORDER BY COUNT(producer.name) DESC;
```
АБО
```sql
SELECT producer.name AS 'Постачальник',
SUM(sale.quantity) AS 'Кількість одиниць проданого товару'
FROM sale
INNER JOIN product ON
sale.product = product.id
INNER JOIN producer ON
product.producer = producer.id
GROUP BY producer.name
ORDER BY COUNT(producer.name) DESC;
```
<img src = "./images/answ3.PNG"/></br>

4. Для постачальника "тов пекар" отримати звіт по поставленим товарам та загальній вартості
```sql
SELECT product.name AS 'Товар (тов пекар)',
SUM(delivery.price * delivery.quantity)
AS 'Загальна вартість (грн)'
FROM product, delivery, producer
WHERE delivery.product = product.id
AND producer.id = product.producer
AND producer.name = 'тов пекар'
GROUP BY product.name
ORDER BY COUNT(product.name) DESC;
```
АБО
```sql
SELECT product.name AS 'Товар (тов пекар)',
SUM(delivery.price * delivery.quantity)
AS 'Загальна вартість (грн)'
FROM delivery
INNER JOIN product ON
delivery.product = product.id
INNER JOIN producer ON
product.producer = producer.id
WHERE producer.name = 'тов пекар'
GROUP BY product.name
ORDER BY COUNT(product.name) DESC;
```
<img src = "./images/answ4.PNG"/></br>

5. Отримати звіт по поставленій кількості тортів
```sql
SELECT product.name AS 'Товар (торти)',
COUNT(delivery.product) AS 'Кількість поставлених одиниць'
FROM delivery, product
WHERE delivery.product = product.id
AND product.name LIKE '%торт%'
GROUP BY product.name
ORDER BY COUNT(product.name) DESC;
```
АБО
```sql
SELECT product.name AS 'Товар (торти)',
COUNT(delivery.product) AS 'Кількість поставлених одиниць'
FROM delivery
INNER JOIN product ON
delivery.product = product.id
AND product.name LIKE '%торт%'
GROUP BY product.name
ORDER BY COUNT(product.name) DESC;
```
<img src = "./images/answ5.PNG"/></br>

6. Отримати загальну вартість поставок постачальника "тов пекар"
```sql
SELECT SUM(delivery.quantity * delivery.price)
AS 'Загальна вартість поставок "тов пекар"'
FROM delivery,product,producer
WHERE delivery.product = product.id
AND product.producer = producer.id
AND producer.name = 'тов пекар';
```
АБО
```sql
SELECT SUM(delivery.quantity * delivery.price)
AS 'Загальна вартість поставок "тов пекар"'
FROM delivery
INNER JOIN product ON
delivery.product = product.id
INNER JOIN producer ON
product.producer = producer.id
AND producer.name = 'тов пекар';
```
<img src = "./images/answ6.PNG"/></br>

7. Отримати перелік товарів, поставлених до 07.09.2019
```sql
SELECT product.name AS 'Товар (поставки до 07.09.2019)'
FROM delivery, product
WHERE delivery.product = product.id
AND delivery.date < '2019-09-07';
```
АБО
```sql
SELECT product.name AS 'Товар (поставки до 07.09.2019)'
FROM delivery
INNER JOIN product ON
delivery.product = product.id
WHERE delivery.date < '2019-09-07';
```
<img src = "./images/answ7.PNG"/></br>
<!--
```sql

```
АБО
```sql

```
<img src = "./images/answ.PNG"/></br>
-->
