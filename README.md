# EX 3 SubQueries, Views and Joins 

## AIM:
To create a manager database and execute DML queries using SQL

## DML:
The SQL commands that deal with the manipulation of data present in the database belong to DML or Data Manipulation Language and this includes most of the SQL statements.
It is the component of the SQL statement that controls access to data and to the database. Basically, DCL statements are grouped with DML statements.

## Create employee Table
```sql
CREATE TABLE EMP (EMPNO NUMBER(4) PRIMARY KEY,ENAME VARCHAR2(10),JOB VARCHAR2(9),MGR NUMBER(4),HIREDATE DATE,SAL NUMBER(7,2),COMM NUMBER(7,2),DEPTNO NUMBER(2));
```
## Insert the values
```sql
INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7369, 'SMITH', 'CLERK', 7902, '17-DEC-80', 800, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7499, 'ALLEN', 'SALESMAN', 7698, '20-FEB-81', 1600, 300, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7521, 'WARD', 'SALESMAN', 7698, '22-FEB-81', 1250, 500, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7566, 'JONES', 'MANAGER', 7839, '02-APR-81', 2975, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7654, 'MARTIN', 'SALESMAN', 7698, '28-SEP-81', 1250, 1400, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7698, 'BLAKE', 'MANAGER', 7839, '01-MAY-81', 2850, NULL, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7782, 'CLARK', 'MANAGER', 7839, '09-JUN-81', 2450, NULL, 10);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7788, 'SCOTT', 'ANALYST', 7566, '19-APR-87', 3000, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7839, 'KING', 'PRESIDENT', NULL, '17-NOV-81', 5000, NULL, 10);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7844, 'TURNER', 'SALESMAN', 7698, '08-SEP-81', 1500, 0, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7876, 'ADAMS', 'CLERK', 7788, '23-MAY-87', 1100, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7900, 'JAMES', 'CLERK', 7698, '03-DEC-81', 950, NULL, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7902, 'FORD', 'ANALYST', 7566, TO_DATE('03-DEC-81', 'DD-MON-RR'), 3000, 20, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7934, 'MILLER', 'CLERK', 7782, TO_DATE('23-JAN-82', 'DD-MON-RR'), 1300, 10, 10);
```
## OUTPUT:
![image](https://github.com/Yuvaranithulasingam/EX-3-SubQueries-Views-and-Joins/assets/121418522/931f0e98-36a2-48e8-bf1f-5dd1b6e0b74a)

## Create department table
```sql
CREATE TABLE DEPT (DEPTNO NUMBER(2) PRIMARY KEY,DNAME VARCHAR2(14),LOC VARCHAR2(13));
```
## Insert the values in the department table
```sql
INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (10, 'ACCOUNTING', 'NEW YORK');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (20, 'RESEARCH', 'DALLAS');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (30, 'SALES', 'CHICAGO');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (40, 'OPERATIONS', 'BOSTON');
```
## OUTPUT:
![image](https://github.com/Yuvaranithulasingam/EX-3-SubQueries-Views-and-Joins/assets/121418522/469cb5b2-c92b-4273-9902-99431c3d35a3)

### Q1) List the name of the employees whose salary is greater than that of employee with empno 7566.
#### QUERY:
```
select ename from emp where sal>(select sal from emp where empno=7566);
```
#### OUTPUT:
![image](https://github.com/Yuvaranithulasingam/EX-3-SubQueries-Views-and-Joins/assets/121418522/b2c3aa1e-96c4-4a85-9878-02d4066e8b26)

### Q2) List the ename,job,sal of the employee who get minimum salary in the company.
#### QUERY:
```
select ename,job,sal from emp where sal=(select min(sal) from emp);
```
#### OUTPUT:
![image](https://github.com/Yuvaranithulasingam/EX-3-SubQueries-Views-and-Joins/assets/121418522/27be580f-fbee-4912-ae2d-b6e99e96ce14)

### Q3) List ename, job of the employees who work in deptno 10 and his/her job is any one of the job in the department ‘SALES’.
#### QUERY:
```
SELECT ENAME, JOB FROM EMP WHERE DEPTNO = 10 AND JOB IN (SELECT JOB FROM EMP WHERE JOB='SALESMAN');
```
#### OUTPUT:
![image](https://github.com/Yuvaranithulasingam/EX-3-SubQueries-Views-and-Joins/assets/121418522/315ef5de-fd29-4b79-9f67-2eb6af15daa6)

### Q4) Create a view empv5 (for the table emp) that contains empno, ename, job of the employees who work in dept 10.
#### QUERY:
```
create view emv5 as select empno,ename,job from emp where deptno=10;
select ename,empno,job from emv5;
```
### OUTPUT:
![image](https://github.com/Yuvaranithulasingam/EX-3-SubQueries-Views-and-Joins/assets/121418522/c6a263f0-9a1f-4709-a83b-eb504c0dadb8)

### Q5) Create a view with column aliases empv30 that contains empno, ename, sal of the employees who work in dept 30. Also display the contents of the view.
#### QUERY:
```
create view empv30 as select empno,ename,sal from emp where deptno=30;
select ename,empno,sal from empv30;
```
#### OUTPUT:
![image](https://github.com/Yuvaranithulasingam/EX-3-SubQueries-Views-and-Joins/assets/121418522/4dcada7e-12da-40c2-8740-6e4543402bf7)

### Q6) Update the view empv5 by increasing 10% salary of the employees who work as ‘CLERK’. Also confirm the modifications in emp table
#### QUERY:
```
update empv5 set sal=sal+(sal*0.1) where job='clerk';
```
#### OUTPUT:
![image](https://github.com/Yuvaranithulasingam/EX-3-SubQueries-Views-and-Joins/assets/121418522/a6810574-c1d8-4c0e-8d45-e63d6739b99c)

## Create a Customer1 Table
```sql
CREATE TABLE Customer1 (customer_id INT,cust_name VARCHAR(20),city VARCHAR(20),grade INT,salesman_id INT);
```
## Inserting Values to the Table
```sql
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3002, 'Nick Rimando', 'New York', 100, 5001);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3007, 'Brad Davis', 'New York', 200, 5001);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3005, 'Graham Zusi', 'California', 200, 5002);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3008, 'Julian Green', 'London', 300, 5002);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3004, 'Fabian Johnson', 'Paris', 300, 5006);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3009, 'Geoff Cameron', 'Berlin', 100, 5003);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3003, 'Jozy Altidor', 'Moscow', 200, 5007);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3001, 'Brad Guzan', 'London', NULL, 5005);
```
## OUTPUT:
![image](https://github.com/Yuvaranithulasingam/EX-3-SubQueries-Views-and-Joins/assets/121418522/4086faa0-a91c-4c62-85e0-7f138180e27e)

## Create a Salesperson1 table
```sql
CREATE TABLE Salesman1 (salesman_id INT,name VARCHAR(20),city VARCHAR(20),commission DECIMAL(4,2));
```
## Inserting Values to the Table
```sql
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5001, 'James Hoog', 'New York', 0.15);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5002, 'Nail Knite', 'Paris', 0.13);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5005, 'Pit Alex', 'London', 0.11);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5006, 'Mc Lyon', 'Paris', 0.14);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5007, 'Paul Adam', 'Rome', 0.13);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5003, 'Lauson Hen', 'San Jose', 0.12);
```
## OUTPUT:
![image](https://github.com/Yuvaranithulasingam/EX-3-SubQueries-Views-and-Joins/assets/121418522/398b0d5c-5d99-4946-bfd3-da321e85116c)

### Q7) Write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.

### QUERY:
```
SELECT salesman1.name AS "salesman",customer1.cust_name AS "customername", customer1.city FROM salesman1,customer1 WHERE salesman1.city=customer1.city;
```
### OUTPUT:
![image](https://github.com/Yuvaranithulasingam/EX-3-SubQueries-Views-and-Joins/assets/121418522/fbb82a6e-4215-4f36-a41e-7de2de273615)

### Q8) Write a SQL query to find salespeople who received commissions of more than 13 percent from the company. Return Customer Name, customer city, Salesman, commission.
#### QUERY:
```
select customer1.cust_name as "CUSTOMER NAME" , customer1.city as "CUSTOMER CITY" , salesman1.name as "SALESMAN NAME" , salesman1.commission as "COMMISSION" from salesman1 INNER JOIN customer1 on salesman1.salesman_id=customer1.salesman_id where salesman1.commission > 0.13;
```
#### OUTPUT:
![image](https://github.com/Yuvaranithulasingam/EX-3-SubQueries-Views-and-Joins/assets/121418522/b40346e9-f258-4de2-9582-a4dae48082dc)

### Q9) Perform Natural join on both tables
#### QUERY:
```
 select * from customer1 NATURAL JOIN salesman1;
```
#### OUTPUT:
![image](https://github.com/Yuvaranithulasingam/EX-3-SubQueries-Views-and-Joins/assets/121418522/b93ae6a8-967f-4a8d-a880-ddeb5b948feb)

### Q10) Perform Left and right join on both tables
#### QUERY FOR LEFT JOIN:
```
select * from salesman1 LEFT JOIN customer1 on salesman1.salesman_id=customer1.salesman_id;
```
#### OUTPUT FOR LEFT JOIN:
![image](https://github.com/Yuvaranithulasingam/EX-3-SubQueries-Views-and-Joins/assets/121418522/090bddb0-2271-4056-99c3-32c8c4a32ae4)
#### QUERY FOR RIGHT JOIN:
```
select * from salesman1 RIGHT JOIN customer1 on salesman1.salesman_id=customer1.salesman_id;
```
#### OUTPUT FOR RIGHT JOIN:
![image](https://github.com/Yuvaranithulasingam/EX-3-SubQueries-Views-and-Joins/assets/121418522/0f85e4d3-6d60-4e11-b7b0-32a939674d95)

## RESULT:
The program has been executed successfully for the above queries.
