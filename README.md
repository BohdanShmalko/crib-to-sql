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
1. INSERT INTO &table_name& (&field1&, &field2& ...) VALUES ('&value1&', '&value2&' ...); - добавить записи до таблиці
```
