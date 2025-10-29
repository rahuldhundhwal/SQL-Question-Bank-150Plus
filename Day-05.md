
# 🗓️Day 05 — SQL Practice Journal

**Date:** 29/10/2025  
**Platform(s):** [StrataScratch / LeetCode / DataLemur / HackerRank]  
**Total Questions Solved:** 10  

---

## 🧠 Overview


---

## 🧩 Question 1

**Title:**  Not Boring Movies   
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/not-boring-movies/description/)  
**Platform:** LeetCode  
**Difficulty:** Easy  

```sql
MySQL Solution: 
# Write your MySQL query statement below
select * 
from Cinema 
where mod(id,2) <>  0 
and description <> "boring" 
order by rating desc
```
## 🧩 Question 2

**Title:** Monthly Transactions I   
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/monthly-transactions-i/description/)  
**Platform:** LeetCode  
**Difficulty:** Medium  

```sql
MySQL Solution: 
SELECT
    DATE_FORMAT(t.trans_date, '%Y-%m') AS month,
    COALESCE(t.country,null) AS country,
    COUNT(t.id) AS trans_count,
    SUM(CASE WHEN t.state = 'approved' THEN 1 ELSE 0 END) AS approved_count,
    SUM(t.amount) AS trans_total_amount,
    SUM(CASE WHEN t.state = 'approved' THEN t.amount ELSE 0 END) AS approved_total_amount
FROM
    Transactions t
GROUP BY
    month,
    country
ORDER BY
    month,
    country;

```
## 🧩 Question 3

**Title:**Reformat Department Table   
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/reformat-department-table/description/)  
**Platform:** LeetCode  
**Difficulty:** Easy  

```sql
MySQL Solution:
SELECT
    id,
    SUM(CASE WHEN month = 'Jan' THEN revenue ELSE null END) AS Jan_Revenue,
    SUM(CASE WHEN month = 'Feb' THEN revenue ELSE null END) AS Feb_Revenue,
    SUM(CASE WHEN month = 'Mar' THEN revenue ELSE null END) AS Mar_Revenue,
    SUM(CASE WHEN month = 'Apr' THEN revenue ELSE null END) AS Apr_Revenue,
    SUM(CASE WHEN month = 'May' THEN revenue ELSE null END) AS May_Revenue,
    SUM(CASE WHEN month = 'Jun' THEN revenue ELSE null END) AS Jun_Revenue,
    SUM(CASE WHEN month = 'Jul' THEN revenue ELSE null END) AS Jul_Revenue,
    SUM(CASE WHEN month = 'Aug' THEN revenue ELSE null END) AS Aug_Revenue,
    SUM(CASE WHEN month = 'Sep' THEN revenue ELSE null END) AS Sep_Revenue,
    SUM(CASE WHEN month = 'Oct' THEN revenue ELSE null END) AS Oct_Revenue,
    SUM(CASE WHEN month = 'Nov' THEN revenue ELSE null END) AS Nov_Revenue,
    SUM(CASE WHEN month = 'Dec' THEN revenue ELSE null END) AS Dec_Revenue
FROM
    Department
GROUP BY
    id;

```
## 🧩 Question 4

**Title:** Product Price at a Given Date   
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/product-price-at-a-given-date/description/)  
**Platform:** LeetCode  
**Difficulty:** Medium 

```sql
MySQL Solution: 
# Write your MySQL query statement below
select distinct product_id,
        coalesce(new_price,10) as price
from Products p 
where change_date = (
    select max(change_date) 
    from Products where 
    product_id=p.product_id
    and change_date <= '2019-08-16'
)
UNION
SELECT DISTINCT product_id, 10 AS price
FROM Products
WHERE product_id NOT IN (
    SELECT product_id
    FROM Products
    WHERE change_date <= '2019-08-16'
)
order by product_id;
```
## 🧩 Question 5

**Title:** Count Salary Categories   
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/count-salary-categories/description/)  
**Platform:** LeetCode  
**Difficulty:** Medium 

```sql
MySQL Solution: 
# Write your MySQL query statement below
select 
    lt.category,
    coalesce(rt.accounts_count,0) as accounts_count
from
(
    SELECT 'Low Salary' AS category
    UNION ALL SELECT 'Average Salary'
    UNION ALL SELECT 'High Salary'
) as lt
left join
(select 
case 
    when income<20000 then "Low Salary"
    when income between 20000 and 50000 then "Average Salary"
    when income>50000 then "High Salary"
    end as category,
    coalesce(count(account_id),0) as accounts_count
from Accounts
group by category) as rt on lt.category=rt.category

```
## 🧩 Question 6

**Title:** Teams Power Users
Microsoft SQL Interview Question  
**Link:** [🔗 Click to Open Problem](https://datalemur.com/questions/teams-power-users)  
**Platform:** DataLemur  
**Difficulty:** Easy  

```sql
MySQL Solution: 
select sender_id,
       count(message_id) as message_count
from messages
where sent_date between '2022-08-01' and '2022-08-31'
group by sender_id
order by message_count desc
limit 2
       
```
## 🧩 Question 7

**Title:**Laptop vs. Mobile Viewership
NY Times SQL Interview Question   
**Link:** [🔗 Click to Open Problem](https://datalemur.com/questions/laptop-mobile-viewership)  
**Platform:** DataLemur  
**Difficulty:** Easy  

```sql
MySQL Solution: 
SELECT
    COUNT(CASE WHEN device_type = 'laptop' THEN user_id END) AS laptop_views,
    COUNT(CASE WHEN device_type IN ('tablet', 'phone') THEN user_id END) AS mobile_views
FROM
    viewership;

```
## 🧩 Question 8

**Title:** Duplicate Job Listings
LinkedIn SQL Interview Question  
**Link:** [🔗 Click to Open Problem](https://datalemur.com/questions/duplicate-job-listings)  
**Platform:** DataLemur  
**Difficulty:** Easy  

```sql
MySQL Solution: 
select
  count(distinct c1.company_id) as duplicate_companies
from 
  job_listings c1
join 
  job_listings c2
on 
  c1.company_id = c2.company_id
and 
  c1.job_id <> c2.job_id
where c1.title= c2.title and c1.description=c2.description
```
## 🧩 Question 9

**Title:**Data Science Skills
LinkedIn SQL Interview Question   
**Link:** [🔗 Click to Open Problem](https://datalemur.com/questions/matching-skills)  
**Platform:** Datalemur  
**Difficulty:** Easy  

```sql
MySQL Solution: 
select distinct c1.candidate_id 
from candidates c1 
join candidates c2
on c1. candidate_id =c2.candidate_id 
and c1.skill<>c2.skill
join candidates c3
on c1. candidate_id =c3.candidate_id 
and c1.skill<>c3.skill and c2.skill<>c3.skill
where c1.skill in ('Python', 'Tableau', 'PostgreSQL') and 
c2.skill in ('Python', 'Tableau', 'PostgreSQL') and
c3.skill in ('Python', 'Tableau', 'PostgreSQL')
-----------------------------------------
SELECT candidate_id
FROM candidates
WHERE skill IN ('Python', 'Tableau', 'PostgreSQL')
GROUP BY candidate_id
HAVING COUNT(skill) = 3
ORDER BY candidate_id;
```
## 🧩 Question 10

**Title:** Cities With Completed Trades
Robinhood SQL Interview Question   
**Link:** [🔗 Click to Open Problem](https://datalemur.com/questions/completed-trades)  
**Platform:** DataLemur  
**Difficulty:** Easy  

```sql
MySQL Solution: 
SELECT u.city,
  count(t.order_id) as total_orders
from trades t join 
users u 
on t.user_id =u.user_id
where t.status='Completed'
group by city
order by total_orders desc
limit 3

```

---
“Every SQL query I write sharpens how I think, not just how I code.”
----


