
# 🗓️Day 06 — SQL Practice Journal

**Date:** 30/10/2025  
**Platform(s):** [StrataScratch / LeetCode / DataLemur / HackerRank]  
**Total Questions Solved:** 10  

---

## 🧠 Overview


---

## 🧩 Question 1

**Title:** Product Sales Analysis I   
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/product-sales-analysis-i/description/)  
**Platform:** LeetCode  
**Difficulty:** Easy  

```sql
MySQL Solution: 
# Write your MySQL query statement below
select p.product_name,
    s.year,
    s.price
from sales s  left join product p 
on s.product_id=p.product_id

```
## 🧩 Question 2

**Title:**Project Employees I   
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/project-employees-i/description/)  
**Platform:** LeetCode  
**Difficulty:** Easy  

```sql
MySQL Solution: 
# Write your MySQL query statement below
select p.project_id,
    round(avg(e.experience_years),2) as average_years 
from Project p left join Employee e
on p.employee_id=e.employee_id
group by p.project_id
order by p.project_id
```
## 🧩 Question 3

**Title:** User Activity for the Past 30 Days I  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/user-activity-for-the-past-30-days-i/description/)  
**Platform:** LeetCode  
**Difficulty:** Easy  

```sql
MySQL Solution:
select 
    activity_date as day ,
    count(distinct user_id) as active_users
from Activity 
where activity_date <= '2019-07-27' 
and activity_date >= '2019-06-28'
group by activity_date

```
## 🧩 Question 4

**Title:**Last Person to Fit in the Bus   
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/last-person-to-fit-in-the-bus/)  
**Platform:** LeetCode  
**Difficulty:** Medium 

```sql
MySQL Solution: 
with cte as (select person_id,
    person_name,
    turn,
    sum(weight) over(order by turn)as running_weight
from Queue
)

select person_name from cte where running_weight<=1000 order by turn desc limit 1
```
## 🧩 Question 5

**Title:** Sales Analysis III
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/sales-analysis-iii/)  
**Platform:** LeetCode  
**Difficulty:** Medium 

```sql
MySQL Solution: 
SELECT
  p.product_id,
  p.product_name
FROM Product AS p
JOIN Sales AS s
  ON p.product_id = s.product_id
GROUP BY
  p.product_id,
  p.product_name
HAVING
  MIN(s.sale_date) >= '2019-01-01' AND MAX(s.sale_date) <= '2019-03-31';

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


