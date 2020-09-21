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
