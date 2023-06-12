# SQL_Odevler_Patika
Bu repo Patika SQL Dersi kapsamında hazırlanan ödevleri içermektedir.

## SQL Ödev 01 | WHERE ve Karşılaştırma & Mantıksal Operatörler

1. film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.

> ```sql
> SELECT title, description FROM film;

2. film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.

> ```sql
> SELECT * FROM film 
> WHERE length > 60 AND length < 75;

3. film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.

> ```sql
> SELECT * FROM film
> WHERE rental_rate = 0.99 AND replacement_cost = 12.99 OR replacement_cost = 28.99;

4. customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?

> ```sql
> SELECT last_name FROM customer
> WHERE first_name = 'Mary';

5. film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.

> ```sql
> SELECT * FROM film
> WHERE NOT length > 50 AND NOT (rental_rate = 2.99 OR rental_rate = 4.99);

________________________________


## SQL Ödev 02 | BETWEEN ve IN

1. film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)

> ```sql
> SELECT * FROM film
> WHERE replacement_cost BETWEEN 12.99 AND 16.99;

2. .actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)

> ```sql
> SELECT first_name, last_name FROM actor
> WHERE first_name IN ('Penelope', 'Nick', 'Ed');

3. film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. ( IN operatörünü kullanınız.)

> ```sql
> SELECT * FROM film
> WHERE rental_rate IN (0.99, 2.99, 4.99) AND replacement_cost IN (12.99, 15.99, 28.00);

________________________________


## SQL Ödev 03 | LIKE ve ILIKE

1. country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.

> ```sql
> SELECT country FROM country
> WHERE country LIKE 'A%a';

2. country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.

> ```sql
> SELECT country FROM country
> WHERE country LIKE '%_%_%_%_%_%n';

3. film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.

> ```sql
> SELECT title FROM film
> WHERE title ILIKE '%t%t%t%t%';

4.film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.

> ```sql
> SELECT * FROM film
> WHERE title LIKE 'C%' AND length > 90 AND rental_rate = 2.99;

________________________________


## SQL Ödev 04 | DISTINCT ve COUNT

1. film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.

> ```sql
> SELECT DISTINCT replacement_cost FROM film;

2. film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?

> ```sql
> SELECT COUNT (DISTINCT replacement_cost) FROM film;

3. film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?

> ```sql
> SELECT COUNT (title) FROM film
> WHERE title LIKE 'T%' AND rating = 'G';

4. country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?

> ```sql
> SELECT COUNT (country) FROM country
> WHERE country LIKE '_____';

5. city tablosundaki şehir isimlerinin kaç tanesi 'R' veya r karakteri ile biter?

> ```sql
> SELECT COUNT (city) FROM city
> WHERE city ILIKE '%r';

________________________________


## SQL Ödev 05 | ORDER BY | LIMIT ve OFFSET

1. film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.

> ```sql
> SELECT title FROM film
> WHERE title LIKE '%n'
> ORDER BY length DESC
> LIMIT 5;

2. film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci(6,7,8,9,10) 5 filmi(6,7,8,9,10) sıralayınız.

> ```sql
> SELECT title FROM film
> WHERE title LIKE '%n'
> ORDER BY length 
> OFFSET 5
> LIMIT 5;

3. customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.

> ```sql
> SELECT * FROM customer
> WHERE store_id = 1
> ORDER BY last_name DESC 
> LIMIT 4;

________________________________


## SQL Ödev 06 | Aggregate Fonksiyonlar

1.



________________________________


## SQL Ödev 07 | GROUP BY | HAVING



________________________________


## SQL Ödev 08 | Tablo Oluşturmak | Verileri Güncellemek"



________________________________







