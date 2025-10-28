
# 🗓️Day 04 — SQL Practice Journal

**Date:** 28/10/2025  
**Platform(s):** [StrataScratch / LeetCode / DataLemur / HackerRank]  
**Total Questions Solved:** 10  

---

## 🧠 Overview


---

## 🧩 Question 1

**Title:** Insvestments in 2016  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/investments-in-2016/)  
**Platform:** LeetCode  
**Difficulty:** Medium  

```sql
MySQL Solution: 
SELECT ROUND(SUM(tiv_2016), 2) AS tiv_2016
FROM Insurance
WHERE tiv_2015 IN (
    SELECT tiv_2015
    FROM Insurance
    GROUP BY tiv_2015
    HAVING COUNT(*) > 1
)
AND (lat, lon) IN (
    SELECT lat, lon
    FROM Insurance
    GROUP BY lat, lon
    HAVING COUNT(*) = 1
)
```
## 🧩 Question 2

**Title:** Swap Salary  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/swap-salary/description/)  
**Platform:** LeetCode  
**Difficulty:** Easy  

```sql
MySQL Solution: 
UPDATE Salary
SET sex = CASE
    WHEN sex = 'm' THEN 'f'
    WHEN sex = 'f' THEN 'm'
END;
```
## 🧩 Question 3

**Title:** Actors and Directors Who Cooperated At Least Three Times  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/actors-and-directors-who-cooperated-at-least-three-times/submissions/1813895203/)  
**Platform:** LeetCode  
**Difficulty:** Easy  

```sql
MySQL Solution:
# Write your MySQL query statement below
with three_times as(select actor_id,director_id,count(timestamp)
    as total_times from ActorDirector group by Actor_id,Director_id )

select actor_id,director_id from three_times where total_times>=3
```
## 🧩 Question 4

**Title:** Product Sales Analysis III  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/product-sales-analysis-iii/description/)  
**Platform:** LeetCode  
**Difficulty:** Medium 

```sql
MySQL Solution: 
# Write your MySQL query statement below
with first_year as (select product_id,
       min(year) as fy
from sales group by product_id)

select sales.product_id,
       fy as first_year,
       sales.quantity,
       sales.price
 from sales join first_year 
 on sales.product_id=first_year.product_id and year= fy
```
## 🧩 Question 5

**Title:**  Immediate Food Delivery II
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/immediate-food-delivery-ii/description/)  
**Platform:** LeetCode  
**Difficulty:** Medium 

```sql
MySQL Solution: 
with first_order as (
                    select customer_id,
                           min(order_date) first_date
                    from Delivery 
                    group by customer_id)
select round((
    (
        select count(s.delivery_id) 
        from Delivery s 
        join first_order fo 
        on s.customer_id=fo.customer_id  
        and s.order_date= fo.first_date
        where s.customer_pref_delivery_date =fo.first_date)
        /(
            select count(distinct customer_id) 
            from Delivery)*100)
        ,2) as immediate_percentage 
```
## 🧩 Question 6

**Title:** Biggest Single Num  
**Link:** [🔗 Click to Open Problem]()  
**Platform:** LeetCode  
**Difficulty:** Easy  

```sql
MySQL Solution: 

```
## 🧩 Question 7

**Title:**   
**Link:** [🔗 Click to Open Problem]()  
**Platform:** LeetCode  
**Difficulty:** Medium  

```sql
MySQL Solution: 


```
## 🧩 Question 8

**Title:**   
**Link:** [🔗 Click to Open Problem]()  
**Platform:** LeetCode  
**Difficulty:** Medium  

```sql
MySQL Solution: 

```
## 🧩 Question 9

**Title:** 
Uber SQL Interview Question  
**Link:** [🔗 Click to Open Problem]()  
**Platform:** Datalemur  
**Difficulty:** Medium  

```sql
MySQL Solution: 

```
## 🧩 Question 10

**Title:**   
**Link:** [🔗 Click to Open Problem]()  
**Platform:** DataLemur  
**Difficulty:** Easy  

```sql
MySQL Solution: 


```

---
“Behind every dataset lies a decision — and every query is the key to unlocking it.”
----
