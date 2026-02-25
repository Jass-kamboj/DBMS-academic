# DBMS-academic
Start of DBMS with leatcode 
leatcode problem 176___
select max(salary) as SecondHighestSalary from Employee where salary<(select max(salary) from Employee)

leatcode problem 178___
select Score,dense_rank() over(order by score desc) as "rank" from Scores;

leatcode problem 181___
select e1.name as Employee from Employee e1
join Employee e2
on e1.managerID = e2.id
where e1.salary > e2.salary

leatcode problem 184___
SELECT`Department`.`name`AS`Department`,`Employee`.`name`AS`Employee`,
`Employee`.`salary`AS`Salary`
From`Employee`
JOIN`Department`ON`Employee`.`departmentID`=`Department`.`id`
WHERE(`departmentID`,`salary`)IN(
    SELECT`departmentID`,MAX(`Salary`)FROM`Employee`
    GROUP BY`departmentID`

leatcode problem 1757___
SELECT`product_id`FROM`Products`
WHERE`low_fats`='Y'
AND`recyclable`='Y';

leatcode problem 584___
SELECT name from Customer
Where referee_id != '2' or referee_id is null

leatcode problem 595___
SELECT `name`,`population`,`area`FROM `World`
WHERE `population` >= 25000000 OR `area` >= 3000000

leatcode problem 1148___
Select distinct `author_id` as id from `Views`
where `author_id`= `viewer_id`
order by `author_id` asc

leatcode problem 1683___
SELECT`tweet_id`FROM `Tweets`
WHERE LENGTH(`content`) > 15

leatcode problem 1378___
SELECT `EmployeeUNI`.`unique_id`,`Employees`.`name` FROM`Employees`
LEFT JOIN `EmployeeUNI`
ON `Employees`.`id`= `EmployeeUNI`.`id`

leatcode problem 1068___
SELECT`Product`.`product_name`,`Sales`.`year`,`price` FROM Sales
JOIN`Product`ON`Product`.`product_id`=`Sales`.`product_id`

leatcode problem 1581___
SELECT`Visits`.`customer_id`,Count(*)AS`count_no_trans`FROM`Visits`
LEFT JOIN`Transactions`ON
`Visits`.`visit_id`=`Transactions`.`visit_id`
WHERE`Transactions`.`transaction_id`IS NULL
GROUP BY`Visits`.`customer_id`

problem 197___
SELECT W1.id AS Id FROM Weather W1
JOIN WEATHER W2
ON W1.recordDate = DATE_ADD(W2.recordDate, INTERVAL 1 DAY)
WHERE W1.temperature > W2.temperature

problem 1661___
SELECT A1.machine_id, ROUND(AVG(A2.timestamp - A1.timestamp),3) AS processing_time
    FROM Activity A1
    JOIN Activity A2
    ON A1.machine_id = A2.machine_id
    AND A1.process_id = A2.process_id
    AND A1.activity_type = 'start'
    AND A2.activity_type = 'end'
    GROUP BY machine_id;

problem 577___
SELECT E.name, B.bonus FROM Employee E
LEFT JOIN Bonus B
ON E.empId = B.empId
WHERE bonus < 1000 OR bonus IS NULL;
