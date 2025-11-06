
# 🗓️Day  — SQL Practice Journal

**Date:** 06/11/2025  
**Platform(s):** [Newton School]  
**Total Questions Solved:** 10  

---

## 🧠 Overview


---

## 🧩 Question 1

**Title:**  Rank Variance Per Country  
**Link:** [🔗 Click to Open Problem](https://my.newtonschool.co/playground/database/cfzappv6czem?admin-course-hash=2g7by720foge)    
**Difficulty:** Medium  

```sql
MySQL Solution: 
select a.country
from fb_active_users a
join fb_comments_count b 
on a.user_id=b.user_id
where b.created_at between '2019/12/01' and '2020/01/31'
group by a.country
having sum(number_of_comments)  > 0
order by sum(number_of_comments) desc
limit 20
```
## 🧩 Question 2

**Title:** Retrieve the number of processed and not- processed complaints of each type   
**Link:** [🔗 Click to Open Problem](https://my.newtonschool.co/playground/database/idv9xlh82hv5?admin-course-hash=2g7by720foge)    
**Difficulty:** Medium  

```sql
MySQL Solution: 
select 
    sum(processed) as total_processed_complaints
from facEbook_complaints 
```
## 🧩 Question 3

**Title:** Twitter CHECK Constraint_mysql
   
**Link:** [🔗 Click to Open Problem](https://my.newtonschool.co/playground/database/l3599celps2q?admin-course-hash=2g7by720foge)  
**Difficulty:** Medium  

```sql
MySQL Solution:
--Write your code here!!
create table Relationships(
    id INT,
    created_at DATETIME  default Current_TimeStamp,
    follower_id int,
    followed_id int
);
--Your code ends here!!
INSERT INTO Relationships (id, follower_id, followed_id) VALUES
(1, 1001, 2001),
(2, 1002, 2002),
(3, 1003, 2003),
(4, 1004, 2004);
SELECT followed_id FROM Relationships;
```
## 🧩 Question 4

**Title:** Distinct Salaries   
**Link:** [🔗 Click to Open Problem](https://my.newtonschool.co/playground/database/5bsqaflxq104?admin-course-hash=2g7by720foge)  
**Difficulty:** Medium 

```sql
MySQL Solution: 
select 
    department,
    max(salary) as salary
from twitter_employee
group by department
union all
select 
    department,
    max(salary) as salary
from twitter_employee t
where salary <(
    select 
        max(salary) as salary
    from twitter_employee
    where t.department=department
)
group by department
union all
select 
    department,
    max(salary) as salary
from twitter_employee t1
where salary <(
    select 
        max(salary) as salary
    from twitter_employee t
    where salary <(
            select 
                max(salary) as salary
            from twitter_employee
            where t1.department=department
    ) and
    t1.department =department

)
group by department
order by department asc,
    salary desc
```
## 🧩 Question 5

**Title:**Linkedln 
**Link:** [🔗 Click to Open Problem](https://my.newtonschool.co/playground/database/aet0rrkwb93f?admin-course-hash=2g7by720foge)  
**Difficulty:** Medium 

```sql
MySQL Solution: 
select 
    count(distinct a.company_id) as total_duplicate_companies
from job_listings a
join job_listings b
on a.company_id=b.company_id
and a.job_id<>b.job_id
where a.title = b.title
and a.title=b.title

```
## 🧩 Question 6

**Title:** 
Product Transaction Count-1  
**Link:** [🔗 Click to Open Problem](https://my.newtonschool.co/playground/database/1dej93ajomnf?admin-course-hash=2g7by720foge)  
**Difficulty:** Medium  

```sql
MySQL Solution: 
select 
    i.product_name,
    count(transaction_id)
from excel_sql_inventory_data i
join excel_sql_transaction_data t
on i.product_id=t.product_id
group by i.product_id,i.product_name
order by i.product_id asc


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


