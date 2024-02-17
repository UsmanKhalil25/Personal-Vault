#### Data Model
- A set of concepts that can be used to describe the structure of a database, the operations for manipulating these structures, and certain constraints that the database should obey
#### Data Model Structure and Constraints
- Constructs are used to define the database structure
- Constructs typically include elements (and their data types) as well as groups of elements (e.g. entity, record, table), and relationships among such groups
- Constraints specify some restrictions on valid data; these constraints must be enforced at all times
#### Data Model Operations
- These operations are used for specifying database retrievals and updates by referring to the constructs of the data model.
- Operations on the data model may include basic model operations (==e.g. generic insert, delete, update==) and user-defined operations (e.g. compute_student_gpa, update_inventory)
#### Schema
- Database schema
	- the description of database
	- includes description of the database structure, datatypes and the constraints on the database
- Schema Diagram
	- An illustrative display of most aspects of a database schema
- Schema Construct
	- An entity that constructs the schema
	- A component of the schema or an object within the schema
- also called intension
#### Database State:
- the actual data stored in database at a particular moment of time. This includes the collection of all the data in database
- Also called database instance or occurrence or snapshot
- also called extension

#### Schema vs State
- the database schema changes very infrequently
- the database state changes every-time the database changes

#### Three schema architecture
- we divide the schema into three layers
	- external layer
		- this is viewed by the user
		- we can have multiple external schema (views) for different users
	- Conceptual Schema
		- this is where the logical schema of the data is stored(logical level)
	- Physical or Internal Schema
![[Screenshot from 2024-01-28 18-11-37.png]]

#### Data independence
- Logical Data Independence: The capacity to change the conceptual schema without having to change the external schemas and their associated application programs.
- Physical Data Independence: The capacity to change the internal schema without having to change the conceptual schema.

#### DBMS Languages
- **Data Definition languages (DDL):**
	- Used by the DBA and database designers to specify the conceptual schema of database
	- In some DBMSs, separate storage definition language (SDL) and view definition language (VDL) are used to define internal and external
schemas.
- **Data Manipulation languages (DML):**
	- Used to specify database retrievals and updates
	- DML commands (data sublanguage) can be embedded in a general-purpose programming language (host language), such as COBOL, C, C++, or Java.
	- **Types of DML:**
		- **High Level or non procedural languages:**
			- For example, the SQL relational language
			- Are “set”-oriented and specify what data to retrieve rather than how to retrieve it.
			- also called declarative languages
		- **Low level or procedural languages:** 
			- Retrieve data one record-at-a-time
			- Constructs such as looping are needed to retrieve multiple records, along with positioning pointers.
#### DBMS Programming Language Interfaces
- **Embedded Approach:** e.g embedded SQL (for C, C++, etc.), SQLJ for Java
- **Procedure Call Approach:** e.g. JDBC for Java, ODBC (Open Database Connectivity) for other programming languages as API’s (application programming interfaces)
- **Database Programming Language Approach:**  e.g. ORACLE has PL/SQL, a programming language based on SQL; language incorporates SQL and its data types as integral components
- **Scripting Languages:** PHP (client-side scripting) and Python (server-side scripting) are used to write database programs.
