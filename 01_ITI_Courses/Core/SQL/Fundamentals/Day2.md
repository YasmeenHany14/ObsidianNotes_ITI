# Keys
* All columns are nullable except primary key

### Foreign key
* Can be null
* Isn't mandatory to be set in each table
* Should be existing value in another table primary key, if the value doesn't exist an error is thrown and transaction is aborted (keeping database integrity)
* Cannot edit or delete parent id if it has a foreign key reference somewhere
* ![[Pasted image 20261018105143.png|316]]
![[Pasted image 20261018105844.png|382]]

# SQL
* ANSI SQL is the standard SQL that each company takes, modifies a bit and makes it their own
* ![[Pasted image 20261018130120.png|326]]
## SQL Categories
* DDL
	* Data difinition language
	* Targets database structure
	* create table - create view - alter - drop - select into
* DML
	* Data manipulation language
	* Targets data inside tables
	* insert - update - alter - delete
* DCL
	* Data control lanuage
	* Targets database security and permissions
	* logins - grant - deny - revoke
* DQL
	* Data query langauge
	* Targets how data is displayed
	* select - joins - subqueries - union - grouping
* TCL
	* Transacional control language
	* Targets query execution and transactions
	* begin transaction - commit - rollback
	

``` SQL
CREATE DATABASE db2

BACKUP DATABASE db2
TO DISK='location'

RESTORE DATABASE bd2
FROM DISK='location'

DROP DATABASE db2

USE DATABASE db2

CREATE TABLE emp (
	eid int NOT NULL,
	ename VARCHAR(10) default 'cairo',
	eadd VARCHAR(10),
	hiredate DATE default getdate(), --builtin function to get current system date
	salary INT default 5000,
	age INT,
	dnum INT
)

-- ALTER TABLE

ALTER TABLE emp
	ADD overtime int -- add column overtime of type int

ALTER TABLE emp
	ALTER COLUMN overtime bigint

ALTER TABLE emp
	DROP COLUMN overtime

-- drop table
DROP TABLE emp

-------------- DML -------------

INSERT INTO emp VALUES(
	(1, 'ahmed', 'cairo', '1/1/2000', 8000, 40, NULL)
	('ali', 2)
)

UPDATE emp
	SET eadd = 'mansuora' -- update for all records in the table

UPDATE emp
	set eadd = 'btats'
	WHERE eid = 1

DELETE
	FROM emp
	WHERE eid = 1 -- if we didnt specify, all records will get deleted

---------- DQL -------------------
-- DISPLAY , SELECT
SELECT eid, name AS e_name
FROM emp
WHERE salary = 5000
ORDER BY age

SELECT eid, distinct name AS e_name -- orders and filters only unique values
FROM emp

SELECT name
FROM emp
WHERE name IS NOT NULL -- null checking is done with is/is not
-- this is because NULL is not a value in sql, 2 NULLs are not equal as there is no way to compare 2 no values together

SELECT fname + ' ' + lname name -- aliasaing
FROM emp

SELECT fullname = fname + ' ' + lname
FROM emp -- same as the one before

SELECT eid, name AS e_name
FROM emp
WHERE city IN ('alex', 'mansoura', 'ismalia')

SELECT *
FROM emp
WHERE age IN(22, 28)

SELECT *
FROM emp 
WHERE age BETWEEN 22 AND 28

SELECT name + ' ' + CONVERT(VARCHAR(20, age) as Emp_Details
FROM emp -- convert age to string so we can concat it as a string

```


``` SQL
USE Company

SELECT * FROM employee
SELECT Fname, LName, Salary, DNO
FROM employee;

SELECT PName, PLocation, DNum
FROM project;

SELECT FName + ' ' + LName AS Name, (12 * Salary) /  10 AS 'ANNUAL COMM'
FROM employee

SELECT SSN, FName + ' ' + LName AS Name
FROM employee
WHERE salary > 1000

SELECT SSN, FName + ' ' + LName AS Name
FROM employee
WHERE salary * 12 > 10000

SELECT FName + ' ' + LName AS Name, Salary
FROM employee
WHERE Sex = 'Female'

SELECT DNum, DName
FROM department
WHERE MGRSSN = 968574

SELECT PNumber, PName, PLocation
FROM Project
WHERE dnum = 10

```