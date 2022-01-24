Chapter 1 Book Notes

Database-management system (DBMS) 
	- a collection of interrelated data and a set of programs to access those data
	- the goal: provide a way to store and retrieve database information that is both convienient and efficient 
Database
	- the collection of data
	- contains information relevent to an enterprise
	- designed to manage large bodies of information 

	Managing data
		- definning structures for storage of information
		- providing mechanisms for the manipulation of information

	Security 
		- must ensure the safety of the information stored 
		- when crashed or attepts of unautherized access must still be secure

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
		- Data Redundancy and inconsistancy: 
			- duplications in different places
			- leads to higher storage needs and therefore a higher cost
			- may lead to data inconsistancy : various copies of the same data may not match if it is changed in one place and not the other
		- Difficulty in accessinig data
			- does not allow needed data to be retreived in a conveinient and effiecent manner
		- Data isolation
			- data is scattered into various files --> files can be in different formats --> writing new programs to retreive the appropriate data is dificult 
		- Integrity problems 
			- Consistency constrainits: When new constraints are added it is difficult to change the program to enforce them  
		- Atomicity Problems 
			- Atomic : it happens either entirety or not at all 
			- it is hard to ensure atomicity in a conventioinal file processing system 
		- Concurrent- access anomalies
			- if two people changed the data at the same time the output would be incorrect becasue it would not have been supervised 
			- supervision is difficult becasue data may be accessed by many different apllication programs that have not been coordinated priviously
		- Security Problem 
			- not every user should be able to access all the data 
			- this is hard to enforce becasue application programs are added to the file-processing system in an adhoc manner 

	- these disadvantages prompted the initial development of database systems and the transition of file based applications to database systems (1960's and 70's)

1.3 View of Data
	
A database system is a collection of interrelated data and a set of programs that allow users to access and modify these data. A major purpose of a database system is to provide users with an abstract view of the data. That is, the system hides certain details of how the data are stored and maintained


	1.3.1 Data Models 
	
	Data Models : a collection of conceptual tools for describing data, data relationships, data semantics, and consistency constraints 

	Four different categories of data models 
		- Relational Model 
			- uses a collection of tabels to represent both data and the relationships among those data 
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
			- allow proocedures to be stored in the database system and execute by the database system 
			- this is an "extension" of the relational model with notations of encapsulation, methods, and object identity

	1.3.2 Relational Data Model 
		- data is represented in the form of tables 
		- table has multiple columns 
		- each column haas a unique name 
		- each row represents one new piece of information 

	1.3.3 Data Abstraction

	Structured Type 
			type instructor = record	 //Defines a new record 'Instructor'
				ID : char (5);		     //feild 1 'ID' type char with 5 characters
				name : char (20);
				dept name : char (20); 
				salary : numeric (8,2);  //feild 4 'Salary' type numeric with 8 digits and 2 are right of the decimal place ex.000000.00
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
			- describes only a paart of the entire database
			- exsists to simplify users interaction with the system 
			- computer user sees a set of apllication programs that hide details of the data types 
			- several veiws of the database are defined 
			- database user sees the veiws 
			- has the secuirity implemented here so all users cant view confidential information


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
			- subschemas : several schemas at the veiw level - descibe different views of the database




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
			- declaring an attribute to a spesific type acts as a constrant on the values that it can take 
			- elementary form of integrity constraint 

		- Referential integrity 
			- ensure a value that appears in one realtion for a given set of attributes also appears in a certain set of attributes in another realtion 
			- when this constraint is violated --> rejection of the action that caused the violation   

		- Authorization 
			- differentiation among the users as far as the type of access thay are permitted on various data valuse in the database
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
			- Procedureal DMLs : require a user to specify what data is needed and how to get the data 

			- Declarative DMLs: (aka: nonprocedural DMLs) require user to specify what data is needed without specifing how to get those data 
				- easier to learn  and use and procedural DMLs
				- database has to figure out have to get the data because it is not told how to 

			Query : a statement requesting the retrieval of information 
			Query language : portion of a DML that involves information retrieval (not the same thing as a DML)

			Physical level (manipulating data)
			- define algorithms that allow efficient access to data 
			Higher level
			- emphasize ease of use 

	1.4.4 The SQL Data-Manipulation Language 
		SQL query language is nonprocedural  
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

		if you want those computations and actioins you write them in host language ex. c/c++/java/python with enbedded SQL queries that access the data in the database 
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























