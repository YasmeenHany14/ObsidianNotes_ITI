# Security
## Edition and version
something about tools
will write later

## Authentication
* Windows authentication
	Using windows credentials to login to SQL
	DBA cannot give it to devs because they will have access to windows this way 
	
* SQL Server authentication
	Create new logins and passwords to give devs access to server
		Create new users for them
		Auth => Setting permissions for what they are allowed to see and do
	A good way to allow remote access to database

# T-SQL
## TOP()
* Return top n values from query executed
* Doesn't return duplicate data
* Doesn't work with group by 
``` SQL
-- return top 2 students from the overall query result
SELECT TOP 2 *
FROM student

-- executes max(salary) query, then returns top result from it
SELECT TOP 2 MAX(salary)
FROM Employee

-- returns max 2 salaries (execution order)
SELECT TOP 2 *
FROM employee
ORDER BY salary

```

## newid()

``` SQL
-- gives each row a different id at each exection in memory, so top here returns different values each time the query is exectued
SELECT TOP(10) *
FROM questions
ORDER BY newid()
```

## GUID()
* Creates a new global id on that should be unique database level


## SELECT INTO
* Creates a table and fill it with data using an exisiting table
* Running this query twice will throw error as table already exists
* DDL
``` SQL
-- this query won't return anything, but it will create a new table called table2 and fill it with data from students
SELECT * INTO table2
FROM students

-- fill it with only st_id and st_name columns and values
SELECT st_id, st_name INTO table4
FROM students
where address = 'alex'

-- assuming the select statement returns nothing, it will create a new empty table with the same structure as the students table
SELECT * INTO table5
FROM students
WHERE 1 = 2 -- false condition

```

## INSERT INTO
* Inserting data from another table, without copying it's structure, and takes the data alone
* DML

``` SQL
INSERT INTO table5
VALUES(, , , )
-- OR 
SELECT INTO table5 (
	SELECT ins_id, ins_name
	FROM instructor
)

```

## BULK INSERT
* Insert bulk data from file by telling sql where and what is delimiter between each record

``` SQL
BULK INSERT table5
FROM 'G:\student.txt'
WITH(FILETERMINATOR=',')
```

## Full path
* `ServerName.DBName.SchemaName.ObjectName`
* Used to connect and get database from multiple databases or server in the same queries, we must specify the full path of the outsider table
``` SQL
SELECT *
FROM [Yasmeen].[Company].[dbo].[employee]

-- same as
SELECT *
FROM employee
```


## Built-in functions
![[Pasted image 20261021135100.png]]
### Concat
* Concat two or more strings 
* Ignores null values
* A special version => `concat_ws(', ', 'string', 'string')` => concat with separator
* Saves string case(upper stays the same)
### Lower
* Convert upper to lower case in memory only
* `lower('string')`

### Len
* String length
* `LEN(string)`

### Substring
* `SUBSTRING(string, start, len)`

### Charindex
* Return position of character within a string, if not found returns 0
* `CHARINDEX('a', 'Mohamed')`

### Reverse
* Resveres a string
* `REVERSE('Ahmed'`

### Replace
* `REPLACE('ahmed#gmail.com', '#', '@')`

## Delete vs Drop vs Truncate
``` SQL
DROP TABLE student
-- DDL Query, deletes table data and meta data
-- Child tables only

DELETE FROM studnet
-- DML Query, deletes only data inside table
-- Can use where condition
-- Slower, deletes row by row and logs deletion in log file
-- Can rollback becuase changes are logged
-- Parent and child tables
-- Doesn't reset identity

TRUNCATE TABLE student
-- DDL Query, deletes old table completly and recreates it as empty
-- Cant use where condition
-- Faster, deletes page by page and doesn't log
-- Cant rollback
-- Child tables only
-- Resets identity counter, as the table is completly deleted and recreated

```


# Window Functions 
* Aggregating over a specified window of the table without grouping the data

## Ranking Functions
* Ranks columns based on a specific criteria, and gives each row a number
* ![[SQL_Window_Functions_1_1.pdf]]
![[Pasted image 20261021131931.png]]
![[Pasted image 20261021131950.png]]

### Row_number()
* 2 columns with the same value are not given the same rank/number

``` SQL
SELECT *, ROW_NUMBER() OVER(ORDER BY salary DESC) AS RN
FROM employee

SELECT ROW_NUMBER() OVER(PARTITION BY Did ORDER BY salary DESC) AS RN
```
### Dense_rank()
* 2 columns with the same value are given the same rank/number


> [!NOTE]
> `DESCRIPTION LIKE '%[_]%'` => The  square brackets means _ can be anywhere even at the start or the end