# MySQL

---

# **Example 1**

---

Create Table `Worker`

```sql
CREATE TABLE Worker (
	WORKER_ID INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
	FIRST_NAME CHAR(25),
	LAST_NAME CHAR(25),
	SALARY INT(15),
	JOINING_DATE DATETIME,
	DEPARTMENT CHAR(25)
);
```

Insert data to table `Worker`

```sql
INSERT INTO Worker
	(WORKER_ID, FIRST_NAME, LAST_NAME, SALARY, JOINING_DATE, DEPARTMENT)
    VALUES
	    (001, 'Monika', 'Arora', 100000, '14-02-20 09.00.00', 'HR'),
		(002, 'Niharika', 'Verma', 80000, '14-06-11 09.00.00', 'Admin'),
		(003, 'Vishal', 'Singhal', 300000, '14-02-20 09.00.00', 'HR'),
		(004, 'Amitabh', 'Singh', 500000, '14-02-20 09.00.00', 'Admin'),
		(005, 'Vivek', 'Bhati', 500000, '14-06-11 09.00.00', 'Admin'),
		(006, 'Vipul', 'Diwan', 200000, '14-06-11 09.00.00', 'Account'),
		(007, 'Satish', 'Kumar', 75000, '14-01-20 09.00.00', 'Account'),
		(008, 'Geetika', 'Chauhan', 90000, '14-04-11 09.00.00', 'Admin');

```

Create Table `Bonus`

```sql
CREATE TABLE Bonus (
	WORKER_REF_ID INT,
	BONUS_AMOUNT INT(10),
	BONUS_DATE DATETIME,
	FOREIGN KEY (WORKER_REF_ID)
		REFERENCES Worker(WORKER_ID)
        ON DELETE CASCADE
);
```

Insert data to `Bonus`

```sql
INSERT INTO Bonus
	(WORKER_REF_ID, BONUS_AMOUNT, BONUS_DATE)
    VALUES
		(001, 5000, '16-02-20'),
		(002, 3000, '16-06-11'),
		(003, 4000, '16-02-20'),
		(001, 4500, '16-02-20'),
		(002, 3500, '16-06-11');
```

Create Table `Title`

```sql
CREATE TABLE Title (
	WORKER_REF_ID INT,
	WORKER_TITLE CHAR(25),
	AFFECTED_FROM DATETIME,
	FOREIGN KEY (WORKER_REF_ID)
		REFERENCES Worker(WORKER_ID)
        ON DELETE CASCADE
);
```

Insert data to `Title`

```sql
INSERT INTO Title
	(WORKER_REF_ID, WORKER_TITLE, AFFECTED_FROM)
    VALUES
        (001, 'Manager', '2016-02-20 00:00:00'),
        (002, 'Executive', '2016-06-11 00:00:00'),
        (008, 'Executive', '2016-06-11 00:00:00'),
        (005, 'Manager', '2016-06-11 00:00:00'),
        (004, 'Asst. Manager', '2016-06-11 00:00:00'),
        (007, 'Executive', '2016-06-11 00:00:00'),
        (006, 'Lead', '2016-06-11 00:00:00'),
        (003, 'Lead', '2016-06-11 00:00:00');

```

---

## Execute Query for **Example 1**

```sql
select * from Worker;
```

| WORKER_ID | FIRST_NAME | LAST_NAME | SALARY | JOINING_DATE         | DEPARTMENT |
| --------- | ---------- | --------- | ------ | -------------------- | ---------- |
| 1         | Monika     | Arora     | 100000 | 2014-02-20T09:00:00Z | HR         |
| 2         | Niharika   | Verma     | 80000  | 2014-06-11T09:00:00Z | Admin      |
| 3         | Vishal     | Singhal   | 300000 | 2014-02-20T09:00:00Z | HR         |
| 4         | Amitabh    | Singh     | 500000 | 2014-02-20T09:00:00Z | Admin      |
| 5         | Vivek      | Bhati     | 500000 | 2014-06-11T09:00:00Z | Admin      |
| 6         | Vipul      | Diwan     | 200000 | 2014-06-11T09:00:00Z | Account    |
| 7         | Satish     | Kumar     | 75000  | 2014-01-20T09:00:00Z | Account    |
| 8         | Geetika    | Chauhan   | 90000  | 2014-04-11T09:00:00Z | Admin      |

---

```sql
select * from Bonus;
```

| WORKER_REF_ID | BONUS_AMOUNT | BONUS_DATE           |
| ------------- | ------------ | -------------------- |
| 1             | 5000         | 2016-02-20T00:00:00Z |
| 2             | 3000         | 2016-06-11T00:00:00Z |
| 3             | 4000         | 2016-02-20T00:00:00Z |
| 1             | 4500         | 2016-02-20T00:00:00Z |
| 2             | 3500         | 2016-06-11T00:00:00Z |

---

```sql
select * from Title;
```

| WORKER_REF_ID | WORKER_TITLE  | AFFECTED_FROM        |
| ------------- | ------------- | -------------------- |
| 1             | Manager       | 2016-02-20T00:00:00Z |
| 2             | Executive     | 2016-06-11T00:00:00Z |
| 8             | Executive     | 2016-06-11T00:00:00Z |
| 5             | Manager       | 2016-06-11T00:00:00Z |
| 4             | Asst. Manager | 2016-06-11T00:00:00Z |
| 7             | Executive     | 2016-06-11T00:00:00Z |
| 6             | Lead          | 2016-06-11T00:00:00Z |
| 3             | Lead          | 2016-06-11T00:00:00Z |

---

---

Q-1. Write an SQL query to fetch “FIRST_NAME” from Worker table using the alias name as <WORKER_NAME>.

```sql
Select FIRST_NAME AS WORKER_NAME from Worker;
```

| WORKER_NAME |
| ----------- |
| Monika      |
| Niharika    |
| Vishal      |
| Amitabh     |
| Vivek       |
| Vipul       |
| Satish      |
| Geetika     |

---

---

Q-2. Write an SQL query to fetch “FIRST_NAME” from Worker table in upper case.

```sql
Select upper(FIRST_NAME) from Worker;
```

| upper(FIRST_NAME) |
| ----------------- |
| MONIKA            |
| NIHARIKA          |
| VISHAL            |
| AMITABH           |
| VIVEK             |
| VIPUL             |
| SATISH            |
| GEETIKA           |

---

---

Q-3. Write an SQL query to fetch unique values of DEPARTMENT from Worker table.

```sql
Select distinct DEPARTMENT from Worker;
```

| DEPARTMENT |
| ---------- |
| HR         |
| Admin      |
| Account    |

---

---

Q-4. Write an SQL query to print the first three characters of FIRST_NAME from Worker table.

```sql
Select substring(FIRST_NAME,1,3) from Worker;
```

| substring(FIRST_NAME,1,3) |
| ------------------------- |
| Mon                       |
| Nih                       |
| Vis                       |
| Ami                       |
| Viv                       |
| Vip                       |
| Sat                       |
| Gee                       |

---

---

Q-5. Write an SQL query to find the position of the alphabet (‘a’) in the first name column ‘Amitabh’ from Worker table.

```sql
Select INSTR(FIRST_NAME, BINARY'a') from Worker where FIRST_NAME = 'Amitabh';
```

| INSTR(FIRST_NAME, BINARY'a') |
| ---------------------------- |
| 5                            |

- The INSTR method is in case-sensitive by default.
- Using Binary operator will make INSTR work as the case-sensitive function.

---

---

Q-6. Write an SQL query to print the **FIRST_NAME** from Worker table after removing white spaces from the right side.

```sql
Select RTRIM(FIRST_NAME) from Worker;
```

| RTRIM(FIRST_NAME) |
| ----------------- |
| Monika            |
| Niharika          |
| Vishal            |
| Amitabh           |
| Vivek             |
| Vipul             |
| Satish            |
| Geetika           |

---

---

Q-7. Write an SQL query to print the DEPARTMENT from Worker table after removing white spaces from the left side.

```sql
Select LTRIM(DEPARTMENT) from Worker;
```

| LTRIM(DEPARTMENT) |
| ----------------- |
| HR                |
| Admin             |
| HR                |
| Admin             |
| Admin             |
| Account           |
| Account           |
| Admin             |

---

---

Q-8. Write an SQL query that fetches the unique values of DEPARTMENT from Worker table and prints its length.

```sql
Select distinct length(DEPARTMENT) from Worker;
```

| length(DEPARTMENT) |
| ------------------ |
| 2                  |
| 5                  |
| 7                  |

---

---

Q-9. Write an SQL query to print the FIRST_NAME from Worker table after replacing ‘a’ with ‘A’.

```sql
Select REPLACE(FIRST_NAME,'a','A') from Worker;
```

| REPLACE(FIRST_NAME,'a','A') |
| --------------------------- |
| MonikA                      |
| NihArikA                    |
| VishAl                      |
| AmitAbh                     |
| Vivek                       |
| Vipul                       |
| SAtish                      |
| GeetikA                     |

---

---

Q-10. Write an SQL query to print the FIRST_NAME and LAST_NAME from Worker table into a single column COMPLETE_NAME. A space char should separate them.

```sql
Select CONCAT(FIRST_NAME, ' ', LAST_NAME) AS 'COMPLETE_NAME' from Worker;
```

| COMPLETE_NAME   |
| --------------- |
| Monika Arora    |
| Niharika Verma  |
| Vishal Singhal  |
| Amitabh Singh   |
| Vivek Bhati     |
| Vipul Diwan     |
| Satish Kumar    |
| Geetika Chauhan |

---

---

Q-11. Write an SQL query to print all Worker details from the Worker table order by FIRST_NAME Ascending.

```sql
Select * from Worker order by FIRST_NAME asc;
```

| WORKER_ID | FIRST_NAME | LAST_NAME | SALARY | JOINING_DATE         | DEPARTMENT |
| --------- | ---------- | --------- | ------ | -------------------- | ---------- |
| 4         | Amitabh    | Singh     | 500000 | 2014-02-20T09:00:00Z | Admin      |
| 8         | Geetika    | Chauhan   | 90000  | 2014-04-11T09:00:00Z | Admin      |
| 1         | Monika     | Arora     | 100000 | 2014-02-20T09:00:00Z | HR         |
| 2         | Niharika   | Verma     | 80000  | 2014-06-11T09:00:00Z | Admin      |
| 7         | Satish     | Kumar     | 75000  | 2014-01-20T09:00:00Z | Account    |
| 6         | Vipul      | Diwan     | 200000 | 2014-06-11T09:00:00Z | Account    |
| 3         | Vishal     | Singhal   | 300000 | 2014-02-20T09:00:00Z | HR         |
| 5         | Vivek      | Bhati     | 500000 | 2014-06-11T09:00:00Z | Admin      |

---

---

Q-12. Write an SQL query to print all Worker details from the Worker table order by FIRST_NAME Ascending and DEPARTMENT Descending.

```sql
Select * from Worker order by FIRST_NAME asc,DEPARTMENT desc;
```

| WORKER_ID | FIRST_NAME | LAST_NAME | SALARY | JOINING_DATE         | DEPARTMENT |
| --------- | ---------- | --------- | ------ | -------------------- | ---------- |
| 4         | Amitabh    | Singh     | 500000 | 2014-02-20T09:00:00Z | Admin      |
| 8         | Geetika    | Chauhan   | 90000  | 2014-04-11T09:00:00Z | Admin      |
| 1         | Monika     | Arora     | 100000 | 2014-02-20T09:00:00Z | HR         |
| 2         | Niharika   | Verma     | 80000  | 2014-06-11T09:00:00Z | Admin      |
| 7         | Satish     | Kumar     | 75000  | 2014-01-20T09:00:00Z | Account    |
| 6         | Vipul      | Diwan     | 200000 | 2014-06-11T09:00:00Z | Account    |
| 3         | Vishal     | Singhal   | 300000 | 2014-02-20T09:00:00Z | HR         |
| 5         | Vivek      | Bhati     | 500000 | 2014-06-11T09:00:00Z | Admin      |

---

---

Q-13. Write an SQL query to print details for Workers with the first name as “Vipul” and “Satish” from Worker table.

```sql
Select * from Worker where FIRST_NAME in ('Vipul','Satish');
```

| WORKER_ID | FIRST_NAME | LAST_NAME | SALARY | JOINING_DATE         | DEPARTMENT |
| --------- | ---------- | --------- | ------ | -------------------- | ---------- |
| 6         | Vipul      | Diwan     | 200000 | 2014-06-11T09:00:00Z | Account    |
| 7         | Satish     | Kumar     | 75000  | 2014-01-20T09:00:00Z | Account    |

---

---

Q-14. Write an SQL query to print details of workers excluding first names, “Vipul” and “Satish” from Worker table.

```sql
Select * from Worker where FIRST_NAME not in ('Vipul','Satish');
```

| WORKER_ID | FIRST_NAME | LAST_NAME | SALARY | JOINING_DATE         | DEPARTMENT |
| --------- | ---------- | --------- | ------ | -------------------- | ---------- |
| 1         | Monika     | Arora     | 100000 | 2014-02-20T09:00:00Z | HR         |
| 2         | Niharika   | Verma     | 80000  | 2014-06-11T09:00:00Z | Admin      |
| 3         | Vishal     | Singhal   | 300000 | 2014-02-20T09:00:00Z | HR         |
| 4         | Amitabh    | Singh     | 500000 | 2014-02-20T09:00:00Z | Admin      |
| 5         | Vivek      | Bhati     | 500000 | 2014-06-11T09:00:00Z | Admin      |
| 8         | Geetika    | Chauhan   | 90000  | 2014-04-11T09:00:00Z | Admin      |

---

---

Q-15. Write an SQL query to print details of Workers with DEPARTMENT name as “Admin”.

```sql
Select * from Worker where DEPARTMENT like 'Admin%';
```

| WORKER_ID | FIRST_NAME | LAST_NAME | SALARY | JOINING_DATE         | DEPARTMENT |
| --------- | ---------- | --------- | ------ | -------------------- | ---------- |
| 2         | Niharika   | Verma     | 80000  | 2014-06-11T09:00:00Z | Admin      |
| 4         | Amitabh    | Singh     | 500000 | 2014-02-20T09:00:00Z | Admin      |
| 5         | Vivek      | Bhati     | 500000 | 2014-06-11T09:00:00Z | Admin      |
| 8         | Geetika    | Chauhan   | 90000  | 2014-04-11T09:00:00Z | Admin      |

---

---

Q-16. Write an SQL query to print details of the Workers whose FIRST_NAME contains ‘a’.

```sql
Select * from Worker where FIRST_NAME like '%a%';
```

| WORKER_ID | FIRST_NAME | LAST_NAME | SALARY | JOINING_DATE         | DEPARTMENT |
| --------- | ---------- | --------- | ------ | -------------------- | ---------- |
| 1         | Monika     | Arora     | 100000 | 2014-02-20T09:00:00Z | HR         |
| 2         | Niharika   | Verma     | 80000  | 2014-06-11T09:00:00Z | Admin      |
| 3         | Vishal     | Singhal   | 300000 | 2014-02-20T09:00:00Z | HR         |
| 4         | Amitabh    | Singh     | 500000 | 2014-02-20T09:00:00Z | Admin      |
| 7         | Satish     | Kumar     | 75000  | 2014-01-20T09:00:00Z | Account    |
| 8         | Geetika    | Chauhan   | 90000  | 2014-04-11T09:00:00Z | Admin      |

---

---

Q-17. Write an SQL query to print details of the Workers whose FIRST_NAME ends with ‘a’.

```sql
Select * from Worker where FIRST_NAME like '%a';
```

| WORKER_ID | FIRST_NAME | LAST_NAME | SALARY | JOINING_DATE         | DEPARTMENT |
| --------- | ---------- | --------- | ------ | -------------------- | ---------- |
| 1         | Monika     | Arora     | 100000 | 2014-02-20T09:00:00Z | HR         |
| 2         | Niharika   | Verma     | 80000  | 2014-06-11T09:00:00Z | Admin      |
| 8         | Geetika    | Chauhan   | 90000  | 2014-04-11T09:00:00Z | Admin      |

---

---

Q-18. Write an SQL query to print details of the Workers whose FIRST_NAME ends with ‘h’ and contains six alphabets.

```sql
Select * from Worker where FIRST_NAME like '_____h';
```

| WORKER_ID | FIRST_NAME | LAST_NAME | SALARY | JOINING_DATE         | DEPARTMENT |
| --------- | ---------- | --------- | ------ | -------------------- | ---------- |
| 7         | Satish     | Kumar     | 75000  | 2014-01-20T09:00:00Z | Account    |

---

---

Q-19. Write an SQL query to print details of the Workers whose SALARY lies between 100000 and 500000.

```sql
Select * from Worker where SALARY between 100000 and 500000;
```

| WORKER_ID | FIRST_NAME | LAST_NAME | SALARY | JOINING_DATE         | DEPARTMENT |
| --------- | ---------- | --------- | ------ | -------------------- | ---------- |
| 1         | Monika     | Arora     | 100000 | 2014-02-20T09:00:00Z | HR         |
| 3         | Vishal     | Singhal   | 300000 | 2014-02-20T09:00:00Z | HR         |
| 4         | Amitabh    | Singh     | 500000 | 2014-02-20T09:00:00Z | Admin      |
| 5         | Vivek      | Bhati     | 500000 | 2014-06-11T09:00:00Z | Admin      |
| 6         | Vipul      | Diwan     | 200000 | 2014-06-11T09:00:00Z | Account    |

---

---

Q-20. Write an SQL query to print details of the Workers who have joined in Feb’2014.

```sql
Select * from Worker where year(JOINING_DATE) = 2014 and month(JOINING_DATE) = 2;
```

| WORKER_ID | FIRST_NAME | LAST_NAME | SALARY | JOINING_DATE         | DEPARTMENT |
| --------- | ---------- | --------- | ------ | -------------------- | ---------- |
| 1         | Monika     | Arora     | 100000 | 2014-02-20T09:00:00Z | HR         |
| 3         | Vishal     | Singhal   | 300000 | 2014-02-20T09:00:00Z | HR         |
| 4         | Amitabh    | Singh     | 500000 | 2014-02-20T09:00:00Z | Admin      |

---

---

Q-21. Write an SQL query to fetch the count of employees working in the department ‘Admin’.

```sql
SELECT COUNT(*) FROM worker WHERE DEPARTMENT = 'Admin';
```

| COUNT(\*) |
| --------- |
| 4         |

---

---

Q-22. Write an SQL query to fetch worker names with salaries >= 50000 and <= 100000.

```sql
SELECT CONCAT(FIRST_NAME, ' ', LAST_NAME) As Worker_Name, Salary
FROM worker
WHERE WORKER_ID IN
    (
        SELECT WORKER_ID FROM worker
        WHERE Salary BETWEEN 50000 AND 100000
    );
```

| Worker_Name     | Salary |
| --------------- | ------ |
| Monika Arora    | 100000 |
| Niharika Verma  | 80000  |
| Satish Kumar    | 75000  |
| Geetika Chauhan | 90000  |

---

---

Q-23. Write an SQL query to fetch the no. of workers for each department in the descending order.

```sql
SELECT DEPARTMENT, count(WORKER_ID) No_Of_Workers
FROM worker
GROUP BY DEPARTMENT
ORDER BY No_Of_Workers DESC;
```

| DEPARTMENT | No_Of_Workers |
| ---------- | ------------- |
| Admin      | 4             |
| Account    | 2             |
| HR         | 2             |

---

---

Q-24. Write an SQL query to print details of the Workers who are also Managers.

```sql
SELECT DISTINCT W.FIRST_NAME, T.WORKER_TITLE
FROM Worker W
INNER JOIN Title T
ON W.WORKER_ID = T.WORKER_REF_ID
AND T.WORKER_TITLE in ('Manager');
```

| FIRST_NAME | WORKER_TITLE |
| ---------- | ------------ |
| Monika     | Manager      |
| Vivek      | Manager      |

---

---

Q-25. Write an SQL query to fetch duplicate records having matching data in some fields of a table.

```sql
SELECT WORKER_TITLE, AFFECTED_FROM, COUNT(*)
FROM Title
GROUP BY WORKER_TITLE, AFFECTED_FROM
HAVING COUNT(*) > 1;
```

| WORKER_TITLE | AFFECTED_FROM        | COUNT(\*) |
| ------------ | -------------------- | --------- |
| Executive    | 2016-06-11T00:00:00Z | 3         |
| Lead         | 2016-06-11T00:00:00Z | 2         |

---

---

Q-26. Write an SQL query to show only odd rows from a table.

```sql
SELECT * FROM Worker WHERE MOD (WORKER_ID, 2) <> 0;
```

| WORKER_ID | FIRST_NAME | LAST_NAME | SALARY | JOINING_DATE         | DEPARTMENT |
| --------- | ---------- | --------- | ------ | -------------------- | ---------- |
| 1         | Monika     | Arora     | 100000 | 2014-02-20T09:00:00Z | HR         |
| 3         | Vishal     | Singhal   | 300000 | 2014-02-20T09:00:00Z | HR         |
| 5         | Vivek      | Bhati     | 500000 | 2014-06-11T09:00:00Z | Admin      |
| 7         | Satish     | Kumar     | 75000  | 2014-01-20T09:00:00Z | Account    |

---

---

Q-27. Write an SQL query to show only even rows from a table.

```sql
SELECT * FROM Worker WHERE MOD (WORKER_ID, 2) = 0;
```

| WORKER_ID | FIRST_NAME | LAST_NAME | SALARY | JOINING_DATE         | DEPARTMENT |
| --------- | ---------- | --------- | ------ | -------------------- | ---------- |
| 2         | Niharika   | Verma     | 80000  | 2014-06-11T09:00:00Z | Admin      |
| 4         | Amitabh    | Singh     | 500000 | 2014-02-20T09:00:00Z | Admin      |
| 6         | Vipul      | Diwan     | 200000 | 2014-06-11T09:00:00Z | Account    |
| 8         | Geetika    | Chauhan   | 90000  | 2014-04-11T09:00:00Z | Admin      |

---

---

Q-28. Write an SQL query to clone a new table from another table.

The general query to clone a table with data is:

```sql
SELECT * INTO WorkerClone FROM Worker;
```

The general way to clone a table without information is:

```sql
SELECT * INTO WorkerClone FROM Worker WHERE 1 = 0;
```

An alternate way to clone a table (for MySQL) without is:

```sql
CREATE TABLE WorkerClone LIKE Worker;
```

---

Q-29. Write an SQL query to fetch intersecting records of two tables.

```sql
(SELECT * FROM Worker)
INTERSECT
(SELECT * FROM WorkerClone);
```

> MySQL Doesn't Support `INTERSECT` syntax.

---

---

Q-30. Write an SQL query to show records from one table that another table does not have.

```sql
SELECT * FROM Worker
MINUS
SELECT * FROM Title;
```

> MySQL Doesn't Support `MINUS` syntax.

---

---

Q-31. Write an SQL query to show the current date and time.

Following MySQL query returns the current date:

```sql
SELECT CURDATE();
```

| CURDATE()  |
| ---------- |
| 2020-09-21 |

Following MySQL query returns the current date and time:

```sql
SELECT NOW();
```

| NOW()                |
| -------------------- |
| 2020-09-21T14:51:30Z |

Following SQL Server query returns the current date and time:

```sql
SELECT getdate();
```

> MySQL doesn't support

Following Oracle query returns the current date and time:

```sql
SELECT SYSDATE FROM DUAL;
```

> MySQL doesn't support

---

---

Q-32. Write an SQL query to show the top n (say 10) records of a table.

Following MySQL query will return the top n records using the LIMIT method:

```sql
SELECT * FROM Worker ORDER BY Salary DESC LIMIT 10;
```

| WORKER_ID | FIRST_NAME | LAST_NAME | SALARY | JOINING_DATE         | DEPARTMENT |
| --------- | ---------- | --------- | ------ | -------------------- | ---------- |
| 4         | Amitabh    | Singh     | 500000 | 2014-02-20T09:00:00Z | Admin      |
| 5         | Vivek      | Bhati     | 500000 | 2014-06-11T09:00:00Z | Admin      |
| 3         | Vishal     | Singhal   | 300000 | 2014-02-20T09:00:00Z | HR         |
| 6         | Vipul      | Diwan     | 200000 | 2014-06-11T09:00:00Z | Account    |
| 1         | Monika     | Arora     | 100000 | 2014-02-20T09:00:00Z | HR         |
| 8         | Geetika    | Chauhan   | 90000  | 2014-04-11T09:00:00Z | Admin      |
| 2         | Niharika   | Verma     | 80000  | 2014-06-11T09:00:00Z | Admin      |
| 7         | Satish     | Kumar     | 75000  | 2014-01-20T09:00:00Z | Account    |

---

Following SQL Server query will return the top n records using the TOP command:

```sql
SELECT TOP 10 * FROM Worker ORDER BY Salary DESC;
```

> MySQL doesn't support

Following Oracle query will return the top n records with the help of ROWNUM:

```sql
SELECT * FROM (SELECT * FROM Worker ORDER BY Salary DESC)
WHERE ROWNUM <= 10;
```

> MySQL doesn't supports.

---

---

Q-33. Write an SQL query to determine the nth (say n=5) highest salary from a table.

The following MySQL query returns the nth highest salary: (n-1,1)

```sql
SELECT Salary FROM Worker ORDER BY Salary DESC LIMIT 4,1;
```

| Salary |
| ------ |
| 100000 |

---

The following SQL Server query returns the nth highest salary:

```sql
SELECT TOP 1 Salary
FROM (
 SELECT DISTINCT TOP n Salary
 FROM Worker
 ORDER BY Salary DESC
 )
ORDER BY Salary ASC;
```

> Doesn't Support

---

---

Q-34. Write an SQL query to determine the 5th highest salary without using TOP or limit method.

The following query is using the correlated subquery to return the 5th highest salary:

```sql
SELECT Salary
FROM Worker W1
WHERE 4 = (
 SELECT COUNT( DISTINCT ( W2.Salary ) )
 FROM Worker W2
 WHERE W2.Salary >= W1.Salary
 );
```

| Salary |
| ------ |
| 100000 |

---

Use the following generic method to find nth highest salary without using TOP or limit. (n-1) = (...)

```sql
SELECT Salary
FROM Worker W1
WHERE 5-1 = (
 SELECT COUNT( DISTINCT ( W2.Salary ) )
 FROM Worker W2
 WHERE W2.Salary >= W1.Salary
 );
```

| Salary |
| ------ |
| 100000 |

---

---

Q-35. Write an SQL query to fetch the list of employees with the same salary.

```sql
Select distinct W.WORKER_ID, W.FIRST_NAME, W.Salary
from Worker W, Worker W1
where W.Salary = W1.Salary
and W.WORKER_ID != W1.WORKER_ID;
```

| WORKER_ID | FIRST_NAME | Salary |
| --------- | ---------- | ------ |
| 4         | Amitabh    | 500000 |
| 5         | Vivek      | 500000 |

---

---

Q-36. Write an SQL query to show the second highest salary from a table.

```sql
Select max(Salary) from Worker
where Salary not in (Select max(Salary) from Worker);
```

| max(Salary) |
| ----------- |
| 300000      |

---

---

Q-37. Write an SQL query to show one row twice in results from a table.

```sql
select FIRST_NAME, DEPARTMENT from worker W where W.DEPARTMENT='HR'
union all
select FIRST_NAME, DEPARTMENT from Worker W1 where W1.DEPARTMENT='HR';
```

| FIRST_NAME | DEPARTMENT |
| ---------- | ---------- |
| Monika     | HR         |
| Vishal     | HR         |
| Monika     | HR         |
| Vishal     | HR         |

---

---

Q-38. Write an SQL query to fetch intersecting records of two tables.

---

Q-39. Write an SQL query to fetch the first 50% records from a table.

```sql
SELECT *
FROM WORKER
WHERE WORKER_ID <= (SELECT count(WORKER_ID)/2 from Worker);
```

| WORKER_ID | FIRST_NAME | LAST_NAME | SALARY | JOINING_DATE         | DEPARTMENT |
| --------- | ---------- | --------- | ------ | -------------------- | ---------- |
| 1         | Monika     | Arora     | 100000 | 2014-02-20T09:00:00Z | HR         |
| 2         | Niharika   | Verma     | 80000  | 2014-06-11T09:00:00Z | Admin      |
| 3         | Vishal     | Singhal   | 300000 | 2014-02-20T09:00:00Z | HR         |
| 4         | Amitabh    | Singh     | 500000 | 2014-02-20T09:00:00Z | Admin      |

---

---

Q-40. Write an SQL query to fetch the departments that have less than five people in it.

```sql
SELECT DEPARTMENT, COUNT(WORKER_ID) as 'Number of Workers' FROM Worker GROUP BY DEPARTMENT HAVING COUNT(WORKER_ID) < 5;
```

| DEPARTMENT | Number of Workers |
| ---------- | ----------------- |
| Account    | 2                 |
| Admin      | 4                 |
| HR         | 2                 |

---

---

Q-41. Write an SQL query to show all departments along with the number of people in there.

```sql
SELECT DEPARTMENT, COUNT(DEPARTMENT) as 'Number of Workers' FROM Worker GROUP BY DEPARTMENT;
```

| DEPARTMENT | Number of Workers |
| ---------- | ----------------- |
| Account    | 2                 |
| Admin      | 4                 |
| HR         | 2                 |

---

---

Q-42. Write an SQL query to show the last record from a table.

```sql
Select * from Worker where WORKER_ID = (SELECT max(WORKER_ID) from Worker);
```

| WORKER_ID | FIRST_NAME | LAST_NAME | SALARY | JOINING_DATE         | DEPARTMENT |
| --------- | ---------- | --------- | ------ | -------------------- | ---------- |
| 8         | Geetika    | Chauhan   | 90000  | 2014-04-11T09:00:00Z | Admin      |

---

---

Q-43. Write an SQL query to fetch the first row of a table.

```sql
Select * from Worker where WORKER_ID = (SELECT min(WORKER_ID) from Worker);
```

| WORKER_ID | FIRST_NAME | LAST_NAME | SALARY | JOINING_DATE         | DEPARTMENT |
| --------- | ---------- | --------- | ------ | -------------------- | ---------- |
| 1         | Monika     | Arora     | 100000 | 2014-02-20T09:00:00Z | HR         |

---

---

Q-44. Write an SQL query to fetch the last five records from a table.

```sql
SELECT * FROM Worker WHERE WORKER_ID <=5
UNION
SELECT * FROM (SELECT * FROM Worker W order by W.WORKER_ID DESC) AS W1 WHERE W1.WORKER_ID <=5;
```

| WORKER_ID | FIRST_NAME | LAST_NAME | SALARY | JOINING_DATE         | DEPARTMENT |
| --------- | ---------- | --------- | ------ | -------------------- | ---------- |
| 1         | Monika     | Arora     | 100000 | 2014-02-20T09:00:00Z | HR         |
| 2         | Niharika   | Verma     | 80000  | 2014-06-11T09:00:00Z | Admin      |
| 3         | Vishal     | Singhal   | 300000 | 2014-02-20T09:00:00Z | HR         |
| 4         | Amitabh    | Singh     | 500000 | 2014-02-20T09:00:00Z | Admin      |
| 5         | Vivek      | Bhati     | 500000 | 2014-06-11T09:00:00Z | Admin      |

---

---

Q-45. Write an SQL query to print the name of employees having the highest salary in each department.

```sql
SELECT t.DEPARTMENT,t.FIRST_NAME,t.Salary from(SELECT max(Salary) as TotalSalary,DEPARTMENT from Worker group by DEPARTMENT) as TempNew
Inner Join Worker t on TempNew.DEPARTMENT=t.DEPARTMENT
 and TempNew.TotalSalary=t.Salary;
```

| DEPARTMENT | FIRST_NAME | Salary |
| ---------- | ---------- | ------ |
| HR         | Vishal     | 300000 |
| Admin      | Amitabh    | 500000 |
| Admin      | Vivek      | 500000 |
| Account    | Vipul      | 200000 |

---

---

Q-46. Write an SQL query to fetch three max salaries from a table.

```sql
SELECT distinct Salary from worker a WHERE 3 >= (SELECT count(distinct Salary) from worker b WHERE a.Salary <= b.Salary) order by a.Salary desc;
```

| Salary |
| ------ |
| 500000 |
| 300000 |
| 200000 |

---

---

Q-47. Write an SQL query to fetch three min salaries from a table.

```sql
SELECT distinct Salary from worker a WHERE 3 >= (SELECT count(distinct Salary) from worker b WHERE a.Salary >= b.Salary) order by a.Salary desc;
```

| Salary |
| ------ |
| 90000  |
| 80000  |
| 75000  |

---

---

Q-48. Write an SQL query to fetch nth max salaries from a table. `WHERE n >= (...)`

```sql
SELECT distinct Salary from worker a WHERE 3 >= (SELECT count(distinct Salary) from worker b WHERE a.Salary <= b.Salary) order by a.Salary desc;
```

| Salary |
| ------ |
| 500000 |
| 300000 |
| 200000 |

---

---

Q-49. Write an SQL query to fetch departments along with the total salaries paid for each of them.

```sql
 SELECT DEPARTMENT, sum(Salary) from worker group by DEPARTMENT;
```

| DEPARTMENT | sum(Salary) |
| ---------- | ----------- |
| Account    | 275000      |
| Admin      | 1170000     |
| HR         | 400000      |

---

---

Q-50. Write an SQL query to fetch the names of workers who earn the highest salary.

```sql
SELECT FIRST_NAME, SALARY from Worker WHERE SALARY=(SELECT max(SALARY) from Worker);
```

| FIRST_NAME | SALARY |
| ---------- | ------ |
| Amitabh    | 500000 |
| Vivek      | 500000 |

---

---

---

---

---

---

# **TECHNICAL INTERVIEW QUESTION PREPARATION**

---
