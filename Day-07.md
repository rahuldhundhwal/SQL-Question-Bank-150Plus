
# 🗓️Day 07 — SQL Practice Journal

**Date:** 31/10/2025  
**Platform(s):** [StrataScratch / LeetCode / DataLemur / HackerRank]  
**Total Questions Solved:** 10  

---

## 🧠 Overview


---

## 🧩 Question 1

**Title:** Daily Leads and Partners  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/daily-leads-and-partners/description/)  
**Platform:** LeetCode  
**Difficulty:** Easy  

```sql
MySQL Solution: 
# Write your MySQL query statement below
select date_id,
    make_name,
    count(distinct  lead_id) as unique_leads,
    count(distinct partner_id) as unique_partners
from DailySales
group by date_id,make_name
```
## 🧩 Question 2

**Title:**  Find Loyal Customers  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/find-loyal-customers/)  
**Platform:** LeetCode  
**Difficulty:** Medium  

```sql
MySQL Solution: 
WITH CustomerActivity AS (
    SELECT
        customer_id,
        DATEDIFF(MAX(transaction_date), MIN(transaction_date)) AS period_active_days,
        COUNT(CASE WHEN transaction_type = 'purchase' THEN 1 END) AS purchase_count,
        COUNT(CASE WHEN transaction_type = 'refund' THEN 1 END) AS refund_count
    FROM
        customer_transactions
    GROUP BY
        customer_id
)
SELECT
    customer_id
FROM
    CustomerActivity
WHERE
    period_active_days >= 30
    AND purchase_count >= 3
    AND (
        (refund_count * 100.0) / NULLIF(purchase_count + refund_count, 0)
    ) < 20
ORDER BY
    customer_id ASC;

```
## 🧩 Question 3

**Title:** Recyclable and Low Fat Products  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/recyclable-and-low-fat-products/description/)  
**Platform:** LeetCode  
**Difficulty:** Easy  

```sql
MySQL Solution:
# Write your MySQL query statement below
select product_id 
from Products
where low_fats='Y'
and recyclable='Y'
```
## 🧩 Question 4

**Title:** Movie Rating   
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/movie-rating/)  
**Platform:** LeetCode  
**Difficulty:** Medium 

```sql
MySQL Solution: 
(
SELECT u.name  AS results 
from users u join MovieRating mr 
ON u.user_id = mr.user_id
GROUP BY u.name
ORDER BY count(rating) DESC, u.name
LIMIT 1
)
union all

(
select m.title as results 
from Movies m join MovieRating mr
on m.movie_id =mr.movie_id 
where created_at between '2020/02/01' and '2020/02/29'
group by m.title 
order by avg(rating) desc ,m.title
limit 1

)


```
## 🧩 Question 5

**Title:**  Confirmation Rate
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/confirmation-rate/)  
**Platform:** LeetCode  
**Difficulty:** Medium 

```sql
MySQL Solution: 
# Write your MySQL query statement below
select u.user_id,
    coalesce(round((
        sum(case when c.action="confirmed" then 1 else 0 end )
        /(count(distinct c.time_stamp))),2),0) as confirmation_rate
from signups u left join  confirmations c
on u.user_id=c.user_id
group by user_id
```
## 🧩 Question 6

**Title:**  Find Zombie Sessions  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/find-zombie-sessions/)  
**Platform:** LeetCode  
**Difficulty:** Hard  

```sql
MySQL Solution: 
# Write your MySQL query statement below
with all_values as(
    select 
        user_id,
        session_id,
        min(event_timestamp) as start_time,
        max(event_timestamp) as  end_time,
        sum(case when event_type = "scroll" then 1 else 0 end )
        as scroll_count,
        sum(case when event_type = "click" then 1 else 0 end) 
        as click_count,
        sum(case when event_type = "purchase" then 1 else 0 end) 
        as purchase_count
    from app_events
    group by session_id,user_id
)
select 
    session_id,
    user_id,
    TIMESTAMPDIFF(MINUTE,start_time,end_time) 
    as session_duration_minutes,
    scroll_count
from all_values
where TIMESTAMPDIFF(MINUTE,start_time,end_time)>30
and scroll_count>=5 
and (click_count/scroll_count) <0.2
and purchase_count=0
order by scroll_count desc , session_id asc
```
## 🧩 Question 7

**Title:**Number of Unique Subjects Taught by Each Teacher   
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/number-of-unique-subjects-taught-by-each-teacher/description/)  
**Platform:** LeetCode  
**Difficulty:** Easy  

```sql
MySQL Solution: 
# Write your MySQL query statement below
select teacher_id,
    count(distinct subject_id) as cnt
from Teacher
group by teacher_id


```
## 🧩 Question 8

**Title:** Percentage of Users Attended a Contest  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/percentage-of-users-attended-a-contest/description/)  
**Platform:** LeetCode  
**Difficulty:** Easy  

```sql
MySQL Solution: 
# Write your MySQL query statement below
select contest_id,
    round((count(distinct user_id)/(
        select count(distinct user_id) 
        from Users)*100),2 )as percentage
from Register
group by contest_id
order by percentage desc,contest_id asc
```
## 🧩 Question 9

**Title:** Replace Employee ID With The Unique Identifier 
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/replace-employee-id-with-the-unique-identifier/description/)  
**Platform:** LeetCode  
**Difficulty:** Easy  

```sql
MySQL Solution: 
# Write your MySQL query statement below
select u.unique_id,
    e.name
from EmployeeUNI  u right join Employees e
on u.id =e.id
```
## 🧩 Question 10

**Title:** Employees With Missing Information  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/employees-with-missing-information/description/)  
**Platform:** LeetCode  
**Difficulty:** Easy  

```sql
MySQL Solution: 
# Write your MySQL query statement below
(
    select 
    e.employee_id
    from employees e 
    where name is null or (
         select salary from salaries
        where employee_id=e.employee_id
    ) is null
)
union (
    select 
    s.employee_id
    from salaries s 
    where salary is null or (
         select name from employees
        where employee_id=s.employee_id
    ) is null
)
order by employee_id asc

```

---
“Behind every dataset lies a decision — and every query is the key to unlocking it.”
----


