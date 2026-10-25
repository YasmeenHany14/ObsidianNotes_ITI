
# File groups / Pointers
* File groups are also called pointers
* Files are assigned to a specific pointer thats responsible for all tables inside the file group
* Pointer points to the physical file that contains the table
* Default pointer is Primary pointer
* One pointer/file group can have many files in it

## Why would we use file groups?
1. Parallel reading, reading from multiple tables at once when we join them, by having each pointer reading it's own table
2. Partitioning one database into many file groups, is the same as breaking it into multiple files - why would we do that?
	1. Protects from losing the whole database incase of hardware failure (bad sector)
	2. Faster backups by only backing up file groups with changes instead of the whole database

%%inital size, file names file extensions%%

# Derived attribute in database
## When are we allowed to save it in database?
1.  When another derived attr depends on that derived attr (calculate overtime to calculate net salary)
2. Or takes time to calculate
## Computed column in Sql server
* Property introduced in sql server
* Computed column has two properties:
	1. Formula => calculation formula
	2. IsPersisted => Should it be saved on disk or not
* We use computed column property in sql server with 2 cases:
	Formula doesnt depend on values in disk - persisted = no
	Formula depends on values on disk - persisted  = yes (saves that as a new column in database)
* If formula uses a builtin function like `(getdate())`, the column cannot be persisted (will throw error)
![[Pasted image 20261022114552.png]]
![[Pasted image 20261022114747.png]]

### How to create with code
``` SQL
CREATE TABLE emps
(
	 eid INT IDENTITY(1,1),
	 netsal AS ISNULL(salary,0) + ISNULL(overtime,0) PERSISTED, --computed
)
```

# `IsSparse`
* Used to make null values take less space incase i know this column will take many nulls and wont need to edit it frequently
	==🔴Open IsSparse column property in sql server==


# Foreign key properties
## Delete and Update rules
* Cascade => modify/delete children when you modify parent
* No action => dont do anything, dev will handle this manually
* Set null => in delete cases, set foreign key for children table as null
* Set default => in delete cases, sets foreign key value to a default value specified before - that default value should exist in the parent table


# Schema
* Logical group of objects
* Default schema for every new database is the `[dto]` schema and all objects belong to it by default
## Problems schema solved
1. Cant create two tables or objects with the same name in the same database
	Like having 2 functions or views with the same name
2. Harder to find information
3. Harder to set permissions for different users, hat to manually set delete modify permissions for every single table manually

## Code

``` SQL
-- Create
CREATE SCHEMA HR
CREATE SCHEMA Sales

-- adding tables to schema
ALTER SCHEMA HR TRANSFER Student
ALTER SCHEMA HR TRANSFER Instructor

-- will throw error, because now it belongs to a schema other than the default dbo schema
SELECT * FROM Student

-- wont throw an error, will execute and create a new table called student in the dbo schema
CREATE TABLE Student(id INT, ename VARCHAR(20))

-- permissions
-- ITI ISMdeveloper ==> user
-- grant student instructor => select insert
-- deny delete update
-- add user to schema with gui

```

10 steps to set db permissions
1. change authentication mode (sql and windows)
2. Restart server
3. Create login and user
4. Create DB
5. Create schema
6. Assign objects to schema
7. link schema and users together
8. set permissions
9. disconnect and reconnect with the new user
10. test queries to check whether they will execute

# Synonym
* A variable holding an alias for a path
* Problem in the first query is that if we are using this line in many places in code, and changed name of any part of the path, we would need to modify every single line that is referencing it
``` SQL
-- 1
select * from iti.hr.employee

--2 
create synonym emp
for iti .hr.employee

select * from emp

```

# Datatypes in SQL Server
## Built-in
### Numeric
`bit`           => boolean 0:1
`tinyint`   => 1 bit (values 0:255)
`smallint` => 2byte (values -32768:+32767)
`int`          => 4 bytes
`bigint`     => 8bytes
### decimal dt
`smallmoney` => 4B   .0000$
`money`          => 8B   .0000P
`real`            => .00000000
`float`          => .000000000000000
`dec`              => decimal  `dec(5,2)`   123.54    1.7    76.333 XXXXX
### string and text dt
`char(10)`   --array  --fixed length string           ahmed 10  ali 10 على محمد ؟؟؟؟؟
`varchar(10)` --dynamic --variable length character   ahmed 5   ali 3 على محمد ؟؟؟؟؟
`nchar(10)`   --unicode  lang  محمد
`nvarchar(10)`--unicode lang محمد
`nvarchar(max)` --up to 2GB
### date and time dt
`date`    MM/dd/yyyy
`time`    hh:mm:12.742
`time(7)` hh:mm:12.7428743
`smalldatetime`  1/1/2000 10:30:00         `[year up to 100]`
`datetime`       1/1/2000 10:30:ss.432    `[year 1753:9999]`
`datetime2(7)`   1/1/2000 10:30:ss.4329875 `[year 1:9999]`
`datetimeoffset`  11/11/2026 10:30 +2:00
### binary dt
`binary`    => 1010101  11001  110001001
`image`      => Convert image to binaries  `bytes[]`
### others dt
`XML`
`SQL_variant`
`Geography`
`uniqueidentifier`
`hierarchyid`

## User defined datatypes


# Rules and Constraints

# Constraints
![[Pasted image 20261022132544.png]]
## Built-in Constraints
1. Primary key constraint
2. Unique constraint
3. Check constraint
4. Foreign key constraint
One way of writing constraints:
* ``` SQL
  create table emps (
	 eid INT identity(1,1) PRIMARY KEY,
	 ename VARCHAR(20) NOT NULL,
	 eadd VARCHAR(20) DEFAULT 'cairo',
	 hiredate DATE DEFAULT getdate(),
	 did INT FOREIGN KEY
)
  ```
Another one is by defining them and giving them a name manually
``` SQL
  create table emps (
	 eid INT identity(1,1),
	 ename VARCHAR(20) NOT NULL,
	 eadd VARCHAR(20) DEFAULT 'cairo',
	 hiredate DATE DEFAULT getdate(),
	 did INT FOREIGN KEY
	 
	 constraint c1 primary key(eid,ename), --composite PK
	 constraint c2 unique(salary),
	 constraint c3 unique(overtime),
	 constraint c4 check(salary>1000),
	 constraint c5 check(overtime between 100 and 500),
	 constraint c6 check(eadd in('mansoura','alex','cairo')),
	 constraint c7 check(gender='f' or gender='m'),
	 constraint c8 foreign key(dnum) references dept(did)
	  on delete set null  on update cascade
)
```

## Rules
rules/constraints
1 rules per column - many constraints per column
![[Pasted image 20261022140442.png]]

> [!NOTE]
> THIS PART IS STILL WORK IN PROGRESS

# Identity gap


![[Pasted image 20261022140446.png]]

default is off
if we disabled it, then filled identity gaps manually, turned it on again, it will scan for the largest number existing in the column and continue from there

``` SQL
 alter table emps drop constraint c3

  

 alter table emps add constraint c40 check(hour_rate>1000)

  

 alter table instructor add constraint c10 check(salary>5000)

  

 --constraint ---> new data XXXXX

 --constraint ---> shared between tables XXXXX

 --constraint ---> Data types XXXX

  

 ----> Rules

 ---->global check constraint

 create rule r1 as @x>5000

  

 sp_bindrule r1,'instructor.salary'

 sp_bindrule r1,'emps.overtime'

  

 sp_unbindrule 'instructor.salary'

 sp_unbindrule 'emps.overtime'

  

  drop rule r1

---------------------------------------------

create default def1 as 10000

sp_bindefault def1,'instructor.salary'

sp_unbindefault 'instructor.salary'

drop default def1

---------------------------------------------------

--new data type     int       value>5000    default 10000

  

sp_Addtype complexdt,'int'

  

create rule r1 as @x>5000

  

create default def1 as 10000

  

sp_bindrule r1,complexdt

  

sp_bindefault def1,complexdt

  

create table mydata

(

 eid int primary key,

 ename varchar(20),

 salary complexdt

)
```