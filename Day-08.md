
# 🗓️Day 08 — SQL Practice Journal

**Date:** 01/11/2025  
**Platform(s):** [StrataScratch / LeetCode / DataLemur / HackerRank]  
**Total Questions Solved:** 10  

---

## 🧠 Overview


---

## 🧩 Question 1

**Title:** Find Valid Emails   
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/find-valid-emails/description/)  
**Platform:** LeetCode  
**Difficulty:** Easy  

```sql
MySQL Solution: 
# Write your MySQL query statement below
select * 
from Users
where email rlike '^[a-zA-Z0-9_]+@[a-zA-Z]+\\.com$'
order by user_id asc

```
## 🧩 Question 2

**Title:** Seasonal Sales Analysis  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/seasonal-sales-analysis/)  
**Platform:** LeetCode  
**Difficulty:** Medium  

```sql
MySQL Solution: 
# Write your MySQL query statement below
with season_products as (
    select 
    case 
        when extract(month from sale_date) in (12,1,2) then "Winter"
        when extract(month from sale_date) in (3,4,5) then "Spring"
        when extract(month from sale_date) in (6,7,8) then "Summer"
        when extract(month from sale_date) in (9,10,11) then "Fall"
    end as season,
        p.category,
        sum(s.quantity) as total_quantity,
        sum(quantity*price) as total_revenue

    from sales s join products p 
    on p.product_id=s.product_id
    group by season,p.category
)

select * 
from season_products sp 
where total_revenue =(
    select max(total_revenue)
    from season_products 
    where season =sp.season and total_quantity =(
        select max(total_quantity)
        from season_products 
        where season =sp.season
)
)
order by season asc

```
## 🧩 Question 3

**Title:** Find Books with Polarized Opinions   
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/find-books-with-polarized-opinions/)  
**Platform:** LeetCode  
**Difficulty:** Easy  

```sql
MySQL Solution:
# Write your MySQL query statement below
with book_finds as(
    select b.*,
    sum(case when session_rating >=4 then 1 else 0 end) as 4th_rating,
    sum(case when session_rating <=2 then 1 else 0 end) as 2nd_rating,
    count(distinct session_id) as reading_sessions,
    (max(session_rating)-min(session_rating)) as rating_spread
from books b join reading_sessions s
on b.book_id=s.book_id
group by book_id
)

select  book_id,
        title,
        author,
        genre,pages,
        rating_spread,
        round((4th_rating+2nd_rating)/reading_sessions,2) as polarization_score 
from book_finds
where 
    4th_rating > 0 and 
    2nd_rating >0  and 
    reading_sessions>=5 and 
    ((4th_rating+2nd_rating)/reading_sessions)>=0.6
order by polarization_score desc , title desc

```
## 🧩 Question 4

**Title:** Find Products with Valid Serial Numbers  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/find-products-with-valid-serial-numbers/description/)  
**Platform:** LeetCode  
**Difficulty:** Medium 

```sql
MySQL Solution: 
# Write your MySQL query statement below
select * 
from products
where  regexp_like ( description,'\\bSN[0-9]{4}-[0-9]{4}\\b','c')
order by product_id asc
```
## 🧩 Question 5

**Title:** 
**Link:** [🔗 Click to Open Problem]()  
**Platform:** LeetCode  
**Difficulty:** Medium 

```sql
MySQL Solution: 

```
## 🧩 Question 6

**Title:** Invalid Tweets  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/invalid-tweets/description/)  
**Platform:** LeetCode  
**Difficulty:** Easy  

```sql
MySQL Solution: 
# Write your MySQL query statement below
select tweet_id from Tweets
where char_length(content) >15
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


