![[Pasted image 20261017121252.png]]

# Database life cycle
1. Analysis
	* Conducted by system analyst
	* Have experience in both the business domain and a tech background, so he can act as the middle man between developers and the client
	* Produces a requirement document which is the scope of what should be done
2. DB design
	* By DB designer
	* Is represented with a ER Diagram
3. DB Mapping
	* By DB designer
	* Convert ER Diagram to actual tables + relationships
4. DB Implementation
	* Done by DB developer
	* Create the physical database in this stage using database tools
		* .MDF => Database files
		* .LDF => log files
	* Databases (RDBMS) are relational or not
	* Relational => sql server/oracle/mysql/...
	* Working in teams requires working with DB sharing (having one copy hosted somewhere and other people accessing the same instance)

5. Application Layer
	* Middle ground between client and database
	* Application programmer (Can also be called database user)
	* Any website or application with any language

6. Client => enduser => browser(url)

### Data vs Metadata
* Metadata is data about data (table names/column names/ schema info in general)
* Data is the values inside each tables
# Saving data methods
## File based systems
* Storing data in files in each client machine
* Two formats, 
	* Delimited files => between each value a coma
	* ![[Pasted image 20261017114824.png]]
	* Fixes width files [bytes] => 
		* Read data each specific number of bytes
		![[Pasted image 20261017114856.png]]

### Cons
* Search and modifications are hard, needs to conduct a full file scan to find info
* Lower performance
* Data duplication (no way to enforce unique constraints) => Bigger files
* No relationships between data
* No data integrity (because of constraints to validate data or even datatypes)
* No sharing because each user has a separeted copy of the data
* Long development times()
* No security
* No backup and restore (could only be done manually)
## Database systems 
* One standard between different database engines which is for example, SQL for relational databases
	each engine may add it's own version/modifications for sql
* A standard for how to store data physically
* اعكس كل اللي فوق و يبقى اتعمل هنا 
* DB integrity, Constraints, Rules, Sharing, Security, Quality, Types
![[Pasted image 20261017120845.png]]


![[Pasted image 20261017121700.png|371]]![[Pasted image 20261017122254.png|378]]

# ERD Notations
### Strong vs weak entity
* Strong entity
	* Has as primary key
	* Deleting data from a strong entity affects other tables/data
* Weak entity
	* Deleted whenever parent is deleted (dependent)
	* Doesn't have enough distinct attributes to form a primary key
	* Has a partial key instead

## Attribute types
* Simple
	Can't be broken up to multiple attributes (like how name can be broken to first and last name)
	Can't be calculated
* Composite
	Attribute broken into many parts (like name => first/last or address => city/state)
* Derived attribute
	Can be calculated from another attribute
	Age can be derived from birthdate
	Dashed elipse
* Multivalued
	Many values for the same object
	A person can have many phone numbers
* Complex attribute
	For example, having one attribute of 2 types like multivalued + composite


## Relationship Props
### Degree
* Number of entities in a relationship
* Unary
	* Self/Recursive relationship
	* ![[Pasted image 20261017132130.png|272]]
- Binary
	- ![[Pasted image 20261017132300.png|271]]
- Ternary
	- More than 2 entities
	- Rare, usually the cause is a shared attribute between them or relies on all of them to exist
	- ![[Pasted image 20261017132338.png|255]]


### Cardinality
* Each row of one entity is connected to how many rows of the other one
* One to one
* One to many
* Many to many

### Participation
* Mandatory or optional


## Keys types
1. Candidate key
	A key that can be a primary key (meets requirements)
2. Primary key
3. Partial key
4. Foreign key
5. Composite key
Task self study => what are keys types in databases



![[Pasted image 20261017141946.png]]