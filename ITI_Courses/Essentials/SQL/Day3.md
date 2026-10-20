* WORK IN PROGRESS

# Normalization
* Can be used to validate existing database schema?
* kol step esmha normal form, each form has some rules to say that this table is normalized to this normal form
![[Pasted image 20261019131235.png]]


![[Pasted image 20261019134040.png]]


![[Pasted image 20261019134444.png]]


![[Pasted image 20261019134945.png]]

![[Pasted image 20261019135110.png]]


``` SQL
USE company

-- 1
SELECT d.dnum, d.DName, e.ssn, e.FName + ' ' + e.LName as Name 
FROM Department d
join Employee e
on d.MGRSSN = e.SSN

-- 2
SELECT d.dname, p.PName 
FROM Department d
JOIN Project p
ON p.DNum = d.DNum

-- 3
SELECT e.FName + ' ' + e.LName as Name, d.*
FROM Employee e
JOIN Dependent d
ON d.ESSN = e.SSN

-- 4
SELECT PNumber, PName, PLocation
FROM project
WHERE plocation in ('cairo', 'alex')

-- 5
SELECT *
FROM project
WHERE PName like 'a%'

-- 6
SELECT *
FROM Employee
WHERE DNO = 30 AND salary BETWEEN 1000 AND 2000

-- 7
SELECT e.FName + ' ' + e.LName as Name
FROM Project p
JOIN Works_On w
ON p.PNumber = w.PNO
JOIN Employee e
ON e.SSN = w.ESSN
WHERE
	p.PName = 'AL Rabwah' AND w.Hours >= 10

-- 8
SELECT e1.FName + ' ' + e1.LName as Name
FROM Employee e1
JOIN Employee e2
ON e1.SuperSSN = e2.SSN
WHERE e2.FName + ' ' + e2.LName = ' Kamel Mohamed'

-- 9
SELECT e.FName + ' ' + e.LName as Name
FROM Works_On w
JOIN Project p
ON w.PNO = p.PNumber
JOIN Employee e
ON w.ESSN = e.SSN
ORDER BY p.PName

-- 10
SELECT p.PNumber 'Project Number', d.DName 'Dept Name',
		e.LName 'Mgr Last Name', e.Address 'MGR Address',
		e.BDate 'MGR BirthDate'
FROM Project p
JOIN Department d
ON p.DNum = d.DNum
JOIN Employee e
ON d.MGRSSN = e.SSN
WHERE p.PLocation = 'Cairo City'

-- 11
SELECT e.*
FROM Employee e
JOIN Department d
ON e.SSN = MGRSSN

-- 12
SELECT e.* , d.*
FROM Employee e
LEFT JOIN Dependent d
ON d.ESSN = e.SSN

-- 13
INSERT INTO Employee VALUES
	(102672, 'Yasmeen', 'Hany', '1/1/2001', 'Ismailia', 'Female', 3000, 112233)

-- 14
INSERT INTO Employee (SSN, FName, LName, BDate, Address, Sex, DNO)
VALUES
	(102660, 'Friend', 'Yasmeen', '1/1/2001', 'Ismailia', 'Female', 30)

-- 15
UPDATE Employee
SET Salary = Salary + (Salary * 20/100)
WHERE SSN = 102672

```