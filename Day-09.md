
# 🗓️Day 09 — SQL Practice Journal

**Date:** 03/11/2025  
**Platform(s):** [StrataScratch / LeetCode / DataLemur / HackerRank]  
**Total Questions Solved:** 10  

---

## 🧠 Overview


---

## 🧩 Question 1

**Title:**   
**Link:** [🔗 Click to Open Problem]()  
**Platform:** LeetCode  
**Difficulty:** Easy  

```sql
MySQL Solution: 

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

**Title:**   
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


