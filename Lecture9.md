# DB-Repo
 
# Lecture 9

# Complete sql in one lecture 

# Note:
		SQL is not DB, is a query language.
		MySQL used client-server model, where client is CLI or frontend (dbever,mysql workbanch) through which we can access MySQL server.

# SQL :
	 Structured Query Language, used to access and manipulate data.
	 SQL used CRUD operations to communicate with DB.
		# 1. CREATE 
				execute INSERT statements to insert new tuple/record into the relation/table.
		# 2. READ 
				Read data already in the relations/tables.
		# 3. UPDATE 
				Modify already inserted data/record in the relation/table.
		# 4. DELETE 
				Delete specific data point/tuple/row or multiple rows from a table/relation.


# Difference between SQL and MySQL
	sql is structured query language used to perform sql CRUD operations at relational DB while MySQL is a software, through which we can manage, manipulate
	store data.

# SQL DataTypes
	Certainly, here's a table that summarizes some common data types used in databases:

	| Data Type                   | Description                                  | Example Values           |
	|-----------------------------|----------------------------------------------|--------------------------|
	| INTEGER (INT)               | Whole numbers without decimal points.        | 1, -42, 1000             |
	| DECIMAL or NUMERIC          | Fixed-point numbers with precise decimals.   | 3.14, -0.001, 123.456    |
	| FLOAT or REAL or DOUBLE     | Approximate numeric values with flexibility. | 3.14, -0.001, 123.456789 |
	| CHAR                        | Fixed-length character strings.              | "John", "Database"       |
	| VARCHAR                     | Variable-length character strings.           | "123 Main St"            |
	| DATE                        | Date values only.                            | "2023-09-01"             |
	| TIME                        | Time values only.                            | "14:30:00"               |
	| DATETIME or TIMESTAMP       | Date and time values.                        | "2023-09-01 14:30:00"    |
	| BOOLEAN (BOOL or BOOLEAN)   | True or false values.                        | true, false, 1, 0        |
	| BLOB (Binary Large Object)  | Binary data, such as images or documents.    | Binary data              |
	| TEXT or CLOB or VARCHAR(MAX)| Large text values.                           | Long paragraphs of text  |
	| ENUM                        | A list of predefined values.                 | "Red", "Green", "Blue"   |
	|-----------------------------|----------------------------------------------|--------------------------|	
	

# Types of SQL commands:
		
		# Data Definition Language (DDL) Commands
			defining relation schema.
			
			1) CREATE TABLE: 
				Creates a new table.
			2) ALTER TABLE: 
				Modifies an existing table structure.
			3) DROP TABLE: 
				Deletes an existing table and its data.
			4) CREATE INDEX:
				Creates an index on one or more columns.
			5) DROP INDEX: 
				Deletes an index.
				
		# DRL/DQL (data retrieval language / data query language)
			retrieve data from the tables.
			
			1) SELECT
			    Retrieves data from one or more tables.
			2) FROM
				Specifies the table(s) from which to retrieve data.
			3) WHERE
				Filters rows based on specified conditions.
			4) GROUP BY
				Groups rows into summary rows.
			5) HAVING 
				Filters grouped rows based on specified conditions.
			6) ORDER BY 
			    Sorts the result set based on specified columns and sorting directions.
		
		# DML (data modification language)
			use to perform modifications in the DB
			
			1) INSERT: insert data into a relation
			2) UPDATE: update relation data.
			3) DELETE: delete row(s) from the relation.
		
		# DCL (Data Control language)
			grant or revoke authorities from user.
			
			1) GRANT: access privileges to the DB
			2) REVOKE: revoke user access privileges.
		
		# TCL (Transaction control language)
			to manage transactions done in the DB
			
			1) START TRANSACTION
				begin a transaction
			2) COMMIT
				apply all the changes and end transaction
			3) ROLLBACK
				discard changes and end transaction
			4) SAVEPOINT
				checkout within the group of transactions in which to rollback.