Chapter 2

1. Structure of relational database
- 

2. Database schema 
- logical design of the database 

3. Keys 
- four types of keys 
	- super
		- a set of one or more attribute that, taken collectively, uniquely identify a tuple in the relation 
		- in the Instructor (ID) can be useed as asuper key but if you wanted to combine more than just the ID youcan
		- you want to make sure that the super key will be able to distinguish that row from every other row
		- if the key choosen for superkey matches more than one row then that would not be the super key
	- primary 
		- a canidate key that is choosen 
		- in the instructor 
	- candidate  
		- super key for which no proper subset is a superkey (minimal superkey) one relation can have several candidate key
		- in the Instructor (ID) is the only key that is a canidate key
		- 

	- foreign 
