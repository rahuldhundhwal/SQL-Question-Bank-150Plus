
# 🗓️Day 09 — SQL Practice Journal

**Date:** 03/11/2025  
**Platform(s):** [StrataScratch / LeetCode / DataLemur / HackerRank]  
**Total Questions Solved:** 10  

---

## 🧠 Overview


---

## 🧩 Question 1

**Title:**Final Account Balance
PayPal SQL Interview Question   
**Link:** [🔗 Click to Open Problem](https://datalemur.com/questions/final-account-balance)  
**Platform:** Datalemur  
**Difficulty:** Easy  

```sql
MySQL Solution: 
select account_id,
    sum(case when transaction_type= 'Deposit' then amount end)-
    sum(case when transaction_type= 'Withdrawal' then amount end) as final_balance
from TRANSACTIONs
group by account_id

```
## 🧩 Question 2

**Title:** Odd and Even Transactions   
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/odd-and-even-transactions/submissions/1819399900/)  
**Platform:** LeetCode  
**Difficulty:** Medium  

```sql
MySQL Solution: 
# Write your MySQL query statement below
select 
    transaction_date,
    sum(case when (amount%2)=1  then amount else 0 end ) as odd_sum,
    sum(case when (amount%2)=0  then amount else 0 end ) as even_sum
from transactions
group by transaction_date
order by transaction_date
```
## 🧩 Question 3

**Title:** Patients With a Condition   
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/patients-with-a-condition/description/)  
**Platform:** LeetCode  
**Difficulty:** Easy  

```sql
MySQL Solution:
# Write your MySQL query statement below
select * from Patients 
where conditions like 'DIAB1%' OR conditions LIKE '% DIAB1%'
```
## 🧩 Question 4

**Title:** Find Students Who Improved  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/find-students-who-improved/description/)  
**Platform:** LeetCode  
**Difficulty:** Medium 

```sql
MySQL Solution: 
# Write your MySQL query statement below
select student_id,
    subject,
    (
        select score
        from Scores 
        where s.student_id=student_id and 
        s.subject=subject
        and exam_Date = (
            select min(exam_date)
            from Scores 
            where s.student_id=student_id and 
            s.subject=subject
        )
    ) as first_score,
    (
        select score
        from Scores 
        where s.student_id=student_id and 
        s.subject=subject
        and exam_Date = (
            select max(exam_date)
            from Scores 
            where s.student_id=student_id and 
            s.subject=subject
        )
    ) as latest_score
from Scores s
group by student_id,subject
having first_score<latest_score and count(distinct exam_date)>1


```
## 🧩 Question 5

**Title:** Find Churn Risk Customers
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/find-churn-risk-customers/description/)  
**Platform:** LeetCode  
**Difficulty:** Medium 

```sql
MySQL Solution: 
# Write your MySQL query statement below
select user_id,
    (
        select plan_name
        from subscription_events 
        where user_id= s.user_id 
        and  event_id =(
            select max(event_id)
            from subscription_events where user_id= s.user_id
        )
    ) as current_plan,
    (
        select monthly_amount
        from subscription_events 
        where user_id= s.user_id 
        and  event_id =(
            select max(event_id)
            from subscription_events where user_id= s.user_id
        )
    ) as current_monthly_amount,
    (
        select max(monthly_amount)
        from subscription_events where user_id= s.user_id
    )as max_historical_amount,
    datediff(max(event_date ),min(event_date )) as days_as_subscriber 
from subscription_events s
where 0<(
    select count(event_id)
    from subscription_events
    where event_type="downgrade"
    and user_id= s.user_id
)
group by user_id 
having days_as_subscriber>=60 and current_plan is not null  and current_monthly_amount < 0.5*(max_historical_amount)
order by days_as_subscriber  desc,user_id

```
## 🧩 Question 6

**Title:** Customer Who Visited but Did Not Make Any Transactions  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/customer-who-visited-but-did-not-make-any-transactions/submissions/1820185648/)  
**Platform:** LeetCode  
**Difficulty:** Easy  

```sql
MySQL Solution: 
# Write your MySQL query statement below
select customer_id,
    count(visit_id) as count_no_trans
from Visits
where visit_id not in (
    select visit_id from Transactions
)
group by customer_id
```
## 🧩 Question 7

**Title:** DNA Pattern Recognition   
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/dna-pattern-recognition/)  
**Platform:** LeetCode  
**Difficulty:** Medium  

```sql
MySQL Solution: 
# Write your MySQL query statement below
SELECT
    sample_id,
    dna_sequence,
    species,
    case  when dna_sequence LIKE 'ATG%' then 1 else 0 end as has_start,
    case  when dna_sequence LIKE '%TGA' or dna_sequence LIKE '%TAA' or dna_sequence LIKE '%TAG' then 1 else 0 end as has_stop,
    case  when dna_sequence LIKE '%ATAT%' then 1 else 0 end as has_atat,
    case  when dna_sequence LIKE '%GGG%' then 1 else 0 end as has_ggg    
FROM
    Samples

ORDER BY
    sample_id ASC;


```
## 🧩 Question 8

**Title:** Rearrange Products Table   
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/rearrange-products-table/description/)  
**Platform:** LeetCode  
**Difficulty:** Medium  

```sql
MySQL Solution: 
select product_id, "store1" as store,store1 as price 
from Products where store1 is not null
union all
select product_id, "store2" as store,store2 as price 
from Products where store2 is not null
union all
select product_id, "store3" as store,store3 as price 
from Products where store3 is not null
```
## 🧩 Question 9

**Title:** Human Traffic of Stadium 
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/human-traffic-of-stadium/submissions/1820200435/)  
**Platform:** LeetCode  
**Difficulty:** Hard  

```sql
MySQL Solution: 
select 
    a.*
from Stadium a 
join Stadium b
on a.id +1 = b.id
join stadium c
on a.id+2=c.id
where a.people>=100 and b.people>=100 and c.people>=100
union
 select 
    b.*
from Stadium a 
join Stadium b
on a.id +1 = b.id
join stadium c
on a.id+2=c.id
where a.people>=100 and b.people>=100 and c.people>=100
union 
select 
    c.*
from Stadium a 
join Stadium b
on a.id +1 = b.id
join stadium c
on a.id+2=c.id
where a.people>=100 and b.people>=100 and c.people>=100

order by visit_date asc

```
## 🧩 Question 10

**Title:** Find Followers Count  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/find-followers-count/description/)  
**Platform:** Leetcode  
**Difficulty:** Easy  

```sql
MySQL Solution: 
# Write your MySQL query statement below
select user_id,
    count(follower_id) as followers_count
from Followers
group by user_id
order by user_id asc

```

---
“Behind every dataset lies a decision — and every query is the key to unlocking it.”
----


