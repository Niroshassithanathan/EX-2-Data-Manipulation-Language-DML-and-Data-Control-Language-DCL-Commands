# EX 2 Data Manipulation Language (DML) Commands and built in functions in SQL
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
insert into manager values(7369,'Aarik',2500,500,30000,
'30-June-81','clerk',10,'John');
insert into manager values(7839,'Riyaz',3000,400,36000,
'1-Jul-82','manager',null,'Khan');
insert into manager values(7934,'Zayn',3500,300,42000,
'1-May-82','manager',30,NULL);
insert into manager values(7788,'Sam',4000,0,48000,
'12-Aug-82','clerk',50,'Joel');
```
## Q1) Update all the records of manager table by increasing 10% of their salary as bonus.
## QUERY:
```
UPDATE manager
SET salary = salary + (salary * 0.10),
annualsalary = annualsalary + (annualsalary * 0.10);
```
## OUTPUT:
![image](https://github.com/Niroshassithanathan/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/121418437/9af41208-c7b4-4c02-8d2d-09106eaefa30)

## Q2) Delete the records from manager table where the salary less than 2750.
## QUERY:
```
DELETE FROM manager WHERE salary < 2750;
```
## OUTPUT:
![image](https://github.com/Niroshassithanathan/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/121418437/69b42fa3-fd8a-4566-94f7-09e241ff08f9)

## Q3) Display each name of the employee as “Name” and annual salary as “Annual Salary” (Note: Salary in emp table is the monthly salary)
## QUERY:
```
SELECT ename AS "Name", salary * 12 AS "Annual Salary"
FROM manager;
```
## OUTPUT:
![image](https://github.com/Niroshassithanathan/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/121418437/32d9eeae-ff86-4cdc-a59e-163ec10a554a)

## Q5) List the names of Clerks from emp table.
## QUERY:
```
SELECT ename from manager where designation='clerk';
```
## OUTPUT:
![image](https://github.com/Niroshassithanathan/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/121418437/7c38781d-35b4-4f6c-b1df-37828c07c916)

## Q6) List the names of employee who are not Managers.
## QUERY:
```
SELECT ename from manager where designation!='manager';
```
## OUTPUT:
![image](https://github.com/Niroshassithanathan/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/121418437/13452690-3b8e-4a0c-8da5-edfd784500db)

## Q7) List the names of employees not eligible for commission.
## QUERY:
```
SELECT ename from manager where commission=0;
```
## OUTPUT:
![image](https://github.com/Niroshassithanathan/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/121418437/84d80fba-0274-486d-bc2a-032cd9f6051c)

## Q8) List employees whose name either start or end with ‘s’.
## QUERY:
```
SELECT ename
FROM manager
WHERE ename LIKE 'S%' OR ename LIKE '%s';
```
## OUTPUT:
![image](https://github.com/Niroshassithanathan/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/121418437/81fa7dc3-f85c-4ea6-a860-5ab6bf52afac)


## Q9) Sort emp table in ascending order by hire-date and list ename, job, deptno and hire-date.
## QUERY:
```
select ename,designation,deptno,Hiredate from manager
order by Hiredate asc;
```
## OUTPUT:
![image](https://github.com/Niroshassithanathan/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/121418437/3870994d-0b59-4d17-9389-b52698c77e4e)

## Q10) List the Details of Employees who have joined before 30 Sept 81.
## QUERY:
```
SELECT *
FROM manager
WHERE Hiredate < TO_DATE('1981-09-30', 'YYYY-MM-DD');
```
## OUTPUT:
![image](https://github.com/Niroshassithanathan/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/121418437/ff9e1177-35f6-4342-8317-d06ae8b972aa)

## Q11) List ename, deptno and sal after sorting emp table in ascending order by deptno and then descending order by sal.
## QUERY:
```
select ename,deptno,salary from manager order by deptno asc;
select ename,deptno,salary from manager order by salary desc;
```
## OUTPUT:
![image](https://github.com/Niroshassithanathan/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/121418437/2dc8e630-7120-47e2-9330-d9b8ce36cbfb)

## Q12) List the names of employees not belonging to dept no 30,40 & 10
## QUERY:
```
select ename from manager where deptno not in (10,30,40);
```
## OUTPUT:
![image](https://github.com/Niroshassithanathan/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/121418437/bbbc94d4-432b-4fe3-a6e4-b7842b876f6e)

## Q13) Find number of rows in the table EMP
## QUERY:
```
select count(*) from manager;
```
## OUTPUT:
![image](https://github.com/Niroshassithanathan/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/121418437/12f06424-6d63-47e0-995b-630b5f3e32d0)

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
![image](https://github.com/Niroshassithanathan/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/121418437/7203e987-c433-44ee-9c08-f2239af19d16)

## Q15) List the jobs and number of employees in each job. The result should be in the descending order of the number of employees.
## QUERY:
```
SELECT designation, COUNT(*) AS "Number of Employees"
FROM manager
GROUP BY designation
ORDER BY COUNT(*) DESC;
```
## OUTPUT:
![image](https://github.com/Niroshassithanathan/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/121418437/915592e1-122b-4247-b918-836980132e0f)

## SUBMITTED BY :

## NAME : NIROSHA S

## REGNO: 212222230097

## RESULT:
Thus, Manager database is created and DML queries such as insertion, updation, deletion are executed using SQL.
