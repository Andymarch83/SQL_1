# Урок 1. Установка СУБД, подключение к БД, просмотр и создание таблиц
#### https://gbcdn.mrgcdn.ru/uploads/asset/5639966/attachment/85f692d44a9595204b50c9f3a25ceb2b.pdf
#### https://gbcdn.mrgcdn.ru/uploads/asset/4490267/attachment/c1c82cfc32e4ce9b63cd309bba9c0106.pdf
#### https://gbcdn.mrgcdn.ru/uploads/asset/4490272/attachment/0e9e9e90f6197d1a17d4906587d1b141.pdf
#### https://gbcdn.mrgcdn.ru/uploads/record/245971/attachment/105ea179a327e9df59d4737d09df10c6.mp4
#### https://pollen-attempt-4ac.notion.site/SQL-9072b1ca09f94e6fa3c588804919e1ae
#### https://pollen-attempt-4ac.notion.site/SQL-1-48c66b131571455b90b2220dfdaeaf1e
#### ссылки на установку: https://info-comp.ru/install-mysql-on-windows-10 - Windows
Mac: https://youtu.be/FbmjjTX0HQY

#### На Мас есть проблема: последняя версия нестабильно работает(вылетает при выводе данных из таблицы). Рекомендую cкачать архивную версию: https://downloads.mysql.com/archives/workbench/ (8.0.30., к примеру)

#### postgrespro https://postgrespro.ru/docs/postgresql/9.6/functions-matching


#### 1. Создайте таблицу с мобильными телефонами mobile_phones, используя графический интерфейс. Заполните БД данными.
#### Названия столбцов: product_name, manufacturer, product_count, price.

DROP TABLE IF EXISTS {schema_name}.mobile_phones;
-- создаём таблицу с мобильными телефонами (mobile_phones)
CREATE TABLE {schema_name}.mobile_phones (
    id SERIAL PRIMARY KEY,
    product_name VARCHAR(100) NOT NULL,
    manufacturer VARCHAR(100) NOT NULL,
    product_count INT,
    price BIGINT
);

-- Наполнение таблицы
INSERT INTO {schema_name}.mobile_phones (product_name, manufacturer, product_count, price)
VALUES
    ('iPhone X', 'Apple', 3, 76000),  
    ('iPhone 8', 'Apple', 2, 51000),  
    ('Galaxy S9', 'Samsung', 2, 56000),  
    ('Galaxy S8', 'Samsung', 1, 41000),
    ('P20 Pro', 'Huawei', 5, 36000);

    У вас есть таблица с мобильными телефонами mobile_phones.

#### 2. Вывести название (product_name), производителя (manufacturer) и цену (price) для товаров из базы данных, у которых количество #### (product_count) больше чем 2.

SELECT product_name, manufacturer, price FROM mobile_phones
WHERE product_count > 2;

#### 3. Выведите весь ассортимент товаров марки Samsung из таблицы mobile_phones, и вывести поля id, product_name, manufacturer, 
#### product_count и price для этих записей.

SELECT id, product_name, manufacturer, product_count, price
FROM mobile_phones
WHERE manufacturer = 'Samsung';

#### 4. Выбрать все товары из таблицы mobile_phones, в которых есть упоминание "Iphone" (независимо от регистра букв), и вывести поля  
#### id, product_name, manufacturer, product_count и price для этих записей.

SELECT id, product_name, manufacturer, product_count, price
FROM mobile_phones
WHERE product_name LIKE '%iPhone%';

#### 5. Выбрать все товары из таблицы mobile_phones, в которых есть упоминание "Samsung" (независимо от регистра букв), и вывести поля #### id, product_name, manufacturer, product_count и price для этих записей.

SELECT id, product_name, manufacturer, product_count, price
FROM mobile_phones
WHERE manufacturer LIKE '%Samsung%';

#### 6. Выбрать все записи из таблицы mobile_phones, где в поле product_name есть хотя бы одна цифра, и вывести поля id, product_name, #### manufacturer, product_count и price для этих записей.

SELECT id, product_name, manufacturer, product_count, price
FROM mobile_phones
WHERE product_name RLIKE '[0-9]';

#### 7. Выбрать все записи из таблицы mobile_phones, в которых поле product_name содержит цифру 8, и вывести поля id, product_name, 
#### manufacturer, product_count и price для этих записей.

SELECT id, product_name, manufacturer, product_count, price
FROM mobile_phones WHERE product_name LIKE '%8%'


