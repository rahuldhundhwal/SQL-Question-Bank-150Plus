
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

**Title:** Highest Salary In Department. - MySQL
**Link:** [🔗 Click to Open Problem](https://my.newtonschool.co/playground/database/usa1lt7lf46a?admin-course-hash=2g7by720foge)  
**Platform:** Newton School  
**Difficulty:** Medium 

```sql
MySQL Solution: 
select 
    department,
    first_name as employee_name,
    salary
from employee e1
where salary =(
    select max(salary) 
    from employee 
    where department =e1.department
)
order by salary desc
```
## 🧩 Question 6

**Title:** Biggest Single Num  
**Link:** [🔗 Click to Open Problem](https://my.newtonschool.co/playground/database/gq7rc45wymwo?admin-course-hash=2g7by720foge)  
**Platform:** Newton  
**Difficulty:** Medium  

```sql
MySQL Solution: 
with my_helper as (
    select date,
    consumption
    from fb_eu_energy

    union all
    
    select date,
    consumption
    from fb_asia_energy

    union all
    
    select date,
    consumption
    from fb_na_energy
)

select date,
    sum(consumption) as total_energy 
from my_helper e
group by date 
having  total_energy  = (
    select 
    (sum(consumption)) as total_enery
    from my_helper
    group by date 
    order by total_enery desc
    limit 1
)

order by date 
```
## 🧩 Question 7

**Title:** Developers project assignments  
**Link:** [🔗 Click to Open Problem](https://my.newtonschool.co/playground/database/ksx84flc81q4?admin-course-hash=2g7by720foge)  
**Platform:** Newton  
**Difficulty:** Medium  

```sql
MySQL Solution: 
select 
    distinct developer_id,
case
    when developer_id in(
        select developer_id
        from CompanyA_developers
    ) then "CompanyA" 
    when developer_id in(
        select developer_id
        from CompanyB_developers
    ) then "CompanyB"
    end as status
from project_assignments
where developer_id not in (
    select a.developer_id
    from CompanyA_developers a
    join CompanyB_developers b
on a.developer_id=b.developer_id
)
order by developer_id

```
## 🧩 Question 8

**Title:** 
Customers with Specific Brands - MySQL   
**Link:** [🔗 Click to Open Problem](https://my.newtonschool.co/playground/database/9yj38a62q5oq?admin-course-hash=2g7by720foge)  
**Platform:** Newton  
**Difficulty:** Medium  

```sql
MySQL Solution: 
select 
    customer_id 
from facebook_sales fs
join facebook_products fp
on fs.product_id=fp.product_id
where brand_name = "Fort West"
intersect
select 
    customer_id 
from facebook_sales fs
join facebook_products fp
on fs.product_id=fp.product_id
where brand_name = "Golden"

order by customer_id
```
## 🧩 Question 9

**Title:** Authors publishing every month 
**Link:** [🔗 Click to Open Problem](https://my.newtonschool.co/playground/database/0t86210aumyl?admin-course-hash=2g7by720foge)  
**Platform:** Newton  
**Difficulty:** Medium  

```sql
MySQL Solution: 
select 
    a.AuthorName,
case 
    when count(distinct extract(Year_month from p.PublicationDate)) >= 8 then "Prolific Authors"
    when count(distinct extract(year_month from p.PublicationDate)) <= 7 and count(distinct extract(year_month from p.PublicationDate))>=4 then "Active Authors"
    when count(distinct extract(year_month from p.PublicationDate)) < 4 then "Occasional Authors"
    end as Category
from authors a join Publications p 
on a.authorId=p.authorID
where p.Genre ="Fiction"
group by a.authorid
having count(p.publicationID)>=1
order by a.AuthorName
```
## 🧩 Question 10

**Title:** 
Frequent Travellers-1   
**Link:** [🔗 Click to Open Problem](https://my.newtonschool.co/playground/database/rw5tbs81z5bm?admin-course-hash=2g7by720foge)  
**Platform:** Newton  
**Difficulty:** Medium  

```sql
MySQL Solution: 
select * 
from travel_history t
where 3 <= (
    select count(distinct end_city)
    from travel_history 
    where t.traveler =traveler

)
and 
date in (
    select min(date) 
    from travel_history
    where traveler=t.traveler and end_city in(
        select distinct end_city
        from travel_history 
        where t.traveler =traveler  
    )
    group by end_city

)
and end_city in(
        select distinct end_city
        from travel_history 
        where t.traveler =traveler  
)
order by traveler,date,start_city

```

---
“Behind every dataset lies a decision — and every query is the key to unlocking it.”
----


