# 🗓️Day 03 — SQL Practice Journal

**Date:** 27/10/2025  
**Platform(s):** [StrataScratch / LeetCode / DataLemur / HackerRank]  
**Total Questions Solved:** [10]  
**Estimated Practice Time:** [X hours]

---

## 🧠 Overview


---

## 🧩 Question 1

**Title:** Top Travellers  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/top-travellers/submissions/1812850334/)  
**Platform:** LeetCode  
**Difficulty:** Easy  

```sql
MySQL Solution: 
# Write your MySQL query statement below
select name,
    (select coalesce(sum(distance),0) from Rides where user_id = users.id) as travelled_distance
from users
order by travelled_distance desc,name asc
```
## 🧩 Question 2

**Title:** Captial Gain/Loss  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/capital-gainloss/)  
**Platform:** LeetCode  
**Difficulty:** Medium  

```sql
MySQL Solution: 
SELECT DISTINCT 
    stock_name, 
    (
        (SELECT SUM(COALESCE(price, 0)) 
         FROM stocks 
         WHERE operation = 'Sell' AND stock_name = s.stock_name) 
        - 
        (SELECT SUM(COALESCE(price, 0)) 
         FROM stocks 
         WHERE operation = 'Buy' AND stock_name = s.stock_name)
    ) AS capital_gain_loss
FROM stocks s;

```
## 🧩 Question 3

**Title:** Game PLay Analysiss  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/game-play-analysis-i/)  
**Platform:** LeetCode  
**Difficulty:** Easy  

```sql
MySQL Solution: 
# Write your MySQL query statement below
select player_id,min(event_date) as first_login 
from Activity group by player_id
```
## 🧩 Question 4

**Title:** Game Analysis IV  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/game-play-analysis-iv/)  
**Platform:** LeetCode  
**Difficulty:** Medium 

```sql
MySQL Solution: 
SELECT
  ROUND(
    COUNT(A1.player_id)
    / (SELECT COUNT(DISTINCT A3.player_id) FROM Activity A3)
  , 2) AS fraction
FROM
  Activity A1
WHERE
  (A1.player_id, DATE_SUB(A1.event_date, INTERVAL 1 DAY)) IN (
    SELECT
      A2.player_id,
      MIN(A2.event_date)
    FROM
      Activity A2
    GROUP BY
      A2.player_id
  );
```
## 🧩 Question 5

**Title:** Manager with at Least 5 Direct  Reports
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/managers-with-at-least-5-direct-reports/)  
**Platform:** LeetCode  
**Difficulty:** Medium 

```sql
MySQL Solution: 
# Write your MySQL query statement below
select name from employee e where (select count(id) from employee where managerID=e.id)>=5
```
## 🧩 Question 6

**Title:** Employee Bonus  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/employee-bonus/)  
**Platform:** LeetCode  
**Difficulty:** Easy  

```sql
MySQL Solution: 
# Write your MySQL query statement below
select e.name, b.bonus from Employee e left join Bonus b 
on e.empId=b.empId
where b.bonus<1000 or b.bonus is null;
```
## 🧩 Question 7

**Title:** Customer Placing the Largest Number of Orders  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/customer-placing-the-largest-number-of-orders/description/)  
**Platform:** LeetCode  
**Difficulty:** Easy  

```sql
MySQL Solution: 
# Write your MySQL query statement below
select distinct customer_number from orders o where (select count(order_number) from orders
where customer_number= o.customer_number) =
(select max(order_count) from (select count(order_number)
 as order_count from orders group by customer_number)
 as max_order_count)

```
## 🧩 Question 8

**Title:** Big Countries  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/big-countries/)  
**Platform:** LeetCode  
**Difficulty:** Easy  

```sql
MySQL Solution: 
# Write your MySQL query statement below
select name,population,area
from world
where area>=3000000  or population>=25000000
```
## 🧩 Question 9

**Title:** Friend Requests II: Who Has the Most Friends  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/friend-requests-ii-who-has-the-most-friends/description/)  
**Platform:** LeetCode  
**Difficulty:** Medium  

```sql
MySQL Solution: 
# Write your MySQL query statement below
select distinct requester_id as id , ((select count(accepter_id  )
from RequestAccepted where requester_id =r.requester_id ) +
(select count(requester_id) from RequestAccepted where accepter_id =r.requester_id )) as num
from RequestAccepted r 
union 
select distinct accepter_id as id , ((select count(requester_id )
from RequestAccepted where accepter_id =r2.accepter_id ) +
(select count(accepter_id) from RequestAccepted where r2.accepter_id =requester_id )) as num
from RequestAccepted r2 

order by num desc limit 1
```
## 🧩 Question 10

**Title:** Tree  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/tree-node/)  
**Platform:** LeetCode  
**Difficulty:** Medium  

```sql
MySQL Solution: 
select id,
case 
    when p_id is null  then "Root"
    when p_id is not null and ((select count(id) from tree where p_id = p.id)>0) then "Inner"
    else "Leaf"
    end as type 
from tree p

```

---
“Behind every dataset lies a decision — and every query is the key to unlocking it.”
----
