Start of DBMS with leatcode 
leatcode problem 176___
select max(salary) as SecondHighestSalary from Employee where salary<(select max(salary) from Employee)

1.leatcode problem 178___
select Score,dense_rank() over(order by score desc) as "rank" from Scores;

2.leatcode problem 181___
select e1.name as Employee from Employee e1
join Employee e2
on e1.managerID = e2.id
where e1.salary > e2.salary

3.leatcode problem 184___
SELECT`Department`.`name`AS`Department`,`Employee`.`name`AS`Employee`,
`Employee`.`salary`AS`Salary`
From`Employee`
JOIN`Department`ON`Employee`.`departmentID`=`Department`.`id`
WHERE(`departmentID`,`salary`)IN(
    SELECT`departmentID`,MAX(`Salary`)FROM`Employee`
    GROUP BY`departmentID`

4.leatcode problem 1757___
SELECT`product_id`FROM`Products`
WHERE`low_fats`='Y'
AND`recyclable`='Y';

5.leatcode problem 584___
SELECT name from Customer
Where referee_id != '2' or referee_id is null

6.leatcode problem 595___
SELECT `name`,`population`,`area`FROM `World`
WHERE `population` >= 25000000 OR `area` >= 3000000

7.leatcode problem 1148___
Select distinct `author_id` as id from `Views`
where `author_id`= `viewer_id`
order by `author_id` asc

8.leatcode problem 1683___
SELECT`tweet_id`FROM `Tweets`
WHERE LENGTH(`content`) > 15

9.leatcode problem 1378___
SELECT `EmployeeUNI`.`unique_id`,`Employees`.`name` FROM`Employees`
LEFT JOIN `EmployeeUNI`
ON `Employees`.`id`= `EmployeeUNI`.`id`

10.leatcode problem 1068___
SELECT`Product`.`product_name`,`Sales`.`year`,`price` FROM Sales
JOIN`Product`ON`Product`.`product_id`=`Sales`.`product_id`

11.leatcode problem 1581___
SELECT`Visits`.`customer_id`,Count(*)AS`count_no_trans`FROM`Visits`
LEFT JOIN`Transactions`ON
`Visits`.`visit_id`=`Transactions`.`visit_id`
WHERE`Transactions`.`transaction_id`IS NULL
GROUP BY`Visits`.`customer_id`

12.problem 197___
SELECT W1.id AS Id FROM Weather W1
JOIN WEATHER W2
ON W1.recordDate = DATE_ADD(W2.recordDate, INTERVAL 1 DAY)
WHERE W1.temperature > W2.temperature

13.problem 1661___
SELECT A1.machine_id, ROUND(AVG(A2.timestamp - A1.timestamp),3) AS processing_time
    FROM Activity A1
    JOIN Activity A2
    ON A1.machine_id = A2.machine_id
    AND A1.process_id = A2.process_id
    AND A1.activity_type = 'start'
    AND A2.activity_type = 'end'
    GROUP BY machine_id;

14.problem 577___
SELECT E.name, B.bonus FROM Employee E
LEFT JOIN Bonus B
ON E.empId = B.empId
WHERE bonus < 1000 OR bonus IS NULL;

15.problem 1280___
SELECT S1.student_id, S1.student_name, S2.subject_name, COUNT(E.student_id) AS attended_exams FROM Students S1
CROSS JOIN Subjects S2
LEFT JOIN Examinations E
ON S1.student_id = E.student_id
AND S2.subject_name = E.subject_name
GROUP BY S1.student_id,S1.student_name,S2.Subject_name
ORDER BY S1.student_id, S2.subject_name

16.problem 570___
SELECT E1.name FROM Employee E1
JOIN Employee E2
ON E1.id = E2.managerId
GROUP BY E1.id, E1.name
HAVING COUNT(E2.id) >= 5;

17.problem 2356___
SELECT teacher_id, COUNT(DISTINCT subject_id)AS cnt FROM Teacher
GROUP BY teacher_id

18.problem 1934___
SELECT S.user_id,ROUND(IFNULL(AVG(C.action='confirmed'),0),2)AS confirmation_rate FROM Signups S
LEFT JOIN Confirmations C
ON S.user_id = C.user_id
GROUP BY s.user_id

19.problem 620___
SELECT`id`,`movie`,`description`,`rating`FROM`Cinema`
WHERE id%2!=0 AND`description`!='boring'
ORDER BY`rating`DESC

20.problem 1251___
SELECT P.product_id,
        IFNULL(ROUND(SUM(P.price*U.units)/SUM(U.units),2),0) As average_price
FROM Prices P
LEFT JOIN UnitsSold U
ON P.product_id = U.product_id
AND U.purchase_date BETWEEN P.start_date AND P.end_date
GROUP BY P.product_id

21.problem 1075___
SELECT P.project_id, IFNULL(ROUND(AVG(E.experience_years),2),0) AS average_years
FROM Project P
LEFT JOIN Employee E
ON P.employee_id = E.employee_id
GROUP BY P.project_id

22.problem 1633___
select contest_id, 
round(count(distinct user_id) * 100 /(select count(user_id) from Users) ,2) as percentage
from Register
group by contest_id
order by percentage desc,contest_id ASC

23.problem 1211___
SELECT Q.query_name,
ROUND(AVG(Q.rating/Q.position),2) AS quality,
ROUND(AVG(CASE WHEN rating < 3 THEN 1 ELSE 0 END)*100,2) AS poor_query_percentage
FROM Queries Q
GROUP BY Q.query_name

24.problem 1193___
SELECT DATE_FORMAT(trans_date,'%Y-%m') AS month,
country,
COUNT(trans_date) AS trans_count,
COUNT(IF(state = 'approved' ,1, NULL)) AS approved_count,
SUM(amount) AS trans_total_amount,
SUM(IF(state = 'approved' ,amount, 0)) AS approved_total_amount
FROM Transactions
GROUP BY country,(DATE_FORMAT(trans_date,'%Y-%m'))

25.problem 1174___
SELECT
ROUND((SUM(IF(order_date = customer_pref_delivery_date,1,0))/COUNT(customer_id))*100,2)AS immediate_percentage FROM Delivery
WHERE(customer_id,order_date)IN
(SELECT customer_id,MIN(order_date) FROM Delivery
GROUP BY customer_id)

26.problem 550___
SELECT
ROUND(
    (SELECT COUNT(DISTINCT A1.player_id)
    FROM Activity A1 JOIN (SELECT player_id,MIN(event_date) AS first_login
    FROM Activity GROUP BY player_id) A2
    ON A1.player_id = A2.player_id
    AND A1.event_date = A2.first_login + INTERVAL 1 DAY)/COUNT(DISTINCT player_id),2) AS fraction
FROM Activity

27.problem 183___
SELECT C.name AS Customers FROM Customers C
LEFT JOIN Orders O
ON C.id = O.customerId
WHERE O.id IS NULL;

28.problem 1141___
SELECT DISTINCT activity_date AS day, COUNT(DISTINCT user_id) AS active_users FROM Activity
WHERE activity_date BETWEEN SUBDATE('2019-07-27', INTERVAL 29 DAY) AND '2019-07-27'
GROUP BY activity_date

29.problem 1070___
select product_id, year as first_year, quantity, price 
from sales where (product_id, year) in (
    select product_id, min(year)
    from sales
    group by product_id
)

30.problem 596___
SELECT class FROM Courses
GROUP BY class HAVING COUNT(class)>=5

31.peoblem 1045___
SELECT customer_id FROM Customer
GROUP BY customer_id
HAVING COUNT(DISTINCT product_key)= (SELECT COUNT(product_key) FROM Product)

32.problem 619___
SELECT MAX(num) AS num FROM MyNumbers
WHERE num IN(
SELECT num FROM MyNumbers
GROUP BY num
HAVING Count(num) = 1);

33.problem 1731___
SELECT E1.employee_id,E1.name,COUNT(E2.reports_to) AS reports_count,
ROUND(AVG(E2.age),0) AS average_age
FROM Employees E1
JOIN Employees E2
ON E1.employee_id = E2.reports_to
GROUP BY E1.employee_id
ORDER BY employee_id

34.problem 175___
SELECT P.firstName,P.lastName,A.city,A.state
FROM Person P
LEFT JOIN Address A
ON P.personId = A.personId

35.problem 1789___
SELECT employee_id,department_id FROM Employee
WHERE primary_flag = 'Y'
UNION
SELECT employee_id,department_id FROM Employee
GROUP BY employee_id
HAVING COUNT(employee_id) = 1
