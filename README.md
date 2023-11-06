# EX 2 Data Manipulation Language (DML) Commands and built in functions in SQL
## DATA:10/8/23
## AIM:
To create a manager database and execute DML queries using SQL.

## DML(Data Manipulation Language)
The SQL commands that deal with the manipulation of data present in the database belong to DML or Data Manipulation Language and this includes most of the SQL statements. It is the component of the SQL statement that controls access to data and to the database. Basically, DCL statements are grouped with DML statements.
## List of DML commands:
INSERT: It is used to insert data into a table.
UPDATE: It is used to update existing data within a table.
DELETE: It is used to delete records from a database table.
## Create the table as given below:
```
create table manager(enumber number(6),ename char(15),
salary number(5),commission number(4),
annualsalary number(7),Hiredate date,designation char(10),
deptno number(2),reporting char(10));
```
## insert the following values into the table
```
insert into manager values(7369,'Dharsan',2500,500,30000,
'30-June-81','clerk',10,'John');
insert into manager values(7839,'Subu',3000,400,36000,
'1-Jul-82','manager',null,'James');
insert into manager values(7934,'Aadhi',3500,300,42000,
'1-May-82','manager',30,NULL);
insert into manager values(7788,'Vikash',4000,0,48000,
'12-Aug-82','clerk',50,'Bond');
```
## Q1) Update all the records of manager table by increasing 10% of their salary as bonus.
## QUERY:
```
UPDATE manager
SET salary = salary + (salary * 0.10),
annualsalary = annualsalary + (annualsalary * 0.10);
```
## OUTPUT:
![image](https://github.com/Niroshassithanathan/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/121418437/706f00e1-bd04-456f-97f1-3550978984f7)

## Q2) Delete the records from manager table where the salary less than 2750.
## QUERY:
```
DELETE FROM manager WHERE salary < 2750;
```
## OUTPUT:
![image](https://github.com/Niroshassithanathan/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/121418437/0735eaaa-f8b4-42f4-b340-0598d0ba1374)

## Q3) Display each name of the employee as “Name” and annual salary as “Annual Salary” (Note: Salary in emp table is the monthly salary)
## QUERY:
```
SELECT ename AS "Name", salary * 12 AS "Annual Salary"
FROM manager;
```
## OUTPUT:
![image](https://github.com/Niroshassithanathan/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/121418437/deaee003-eab2-4583-a0d0-902486886885)

## Q5) List the names of Clerks from emp table.
## QUERY:
```
SELECT ename from manager where designation='clerk';
```
## OUTPUT:
![image](https://github.com/Niroshassithanathan/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/121418437/c499e1c3-9e35-4d99-8107-886c674d25bb)


## Q6) List the names of employee who are not Managers.
## QUERY:
```
SELECT ename from manager where designation!='manager';
```
## OUTPUT:
![image](https://github.com/Niroshassithanathan/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/121418437/d49bb5b8-c5da-4c22-a887-0a6141d3ce13)


## Q7) List the names of employees not eligible for commission.
## QUERY:
```
SELECT ename from manager where commission=0;
```
## OUTPUT:
![image](https://github.com/Niroshassithanathan/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/121418437/cae8eaeb-fe9b-4c16-bb14-9943e94edb61)

## Q8) List employees whose name either start or end with ‘s’.
## QUERY:
```
SELECT ename
FROM manager
WHERE ename LIKE 'S%' OR ename LIKE '%s';
```
## OUTPUT:
![image](https://github.com/Niroshassithanathan/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/121418437/0e18a5e8-bff1-4ce1-a2d4-a8445c0b445f)


## Q9) Sort emp table in ascending order by hire-date and list ename, job, deptno and hire-date.
## QUERY:
```
select ename,designation,deptno,Hiredate from manager
order by Hiredate asc;
```
## OUTPUT:
![image](https://github.com/Niroshassithanathan/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/121418437/31f13488-ec89-4bba-b89d-56ccd1337913)

## Q10) List the Details of Employees who have joined before 30 Sept 81.
## QUERY:
```
SELECT *
FROM manager
WHERE Hiredate < TO_DATE('1981-09-30', 'YYYY-MM-DD');
```
## OUTPUT:
![image](https://github.com/Niroshassithanathan/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/121418437/7b1032f2-3f35-428e-9e95-eef25202acc5)


## Q11) List ename, deptno and sal after sorting emp table in ascending order by deptno and then descending order by sal.
## QUERY:
```
select ename,deptno,salary from manager order by deptno asc;
select ename,deptno,salary from manager order by salary desc;
```
## OUTPUT:
![image](https://github.com/Niroshassithanathan/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/121418437/1ce67532-546a-45fc-8d7c-8b56e3271058)
![image](https://github.com/Niroshassithanathan/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/121418437/02ca97c0-6026-4cab-94b6-9509ca955970)

## Q12) List the names of employees not belonging to dept no 30,40 & 10
## QUERY:
```
select ename from manager where deptno not in (10,30,40);
```
## OUTPUT:
![image](https://github.com/Niroshassithanathan/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/121418437/b1e62d5c-76de-4d73-a05f-574557455da2)


## Q13) Find number of rows in the table EMP
## QUERY:
```
select count(*) from manager;
```
## OUTPUT:
![image](https://github.com/Niroshassithanathan/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/121418437/8375e2fd-4734-4f78-8c4d-2b1dfb048cd2)


## Q14) Find maximum, minimum and average salary in EMP table.
## QUERY:
```
select ename ,salary,annualsalary from manager
where salary = (select max(salary) from manager);

select ename ,salary,annualsalary from manager
where salary = (select min(salary) from manager);

select avg(salary) from manager;
```
## OUTPUT:
![image](https://github.com/Niroshassithanathan/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/121418437/d837746d-5ec5-41d6-ad25-dd0540da53ff)
![image](https://github.com/Niroshassithanathan/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/121418437/d48afe3d-3b12-4a4c-a897-d58d610f9a00)
![image](https://github.com/Niroshassithanathan/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/121418437/3f51ebf3-066a-49a8-9f64-e526ca65e038)

## Q15) List the jobs and number of employees in each job. The result should be in the descending order of the number of employees.
## QUERY:
```
SELECT designation, COUNT(*) AS "Number of Employees"
FROM manager
GROUP BY designation
ORDER BY COUNT(*) DESC;
```
## OUTPUT:
![image](https://github.com/Niroshassithanathan/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/121418437/82ea08b2-668b-477d-a17b-6cffe2bce754)


## RESULT:
Thus, Manager database is created and DML queries such as insertion, updation, deletion are executed using SQL.
