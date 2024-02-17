# Databases and Database Users
#### General definition
- A **database** is a collection of related data. By data we mean know facts that can be recorded and that have implicit meaning.
#### Properties of database

1. **A database shows something from the real world. When things change in real life, they also change in the database.**
2. **A database is a well-organized collection of information that makes sense. It's not just a bunch of random facts.**
3. **A database is made for a reason and has specific users in mind.**

- Accurate and reliable databases must reflect changes from the real world as soon as possible.
- Databases vary in size and complexity, from a few hundred records to millions of entries.
- Databases can be generated and maintained manually or computerized, with computerized databases being the focus in this context.
#### DBMS
- A database management system (DBMS) is a computerized system that enables users to create and maintain a database. The DBMS is a general-purpose software system that facilitates the processes of defining, constructing, manipulating, and sharing databases among various users and applications.
- **Defining DB**: Database definition includes specifying data types, structures, and constraints, stored as meta-data in a catalog or dictionary.
- **Constructing DB**: Constructing a database involves storing data on a storage medium controlled by the DBMS.
- **Manipulating DB**: Manipulating a database includes querying for specific data, updating to reflect real-world changes, and generating reports.
- **Sharing DB**: Sharing a database allows multiple users and programs simultaneous access.
- **Query**: A query typically causes some data to be retrieved, whereas transaction may cause some data to be read and some data to be written into the database.
- **Meta-Data**: Metadata in DBMS is characterized as **data about data**. It describes the context and information about data, the way that data is stored and the various relations among data.
- **Catalog**: The system catalogue is **a collection of tables and views that contain important information about a database**. It is the place where a relational database management system stores schema metadata, such as information about tables and columns, and internal bookkeeping information.
#### DBMS Illustration

![[Screenshot from 2024-01-28 16-45-32.png]]

#### Characteristics of Database Approach
- In the traditional way of handling data, each user or department creates and manages their own files for specific tasks. For example, one department might keep records of student grades, while another department tracks fees and payments. Each department has its own set of files and programs to work with this data. However, because each department's needs are slightly different, they end up duplicating some information. For instance, while both departments might need student information, they each store it separately because they require different details. This duplication wastes storage space and requires extra effort to keep all the data up to date.
	- the generic information about the students will be same
	- the departments will be duplicating the information

#### Database approach vs File processing approach
- ###### Self describing nature of database system
	- A fundamental characteristic of the database approach is that the database system contains not only the database itself but also a complete definition or description of the database structure and constraints.
	- The information stored in the catalog is called meta-data, and it describes the structure of the primary database
- ###### Insulation between programs and data, data abstraction
	- **Program-data-Independence:** In traditional file processing, the structure of data files is embedded in the application programs, so any changes to the structure of a file may require changing all programs that access that file. By contrast, DBMS access programs do not require such changes in most cases. The structure of data files is stored in the DBMS catalog separately from the access programs. We call this property program-data independence.
	- **Program-operation-independence:** Users have the ability to create their own functions or methods to perform actions on the data.These functions are made up of two parts:
		1. The interface, which includes the function's name and the types of data it works with.
		2. The implementation, which is how the function actually carries out its task.
		The good part is, users can change how the function works without changing how it's used. So, even if the inner workings of the function change, other programs can still use it in the same way. This flexibility is called program-operation independence.
- ###### Support of multiple views of data
	- In a database, there are different kinds of users, and each may need to see the information in a different way. We call these different ways of looking at the data "views."
	- A view can be a part of the database or it can be made up of virtual data that's not actually stored in the database. Some users might not even realize whether the data they're using is stored or derived from other information.
	- When there are many users with different needs, a multi-user database system has to provide ways for creating different views. For example, one user might only need to see and print student transcripts, while another user might only need to check if students have taken the required courses. Each user's view of the database can be tailored to their specific needs.
- ###### Sharing of data and multi-user transaction processing
	- In many database systems, transactions play a crucial role. A **transaction** is basically a program or process that involves accessing the database, like reading or updating records. The idea is that each transaction should perform its actions correctly if it's allowed to complete without any interruption from other transactions.
	- The database management system (DBMS) has to make sure that transactions follow certain rules. One important rule is ==isolation==, which means that each transaction should seem like it's running by itself, even if there are many transactions happening at the same time. Another important rule is **==atomicity==**, which ensures that either all the actions in a transaction are completed successfully, or none of them are.

#### Actors on the Scene
1. **Database Administrators (DBAs):**
   - DBAs oversee and manage databases and related software.
   - They authorize access, monitor usage, and handle resource acquisition.
   - In large organizations, DBAs may have staff to assist them.

2. **Database Designers:**
   - Responsible for identifying data to be stored and choosing appropriate structures.
   - They communicate with users to understand requirements and create a design to meet them.
   - Designers develop views of the database for different user groups and integrate them into a final design.

3. **End Users:**
   - Primary users who query, update, and generate reports from the database.
   - Categories include:
     - Casual users who occasionally access the database for varied information.
     - Naive users who perform standard queries and updates, often using mobile apps.
     - Sophisticated users who deeply understand the DBMS to meet complex requirements.
     - Standalone users who maintain personal databases using specific software packages.

4. **System Analysts and Application Programmers (Software Engineers):**
   - System analysts determine user requirements and develop specifications for standard transactions.
   - Application programmers implement these specifications, test, debug, and maintain the transactions.
   - They need to be familiar with the capabilities of the DBMS to accomplish their tasks effectively.

#### Workers Behind the Scene:

1. **DBMS System Designers and Implementers:**
   - Design and implement various modules and interfaces of the DBMS software package.
   - DBMS consists of many components, including catalog management, query processing, data access, concurrency control, and security.
   - Interface with other system software like the operating system and compilers.

2. **Tool Developers:**
   - Design and develop software tools to facilitate database modeling, system design, and performance improvement.
   - Tools are optional packages often purchased separately.
   - Include packages for design, performance monitoring, interfaces, prototyping, simulation, and test data generation.
   - Independent software vendors often develop and market these tools.

3. **Operators and Maintenance Personnel (System Administration Personnel):**
   - Responsible for running and maintaining the hardware and software environment for the database system.
   - Handle day-to-day operations and ensure system stability and performance.

Although these workers play crucial roles in making the database system functional, they typically do not interact with the database content for their own purposes.

#### Advantages of database approach
- Controlling redundancy in data storage and in development and maintenance efforts.
	- Sharing data among multiple users
- Restricting unauthorized access to data. Only the DBA staff uses privileged commands and facilities.
- Providing persistent storage for program Objects
	- Object-oriented DBMSs make program objects persistent
- Providing Storage Structures (e.g. indexes) for efficient Query processing
- Providing optimization of queries for efficient processing.
- Providing backup and recovery services.
- Providing multiple interfaces to different classes of users.
- Representing complex relationships among data.
- Enforcing integrity constraints on the database.
- Drawing inferences and actions from the stored data using deductive and active rules and triggers.

Determining when to use a Database Management System (DBMS) and when not to use it depends on various factors, including the nature of the data, the requirements of the application, and the resources available. Here are some considerations:

**When to Use DBMS:**

1. **Multiple Users:** If multiple users need simultaneous access to the data, a DBMS is beneficial. It helps manage concurrent access and ensures data integrity.

2. **Complex Data Relationships:** If the data has complex relationships and needs to be organized efficiently, a DBMS with relational capabilities can be useful. It allows for the creation of structured data models with relationships between entities.

3. **Data Integrity and Security:** DBMS provides mechanisms for enforcing data integrity constraints and implementing security measures, such as user authentication and access control, which are critical for sensitive data.

4. **Scalability:** A DBMS can scale to handle large volumes of data and users as the system grows. It offers features like indexing, partitioning, and replication to improve performance and scalability.

5. **Data Consistency:** DBMS ensures that data remains consistent across the system, even when multiple users are accessing and modifying it simultaneously. It provides features like transactions and locking mechanisms to maintain data consistency.

6. **Query and Reporting:** DBMS offers query languages and reporting tools for efficiently retrieving and analyzing data. It supports complex queries, aggregations, and joins, making it suitable for applications requiring advanced data analysis.

**When Not to Use DBMS:**

1. **Simple Data Storage:** For small-scale applications with simple data storage needs, where data volume and complexity are low, using a DBMS might be overkill. Storing data in flat files or simple data structures may suffice and be more straightforward to implement.

2. **Performance-Critical Applications:** In some cases, especially for high-performance applications with strict latency requirements, direct file access or in-memory data structures may be more efficient than using a DBMS. DBMS introduces overhead due to query processing and transaction management.

3. **Limited Resources:** If resources such as memory, storage, or processing power are severely constrained, using a lightweight data storage solution or managing data manually may be more practical than deploying a full-fledged DBMS.

4. **Flexibility and Control:** For applications requiring highly customized data storage and access patterns, where the overhead of a DBMS is not justified, using custom file formats or data structures may offer more flexibility and control over the data management process.

5. **Cost Considerations:** Deploying and maintaining a DBMS can incur significant costs, including licensing fees, hardware requirements, and personnel training. For small projects or budget-constrained environments, these costs may outweigh the benefits of using a DBMS.

In summary, the decision to use a DBMS should consider factors such as data complexity, scalability requirements, performance constraints, security and integrity needs, and available resources. While a DBMS offers numerous advantages for managing complex and shared data, simpler applications or environments with limited resources may find alternative approaches more suitable.