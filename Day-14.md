# 🗓️Day 14 — SQL Practice Journal

**Date:** 21/11/2025  
**Platform(s):** [Newton School]  
**Total Questions Solved:** 10  

---

## 🧠 Overview


---

## 🧩 Question 1

**Title:** SQL- Previous Highest Wickets - MySQL
   
**Link:** [🔗 Click to Open Problem](https://my.newtonschool.co/playground/database/ysar6yjii3q0)    
**Difficulty:** Medium  

```sql
MySQL Solution:
SELECT 
    player_name,
    wickets_taken,
    LAG(wickets_taken) OVER (
        ORDER BY wickets_taken DESC, player_name ASC
    ) AS previous_highest_wickets
FROM CricketPlayer
ORDER BY wickets_taken DESC, player_name ASC;

```
## 🧩 Question 2

**Title:** Performance Ranking!!
   
**Link:** [🔗 Click to Open Problem](https://my.newtonschool.co/playground/database/teiwsmmhfrpo)    
**Difficulty:** Medium  

```sql
MySQL Solution:
select 
    department_id,
    employee_id,
    performance_score ,
    rank() over(partition by department_id order by performance_score  desc) as ranking
from employee_performance e
where evaluation_date= (
    select max(evaluation_date)
    from employee_performance
    where e.employee_id =employee_id 
    and e.department_id=department_id
)
order by ranking desc
```
## 🧩 Question 3

**Title:** Newton's Call length!!
   
**Link:** [🔗 Click to Open Problem](https://my.newtonschool.co/playground/database/haqg0n63qgmu)  
**Difficulty:** Medium  

```sql
MySQL Solution:
select 
    request_id,
    round(avg(call_duration),2) as avg_call_duration
from newtons_call_tracking nct
where created_on <> (
    select min(created_on)
    from newtons_call_tracking
    where nct.request_id=request_id
)
group by request_id
order by avg_call_duration desc,request_id asc
```
## 🧩 Question 4

**Title:** Beds and Hotels
   
**Link:** [🔗 Click to Open Problem](https://my.newtonschool.co/playground/database/0yqpp0skagwh)  
**Difficulty:** Medium 

```sql
MySQL Solution: 
select 
    host_id,
    sum(n_beds) as total_beds,
    rank() over(order by sum(n_beds) desc) as bed_rank
from apartments
group by host_id
order by total_beds desc, host_id asc
```
## 🧩 Question 5

**Title:** 
   
**Link:** [🔗 Click to Open Problem]()  
**Difficulty:** Medium 

```sql
MySQL Solution:
 
```
## 🧩 Question 6

**Title:** 
   
**Link:** [🔗 Click to Open Problem]()  
**Difficulty:** Medium 

```sql
MySQL Solution:
 
```
## 🧩 Question 7

**Title:** 
   
**Link:** [🔗 Click to Open Problem]()  
**Difficulty:** Medium 

```sql
MySQL Solution:
 
```
## 🧩 Question 8

**Title:** 
   
**Link:** [🔗 Click to Open Problem]()  
**Difficulty:** Medium 

```sql
MySQL Solution:
 
```
## 🧩 Question 9

**Title:** 
   
**Link:** [🔗 Click to Open Problem]()  
**Difficulty:** Medium 

```sql
MySQL Solution:
 
```
## 🧩 Question 10

**Title:** 
   
**Link:** [🔗 Click to Open Problem]()  
**Difficulty:** Medium 

```sql
MySQL Solution:
 
```
---
“Behind every dataset lies a decision — and every query is the key to unlocking it.”
----
