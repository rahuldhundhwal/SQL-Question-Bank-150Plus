# 🗓️Day 13 — SQL Practice Journal

**Date:** 07/11/2025  
**Platform(s):** [Newton School]  
**Total Questions Solved:** 10  

---

## 🧠 Overview


---

## 🧩 Question 1

**Title:**  Highest Cost Orders. - MySQL  
**Link:** [🔗 Click to Open Problem](https://my.newtonschool.co/playground/database/38tvytutmv86?admin-course-hash=2g7by720foge)    
**Difficulty:** Medium  

```sql
MySQL Solution: 
with my_helper as(
    select  
    c.first_name  AS first_name,
    o.order_date AS order_date,
    (sum(total_order_cost)) as total_order_cost
    from orders o join customers c
    on o.cust_id=c.id
    where order_date between '2019/02/01' and '2019/05/01'
    group by c.first_name, order_date
)

select first_name,
    total_order_cost,
    order_date
from my_helper m
where total_order_cost =(
    select max(total_order_cost)
    from my_helper    
)

```
## 🧩 Question 2

**Title:** Seat Availability - MySQL   
**Link:** [🔗 Click to Open Problem](https://my.newtonschool.co/playground/database/22r9ahnsjd3b?admin-course-hash=2g7by720foge)    
**Difficulty:** Medium  

```sql
MySQL Solution: 
select 
    a.seat_number as available_seat1,
    b.seat_number as available_seat2
from theater_availability a
join theater_availability b
on a.seat_number =b.seat_number-1
and a.is_available = 1 and b.is_available=1
```
## 🧩 Question 3

**Title:** Snapchat
   
**Link:** [🔗 Click to Open Problem](https://my.newtonschool.co/playground/database/gdoxeavkdbm5?admin-course-hash=2g7by720foge)  
**Difficulty:** Medium  

```sql
MySQL Solution:
with my_helper as (
    select 
     a.age_bucket as age_bucket,
     sum(case when activity_type = "send" then time_spent else 0 end ) as send_time,
     sum(case when activity_type = "open" then time_spent else 0 end ) as open_time,
     sum(time_spent) as total_time
from age_breakdown a 
join activities b
on a.user_id =b.user_id
and b.activity_type in ("send","open")
group by age_bucket

)

select 
    age_bucket,
    round(send_time*100.0/total_time,1) as send_perc,
    round(open_time*100.0/total_time,1) as open_perc
from my_helper
order by age_bucket
```
## 🧩 Question 4

**Title:** World Tours - MySQL
   
**Link:** [🔗 Click to Open Problem](https://my.newtonschool.co/playground/database/5g1a5yzdq5g9?admin-course-hash=2g7by720foge)  
**Difficulty:** Medium 

```sql
MySQL Solution: 
select count(distinct t1.traveler) as n_travelers_returned
from travel_history t1
join travel_history t2
on t1.traveler =t2.traveler
and  t1.start_city =t2.end_city
where t1.date = (
    select min(date)
    from travel_history
    where traveler = t1.traveler
)
and  t2.date = (
    select max(date)
    from travel_history
    where traveler = t1.traveler
)
```
## 🧩 Question 5

**Title:**CTR Analysis Based on Dynamic Rating Buckets in E-Commerce Search
 
**Link:** [🔗 Click to Open Problem](https://my.newtonschool.co/playground/database/0s5leb1rkh0t?admin-course-hash=2g7by720foge)  
**Difficulty:** Medium 

```sql
MySQL Solution: 
with my_helper as(
    select 
case
    when rating <=1 then "low_ratings" 
    when rating >1 and rating <=2 then "mid_ratings"
    when rating >2 and rating<=3 then "high_ratings"
    end as rating_bucket ,
    has_clicked
from product_search_events

)

select rating_bucket,
    round(sum(has_clicked)/count(has_clicked),4) as ctr
from my_helper
group by rating_bucket
order by rating_bucket
```
## 🧩 Question 6

**Title:** Comparing Store Revenue to Company Average for April 2024

Product Transaction Count-1  
**Link:** [🔗 Click to Open Problem](https://my.newtonschool.co/playground/database/rs6dw87fguy2?admin-course-hash=2g7by720foge)  
**Difficulty:** Medium  

```sql
MySQL Solution: 
with my_helper as(
    select
    store_id,
    Date_Format(sale_date, '%Y-%m') as sale_month,
    avg(revenue) as avg_sales
    from sales 
    group by store_id,Date_Format(sale_date, '%Y-%m')
)

select
    store_id,
    sale_month,
case
    when avg_sales> (
        select  avg(revenue)
        from sales
        where Date_Format(sale_date, '%Y-%m')= a.sale_month
        group by Date_Format(sale_date, '%Y-%m')
    ) then "higher"
    when avg_sales< (
        select  avg(revenue)
        from sales
        where Date_Format(sale_date, '%Y-%m')= a.sale_month
        group by Date_Format(sale_date, '%Y-%m')
    ) then "lower"
    else "same"
    end as comparison
from my_helper a
order by store_id

```
## 🧩 Question 7

**Title:** My SQL-Rows With Missing Values
   
**Link:** [🔗 Click to Open Problem](https://my.newtonschool.co/playground/database/5jytyeypgjks?admin-course-hash=2g7by720foge)  
**Difficulty:** Medium  

```sql
MySQL Solution: 
select * 
from user_flags
where ((user_firstname ="None") + (user_lastname = "None" )+ (video_id ="None") + (flag_id="None")) >1
    
order by user_firstName,user_LastName
```
## 🧩 Question 8

**Title:**Analyzing Costs of All 3-Flavor Ice Cream Sundae Combinations

   
**Link:** [🔗 Click to Open Problem](https://my.newtonschool.co/playground/database/4eclfw5t7vqs?admin-course-hash=2g7by720foge)  
**Difficulty:** Medium  

```sql
MySQL Solution: 
with sorted as(
    select * from ice_cream_flavors
    order by flavor_name asc
)

select 
    concat(a.flavor_name,',',b.flavor_name,',',c.flavor_name) as sundae,
    a.cost +b.cost +c.cost as total_cost 
from sorted a
join sorted b
on a.flavor_name < b.flavor_name
join sorted c
on a.flavor_name < c.flavor_name and
c.flavor_name > b.flavor_name
order by total_cost desc, sundae asc
```
## 🧩 Question 9

**Title:** Sales Recency Classification by Product – Fixed Year Analysis
  
**Link:** [🔗 Click to Open Problem](https://my.newtonschool.co/playground/database/b879q6o5y4ft?admin-course-hash=2g7by720foge)  
**Difficulty:** Medium  

```sql
MySQL Solution: 
select 
    p.product_id,
    p.product_name,
    (select distinct c.category_name from categories c where p.category_id=c.category_id) as category_name,
    (select distinct r.region_id from product_regions r where p.product_id=r.product_id) as region_id,
    (select distinct m.manager_name from managers m where m.region_id=(select distinct r.region_id from product_regions r where p.product_id=r.product_id)) as manager_name,
    sum(s.sale_amount) as total_sales_amount,
    count(distinct month(s.sale_date)) as months_sold,
    case
        when max(sale_date)>='2025-07-02' then "Fresh"
         when max(sale_date)<'2025-07-02' and  max(sale_date)>= "2025-05-03" then "Stale"
         else "Dormant"
    end as recent_flag 
from sales_transactions s right join
    products p
on p.product_id=s.product_id
where year(sale_date)=2025
group by p.product_id, p.product_name,category_name,region_id,manager_name
order by p.product_id
```
## 🧩 Question 10

**Title:** Top Rated Models  
**Link:** [🔗 Click to Open Problem]()  
**Difficulty:** Medium  

```sql
MySQL Solution: 


```

---
“Behind every dataset lies a decision — and every query is the key to unlocking it.”
----
