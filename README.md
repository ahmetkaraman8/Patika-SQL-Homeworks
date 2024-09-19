# Ödev-1
### 1-film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.
```
SELECT title, description FROM film
```

### 2-film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.
```
SELECT * FROM film 
WHERE length > 60 AND length < 75;
```

### 3-film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.
```
SELECT * FROM film
WHERE rental_rate = 0.99 AND (replacement_cost = 12.99 OR replacement_cost = 28.99);
```

### 4-customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?
```
SELECT last_name FROM customer
WHERE first_name = 'Mary
```

### 5-film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.
```
SELECT * FROM film
WHERE NOT length > 50 AND rental_rate != 2.99 AND rental_rate != 4.99;
```



# Ödev-2
### 1-film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)
```
SELECT * FROM film
WHERE replacement_cost BETWEEN 12.99 AND 16.99;
```

### 2-actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)
```
SELECT first_name, last_name FROM actor
WHERE first_name IN('Penelope', 'Nick', 'Ed');
```

### 3-film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. ( IN operatörünü kullanınız.)
```
SELECT * FROM film
WHERE rental_rate IN(0.99, 2.99, 4.99) AND replacement_cost IN(12.99, 15.99, 28.99);
```



# Ödev-3
### 1-country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.
```
SELECT country FROM country
WHERE country LIKE 'A%a';
```

### 2-country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.
```
SELECT country FROM country
WHERE LENGTH(country) = 6 AND country LIKE '%n';
```

### 3-film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.
```
SELECT title FROM film
WHERE title ILIKE '%t%t%t%t%;'
```

### 4-film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.
```
SELECT * FROM film
WHERE title LIKE 'C%' AND length > 90 AND 'rental_rate' = 2.99;
```



# Ödev 4
### 1-film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.
```
SELECT DISTINCT replacement_cost FROM film;
```

### 2-film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?
```
SELECT COUNT(DISTINCT replacement_cost) FROM film;
```

### 3-film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?
```
SELECT COUNT(*) FROM film
WHERE title LIKE 'T%' AND rating = 'G';
```

### 4-country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?
```
SELECT COUNT(*) FROM country
WHERE LENGTH(country) = 5;
```

### 5-city tablosundaki şehir isimlerinin kaç tanesi 'R' veya r karakteri ile biter?
```
SELECT COUNT(*) FROM city
WHERE title ILIKE '%r';
```



# Ödev 5
### 1-film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.
```
SELECT * FROM film
WHERE title LIKE '%n'
ORDER BY length DESC
LIMIT 5;
```

### 2-film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci(6,7,8,9,10) 5 filmi(6,7,8,9,10) sıralayınız.
```
SELECT * FROM film
WHERE title LIKE '%n'
ORDER BY length ASC
LIMIT 5
OFFSET 5;
```

### 3-customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.
```
SELECT * FROM customer
WHERE store_,d = 1
ORDER BY last_name DESC
LIMIT 4;
```



# Ödev 6
### 1-film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?
```
SELECT AVG(rental_rate) FROM film;
```

### 2-film tablosunda bulunan filmlerden kaç tanesi 'C' karakteri ile başlar?
```
SELECR COUNT(*) FROM film
WHERE title LIKE 'C%'
```

### 3-film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?
```
SELECT MAX(length) FROM film
WHERE rental_rate = 0.99;
```

### 4-film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?
```
SELECT COUNT(DISTINCT replacement_cost) FROM film
WHERE length > 150;
```



# Ödev 7
### 1-film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.
```
SELECT rating, COUNT(*) FROM film
GROUP BY rating;
```

### 2-film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.
```
SELECT replacement_cost, COUNT(*) FROM film
GROUP BY replacement_cost
HAVING COUNT(*) > 50;
```

### 3-customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir? 
```
SELECT store_id, COUNT(*) FROM customer
GROUP BY store_id;
```

### 4-city tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıran country_id bilgisini ve şehir sayısını paylaşınız.
```
SELECT country_id, COUNT(*) FROM city
GROUP BY country_id
ORDER BY COUNT(*) DESC
LIMIT 1;
```



# Ödev 8
### 1-test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.
```
CREATE TABLE employee(
      id INTEGER PRIMARY KEY,
      name VARCHAR(50),
      birthday DATE,
      email VARCHAR(50)
);
```

### 2-Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.
```
insert into employee (id, name, birthday, email) values (1, 'Devland', '1910/11/04', 'domohun0@yale.edu');
insert into employee (id, name, birthday, email) values (2, 'Paton', '1913/02/06', 'plenormand1@archive.org');
insert into employee (id, name, birthday, email) values (3, 'Caspar', '1977/09/07', 'cquare2@addthis.com');
insert into employee (id, name, birthday, email) values (4, 'Claiborn', '1926/02/27', 'ctour3@e-recht24.de');
insert into employee (id, name, birthday, email) values (5, 'Sue', '1951/06/03', 'sgoghin4@businessinsider.com');
insert into employee (id, name, birthday, email) values (6, 'Jocelin', '1961/07/15', 'jloder5@pcworld.com');
insert into employee (id, name, birthday, email) values (7, 'Arly', '1974/05/07', 'alaight6@si.edu');
insert into employee (id, name, birthday, email) values (8, 'Coriss', '1950/10/08', 'cmacdearmaid7@archive.org');
insert into employee (id, name, birthday, email) values (9, 'Valentin', '2001/04/26', 'vbukowski8@etsy.com');
insert into employee (id, name, birthday, email) values (10, 'Roderic', '1954/02/09', 'rreinbach9@about.me');
insert into employee (id, name, birthday, email) values (11, 'Saxe', '1910/12/20', 'snoicea@microsoft.com');
insert into employee (id, name, birthday, email) values (12, 'Vlad', '1910/08/30', 'vkenwinb@skyrock.com');
insert into employee (id, name, birthday, email) values (13, 'Neille', '1908/03/23', 'ncudihyc@unesco.org');
insert into employee (id, name, birthday, email) values (14, 'Cordie', '1935/07/26', 'cpaddemored@photobucket.com');
insert into employee (id, name, birthday, email) values (15, 'Suzanna', '1900/03/31', 'sraincine@blinklist.com');
insert into employee (id, name, birthday, email) values (16, 'Noni', '1991/10/12', 'nsulleyf@reverbnation.com');
insert into employee (id, name, birthday, email) values (17, 'Martie', '1912/11/09', 'mtottieg@bravesites.com');
insert into employee (id, name, birthday, email) values (18, 'Joelie', '1950/01/19', 'jheigoldh@craigslist.org');
insert into employee (id, name, birthday, email) values (19, 'Parsifal', '2004/02/06', 'prodgieri@elegantthemes.com');
insert into employee (id, name, birthday, email) values (20, 'Galina', '1937/11/19', 'gcuerdallj@technorati.com');
insert into employee (id, name, birthday, email) values (21, 'Sloan', '1931/12/01', 'strautk@usnews.com');
insert into employee (id, name, birthday, email) values (22, 'Dukie', '1910/10/30', 'dparsleyl@amazon.co.uk');
insert into employee (id, name, birthday, email) values (23, 'Gaston', '1903/03/25', 'gjacobovitzm@yandex.ru');
insert into employee (id, name, birthday, email) values (24, 'Townie', '1941/08/05', 'tdowtryn@ucsd.edu');
insert into employee (id, name, birthday, email) values (25, 'Jehanna', '1934/11/24', 'jcasarinoo@tripod.com');
insert into employee (id, name, birthday, email) values (26, 'Petronille', '1993/04/13', 'pmattaserp@about.com');
insert into employee (id, name, birthday, email) values (27, 'Norah', '1981/07/09', 'ntidmanq@ucoz.ru');
insert into employee (id, name, birthday, email) values (28, 'Giraldo', '1964/12/20', 'gaxtensr@dot.gov');
insert into employee (id, name, birthday, email) values (29, 'Cull', '1901/10/31', 'cheinekens@edublogs.org');
insert into employee (id, name, birthday, email) values (30, 'Peder', '1907/09/27', 'posoriot@eventbrite.com');
insert into employee (id, name, birthday, email) values (31, 'Avie', '1919/02/15', 'ashillamu@goo.gl');
insert into employee (id, name, birthday, email) values (32, 'Hyacinthe', '1942/12/09', 'hdelcastellov@nih.gov');
insert into employee (id, name, birthday, email) values (33, 'Elisha', '1953/07/09', 'ehaggletonw@ycombinator.com');
insert into employee (id, name, birthday, email) values (34, 'Alexander', '1911/12/28', 'abengefieldx@samsung.com');
insert into employee (id, name, birthday, email) values (35, 'Der', '1929/05/13', 'dvellendery@blinklist.com');
insert into employee (id, name, birthday, email) values (36, 'Susanetta', '1927/12/07', 'sdowardz@lulu.com');
insert into employee (id, name, birthday, email) values (37, 'Leona', '1921/05/22', 'lleward10@digg.com');
insert into employee (id, name, birthday, email) values (38, 'Danila', '1909/05/05', 'dsiddele11@hc360.com');
insert into employee (id, name, birthday, email) values (39, 'Jerrome', '1992/03/01', 'jdunseath12@flavors.me');
insert into employee (id, name, birthday, email) values (40, 'Jorgan', '1950/02/12', 'jdiwell13@berkeley.edu');
insert into employee (id, name, birthday, email) values (41, 'Amalia', '1989/02/28', 'aferryn14@samsung.com');
insert into employee (id, name, birthday, email) values (42, 'Kippie', '2003/09/25', 'kjuschka15@berkeley.edu');
insert into employee (id, name, birthday, email) values (43, 'Alonzo', '1931/11/05', 'awillisch16@barnesandnoble.com');
insert into employee (id, name, birthday, email) values (44, 'Inessa', '1971/08/21', 'iskingle17@vkontakte.ru');
insert into employee (id, name, birthday, email) values (45, 'Ardine', '2000/01/23', 'aassel18@slashdot.org');
insert into employee (id, name, birthday, email) values (46, 'Zackariah', '1960/08/23', 'zbryns19@gov.uk');
insert into employee (id, name, birthday, email) values (47, 'Christen', '1973/10/13', 'coldroyd1a@seesaa.net');
insert into employee (id, name, birthday, email) values (48, 'Maximilien', '1907/05/31', 'mjanicijevic1b@com.com');
insert into employee (id, name, birthday, email) values (49, 'Alvie', '1906/10/12', 'amckomb1c@who.int');
insert into employee (id, name, birthday, email) values (50, 'Alex', '1959/09/10', 'akabsch1d@vk.com');
```

### 3-Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.
```
UPDATE employee SET id = 51
WHERE id = 50;
------------------------------------------------------
UPDATE employee SET name = 'Ahmet'
WHERE id = 8;
------------------------------------------------------
UPDATE employee SET email = 'ahmetSQL@gmail.com'
WHERE id = 8;
------------------------------------------------------
UPDATE employee SET birthday = '2002/11/20'
WHERE id = 8;
------------------------------------------------------
UPDATE employee SET id = 61
WHERE id = 8;
```

### 4-Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.
```
DELETE FROM employee
WHERE name = 'Alvie';
------------------------------------------------------
DELETE FROM employee
WHERE email = 'kjuschka15@berkeley.edu';
------------------------------------------------------
DELETE FROM employee
WHERE birthday = '1950/02/12';
------------------------------------------------------
DELETE FROM employee
WHERE id = 14;
------------------------------------------------------
DELETE FROM employee
WHERE name = 'Giraldo';
```



# Ödev 9
### 1-city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
```
SELECT city.city, country.country FROM city
INNER JOIN country ON city.country_id = country.country_id;
```

### 2-customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
```
SELECT payment.payment_id, customer.first_name, customer.last_name FROM payment
INNER JOIN customer ON payment.payment_id = customer.customer_id;
```

### 3-customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
```
SELECT rental.rental_id, customer.first_name, customer.first_name FROM rental
INNER JOIN customer ON rental.customer_id = customer.customer_id;
```



# Ödev 10
### 1-city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz LEFT JOIN sorgusunu yazınız.
```
SELECT city.city, country.country FROM city
LEFT JOIN country ON city.country_id = country.country_id;
```

### 2-customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz RIGHT JOIN sorgusunu yazınız.
```
SELECT payment.payment_id, customer.first_name, customer.last_name FROM payment
RIGHT JOIN customer ON payment.customer_id = customer.customer_id;
```

### 3-customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz FULL JOIN sorgusunu yazınız.
```
SELECT rental.rental_id, customer.first_name, customer.last_name FROM rental
FULL JOIN customer ON rental.customer_id = customer.customer_id;
```



# Ödev 11
### 1-actor ve customer tablolarında bulunan first_name sütunları için tüm verileri sıralayalım.
```
(SELECT first_name FROM actor)
UNION
(SELECT first_name FROM customer);
```

### 2-actor ve customer tablolarında bulunan first_name sütunları için kesişen verileri sıralayalım.
```
(SELECT first_name FROM actor)
INTERSECT
(SELECT first_name FROM customer);
```

### 3-actor ve customer tablolarında bulunan first_name sütunları için ilk tabloda bulunan ancak ikinci tabloda bulunmayan verileri sıralayalım.
```
(SELECT first_name FROM actor)
EXCEPT
(SELECT first_name FROM customer);
```

### 4-İlk 3 sorguyu tekrar eden veriler için de yapalım.
```
(SELECT first_name FROM actor)
UNION ALL
(SELECT first_name FROM customer);
------------------------------------------------------
(SELECT first_name FROM actor)
INTERSECT ALL
(SELECT first_name FROM customer);
------------------------------------------------------
(SELECT first_name FROM actor)
EXCEPT ALL
(SELECT first_name FROM customer);
```
