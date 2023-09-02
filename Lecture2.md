# DB-Repo
 
#Lecture 2

#Abstraction:
			--> The important concept in DBMS where we only show those information which is related, reset will be hidden from user is called abstraction.
			1. e.g  when you visit an atm you can only see relevent information like withdraw, amount, check balance etc, but you don't know how it workds behind the 
			scen and that is non of your bussiness.
			2. e.g we store all data in single db but when one of company department want to access data we only show related information like logistics department
			need name, phone number and address of a person not other then that, is called Abstraction.
	##Note 
			Abstraction can be achive by using view 

**Abstraction can be achive by implementing 3 layer achitecture 
		
		**1) Physical level	
					. The lowest level of Abstraction describe how data is stored
					. data is stored in bytes/bit form
					. Talk about storae allocation, data compression, and encryption
					. We must define algorithms that allows to retive data efficintly 
		
		**2) Logical / conceptual level
					. How data should be represented in tabuler form in database, after converting Physical view 
					. A user at logical view does not have any concern with Phisical view.
					. DBA (Database administration) who must decide what information should keep in the database
					. ease to use.
					
		**3) External / view level
					. Highest level of Abstraction aims to provide only relevent data to end user.
					. At external level, a database contains severl schems. schems is nothing but design.
					. At external level their are different level of security mechanism to prevent user from accessing certain parts of schema of DB.


# Instances
			. The data store at a particular moment in the db is called instance of database. 
			. we can also say, how many records we have in the db at the moment.

#Schema			
	. overall design of the db is called schema.
	. there are 3 types of schema 1) Physical schema 2) Logical schema and 3) External schema
	. schema is the structural description of data. mean how should be data look like, it doesn't change frequently.
	. DB schema corresponds to the variable declerations along with datatypes in a program.
	. definition of consistency constraints like a field should not be empty, only accept integer value, only accept date time etc.
	

#Data Models:
	. data model is used to define how will be the Logical level schema look like.mean data type, consistency constraints, data relationship
	. which type of relation we need to use.
	. e.g ER model, Relational model, object-oriented model and object-relational model. (we will discuss in up coming chapter)

#Database Languagues:
		There are 3 types of database languages
		**1) DDL
				. Stand for Data definition language 
				. to define the database schema
				. specifiy constraints on attributes which must be check when db is updating.
		**2) DML
				. Stand for data manipulation language
				**Data manipulation involves
				           . Retrieval of stored information in db.
						   . insertion into db.
						   . add into db.
						   . update a record in db.
						   . delete a record from db
		**3) QLM
				. Stand for query language model
				. a part of DML to specifiy statment requesting the Retrieval of information
				.e.g select * from customer.


#Database Administrator (DBA)
		. A person who has central control of both the data and the programs that access those data.
		. Responsibilities of DBA	
					. Schema definition
					. Stroage structure and access method.
					. schema and physical organization modifications
					. Authorization control.
					. Routine maintance
							. Preodic backup
							. Security patches.
							. Any upgards
			
