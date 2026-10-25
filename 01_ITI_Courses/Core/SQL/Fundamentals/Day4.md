# Aggregate functions
* Performs calculations across the entire result set (after filtering)
* Ignores null values (literally filters them before counting or calculating)
	* In this example, selecting count(ename) will count 14 not 15
	* A good way to pypass the null filtering, is using ISNULL(column, value)
		* Replaces each NULL value in the specified column with the value provided
		* ![[Pasted image 20261020120058.png|231]]
		![[Pasted image 20261020112144.png|261]]
* د
![[Pasted image 20261020114105.png|488]]
* To filter after grouping we use HAVING
	![[Pasted image 20261020114541.png|297]]

Using having with where:
	Filter first with where, group, then filter group with having
	![[Pasted image 20261020115405.png|463]]


* Rule:
	Selecting aggregate + other columns will throw an error if we did not group by the selected columns
		Why though?
		Aggregates returns a single value which restricts returning other rows with it, grouping help with this problem by returning a single value for each group
	``` SQL
	-- ERROR BECAUSE WE DIDNT GROUP BY NAME, ID
	SELECT SUM(salary), Name, Id
	FROM emp
	
	-- ERROR BECAUSE WE GROUPED BY ONLY ID
	SELECT SUM(salary), Name, Id
	FROM emp
	GROUP BY id
	
	-- RUNS
	SELECT SUM(salary), Name, Id
	FROM emp
	GROUP BY Name, Id
	```

* We can use aggregate functions in having
``` SQL 
SELECT SUM(salary), Name
FROM emp
GROUP BY Name
HAVING COUNT(id) = 10 -- return only groups with 10 values
```

* Using where with aggregates is not allowed
``` SQL
-- WILL THROW ERROR
SELECT *
FROM student 
WHERE st_age < AVG(age)
```

# Subqueries
* Use output of one query inside another query

```SQL
-- return students with age less than all students average age
  SELECT *
  FROM student
  WHERE st_age < (
	SELECT AVG(st_age)
	FROM student
  )
  
  SELECT *, SELECT(COUNT(st_id) FROM student)
  FROM student
  
  -- return department names with students in it
  SELECT dept_name
  FROM department
  WHERE dept_id IN (
	  SELECT DISTINCT dept_id
	  FROM student
	  WHERE dept_id IS NOT NULL
  )

-- could also be written as
SELECT dept_name
FROM department
JOIN student
ON s.dept_id = d.id

-- Joins are faster than subqueries, so if what we want can be achieved with joins select them
-- Subqueries are slower than other approaches in general, make it the last thing you try
```

``` SQL
-- subqueries + DML [DELETE]

-- will throw an error, crs name doesnt exist in student course table
DELETE
FROM student_course
WHERE crs_name IN ('html', 'js')

-- will work
DELETE 
FROM student_course
WHERE crs_name IN (
	SELECT crs_id FROM course WHERE crs_name IN ('html', 'js')
)
```


![[Pasted image 20261020122658.png]]

# EERD (Enhanced ER Diagram)
* Using inheritance inside ER diagram 
* Assume we have a diagram for a collage system, which stores information for under graduate students, and post graduate students
	* Both are students with shared attributes, and unique attributes per type 
	* Here we can use inheritance, as they both share parent type (Student)
	* ![[Pasted image 20261020125952.png|242]]
* Parent is called ==🔵Supertype== entity
* Child is called ==🔵Subtype== entity
![[Pasted image 20261020130525.png|324]]

* Double line => total specialization
* Single line => Partial specialization
	To know which to use we ask, are all parent entities can belong and be categorized into child types? if yes it's total, if no it's partial
	Are all vehicles car or bike? if there are other types with no special attributes (means they are grouped with the parent type for now) it's partial
* Disjoin - Overlap
	Can the child belong to two types of children types at the same time?![[Pasted image 20261020131804.png|339]]

* EX:
	* ![[Pasted image 20261020132053.png|286]]
	* All employees are Hourly or salaried or consultants
	* Employee can only be one of them cant do both at the same time

### Discriminator column
* Used in parent table, to specify which subtype this record belongs to
* Helps reducing joins incase the only info i need from child is it's type![[Pasted image 20261020132619.png|296]]

# Set operators
* Union all, Union, intersect, except
## Union all - Union
* Concats rows of two or more queries together of the same result set
* Assuming selected columns in both tables have the same name and datatype, and the number of columns in the two select statements is the same
* Union filters duplicate values, which makes it slower than UNION ALL, which doesn't filter the result set
``` SQL
SELECT Name 
FROM student
UNION 
SELECT Name
FROM outsource_studend

-- casting to bypass the same types constraint
SELECT CONVERT(VARCHAR(20), st_id)
FROM student
UNION ALL
SELECT ins_name
FROM instructore
```

## Intersect and Except
#### Intersect
* Returns only duplicate values between both queries
* Returns matching rows in the two queries
* Filters duplicates and sorts the result set
``` SQL
SELECT st_name, st_id
FROM student
INTERSECT
SELECT ins_name, ins_id
FROM instructor
```

#### Except
* Returns values exists in the first result set and not the second result set
* Filters duplicates and sorts the result set
``` SQL
SELECT st_name, st_id
FROM student
EXCEPT
SELECT ins_name, ins_id
FROM instructor
```

# Query execution order
![[Pasted image 20261020134924.png|373]]
* The first one works and the second fails because of query execution order/cycle
		1. FROM
		2. JOIN
		3. ON
		4. WHERE
		5. GROUP BY
		6. HAVING
		7. SELECT
		8. ORDER BY
		9. TOP
		10. INTO
* The first one, select is already executed so it recognizes full name column, while in the second one, where still doesn't know what full name is
* A way to bypass this restriction is to use subquery
	* Using a subquery with from creates a runtime temp table, which we can query
``` SQL
SELECT *
FROM (
	SELECT st_fname + ' '  + st_lname AS fullname
	FROM Student
) AS NewTable
WHERE fullname = 'ahmed hassan'
```

![[Pasted image 20261020135650.png]]


select/from/where > distinct > order> joins > grouping/aggr > subquery