
# 🗓️Day 11 — SQL Practice Journal

**Date:** 05/11/2025  
**Platform(s):** Newton School  
**Total Questions Solved:** 10  

---

## 🧠 Overview


---

## 🧩 Question 1

**Title:** SQL- Average Salary  
**Link:** [🔗 Click to Open Problem](https://my.newtonschool.co/playground/database/d4msf6jrw57k)  
**Platform:** Netwon School  
**Difficulty:** Easy  

```sql
MySQL Solution: 
with my_helper as(
    select department_id,
    count(employee_id) as employee_count,
    avg(salary) as average_salary
    from Employees
    group by department_id
)

select d.department_name,
    m.average_salary,
    m.employee_count
from departments d 
join my_helper m
on d.department_id=m.department_id
order by average_salary desc
```
## 🧩 Question 2

**Title:**Top Courses by Enrollment
   
**Link:** [🔗 Click to Open Problem](https://my.newtonschool.co/playground/database/4qh318ruf6d9)  
  

```sql
MySQL Solution: 
select * from courses 
order by enrollment desc,
    course_name
limit 3
```
## 🧩 Question 3

**Title:** Top Distinct Product Prices  
**Link:** [🔗 Click to Open Problem](https://my.newtonschool.co/playground/database/fb7m9m7t9qyc)  
 

```sql
MySQL Solution:
select distinct price from products 
order by price desc
limit 3
```
## 🧩 Question 4

**Title:** Extract Country Code from Phone Numbers  
**Link:** [🔗 Click to Open Problem](https://my.newtonschool.co/playground/database/nv4gsyhu33kc)  
 

```sql
MySQL Solution: 
select *,
    substr(phone_number,locate('+',substr(phone_number,locate('+',phone_number)))+1,locate('-',phone_number,1)-2) as country_code
from contacts
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


