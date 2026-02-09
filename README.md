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
