## FUNNY BAKER

### Бази данних

<img src = "data1.PNG"/></br>
<img src = "data2.PNG"/></br>

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
<img src = "answ1.PNG"/></br>
