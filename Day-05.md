
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
“Every SQL query I write sharpens how I think, not just how I code.”
----


