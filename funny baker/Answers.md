## FUNNY BAKER

### Бази данних

<img src = "./data1.png"/></br>
<img src = "data2.png"/></br>

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
<img src = "answ1.png"/></br>
