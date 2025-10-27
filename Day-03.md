# 🗓️Day 03 — SQL Practice Journal

**Date:** 27/10/2025  
**Platform(s):** [StrataScratch / LeetCode / DataLemur / HackerRank]  
**Total Questions Solved:** [10]  
**Estimated Practice Time:** [X hours]

---

## 🧠 Overview


---

## 🧩 Question 1

**Title:** Top Travellers  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/top-travellers/submissions/1812850334/)  
**Platform:** LeetCode  
**Difficulty:** Easy  

```sql
MySQL Solution: 
# Write your MySQL query statement below
select name,
    (select coalesce(sum(distance),0) from Rides where user_id = users.id) as travelled_distance
from users
order by travelled_distance desc,name asc
```
## 🧩 Question 2

**Title:** Captial Gain/Loss  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/capital-gainloss/)  
**Platform:** LeetCode  
**Difficulty:** Medium  

```sql
MySQL Solution: 
SELECT DISTINCT 
    stock_name, 
    (
        (SELECT SUM(COALESCE(price, 0)) 
         FROM stocks 
         WHERE operation = 'Sell' AND stock_name = s.stock_name) 
        - 
        (SELECT SUM(COALESCE(price, 0)) 
         FROM stocks 
         WHERE operation = 'Buy' AND stock_name = s.stock_name)
    ) AS capital_gain_loss
FROM stocks s;

```
## 🧩 Question 3

**Title:** Classes With at Least 5 Students  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/classes-with-at-least-5-students/description/)  
**Platform:** LeetCode  
**Difficulty:** Easy  

```sql
MySQL Solution: 
select distinct class
from courses c
where (select count(student) from courses where c.class=class)>=5
```
## 🧩 Question 4

**Title:** SalesPerson  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/sales-person/submissions/1812918093/)  
**Platform:** LeetCode  
**Difficulty:** Medium 

```sql
MySQL Solution: 
select name 
from salesperson 
where sales_id not in ( 
    select sales_id 
    from orders 
    where com_id  in (
        select com_id 
        from company 
        where name="Red"
    )
)
```
## 🧩 Question 5

**Title:** Triangle Judgement
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/triangle-judgement/)  
**Platform:** LeetCode  
**Difficulty:** Medium 

```sql
MySQL Solution: 
select x,y,z,
case 
    when ((x+y)>z) and ((y+z)>x) and ((z+x)>y) then "Yes"
    else "No"
    end as triangle
from Triangle
```
## 🧩 Question 6

**Title:** Biggest Single Num  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/biggest-single-number/)  
**Platform:** LeetCode  
**Difficulty:** Easy  

```sql
MySQL Solution: 
# Write your MySQL query statement below

select max(distinct num ) as num
from MyNumbers
where num  in (select distinct num from MyNUmbers m where (select count(num) from MynUmbers where num = m.num)=1)  
```
## 🧩 Question 7

**Title:** Customers Who Bought All Products  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/customers-who-bought-all-products/description/)  
**Platform:** LeetCode  
**Difficulty:** Medium  

```sql
MySQL Solution: 
# Write your MySQL query statement below
select distinct customer_id
from Customer c
group by customer_id
having count(distinct product_key) = (select count(product_key) from Product)

```
## 🧩 Question 8

**Title:** Market Analysis 1  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/market-analysis-i/)  
**Platform:** LeetCode  
**Difficulty:** Medium  

```sql
MySQL Solution: 
select user_id as buyer_id,
       join_date,
       ( 
          select count(order_id)
          from Orders 
          where Year(Order_date)='2019' and buyer_id=u.user_id
       ) as orders_in_2019 
from users  u
```
## 🧩 Question 9

**Title:** User's Third Transaction
Uber SQL Interview Question  
**Link:** [🔗 Click to Open Problem](https://datalemur.com/questions/sql-third-transaction)  
**Platform:** Datalemur  
**Difficulty:** Medium  

```sql
MySQL Solution: 
# Write your MySQL query statement below
 SELECT t1.user_id
     , t1.spend
     , t1.transaction_date
  FROM transactions t1
       INNER JOIN
       transactions t2
        ON t1.user_id = t2.user_id
       AND t2.transaction_date < t1.transaction_date
 GROUP BY t1.user_id
        , t1.spend
        , t1.transaction_date
HAVING COUNT(t2.transaction_date)=2;
```
## 🧩 Question 10

**Title:** Histogram of Tweets
Twitter SQL Interview Question  
**Link:** [🔗 Click to Open Problem](https://datalemur.com/questions/sql-histogram-tweets)  
**Platform:** DataLemur  
**Difficulty:** Easy  

```sql
MySQL Solution: 
select tweet_count as tweet_bucket,
        count(user_id) as users_num
 from (select user_id, count(tweet_id) as tweet_count
            from tweets
            where year(tweet_date)='2022'
            group by user_id
      ) as tweet_table
group by tweet_count

```

---
“Behind every dataset lies a decision — and every query is the key to unlocking it.”
----
