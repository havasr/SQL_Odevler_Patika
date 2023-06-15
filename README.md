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

1.film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?

> ```sql
> SELECT AVG(rental_rate) FROM film;

2.film tablosunda bulunan filmlerden kaç tanesi 'C' karakteri ile başlar?

> ```sql
> SELECT COUNT(*) FROM film
> WHERE title LIKE 'C%';

3.film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?

> ```sql
> SELECT MAX(length) FROM film
> WHERE rental_rate = 0.99;

4.film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?

> ```sql
> SELECT COUNT (DISTINCT replacement_cost) FROM film
> WHERE length > 150;


________________________________


## SQL Ödev 07 | GROUP BY | HAVING

1. film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.

> ```sql
> SELECT rating, COUNT(*) FROM film
> GROUP BY rating;

2. film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.

> ```sql
> SELECT replacement_cost, COUNT(*) FROM film
> GROUP BY replacement_cost
> HAVING COUNT(*) > 50;

3. customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir?

> ```sql
> SELECT store_id, COUNT(*) FROM customer
> GROUP BY store_id;

4. city tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıran country_id bilgisini ve şehir sayısını paylaşınız.

> ```sql
> SELECT country_id, COUNT(*) FROM city 
> GROUP BY country_id
> ORDER BY COUNT(*)
> LIMIT 1;

________________________________


## SQL Ödev 08 | Tablo Oluşturmak | Verileri Güncellemek"

1. test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.

> ```sql
> CREATE TABLE employee(
> id INTEGER,
> name VARCHAR (50),
> birthday VARCHAR(100),
> email VARCHAR(100)
);

2. Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.


> ```sql
> insert into employee (id, name, birthday, email) values (1, 'Ambros', '1987-09-30', 'astodhart0@nature.com');
> insert into employee (id, name, birthday, email) values (2, 'Ethe', '1945-03-28', 'eolpin1@comcast.net');
> insert into employee (id, name, birthday, email) values (3, 'Ranique', '1975-06-01', 'rarnli2@bloglovin.com');
> insert into employee (id, name, birthday, email) values (4, 'Fernando', '1985-06-12', 'fsmithe3@mediafire.com');
> insert into employee (id, name, birthday, email) values (5, 'Erinna', '1974-12-16', 'epolglase4@topsy.com');
> insert into employee (id, name, birthday, email) values (6, 'Cello', '1950-04-17', 'cfomichyov5@cdc.gov');
> insert into employee (id, name, birthday, email) values (7, 'Che', '1927-01-11', 'ctomasutti6@cloudflare.com');
> insert into employee (id, name, birthday, email) values (8, 'Dougy', '1996-01-18', 'despinoy7@biblegateway.com');
> insert into employee (id, name, birthday, email) values (9, 'Harley', '1972-04-30', 'hcallaby8@netvibes.com');
> insert into employee (id, name, birthday, email) values (10, 'Bay', '1931-02-01', 'bpaulus9@howstuffworks.com');
> insert into employee (id, name, birthday, email) values (11, 'Zsa zsa', '1925-07-10', 'zgrishunina@google.co.uk');
> insert into employee (id, name, birthday, email) values (12, 'Cosmo', '1973-05-24', 'cswetlandb@bigcartel.com');
> insert into employee (id, name, birthday, email) values (13, 'Nolie', '1968-09-13', 'nmeccoc@tiny.cc');
> insert into employee (id, name, birthday, email) values (14, 'Cortney', '1925-01-08', 'cmattiellod@163.com');
> insert into employee (id, name, birthday, email) values (15, 'Elsy', '1960-12-03', 'ecorwoode@slashdot.org');
> insert into employee (id, name, birthday, email) values (16, 'Cleon', '1955-04-21', 'caubinf@odnoklassniki.ru');
> insert into employee (id, name, birthday, email) values (17, 'Dolley', '1952-12-20', 'dgladtbachg@marketwatch.com');
> insert into employee (id, name, birthday, email) values (18, 'Katerina', '1958-08-29', 'kgaudenh@unicef.org');
> insert into employee (id, name, birthday, email) values (19, 'Jillane', '1971-11-16', 'jwellingtoni@wordpress.com');
> insert into employee (id, name, birthday, email) values (20, 'Colet', '1948-01-22', 'cdubblej@mail.ru');
> insert into employee (id, name, birthday, email) values (21, 'Dallas', '1986-08-08', 'dbathok@netlog.com');
> insert into employee (id, name, birthday, email) values (22, 'Cristal', '1971-07-10', 'csyriel@umn.edu');
> insert into employee (id, name, birthday, email) values (23, 'Franklin', '1994-09-16', 'fjagiellom@goo.ne.jp');
> insert into employee (id, name, birthday, email) values (24, 'Locke', '2009-10-20', 'lboullenn@typepad.com');
> insert into employee (id, name, birthday, email) values (25, 'Barbee', '2019-12-04', 'bburnsideso@discuz.net');
> insert into employee (id, name, birthday, email) values (26, 'Tamarra', '1932-12-07', 'tkearnp@toplist.cz');
> insert into employee (id, name, birthday, email) values (27, 'Lissa', '2002-01-06', 'lincognaq@addtoany.com');
> insert into employee (id, name, birthday, email) values (28, 'Hans', '1923-02-06', 'hgaskoinr@ycombinator.com');
> insert into employee (id, name, birthday, email) values (29, 'Merna', '2021-08-31', 'meversons@flickr.com');
> insert into employee (id, name, birthday, email) values (30, 'Palm', '1975-05-11', 'pstanwayt@microsoft.com');
> insert into employee (id, name, birthday, email) values (31, 'Chad', '1924-10-30', 'cstrelitzeru@gizmodo.com');
> insert into employee (id, name, birthday, email) values (32, 'Desmund', '1920-08-09', 'ddeansv@fastcompany.com');
> insert into employee (id, name, birthday, email) values (33, 'Sauveur', '1958-12-18', 'srodderw@scientificamerican.com');
> insert into employee (id, name, birthday, email) values (34, 'Chad', '1980-03-22', 'cpetrovskyx@bbc.co.uk');
> insert into employee (id, name, birthday, email) values (35, 'Lowrance', '1952-09-29', 'lfearny@huffingtonpost.com');
> insert into employee (id, name, birthday, email) values (36, 'Vonni', '1966-10-29', 'vmcreynoldz@chicagotribune.com');
> insert into employee (id, name, birthday, email) values (37, 'Carolynn', '2018-11-13', 'ccastiello10@rediff.com');
> insert into employee (id, name, birthday, email) values (38, 'Olivier', '1989-11-15', 'oridsdell11@yellowbook.com');
> insert into employee (id, name, birthday, email) values (39, 'Waiter', '2021-03-20', 'wplevey12@mediafire.com');
> insert into employee (id, name, birthday, email) values (40, 'Kellby', '1990-05-27', 'ksmallcomb13@deliciousdays.com');
> insert into employee (id, name, birthday, email) values (41, 'Naomi', '1921-12-30', 'nweems14@123-reg.co.uk');
> insert into employee (id, name, birthday, email) values (42, 'Melania', '1993-01-20', 'mloy15@house.gov');
> insert into employee (id, name, birthday, email) values (43, 'Laurens', '1921-11-12', 'lgreasty16@theguardian.com');
> insert into employee (id, name, birthday, email) values (44, 'Tammie', '1952-12-16', 'tjansen17@infoseek.co.jp');
> insert into employee (id, name, birthday, email) values (45, 'Orren', '1991-10-31', 'omeachen18@yelp.com');
> insert into employee (id, name, birthday, email) values (46, 'Sauncho', '1937-11-16', 'slambdin19@who.int');
> insert into employee (id, name, birthday, email) values (47, 'Vinny', '1953-08-30', 'vlockyear1a@eepurl.com');
> insert into employee (id, name, birthday, email) values (48, 'Allyn', '1994-01-05', 'afautly1b@va.gov');
> insert into employee (id, name, birthday, email) values (49, 'Rhodie', '2022-01-15', 'rhayer1c@facebook.com');
> insert into employee (id, name, birthday, email) values (50, 'Elyn', '2021-12-23', 'eforrington1d@gravatar.com');


3. Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.


> ```sql
> UPDATE employee
> SET name = 'Mike'
> WHERE id = 6;

> ```sql
> UPDATE employee
> SET birthday = '1982-01-06'
> WHERE id = 42;

> ```sql
> UPDATE employee
> SET email = 'hulohu@gmail.com'
> WHERE id = 34;

> ```sql
> UPDATE employee
> SET name = 'Sara',
>    birthday = '1997-11-05'
> WHERE id = 11;

> ```sql
> UPDATE employee
> SET name = 'Mike',
>    birthday = '1958-05-01',
>    email = 'miketyson@gmail.com'
> WHERE id = 29;

4. Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.


> ```sql
> DELETE FROM employee
> WHERE id = 19;

> ```sql
> DELETE FROM employee
> WHERE name ='Chad';

> ```sql
> DELETE FROM employee
> WHERE name = 'Cosmo' AND birthday = '1973-05-24';

> ```sql
> DELETE FROM employee
> WHERE email = 'epolglase4@topsy.com';

> ```sql
> DELETE FROM employee
> WHERE id > 45;

________________________________


## SQL Ödev 09 | INNER JOIN

1.city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

> ```sql
> SELECT city, country FROM city
> INNER JOIN country ON city.country_id = country.country_id;

2.customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

> ```sql
> SELECT first_name, last_name, payment_id FROM customer
> INNER JOIN payment ON customer.customer_id = payment.customer_id;

3. customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

> ```sql
> SELECT first_name, last_name, rental_id FROM customer
> INNER JOIN rental ON customer.customer_id = rental.customer_id;


________________________________

## SQL Ödev 10 | LEFT JOIN, RIGHT JOIN, FULL JOIN

1. city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz LEFT JOIN sorgusunu yazınız.

> ```sql
> SELECT city, country FROM city
> LEFT JOIN country ON city.country_id = country.country_id;


2. customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz RIGHT JOIN sorgusunu yazınız.

> ```sql
> SELECT first_name, last_name, payment_id FROM customer
> RIGHT JOIN payment ON customer.customer_id = payment.customer_id;

3. customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz FULL JOIN sorgusunu yazınız.

> ```sql
> SELECT first_name, last_name, rental_id FROM customer
> FULL JOIN rental ON customer.customer_id = rental.customer_id;


________________________________

## SQL Ödev 11 | UNION, INTERSECT ve EXCEPT

1. actor ve customer tablolarında bulunan first_name sütunları için tüm verileri sıralayalım.

> ```sql
> (SELECT first_name FROM actor)
> UNION
> (SELECT first_name FROM customer);

2. actor ve customer tablolarında bulunan first_name sütunları için kesişen verileri sıralayalım.

> ```sql
> (SELECT first_name FROM actor)
> INTERSECT
> (SELECT first_name FROM customer);

3. actor ve customer tablolarında bulunan first_name sütunları için ilk tabloda bulunan ancak ikinci tabloda bulunmayan verileri sıralayalım.

> ```sql
> (SELECT first_name FROM actor)
> EXCEPT
> (SELECT first_name FROM customer);

4. İlk 3 sorguyu tekrar eden veriler için de yapalım.

> ```sql
> <ADD ALL>

________________________________

## SQL Ödev 12 | Sorgu Senaryoları

1. film tablosunda film uzunluğu length sütununda gösterilmektedir. Uzunluğu ortalama film uzunluğundan fazla kaç tane film vardır?

> ```sql 
> SELECT COUNT(*) FROM film
> WHERE length > ( SELECT AVG (length) FROM film );
  
2. film tablosunda en yüksek rental_rate değerine sahip kaç tane film vardır?
  
> ```sql 
> SELECT COUNT(*) FROM film
> WHERE rental_rate =
> (SELECT MAX(rental_rate) FROM film);

3. film tablosunda en düşük rental_rate ve en düşün replacement_cost değerlerine sahip filmleri sıralayınız.
  
> ```sql 
> SELECT * FROM film
> WHERE rental_rate = ALL
> ( SELECT MIN(rental_rate) FROM film )
> AND replacement_cost =
> ( SELECT MIN(replacement_cost) FROM film );

  
4. payment tablosunda en fazla sayıda alışveriş yapan müşterileri(customer) sıralayınız.
  
> ```sql 
> SELECT customer_id, COUNT(*) AS shopping FROM payment
> GROUP BY customer_id
> ORDER BY shopping DESC;

  
________________________________

