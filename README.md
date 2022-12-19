# sql-odev-12

1 - film tablosunda film uzunluğu length sütununda gösterilmektedir. Uzunluğu ortalama film uzunluğundan fazla kaç tane film vardır?

    select  * from film
    where length > ALL
    (
    SELECT AVG(length) from film
    )
    
    
    -- KAÇ FİLM OLDUĞUNUN SAYISINI ÖĞRENMEK İSTİYORSAK -- 
    
    select  COUNT(length) from film
    where length > ALL
    (
    SELECT AVG(length) from film
    )
    
2 - film tablosunda en yüksek rental_rate değerine sahip kaç tane film vardır?
 
    select COUNT(*) from film
    where length > ANY
    (
    SELECT MAX(rental_rate) from film
    )
    
3 - film tablosunda en düşük rental_rate ve en düşün replacement_cost değerlerine sahip filmleri sıralayınız.

    
    select * from film
    where rental_rate = ALL
    (
    SELECT MIN(rental_rate) from film
    )
    AND 
    replacement_cost = ALL
    (
    SELECT MIN(replacement_cost) from film
    )
    
4 - payment tablosunda en fazla sayıda alışveriş yapan müşterileri(customer) sıralayınız.

    SELECT DISTINCT customer_id ,
    (SELECT Count(*) FROM payment WHERE customer_id = payment2.customer_id ) AS pay_count
    FROM payment AS payment2 
    ORDER BY pay_count DESC;
