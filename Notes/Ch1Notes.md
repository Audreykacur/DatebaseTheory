Chapter 1 Book Notes

Database-management system (DBMS) 
	- a collection of interrelated data and a set of programs to access those data
	- the goal: provide a way to store and retrieve database information that is both convenient and efficient 
Database
	- the collection of data
	- contains information relevant to an enterprise
	- designed to manage large bodies of information 

	Managing data
		- defining structures for storage of information
		- providing mechanisms for the manipulation of information

	Security 
		- must ensure the safety of the information stored 
		- when crashed or attempts of unauthorized access must still be secure

	Accuracy
		- when shared between users : the data should be the same with no anomalous results 

Database-System Application
	Use 
		- TO manage collections of data that are 
			highly valuable
			relitavely large
			are accessed by multiple users and applications, often at the same time 
			- database system is a large, complex software system whose task is to manage a large, complex collection of data.

	Abstraction - allows a person to use a complex device or system without having to know the details of how that device or system is constructed 
		- abstraction in a database makes it possible for an enterprise to combine data of various types into a unified repository of the information needed to run the enterprise.



	Two Models where Databases are Used 
	1. to support Online transaction processing
		- large number of users use the database 
		- each user retreives a small amount of data and gets small updates
	2. to support data analysis 
		- the processing of data to draw conclusions and infer rules or decision procedures --> used to drive buisness decisions 


1.2 Purpose of Database System
- file processing system: stores permanent records in various files, needs different application programs to extract records from and add records to the appropriate files 
	- disadvantages : 
		- Data Redundancy and inconsistency: 
			- duplications in different places
			- leads to higher storage needs and therefore a higher cost
			- may lead to data inconsistency : various copies of the same data may not match if it is changed in one place and not the other
		- Difficulty in accessing data
			- does not allow needed data to be retrieve in a convenant and effiecient manner
		- Data isolation
			- data is scattered into various files --> files can be in different formats --> writing new programs to retrieve the appropriate data is difficult 
		- Integrity problems 
			- Consistency constraints: When new constraints are added it is difficult to change the program to enforce them  
		- Atomicity Problems 
			- Atomic : it happens either entirety or not at all 
			- it is hard to ensure atomicity in a conventional file processing system 
		- Concurrent- access anomalies
			- if two people changed the data at the same time the output would be incorrect because it would not have been supervised 
			- supervision is difficult because data may be accessed by many different application programs that have not been coordinated previously
		- Security Problem 
			- not every user should be able to access all the data 
			- this is hard to enforce because application programs are added to the file-processing system in an adhoc manner 

	- these disadvantages prompted the initial development of database systems and the transition of file based applications to database systems (1960's and 70's)

1.3 View of Data
	
A database system is a collection of interrelated data and a set of programs that allow users to access and modify these data. A major purpose of a database system is to provide users with an abstract view of the data. That is, the system hides certain details of how the data are stored and maintained


	1.3.1 Data Models 
	
	Data Models : a collection of conceptual tools for describing data, data relationships, data semantics, and consistency constraints 

	Four different categories of data models 
		- Relational Model 
			- uses a collection of tables to represent both data and the relationships among those data 
			- tables are also called relations 
			- example of a record based model : database is structured in fixed-format records of several types 
			- table has records of a particular type 
			- most widely used data model 

		- Entity-Relationship Model 
			- (E-R) data model 
			- collection of basic objects called entities, and relationships among these objects 
			- entity : a thing or object 
			- widely used in database design 

		- Semi-Structured Data Model 
			- specification of data --> individual data items of the same type can have different sets of attributes 
			- eex. JSON and XML

		- Object-Based Data Model
			- store objects into relational tables 
			- allow procedures to be stored in the database system and execute by the database system 
			- this is an "extension" of the relational model with notations of encapsulation, methods, and object identity

	1.3.2 Relational Data Model 
		- data is represented in the form of tables 
		- table has multiple columns 
		- each column has a unique name 
		- each row represents one new piece of information 

	1.3.3 Data Abstraction

	Structured Type 
			type instructor = record	 //Defines a new record 'Instructor'
				ID : char (5);		     //field 1 'ID' type char with 5 characters
				name : char (20);
				dept name : char (20); 
				salary : numeric (8,2);  //field 4 'Salary' type numeric with 8 digits and 2 are right of the decimal place ex.000000.00
				end;


		- physical level 
			- describes 'how' the data is actually stored 
			- describes complex low level data structures in detail
			- 'Instructor' : a block of consecutive bytes 
			- index : (type of data structure) support efficient retreival of reecords 

		- logical level 
			- describes 'what' data is stored & the relationships among the data
			- describes the entire database in terms of a small number of relativly simple structures 
			- at this level you do not need to know thee details of the physical level : Physical data independence
			- 'Instructor' described by type definition & the interrelationship of the record types are defined 
			- programmers use a programming language at this level 
			- data base administrators work at this level  

		- view level 
			- describes only a part of the entire database
			- exists to simplify users interaction with the system 
			- computer user sees a set of application programs that hide details of the data types 
			- several views of the database are defined 
			- database user sees the views 
			- has the security implemented here so all users cant view confidential information


	1.3.4 Instances and Schemas
		a database changes over time as information is inserted and deleted 
		- instance : the collection of information stored in the database at a particular moment 
		- schema : the overall design of the database 
			- physical schema : describes the database design at the physical level 
				- hidden beneath the logical schema 
				- can be changed easily without affecting application programs 
			- logical schema : describes the database design at the logical level
				- most important when looking at application programs 
				- programmers construct applications by using the logical schema 
			- sub schemas : several schemas at the view level - describe different views of the database




1.4 Database Languages	

a database system defines a 
	- data-definition language (DDL) to specify the database schema 
	- data-manipulation language (DML) to express database queries and updates 
	- "theoretically" these are not two seperate languages : they form parts of a single database language :: SQL language
	- most relational database systems employ the SQL language 

	1.4.1 Data-definition Language 
		- scecify the database schema by a set of definitions expressed by a special language (DDL)
		- specify additional properties of the data 

		- specify the storage structure and access methods used by the database system by a set of statements in DDL specifically data storage and definition language
			- statements define implementation details of the database schemas 

		- Domain constraints 
			- an attribute has a area of possible values  ex. integer, and character types 
			- declaring an attribute to a specific type acts as a constrant on the values that it can take 
			- elementary form of integrity constraint 

		- Referential integrity 
			- ensure a value that appears in one relation for a given set of attributes also appears in a certain set of attributes in another relation 
			- when this constraint is violated --> rejection of the action that caused the violation   

		- Authorization 
			- differentiation among the users as far as the type of access they are permitted on various data valuse in the database
			- Read Authorization : allows reading, but not modification, of data 
			- Insert Authorization : allows insertion of new data but not modification of existing data
			- Update Authorization : allows modification but not deletion of data
			- Delete Authorization : allows deletion of data 
			- one user could have any or none of the authorization types 

		- DDL statements provide an output
		- data dictionary - where the output of the DDL is placed (contains metadata) 
			- can be accessed and updated only by the datbase system itself 
			- database system consults the data dictionary before reading or modifing actual data
		- metadata : data about data


	1.4.2 The SQL Data Definition Language 
		SQL has a rich DDL allowing one to define tables with data types and integrity constraints 
			ex. SQL DDL statement 
				create table department
					(dept_name  char (20),
					 building	char (15), 
					 budget		numeric (12,2));
				exec ution of this table creates the department table with three columns : dept_name, building, and budget ; each has a type associated with it 

		SQL DDL supports a number of types of integrity constraints 
			ex. specify the dept_name attribute value is a primary key to make sure that no two departments can have the same name 


	1.4.3 Data-Manipulation Language (DML)
	- a language that enables users to access or manipulate data as organized by the appropriate data model 
		types of access: 
			- Retrieval of information stored in the database.
			- Insertion of new information into the database.
			- Deletion of information from the database.
			- Modification of information stored in the database.

		two types of DML 
			- Procedural DMLs : require a user to specify what data is needed and how to get the data 

			- Declarative DMLs: (aka: non procedural DMLs) require user to specify what data is needed without specifing how to get those data 
				- easier to learn  and use and procedural DMLs
				- database has to figure out have to get the data because it is not told how to 

			Query : a statement requesting the retrieval of information 
			Query language : portion of a DML that involves information retrieval (not the same thing as a DML)

			Physical level (manipulating data)
			- define algorithms that allow efficient access to data 
			Higher level
			- emphasize ease of use 

	1.4.4 The SQL Data-Manipulation Language 
		SQL query language is non procedural  
		- query take as input table/s and returns a single table 
		ex. of a SQL query
			select instructor.name from instructor
			where instructor.dept
			name = 'History';
		ex. of a SQL query
			select instructor.ID, department.dept_name
			from instructor, department 
			where instructor.dept_name= department.dept_name and department.budget > 95000

	1.4.5 Database Access from Application Programs 
		SQL does not support actions such as input from users, output to display, or communication over the network 

		if you want those computations and actioins you write them in host language ex. c/c++/java/python with embedded SQL queries that access the data in the database 
		application programs - programs that are used to interact with the database in this fashion 

1.5 Database Design (did not 100% get; go over these pages)
- database systems : designed to manage large bodies of information; information does not exsist in isolation; the information is a part of an operation of some enterprise whose end product maybe information from the database 

- database design
	- involves the design of the database schema 
	- the design of the complete database application enviorment -> that meets the needs of the enterprise being modeled -> requires attention to a broader set of issues 
- high level model
	- provides the database designer with conceptual framework 
	--> specifies the data requirements of the database users and how the database will be structured to fulfill the requirements 
	- initial phase of database design : to characterize fully the data needs of the prospective database users 
	- database deigners --> interact with domain expets and users to carry out the task 
	- outcome = specification of user requirements 
--> The designer chhoses the datamodel 
	- by applying the concepts of choosen data maodel  --> translates requirements into conceptual schema of the database 
	conceptual-design : the schema that is developed at this phase; provides detailed over view of the enterprise

- designer reviews the schema to confirm that all data requirements are indeed satisfied and are not in conflict with one another. 
- The designer also examines the design to remove any redundant features. 
- The focus at this point is on describing the data and their relationships, rather than on specifying physical storage details.


- relational model
	- the conceptual-design process involves 
		- decisions on what attributes we want to capture in the database and how to group these attributes to form the various tables. 
		- The “what” part is basically a business decision, and we shall not discuss it further in this text. 
		- The “how” part is mainly a computer-science problem. 
			- two ways to tackle the problem
				- to use the entity-relationship model 
				- to employ a set of algorithms (collectively known as normalization that takes as input the set of all attributes and generates a set of tables 

- A fully developed conceptual schema indicates 
	- the functional requirements of the enterprise. 
		- users describe the kinds of operations (or transactions) that will be performed on the data. 
		- Example operations include 
			- modifying or updating data
			- searching for and retrieving specific data
			- deleting data
		- the designer can review the schema to ensure it meets functional requirements.

- The process of moving from an abstract data model to the implementation of the database proceeds in two final design phases. 
	- In the logical-design phase, the designer maps the high-level conceptual schema onto the implementation data model of the database system that will be used. 
		- The designer uses the resulting system-specific database schema in the subsequent physical-design phase, in which the physical features of the database are specified. 
		- These features include the form of file organization and the internal storage structures

1.6 Database Engine 
- the functional components of the database 
	- the storage manager
		- data bases require a large amount of storage 
		- the information is stored on disks
		- Data is moved between disk storage and main memory as needed (takes a long time)
		- database system should structure the data to minimize the need to move data between disk and main memory 
		-Solid-state disks (SSD) used for database storage : faster than traditional disks but cost more
	- the query processor components 
		- helps the database system to simply and facilitate access to data 
		- creates good performance and ability to work at the view level without needing knowledge of the physical level 
		- logical level : translate updates and queries written in non procedural language
		- physical level : has the efficient sequence of operations 
	- the transaction management component 
		- allows application developers : have a sequence of database accesses as if they are a single unit that happens in entirely or not at all 
		- allows abstraction so the lower level managing effects of concurrent access to the data and of system failures

1.6.1 Storage Manger

Storage manager : provides the interface between the lowlevel data stored and the application programs and queries submitted to the system 
- responsible : interaction with file manager 
	- Translates various DML statements into low level file system commands 
	- storing, retreiving, updating data in the database 

- Components
	- Authorization and integrity manager
		- tests satisfaction of integrity constraints
		- checks authority of users to access data 
	- transaction manager
		- ensures database remains in a consistent state despite failure 
		- concurrent transactions execute without conflicts 
	- file manager
		- manages the allocation of space on disk storage 
		- manages data structures used to represent information stored on disks 
	- buffer manager 
		- fetching data from disk storage into main memory
		- deciding what data to cache in main memory
		- enables the DB to handle data sizes much larger than main memory


data structures for physical system implementation 
- Data files 
	- store the database itself 
- Data Dictionary
	- stores metadata about the structure of the database (schema)
- Indices
	- provide fast access to data items 


1.6.2 The Query Processor
- DDL interpreter
	- interprets DDL statements 
	- records the definitions in the data dictionary
- DML compiler
	- translates DML statements in a query language --> evaluation plan (low level instruction query instructions understand)
	- query : translated to alternative evaluation plans = same result 
	- performs query optimization : picks the lowest cost evaluation plan among the alternatives
- Query evaluation engine
	- executes low-level instructions generated by DML compiler


1.6.2 Transaction Management 

atomicity - must happen in it's entirety or not at all (all or none requirement)

- execution of the funds transfer preserve the consistency of the database 

consistency - correctness requirement 

durability - persistence requirement (dispite possible system failure)

transaction - collection of operations that perform a single logical function in a database application


recovery manager - ensuring the atomicity and durability properties 

failure recovery - detect system failures and restore the database to the state that exists prior to the failure

concurrent-control manager - control the interaction among the concurrent transactions ; ensure consistency of the database 

transaction manager - consists of the concurrency-control manager and the recovery manager



1.7 Database and application architecture
two - tier architecture 
	- earlier generation 
	- application resides at the client machine 
	- invokes database system functionality at the server machine --> query language 

three - tier architecture (better security and application)
	- modern database applications 
	- client machine acts as a front end; does not have direct database calls
	- front end communicates with an application server
		- application server: communicates with database system to access data


1.8 Database User and Administrators
- database goal : retrieve info to and from and store new information in the database 

1.8.1 Database Users and User Interfaces
- 4 types of database-system users 
	- Näive users 
		- interacts by using predetermined user interfaces
		- fills out forms, reads reports
	- Application Programmers
		- computer professional
		- write application programs 
	- Sophisticated users
		- don't write programs 
		- form requests using a database query language or data analysis software
	- Database Administrator

1.8.2 Database Administrator 
- the person who has control over the DBMS: have a central control of both data and programs that access data
functions 
	- Schema definition
		- executes a set of data definition statements in the DDL --> creates original database schema
	- Storage structure and access-method definition 
		- specify parameters for the physical organization of the data and indices to be created
	- Schema and physical-organization modification
		- changes to reflect the changing needs of the organization 
		- alter the physical organization to improve performance
	- granting of authorization for data access 
		- regulates which part of the database users see
	- routine maintenance 
		- backing up the data system, checking free disk space, monitor jobs running

1.9 History of Database Systems 









































Summary of chapter 1 : 

• A database-management system (DBMS) 
	- consists of a collection of interrelated data and a collection of programs to access those data. The data describe one particular enterprise.
	- goal : to provide an environment that is both convenient and efficient for people to use in retrieving and storing information.

• Database systems are ubiquitous today, and most people interact, either directly or indirectly, with databases many times every day.

• Database systems 
	- designed to store large bodies of information. 
	- management of data involves both the definition of structures for the storage of information and the provision of mechanisms for the manipulation of information. 
	- must provide for the safety of the information stored in the face of system crashes or attempts at unauthorized access. If data are to be shared among several users, the system must avoid possible anomalous results.
	- purpose : to provide users with an abstract view of the data. 
		The system hides certain details of how the data are stored and maintained.

• Under lying the structure of a database is the data model: a collection of conceptual tools for describing data, data relationships, data semantics, and data constraints.

• The relational data model is the most widely deployed model for storing data in databases. Other data models are the object-oriented model, the object-relational model, and semi-structured data models.

• A data-manipulation language(DML)is a language that enables users to accessor manipulate data. Non procedural DMLs, which require a user to specify only what data are needed, without specifying exactly how to get those data, are widely used today.

• A data-definition language (DDL) is a language for specifying the database schema and other properties of the data.

• Database design mainly involves the design of the database schema. The entity-relationship (E-R) data model is a widely used model for database design. It provides a convenient graphical representation to view data, relationships, and constraints.

• A database system has several subsystems.
	° The storage manager subsystem provides the interface between the low-level data stored in the database and the application programs and queries submitted to the system.
	° The query processor subsystem compiles and executes DDL and DML statements.

• Transaction management ensures that the database remains in a consistent (correct) state despite system failures. The transaction manager ensures that concur- rent transaction executions proceed without conflicts.

• The architecture of a database system is greatly influenced by the underlying computer system on which the database system runs. Database systems can be centralized, or parallel, involving multiple machines. Distributed databases span multiple geographically separated machines.

• Database applications are typically broken up into a front-end part that runs at client machines and a part that runs at the back end. In two-tier architectures, the front end directly communicates with a database running at the back end. In three- tier architectures, the back end part is itself broken up into an application server and a database server.

• There are four different types of database-system users, differentiated by the way they expect to interact with the system. Different types of user interfaces have been designed for the different types of users.

• Data-analysis techniques attempt to automatically discover rules and patterns from data. The field of data mining combines knowledge-discovery techniques invented by artificial intelligence researchers and statistical analysts with efficient implementation techniques that enable them to be used on extremely large databases.


Review Terms 
• Database-management system (DBMS)

• Database-system applications
• Online transaction processing
• Data analytics
• File-processing systems
• Data inconsistency
• Consistency constraints
• Data abstraction
	° Physical level 
	° Logical level 
	° View level

• Instance 
• Schema
° Physical schema 
	° Logical schema 
	° Sub schema
• Physical data independence 
• Data models
	° Entity-relationship model
	° Relational data model
	° Semi-structured data model 
	° Object-based data model


• Database languages
	° Data-definition language
	° Data-manipulation language 	
		⋄ Procedural DML
		⋄ Declarative DML
		⋄ non procedural DML
	° Query language
• Data-definition language
	° Domain Constraints
	° Referential Integrity
	° Authorization
		⋄ Read authorization
		⋄ Insert authorization 
		⋄ Update authorization 
		⋄ Delete authorization

• Metadata
• Application program 
• Database design
	° Conceptual design
	° Normalization
	° Specification of functional requirements 
	° Physical Design Phase


• Database Engine
	° Storage manager
		⋄ Authorization and integrity manager
		⋄ Transaction manager ⋄ File manager
		⋄ Buffer manager
		⋄ Data files
		⋄ Data dictionary 
		⋄ Indices
	° Query processor
		⋄ DDL interpreter
		⋄ DML compiler
		⋄ Query optimization
		⋄ Query evaluation engine

	° Transactions 
		⋄ Atomicity
		⋄ Consistency
		⋄ Durability
		⋄ Recovery manager
		⋄ Failure recovery
		⋄ Concurrency-control manager
• Database Architecture 
	° Centralized
	° Parallel
	° Distributed


• Database Application Architecture
	° Two-tier
	° Three-tier
	° Application server
• Database administrator (DBA)


Practice Exercises 

1.1 This chapter has described several major advantages of a database system. What are two disadvantages?

1.2 List five ways in which the type declaration system of a language such as Java or C++ differs from the data definition language used in a database.

1.3 List six major steps that you would take in setting up a database for a particular enterprise.

1.4 Suppose you want to build a video site similar to YouTube. Consider each of the points listed in Section 1.2 as disadvantages of keeping data in a file-processing system. Discuss the relevance of each of these points to the storage of actual video data, and to metadata about the video, such as title, the user who uploaded it, tags, and which users viewed it.

1.5 Keyword queries used in web search are quite different from database queries. List key differences between the two, in terms of the way the queries are specified and in terms of what is the result of a query.

Exercise 

1.6 List four applications you have used that most likely employed a database system to store persistent data.

1.7 List four significant differences between a file-processing system and a DBMS.

1.8 Explain the concept of physical data independence and its importance in database systems.

1.9 List five responsibilities of a database-management system. For each responsibility, explain the problems that would arise if the responsibility were not discharged.

1.10 List at least two reasons why database systems support data manipulation using a declarative query language such as SQL, instead of just providing a library of C or C++ functions to carry out data manipulation.

1.11 Assume that two students are trying to register for a course in which there is only one open seat. What component of a database system prevents both students from being given that last seat?

1.12 Explain the difference between two-tier and three-tier application architectures. Which is better suited for web applications? Why?

1.13 List two features developed in the 2000s and that help database systems handle data-analytics workloads.

1.14 Explain why NoSQL systems emerged in the 2000s, and briefly contrast their features with traditional database systems.

1.15 Describe at least three tables that might be used to store information in a social- networking system such as Facebook.
















