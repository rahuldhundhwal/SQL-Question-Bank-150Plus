
# 🗓️Day 10 — SQL Practice Journal

**Date:** 04/11/2025  
**Platform(s):** [StrataScratch / LeetCode / DataLemur / HackerRank]  
**Total Questions Solved:** 10  

---

## 🧠 Overview


---

## 🧩 Question 1

**Title:** Find Total Time Spent by Each Employee  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/find-total-time-spent-by-each-employee/)  
**Platform:** LeetCode  
**Difficulty:** Easy  

```sql
MySQL Solution: 
# Write your MySQL query statement below
select event_day as day,
    emp_id,
    sum(out_time-in_time) as total_time
from EMployees
group by event_day,emp_id
```
## 🧩 Question 2

**Title:** Find Overbooked Employees  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/find-overbooked-employees/description/)  
**Platform:** LeetCode  
**Difficulty:** Medium  

```sql
MySQL Solution: 
WITH meeting_week AS (
    SELECT 
        employee_id,
        YEARWEEK(meeting_date, 1) AS week_num,
        SUM(duration_hours) AS total_week_hours
    FROM meetings
    GROUP BY employee_id, YEARWEEK(meeting_date, 1)
)
SELECT 
    e.employee_id,
    e.employee_name,
    e.department,
    COUNT(*) AS meeting_heavy_weeks
FROM employees e
JOIN meeting_week m 
    ON e.employee_id = m.employee_id
WHERE m.total_week_hours > 20
GROUP BY e.employee_id, e.employee_name, e.department
HAVING COUNT(*) >= 2
ORDER BY meeting_heavy_weeks DESC, e.employee_name ASC;
```
## 🧩 Question 3

**Title:**Fix Names in a Table   
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/fix-names-in-a-table/)  
**Platform:** LeetCode  
**Difficulty:** Easy  

```sql
MySQL Solution:
# Write your MySQL query statement below
select 
    user_id,
    concat(upper(substr(name,1,1)),lower(substr(name,2,length(name)))) as name
from Users
order by user_id
```
## 🧩 Question 4

**Title:**   
**Link:** [🔗 Click to Open Problem]()  
**Platform:** LeetCode  
**Difficulty:** Medium 

```sql
MySQL Solution: 

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

**Title:** Average Time of Process per Machine  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/average-time-of-process-per-machine/description/)  
**Platform:** LeetCode  
**Difficulty:** Easy  

```sql
MySQL Solution: 
with my_helper as (
    select machine_id,
    process_id,
    max(timestamp)-min(timestamp) as total_time
from Activity
group by process_id,machine_id
)

select machine_id,
    round(sum(total_time)/count(process_id),3) as processing_time 
from my_helper
group by machine_id
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

**Title:** Calculate Special Bonus  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/calculate-special-bonus/description/)  
**Platform:** LeetCode  
**Difficulty:** Easy  

```sql
MySQL Solution: 
# Write your MySQL query statement below
select employee_id,
    case 
        when (employee_id%2=1 and name not like "M%") then salary
        else 0
        end as bonus
from Employees
order by employee_id
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

**Title:** Primary Department for Each Employee  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/primary-department-for-each-employee/description/)  
**Platform:** DataLemur  
**Difficulty:** Easy  

```sql
MySQL Solution: 
# Write your MySQL query statement below
select employee_id,
    department_id
from Employee 
where primary_flag = "Y"
    or employee_id in(
        select employee_id
        from employee 
        group by employee_id
        having count(distinct department_id) =1
    )

```

---
“Behind every dataset lies a decision — and every query is the key to unlocking it.”
----


