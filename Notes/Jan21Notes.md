Chapter 2
- Data models: 
	- relational model 
		- data is storedd logically into tables : each table is called a relation 
		- each relation consists of several columns (attributes) and several rows (records)

- data abstraction 
	- we care about effiecency because we are dealing with a very large number of data iinput 
		- the university stores thousands of student data files ex. all of past student transcripts and current students grades 



- levels of data
	- View level
		- several users can see the data base :: students can see their info from the database, professors have a different view of data that is usefull to them, and sdvisors have a different screen etc. 




	- Logical layer


	- physical layer
		- hard disk 
		- lowest level of abstraction 
		- to create a database correctly you need to think about this level 


- Instances and schemas
	- schemas - a framework 


- Database language
	- (DDL) - defines the database and creates tabels 



	- the SQL Data-Definition Language
		ex 
			create table Department
				(dept_name 	char(20)
				building	char(15)
				budget		numeric (12,2)     					the two means 2 decimal places 
				);

			create table Department
				(dept_name  char(20)
				name		char(15)
				salary		numeric (12,2)     					
				);


	- Domain constraints - if the user does not enter the correct wording it is declined: there are reestraints 
	- Referential Integity- to ensure that a value that appears in some relation for a given set of attributees also appear in a certain set of attributess in another relation
		ex. If there are 1000 departments; and the department name gets misspelled or abreviated then it will not categoritize itself as the same thing
	- Autherization - for security and access control 

	- The output 



- Database design 	
	- mainly invloves the design of the database schemea
	- Specification of usere requirements  phase: Characterize the data needs of the prospective database users
	- Conceptual design phase - 



Transaction management 
	- transaction - several operations on the databse that form a single logical unit of work
		- automicity - all or none requirement of transaction
		- consisteency - correctness requirement
		- Integrity - confident 
		- durability - persistance requirement 
		












