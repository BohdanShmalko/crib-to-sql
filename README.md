## Основні команди по створенню-видаленню

### Створення/видалення баз данних, таблиць, полей
```sql
1. CREATE DATABASE &name&; - ствоити БД
2. DROP DATABASE &name&; - видалити БД
3. CREATE TABLE &table_name& (&field_name& &type_field& NOT NULL AUTO_INCREMENT ... , ... PRIMARY KEY(&field_name&)); - створити таблицю з полями
4. DROP TABLE &table_name&; - видалити таблицю
5. ALTER TABLE &table_name& ADD &field_name& &type_field&; - добавити поле до таблиці
6. ALTER TABLE &table_name& DROP COLUMN &field_name&; - удалить поле з таблиці
```
### Добавлення, обновлення, видалення записів
```sql
1. INSERT INTO &table_name& (&field1&, &field2& ...) VALUES ('&value1&', '&value2&' ...), ...; - добавить записи до таблиці
2. ALTER TABLE &table_name& CHANGE &field& &new_name& &type& &new_atributes&; - змінити імя, тип, атрибути таблиці
3. UPDATE &table_name& SET `&field_name&` = '&new_value&', ... WHERE ...; - перейменувать значення поля в таблиці
4. DELETE FROM &table_name& WHERE ...; - видалити записи
5. TRUNCATE &table_name&; - видалити повністю всі записи з таблиці
```
### Вибірка данних з таблиці
```sql
1. SELECT * FROM &table_name&; - вибрать все(*) з таблиці
2. SELECT &field1&, &field2& ... FROM &table_name&; - вибрать декілька полів з  таблиці
3. SELECT &field1&, &field2& ... FROM &table_name1&, &table_name2&; - вибрать поля з всіх варіантів поєднання таблиць
```
