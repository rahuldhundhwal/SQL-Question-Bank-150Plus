# 🗓️Day 01 — SQL Practice Journal

**Date:** 25/11/2025  
**Platform(s):** [StrataScratch / LeetCode / DataLemur / HackerRank]  
**Total Questions Solved:** [10]  
**Estimated Practice Time:** [X hours]

---

## 🧠 Overview


---

## 🧩 Question 1

**Title:** Salaries Differences  
**Link:** [🔗 Click to Open Problem](https://platform.stratascratch.com/coding/10308-salaries-differences?code_type=3)  
**Platform:** StrataScratch  
**Difficulty:** Easy  

```sql
MySQL Solution: 
SELECT
  abs((SELECT MAX(salary) FROM db_employee WHERE department_id = 4) - 
  (SELECT MAX(salary) FROM db_employee WHERE department_id = 1)) AS salary_difference;
```
## 🧩 Question 2

**Title:** Find Customer Referee  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/find-customer-referee/description/)  
**Platform:** LeetCode 
**Difficulty:** Easy  

```sql
MySQL Solution: 
select
    name from customer
    where referee_id <>2 or referee_id is null
```
## 🧩 Question 3

**Title:** Combine Two Tables  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/combine-two-tables/description/)  
**Platform:** LeetCode 
**Difficulty:** Easy  

```sql
MySQL Solution: 
select p.firstName,
    p.lastName,
    a.city,
    a.state
from person p left  join address a on p.personid=a.personid
```
## 🧩 Question 4

**Title:** Second Highest Salary  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/second-highest-salary/)  
**Platform:** LeetCode 
**Difficulty:** Medium 

```sql
MySQL Solution: 
SELECT (
  SELECT DISTINCT salary
  FROM Employee
  ORDER BY salary DESC
  LIMIT 1 OFFSET 1
) AS SecondHighestSalary;
```
## 🧩 Question 5

**Title:** Nth Highest Salary  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/nth-highest-salary/)  
**Platform:** LeetCode  
**Difficulty:** Medium 

```sql
MySQL Solution: 
CREATE FUNCTION getNthHighestSalary(N INT) RETURNS INT
BEGIN
set N=N-1;
  RETURN (
      # Write your MySQL query statement below.
    select(select distinct salary from Employee
    order by salary desc limit 1 offset n) 
  );
END
```
## 🧩 Question 6

**Title:** Employee Earning more than Managers  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/employees-earning-more-than-their-managers/submissions/1811054854/)  
**Platform:** LeetCode 
**Difficulty:** Easy  

```sql
MySQL Solution: 
# Write your MySQL query statement below
select name as Employee from employee e 
where salary > (select salary from employee where id= e.managerid)
```
## 🧩 Question 7

**Title:** Salaries Differences  
**Link:** [🔗 Click to Open Problem](https://platform.stratascratch.com/coding/10308-salaries-differences?code_type=3)  
**Platform:** StrataScratch  
**Difficulty:** Easy  

```sql
MySQL Solution: 
SELECT
  abs((SELECT MAX(salary) FROM db_employee WHERE department_id = 4) - 
  (SELECT MAX(salary) FROM db_employee WHERE department_id = 1)) AS salary_difference;
```
## 🧩 Question 8

**Title:** Find Customer Referee  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/find-customer-referee/description/)  
**Platform:** LeetCode 
**Difficulty:** Easy  

```sql
MySQL Solution: 
select
    name from customer
    where referee_id <>2 or referee_id is null
```
## 🧩 Question 9

**Title:** Salaries Differences  
**Link:** [🔗 Click to Open Problem](https://platform.stratascratch.com/coding/10308-salaries-differences?code_type=3)  
**Platform:** StrataScratch  
**Difficulty:** Easy  

```sql
MySQL Solution: 
SELECT
  abs((SELECT MAX(salary) FROM db_employee WHERE department_id = 4) - 
  (SELECT MAX(salary) FROM db_employee WHERE department_id = 1)) AS salary_difference;
```
## 🧩 Question 10

**Title:** Find Customer Referee  
**Link:** [🔗 Click to Open Problem](https://leetcode.com/problems/find-customer-referee/description/)  
**Platform:** LeetCode 
**Difficulty:** Easy  

```sql
MySQL Solution: 
select
    name from customer
    where referee_id <>2 or referee_id is null
```

