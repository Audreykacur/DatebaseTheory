Chapter 2

Jan 24th

1. Structure of relational database
- 

2. Database schema 
- logical design of the database 

3. Keys 
- four types of keys 
	- super
		- a set of one or more attribute that, taken collectively, uniquely identify a tuple in the relation 
		- in the Instructor (ID) can be used as a super key but if you wanted to combine more than just the ID youcan
		- you want to make sure that the super key will be able to distinguish that row from every other row
		- if the key chosen for super key matches more than one row then that would not be the super key
	- primary 
		- a candidate key that is chosen 
		- in the instructor 
	- candidate  
		- super key for which no proper subset is a super key (minimal super key) one relation can have several candidate key
		- in the Instructor (ID) is the only key that is a candidate key
		- 

	- foreign 
		- Try to understand this from the book
		- the foreign key is relating one attribute to another attribute 


Jan 26th 

Schema Diagram 

relational query language

functions
- Imperative
- Functional
- Declarative

pure languages
- relational algebra 
	- set of operations that take one or two relations as input and produces a new relation as a result 
	- output of one operation can be the input of another operation 
	- 

The select operation 
-  σ dept_name = "Physics" (instructor)
	- result is a table of the instructors in the physics department 


































