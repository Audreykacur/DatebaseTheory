Introduction to the relational model 
- primary model for commercial data-processing

2.1 Structure of Relational Databases
contains 

      The instructor relation
| ID | name | dept_name | salary |


	tables 
		- assigned a unique name (Instructor)
	row 
		- represents a relationship among a set of values 
	tuple 
		- a sequence of values 
	n-tuple of values 
		- represents a relationship between n values 
	relation 
		- refers to a table 
		- the domain of all attributes in a relation must be atomic (elements are indivisible units)
	tuple 
		- refers to a row 
	attribute 
		- refers to a column of a table 
		- 'ID' , 'name', 'dept_name', 'salary'
	relation instance 
		- refer to specific instances of a relation contained in a specific set of rows 

	instance : instructor
		tuples : 12 (# of instructors)

	domain 
		- set of permitted values for each attribute of the relation
		- domain of name attribute is a set of all possible instructors 

	null value 
		- signals that a value is unknown or does not exist


2.2 Database Schema

Database Schema
	- the logical design of the database 
Database instance
	- snapshot of the data in the database at a given instance in time 
relational schema
	- corresponds to the programming language of type definition 
	- consists of a list of attributes and their corresponding domains
	- does not change 
relational instance
	- corresponds to the programming language notion of a value of a variable (value changes with time)
	- contents of a relation instance may change with time 

2.3 Keys 
	- no two tuples in a relation are allowed to have the same values for all attributes 

- super key
	- a set of one or more attribute that, taken collectively, uniquely identify a tuple in the relation 
	- in the Instructor (ID) can be used as a super key but if you wanted to combine more than just the ID you can
	- you want to make sure that the super key will be able to distinguish that row from every other row
	- if the key chosen for super key matches more than one row then that would not be the super key
- primary (primary key restraints)
	- uniquely defines the relation
	- denote a candidate key that is chosen by the designer as the principal means of identifying tuples within a relation
	- 2 individual tuples in a relation are prohibited from having the same value on the key attributes at the same time 
	- listed first and underlined
	- this key usually does not change
- candidate  
	- super key for which no proper subset is a super key (minimal super key) one relation can have several candidate key
	- in the Instructor (ID) is the only key that is a candidate key
	- several distinct sets of attributes could serve as a candidate key
	- social security number 
- foreign 
	- a key in one area is a primary key in another 
	- the foreign key is relating one attribute to another attribute 
	- referential integrity constraint : requires that the values appearing in specified attributes of any tuple in the referencing relation also appear in specified attributes of at least one tuple in the referenced relation. (usually not supported if referenced attribute is not a primary key)


2.4 Schema Diagrams 
schema diagrams
	- database schema & primary key & foreign key constraints 
	- relations appears as a box
	- relation name at the top 
	- attributes listed in a box
	- primary key is underlined 
	- foreign key constraints are arrows from the foreign-key attributes to the primary key of the referencing relation 
	- two-headed arrow, referential integrity constraint that is not a foreign-key constraints


2.5 Relational Query Languages 
Query language 
	- user requests information from the database
	- higher level than a programming language 
	- categorize 
		- imperative (imperative query language)
			- user instructs the system to perform a sequence of operations on the database to compute wanted result
		- functional (functional query language)
			- evaluation of functions that may operate on data in the database 
			- evaluation of results of other functions 
			- does not update the program state 
		- declarative (declarative query language)
			- user described the desired information & no sequence of steps on how to get there
			- desired info is described using mathematical logic 
			- BD system figures out how to obtain the desired information
pure query languages
- Relational algebra
	- functional query language
	- forms the theoretical basis of the SQL query language
- tuple relational calculus & domain relational calculus
	- declarative 
- terse and formal 
	- lacking good syntax of commercial languages 
	- illustrate fundamental techniques for extracting data from the database 

2.6 The Relational Algebra 
- takes one or two relations as input 
- produces new relation as a result 

	unary - operate on one relation 
	binary :(union, cartesian product, set difference operate on pairs of relations 

	relation is a set of tuples : relations cannot contain duplicate tuples 


2.6.1 The Select Operation 
select - selects tuples that satisfy a given predicate 



sigma (σ) - denotes section 
predicate - subscript to σ
argument relation - in the () after σ 

- to select tuples where the instructor is in the physics department 
	note: dept_name = 'Physics' should be a subscript here 
	σ dept_name = “Physics” (instructor)
- find instructor with a salary > 90,000
	σ salary>90000 (instructor)

and ∧
or  ∨
not ¬ 

σ dept_name=“Physics” ∧ salary>90000 (instructor)


2.6.2 The Project Operation 
- unary operation 
- returns its arguments relation w/ certain attributes left out 
- relation is a set 
- duplicate rows are eliminated

- projection - is denoted by Π (pi)
- subscript - attributes we want to include 
- argument relation - in ()

	Π ID, name, salary (instructor)
- to get the monthly salary 
	Π ID, name, salary/12 (instructor)

2.6.3 Composition of Relational Operations 
- find the names of all the instructors names in the physics department 
	Π name (σ dept name = “Physics” (instructor))
- relational-algebra expression - relational algebra operations can be composed together

2.6.4 The Cartesian-Product Operation 
- denoted by a X
- allows us to combine information from the two relations 


2.6.5 The Join Operation 
- find the information about all the instructors together w/ course_ID

- to get the tuples of instructor X teaches that have instructors and the courses they taught
σ instructor.ID=teaches.ID (instructor × teaches)

join operation 
	r ⋈θ s = σθ(r × s)


2.6.6 Set operations 
	- To find the set of all courses taught in the Fall 2017 semester, we write:
		Π course_id (σ semester=“Fall”∧year=2017 (section))
		union - needed to answer a query of two datasets 
		- need all the course that appear in either or both of the relations 
			Π course_id (σsemester=“Fall”∧year=2017 (section)) ∪ Π course_id(σsemester=“Spring”∧year=2018 (section))
	
	union operation 
		- ensure the input relations to the union operation have the same number of attributes; (# of attributes = arity)
		- atributes have associated types : types of the ith attribute of both input relations must be the same for each i
	
	intersection operation (∩)
		- finds tuples that are both the input relations 

	set-difference operation (-)
		- finds tuples that are in one relation but not the other 

2.6.7 The Assignment Operation
assignment operation (v)
	- result of the right operation is assigned to the left operation 

2.6.8 The Rename Operation 
rename operation (ρ)
	- allows naming of relational-algebra expressions 

2.6.8 Equivalent Queries 
- multiple ways to write a query that means the same thing 
- equivalent : they give the smae result on any database 































Summary of Chapter 2
• The relational data model is based on a collection of tables. The user of the database system may query these tables, insert new tuples, delete tuples, and up- date (modify) tuples. There are several languages for expressing these operations.

• The schema of a relation refers to its logical design, while an instance of the relation refers to its contents at a point in time. The schema of a database and an instance of a database are similarly defined. The schema of a relation includes its attributes, and optionally the types of the attributes and constraints on the relation such as primary and foreign-key constraints.

• A superkey of a relation is a set of one or more attributes whose values are guaranteed to identify tuples in the relation uniquely. A candidate key is a minimal superkey, that is, a set of attributes that forms a superkey, but none of whose sub- sets is a superkey. One of the candidate keys of a relation is chosen as its primary key.

• A foreign-key constraint from attribute(s) A of relation r1 to the primary-key B of relation r2 states that the value of A for each tuple in r1 must also be the value of B for some tuple in r2. The relation r1 is called the referencing relation, and r2 is called the referenced relation.

• A schema diagram is a pictorial depiction of the schema of a database that shows
the relations in the database, their attributes, and primary keys and foreign keys.

• The relational query languages define a set of operations that operate on tables and output tables as their results. These operations can be combined to get expressions that express desired queries.

• The relational algebra provides a set of operations that take one or more relations as input and return a relation as an output. Practical query languages such as SQL are based on the relational algebra, but they add a number of useful syntactic features.

• The relational algebra defines a set of algebraic operations that operate on tables, and output tables as their results. These operations can be combined to get expressions that express desired queries. The algebra defines the basic operations used within relational query languages like SQL.





Review terms

• Table
• Relation
• Tuple
• Attribute
• Relation instance 
• Domain
• Atomic domain 
• Null value
• Database schema 
• Database instance 
• Relation schema 
• Keys
	° Super key
	° Candidate key
	° Primary key
	° Primary key constraints
• Foreign-key constraint ° Referencing relation ° Referenced relation

• Referential integrity constraint
• Schema diagram
• Query language types
	° Imperative 	
	° Functional 
	° Declarative
• Relational algebra
• Relational-algebra expression
• Relational-algebra operations
	° Select σ
	° Project Π
	° Cartesian product × 
	° Join ⋈
	° Union ∪
° Set difference −
° Set intersection ∩
° Assignment←
° Rename ρ



Employee database (figure 2.17)
employee (person name, street, city)
works (person name, company name, salary) company (company name, city)


Practice Exercises
2.1 Consider the employee database of Figure 2.17. What are the appropriate primary keys?

2.2 Consider the foreign-key constraint from the dept name attribute of instructor to the department relation. Give examples of inserts and deletes to these relations that can cause a violation of the foreign-key constraint.

2.3 Consider the time slot relation. Given that a particular time slot can meet more than once in a week, explain why day and start time are part of the primary key of this relation, while end_time is not.

2.4 In the instance of instructor shown in Figure 2.1, no two instructors have the same name. From this, can we conclude that name can be used as a superkey (or primary key) of instructor?

2.5 What is the result of first performing the Cartesian product of student and advisor, and then performing a selection operation on the result with the predicate s.id = ID? (Using the symbolic notation of relational algebra, this query can be written as σsid=ID(student × advisor).)

2.6 Consider the employee database of Figure 2.17. Give an expression in the relational algebra to express each of the following queries:
	a. Find the name of each employee who lives in city “Miami”.
	b. Find the name of each employee whose salary is greater than $100000.
	c. Find the name of each employee who lives in “Miami” and whose salary is greater than $100000.

2.7 Consider the bank database of Figure 2.18. Give an expression in the relational algebra for each of the following queries:
	a. Find the name of each branch located in “Chicago”.
	b. Find the ID of each borrower who has a loan in branch “Downtown”.



Bank database (Figure 2.18)
	branch(branch_name, branch_city, assets)
	customer (ID, customer_name, customer_street, customer_city)
	loan (loan_number, branch_name, amount) 
	borrower (ID, loan_number)
	account (account_number, branch_name, balance) 
	depositor (ID, account_number)

2.8 Consider the employee database of Figure 2.17. Give an expression in the relational algebra to express each of the following queries:
	a. Find the ID and name of each employee who does not work for “BigBank”.
	b. Find the ID and name of each employee who earns at least as much as every employee in the database.

2.9 The division operator of relational algebra, “÷”, is defined as follows. Let r(R) and s(S) be relations, and let S ⊆ R; that is, every attribute of schema S is also in schema R. Given a tuple t, let t[S] denote the projection of tuple t on the attributes in S. Then r ÷ s is a relation on schema R − S (that is, on the schema containing all attributes of schema R that are not in schema S). A tuple t is in r ÷ s if and only if both of two conditions hold:
	• t is in ΠR−S(r)
	• For every tuple ts in s, there is a tuple tr in r satisfying both of the following:

		a. tr[S] = ts[S] 

		b. tr[R − S] = t
	

		Given the above definition:
		a. Write a relational algebra expression using the division operator to find the IDs of all students who have taken all Comp. Sci. courses. (Hint: project takes to just ID and course id, and generate the set of all Comp. Sci. course ids using a select expression, before doing the division.)

		b. Show how to write the above query in relational algebra, without using division. (By doing so, you would have shown how to define the division operation using the other relational algebra operations.)

2.10 Describe the differences in meaning between the terms relation and relation schema.

2.11 Consider the advisor relation shown in the schema diagram in Figure 2.9, with s id as the primary key of advisor. Suppose a student can have more than one advisor. Then, would s id still be a primary key of the advisor relation? If not, what should the primary key of advisor be?


2.12 Consider the bank database of Figure 2.18. Assume that branch names and cus- tomer names uniquely identify branches and customers, but loans and accounts can be associated with more than one customer.
	a. What are the appropriate primary keys?
	b. Given your choice of primary keys, identify appropriate foreign keys.


2.13 Construct a schema diagram for the bank database of Figure 2.18.

2.14 Consider the employee database of Figure 2.17. Give an expression in the rela- tional algebra to express each of the following queries:
	a. Find the ID and name of each employee who works for “BigBank”.
	b. Find the ID, name, and city of residence of each employee who works for “BigBank”.
	c. Find the ID, name, street address, and city of residence of each employee who works for “BigBank” and earns more than $10000.
	d. Find the ID and name of each employee in this database who lives in the same city as the company for which she or he works.

2.15 Consider the bank database of Figure 2.18. Give an expression in the relational algebra for each of the following queries:
	a. Find each loan number with a loan amount greater than $10000.
	b. Find the ID of each depositor who has an account with a balance greater than $6000.
	c. Find the ID of each depositor who has an account with a balance greater than $6000 at the “Uptown” branch.

2.16 List two reasons why null values might be introduced into a database.

2.17 Discuss the relative merits of imperative, functional, and declarative languages.

2.18 Write the following queries in relational algebra, using the university schema
	a. Find the ID and name of each instructor in the Physics department.
	b. Find the ID and name of each instructor in a department located in the building “Watson”.
	c. Find the ID and name of each student who has taken at least one course in the “Comp. Sci.” department.
	d. Find the ID and name of each student who has taken at least one course section in the year 2018.
	e. Find the ID and name of each student who has not taken any course section in the year 2018.
