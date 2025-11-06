
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

**Title:** Department and salary range   
**Link:** [🔗 Click to Open Problem](https://my.newtonschool.co/playground/database/4n7uoiby6iap?admin-course-hash=2g7by720foge)  
**Difficulty:** Medium  

```sql
MySQL Solution: 
select 
    d.DepartmentName,
    avg(e.salary) as AverageSalary,
    count(e.EmployeeID) as TotalEmployees,
    round(max(e.salary),2) as HighestSalary,
    round(min(e.salary),2) as LowestSalary,
    round(sum(case when salary>70000 then 1 else 0 end)*100.0/
    count(e.EmployeeID),2) as PercentageOver70K,
    round(max(e.salary)-min(e.salary),2) as SalaryRange
from departments d 
join Employees e
on d.departmentid =e.departmentId
group by d.departmentid
having  AverageSalary > 50000 
and TotalEmployees>=5
and SalaryRange >30000
order by d.departmentname asc


```
## 🧩 Question 8

**Title:**Greater than average salary
   
**Link:** [🔗 Click to Open Problem](https://my.newtonschool.co/playground/database/aa5me84exnq0?admin-course-hash=2g7by720foge)  
**Difficulty:** Medium  

```sql
MySQL Solution: 
select 
    name 
from
    Students 
where student_id in (
    select student_id 
    from jobs
    where salary > (
        select avg(salary)
        from jobs
        where student_id in(
            select student_id
            from Students 
            where department_id =(
                select distinct department_id 
                from Departments
                where dept_name="CSE"
            ) 
        )
    )
)
order by name asc
```
## 🧩 Question 9

**Title:** Twitter  
**Link:** [🔗 Click to Open Problem](https://my.newtonschool.co/playground/database/zk5l5cf6gp26?admin-course-hash=2g7by720foge)  
**Difficulty:** Medium  

```sql
MySQL Solution: 
select user_id
from user_topics
where topic_id not in (
    select topic_id
    from topic_rankings
    where ranking <=100
    and ranking_date = "2021/01/01"
)
and follow_date="2021/01/01"
```
## 🧩 Question 10

**Title:** Top Rated Models  
**Link:** [🔗 Click to Open Problem](https://my.newtonschool.co/playground/database/26cjen9uahb2?admin-course-hash=2g7by720foge)  
**Difficulty:** Medium  

```sql
MySQL Solution: 
with agencyStats as (
    select  
        a.agency,
        count(a.model_id) total_models,
        round(coalesce(avg(rating),0),2) as average_rating,
        coalesce(count(assignment_id),0) as total_assignments
    from models a left join assignments m 
    on a.model_id=m.model_id
    group by a.agency

),
modelStats as(
    select 
        m.model_id,
        m.agency,
        coalesce(avg(rating),0) as avg_rating,
        coalesce(count(assignment_id),0) as total_assignments
    from models m left join assignments a
    on m.model_id=a.model_id
    group by m.model_id 
    having avg_rating >4.5
)

select 
    a.agency,
    a.average_rating,
    a.total_assignments
from agencyStats a
join modelStats m 
on a.agency=m.agency
group by a.agency
having a.average_rating>4.5 and 
    total_assignments>10
    and count(m.model_id)*1.0 >=0.7*(select count(model_id) from models where a.agency=agency)

```

---
“Behind every dataset lies a decision — and every query is the key to unlocking it.”
----


