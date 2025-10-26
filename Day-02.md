# 🗓️Day 02 — SQL Practice Journal

**Date:** 26/10/2025  
**Platform(s):** [StrataScratch / LeetCode / DataLemur / HackerRank]  
**Total Questions Solved:** [10]  
**Estimated Practice Time:** [X hours]

---

## 🧠 Overview


---

## 🧩 Question 1

**Title:** Consecutive Numbers 
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/consecutive-numbers/)  
**Platform:** LeetCode  
**Difficulty:** Medium  

```sql
MySQL Solution: 
# Write your MySQL query statement below
select distinct a.num as ConsecutiveNums 
from logs a join logs b
on a.num =b.num and a.id=b.id-1
join logs c
on a.num=c.num and a.id=c.id
```
## 🧩 Question 2

**Title:** Customer Who Never Order  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/customers-who-never-order/submissions/1811931103/)  
**Platform:** LeetCode 
**Difficulty:** Easy  

```sql
MySQL Solution: 
# Write your MySQL query statement below
select name as Customers from Customers where id not in (select distinct customerId from orders)
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

**Title:** Duplicate Emails  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/duplicate-emails/)  
**Platform:** LeetCode 
**Difficulty:** Easy  

```sql
MySQL Solution: 
# Write your MySQL query statement below
select distinct Email from person p where (select count(email) from person where email=p.email)>1
```
## 🧩 Question 8

**Title:** Department Highest Salary  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/department-highest-salary/)  
**Platform:** LeetCode 
**Difficulty:** Medium  

```sql
MySQL Solution: 
select d.name as Department,
       e.name as Employee,
       e.salary as Salary
from   employee e join department d on e.departmentID=d.id
where e.salary = (select max(salary) from employee where departmentID=e.departmentID)
```
## 🧩 Question 9

**Title:** Department Top Three salaries  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/department-top-three-salaries/solutions/5367303/easiest-basic-sql-solution-3-approaches-beginner-level-to-advance/)  
**Platform:** LeetCode  
**Difficulty:** Hard  

```sql
MySQL Solution: 
SELECT
    d.name AS Department,
    e.name AS Employee,
    e.salary AS Salary
FROM
    Employee e
    JOIN Department d ON e.departmentId = d.id
WHERE
    (
        SELECT COUNT(DISTINCT salary)
        FROM Employee e2
        WHERE e2.departmentId = e.departmentId AND e2.salary >= e.salary
    ) <= 3
ORDER BY
    Department, Salary DESC;
```
## 🧩 Question 10

**Title:** Rising Temperature  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/rising-temperature/description/)  
**Platform:** LeetCode 
**Difficulty:** Easy  

```sql
MySQL Solution: 
SELECT
  w1.id
FROM
  Weather AS w1
JOIN
  Weather AS w2 ON DATEDIFF(w1.recordDate, w2.recordDate) = 1
WHERE
  w1.temperature > w2.temperature;

```
