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

8. Отримати звіт про найвищу ціну продажу для товарів в ціновому діапазоні 10..50 грн
```sql
SELECT product.name AS 'Товар',
MAX(sale.cost) AS 'Найвища ціна продажу (діапазон 10..50 грн)'
FROM product, sale
WHERE sale.product = product.id
AND sale.cost BETWEEN 10 AND 50;
```
АБО
```sql
SELECT product.name AS 'Товар',
MAX(sale.cost) AS 'Найвища ціна продажу (діапазон 10..50 грн)'
FROM sale
INNER JOIN product ON
sale.product = product.id
AND sale.cost BETWEEN 10 AND 50;
```
<img src = "./images/answ8.PNG"/></br>

9. Отримати перелік постачалькив, чий товар реалізовувався після 10.09.2020
```sql
SELECT producer.name AS 'Постачальник (реалізований товар після 10.09.2020)'
FROM producer, product, sale
WHERE sale.product = product.id
AND product.producer = producer.id
AND sale.date > '2019-09-10';
```
АБО
```sql
SELECT producer.name AS 'Постачальник (реалізований товар після 10.09.2020)'
FROM sale
INNER JOIN product ON
sale.product = product.id
INNER JOIN producer ON
product.producer = producer.id
WHERE sale.date > '2019-09-10';
```
<img src = "./images/answ9.PNG"/></br>

10. Отримати звіт про середню ціну поставки товарів
```sql
SELECT product.name AS 'Товар',
AVG(delivery.price) AS 'Середня ціна поставки'
FROM product, delivery
WHERE delivery.product = product.id
GROUP BY product.name
ORDER BY AVG(delivery.price) DESC;
```
АБО
```sql
SELECT product.name AS 'Товар',
AVG(delivery.price) AS 'Середня ціна поставки'
FROM delivery
INNER JOIN product ON
delivery.product = product.id
GROUP BY product.name
ORDER BY AVG(delivery.price) DESC;
```
<img src = "./images/answ10.PNG"/></br>

11. Отримати перелік постачальників, чиї товари реалізуються за найвищою ціною
```sql
SELECT producer.name AS 'Постачальник (найвища ціна реалізації товару)'
FROM sale, product, producer
WHERE sale.product = product.id
AND product.producer = producer.id
ORDER BY sale.cost DESC LIMIT 1;
```
АБО
```sql
SELECT producer.name AS 'Постачальник (найвища ціна реалізації товару)'
FROM sale
INNER JOIN product ON
sale.product = product.id
INNER JOIN producer ON
product.producer = producer.id
ORDER BY sale.cost DESC LIMIT 1;
```
<img src = "./images/answ11.PNG"/></br>

12. Отримати перелік неліквідних товарів (тих, що не продаються)
```sql
?
```
АБО
```sql
?
```
<img src = "./images/answ12.PNG"/></br>

13. Отримати перелік товарів з найнижчою ціною поставки
```sql
SELECT product.name AS 'Товар (найнижча ціна поставки)'
FROM delivery, product
WHERE delivery.product = product.id
ORDER BY delivery.price LIMIT 3
```
АБО
```sql
SELECT product.name AS 'Товар (найнижча ціна поставки)'
FROM delivery
INNER JOIN product ON
delivery.product = product.id
ORDER BY delivery.price LIMIT 3
```
<img src = "./images/answ13.PNG"/></br>

14. Отримати звіт про залишки товарів (різницю між кількістю поставлених та проданих одиниць товарів) за весь звітний період.
```sql
?
```
АБО
```sql
?
```
<img src = "./images/answ14.PNG"/></br>

15. Знайти товари, для яких здійснюються необліковані продажі (кількість поставлених товарів менша ніж кількість проданих).
```sql
?
```
АБО
```sql
?
```
<img src = "./images/answ15.PNG"/></br>

16. Отримати звіт про постачальників товарів та їх розташування
```sql
SELECT producer.name AS 'Постачальник',
location.name AS 'Розташування'
FROM producer, location
WHERE producer.location = location.id;
```
АБО
```sql
SELECT producer.name AS 'Постачальник',
location.name AS 'Розташування'
FROM producer
INNER JOIN location ON
producer.location = location.id;
```
<img src = "./images/answ16.PNG"/></br>

17. Отримати звіт про товари, що приносять найбільший прибуток
```sql
?
```
АБО
```sql
?
```
<img src = "./images/answ17.PNG"/></br>

18. Отримати звіт для товарів та загальної суми реалізації >500 грн
```sql
SELECT product.name AS 'Товар',
SUM(sale.cost * sale.quantity) AS 'Загальна сума реалізації (>500)'
FROM product, sale
WHERE sale.product = product.id
GROUP BY product.name
HAVING SUM(sale.cost * sale.quantity) > 500
ORDER BY SUM(sale.cost * sale.quantity) DESC;
```
АБО
```sql
SELECT product.name AS 'Товар',
SUM(sale.cost * sale.quantity) AS 'Загальна сума реалізації (>500)'
FROM sale
INNER JOIN product ON
sale.product = product.id
GROUP BY product.name
HAVING SUM(sale.cost * sale.quantity) > 500
ORDER BY SUM(sale.cost * sale.quantity) DESC;
```
<img src = "./images/answ18.PNG"/></br>

19. Отримати звіт про розташування постачальників
```sql
SELECT location.name AS 'Розташування',
COUNT(producer.name) AS 'Кількість постачальників'
FROM location, producer
WHERE producer.location = location.id
GROUP BY location.name
ORDER BY COUNT(producer.name) DESC;
```
АБО
```sql
SELECT location.name AS 'Розташування',
COUNT(producer.name) AS 'Кількість постачальників'
FROM producer
INNER JOIN location ON
producer.location = location.id
GROUP BY location.name
ORDER BY COUNT(producer.name) DESC;
```
<img src = "./images/answ19.PNG"/></br>
