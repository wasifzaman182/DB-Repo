# DB-Repo
 
# Lecture 9

# Complete sql in one lecture 

# Note:
		SQL is not DB, is a query language.
		MySQL used client-server model, where client is CLI or frontend (dbever,mysql workbanch) through which we can access MySQL server.
		An attribute can be PK and FK both in a table.
		We can also import/export table schema from files (.csv or json).

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
				

# MANAGING DB (DDL)
	    # Creation of DB
				1. CREATE DATABASE IF NOT EXISTS db-name;
					create database if not exists.
				2. USE db-name; 
					need to execute to choose on which DB CREATE TABLE etc commands will be executed.	
				3. DROP DATABASE IF EXISTS db-name;
					dropping database.
				4. SHOW DATABASES; 
					list all the DBs in the server.
				5. SHOW TABLES; 
					list tables in the selected DB.



# DATA RETRIEVAL LANGUAGE (DRL)
				
				1. Syntax: SELECT <set of column names> FROM <table_name>;
				2. Order of execution from RIGHT to LEFT.
				
				**3. Q. Can we use SELECT keyword without using FROM clause?
				1. Yes, using DUAL Tables.
				2. Dual tables are dummy tables created by MySQL, help users to do certain obvious actions without referring to user defined tables.
				3. e.g., SELECT 55 + 11;
				SELECT now();
				SELECT ucase(); etc.
				
				**4. WHERE
					1. Reduce rows based on given conditions.
					2. E.g., SELECT * FROM customer WHERE age > 18;
				
				**5. BETWEEN
					1. SELECT * FROM customer WHERE age between 0 AND 100;
					2. In the above e.g., 0 and 100 are inclusive.
					
				**6. IN
					1. Reduces OR conditions;
					2. e.g., SELECT * FROM officers WHERE officer_name IN ('Lakshay', ‘Maharana Pratap', ‘Deepika’);
					
				**7. AND/OR/NOT
					1. AND: WHERE cond1 AND cond2
					2. OR: WHERE cond1 OR cond2
					3. NOT: WHERE col_name NOT IN (1,2,3,4);
					
				**8. IS NULL
					1. e.g., SELECT * FROM customer WHERE prime_status is NULL;
					
				**9. Pattern Searching / Wildcard (‘%’, ‘_’)
					1. ‘%’, any number of character from 0 to n. Similar to ‘*’ asterisk in regex.
					2. ‘_’, only one character.
					3. SELECT * FROM customer WHERE name LIKE ‘%p_’;
					
				**10. ORDER BY
					1. Sorting the data retrieved using WHERE clause.
					2. ORDER BY <column-name> DESC;
					3. DESC = Descending and ASC = Ascending
					4. e.g., SELECT * FROM customer ORDER BY name DESC;
					
				**11. GROUP BY
				1. GROUP BY Clause is used to collect data from multiple records and group the result by one or more column. It is generally used in a SELECT statement.
				2. Groups into category based on column given.
				3. SELECT c1, c2, c3 FROM sample_table WHERE cond GROUP BY c1, c2, c3.
				4. All the column names mentioned after SELECT statement shall be repeated in GROUP BY, in order to successfully execute the query.
				5. Used with aggregation functions to perform various actions.
					1. COUNT()
					2. SUM()
					3. AVG()
					4. MIN()
					5. MAX()
					
				**12. DISTINCT
					1. Find distinct values in the table.
					2. SELECT DISTINCT(col_name) FROM table_name;
					3. GROUP BY can also be used for the same
						1. “Select col_name from table GROUP BY col_name;” same output as above DISTINCT query.
						2. SQL is smart enough to realise that if you are using GROUP BY and not using any aggregation function, then you mean “DISTINCT”.
				
				**13. GROUP BY HAVING
					1. Out of the categories made by GROUP BY, we would like to know only particular thing (cond).
					2. Similar to WHERE.
					3. Select COUNT(cust_id), country from customer GROUP BY country HAVING COUNT(cust_id) > 50;
					**4. WHERE vs HAVING
						1. Both have same function of filtering the row base on certain conditions.
						2. WHERE clause is used to filter the rows from the table based on specified condition
						3. HAVING clause is used to filter the rows from the groups based on the specified condition.
						4. HAVING is used after GROUP BY while WHERE is used before GROUP BY clause.
						**5. If you are using HAVING, GROUP BY is necessary.
						**6. WHERE can be used with SELECT, UPDATE & DELETE keywords while GROUP BY used with SELECT.
						

# CONSTRAINTS (DDL)
		# 1. Primary Key
			PK is not null, unique and only one per table.
		
		# 2. Foreign Key
			1. FK refers to PK of other table.
			2. Each relation can having any number of FK.
			3. CREATE TABLE ORDER (
									id INT PRIMARY KEY,
									delivery_date DATE,
									order_placed_date DATE,
									cust_id INT,
									FOREIGN KEY (cust_id) REFERENCES customer(id));
		
		# 3. UNIQUE
			1. Unique, can be null, table can have multiple unique atributes.
			2. CREATE TABLE customer (
						...
						email VARCHAR(1024) UNIQUE,
						...
						);
		# 4. CHECK
			1. CREATE TABLE customer ( CONSTRAINT age_check CHECK (age > 12) );
			2. “age_check”, can also avoid this, MySQL generates name of constraint automatically.
		
		# 5. DEFAULT
			1. Set default value of the column.
			2. CREATE TABLE account ( saving-rate DOUBLE NOT NULL DEFAULT 4.25 );
		
		# 7. ALTER OPERATIONS
			1. Changes schema
			
			# 2. ADD
				1. Add new column.
				2. ALTER TABLE table_name ADD new_col_name datatype ADD new_col_name_2 datatype;
				3. e.g., ALTER TABLE customer ADD age INT NOT NULL;
				
			# 3. MODIFY
				1. Change datatype of an attribute.
				2. ALTER TABLE table-name MODIFY col-name col-datatype;
				3. E.g., VARCHAR TO CHAR
				ALTER TABLE customer MODIFY name CHAR(1024);
				
			# 4. CHANGE COLUMN
				1. Rename column name.
				2. ALTER TABLE table-name CHANGE COLUMN old-col-name new-col-name new-col-datatype;
				3. e.g., ALTER TABLE customer CHANGE COLUMN name customer-name VARCHAR(1024);
				
			# 5. DROP COLUMN
				1. Drop a column completely.
				2. ALTER TABLE table-name DROP COLUMN col-name;
				3. e.g., ALTER TABLE customer DROP COLUMN middle-name;
				
			# 6. RENAME
				1. Rename table name itself.
				2. ALTER TABLE table-name RENAME TO new-table-name;
				3. e.g., ALTER TABLE customer RENAME TO customer-details;

# DATA MANIPULATION LANGUAGE (DML)
		
		# 1. INSERT
			1. INSERT INTO table-name(col1, col2, col3) VALUES (v1, v2, v3), (val1, val2, val3);
		
		# 2. UPDATE
			1. UPDATE table-name SET col1 = 1, col2 = ‘abc’ WHERE id = 1;
			2. Update multiple rows e.g.,
				1. UPDATE student SET standard = standard + 1;
			# 3. ON UPDATE CASCADE
			1. Can be added to the table while creating constraints. Suppose there is a situation where we have two tables such that primary key of one table is the foreign 
			   key for another table. if we update the primary key of the first table then using the ON UPDATE CASCADE foreign key of the second table automatically get updated.
			   
		# 3. DELETE
			1. DELETE FROM table-name WHERE id = 1;
			2. DELETE FROM table-name; //all rows will be deleted.
			
			3. **DELETE CASCADE** - (to overcome DELETE constraint of Referential constraints)
				1. What would happen to child entry if parent table’s entry is deleted?
				2. CREATE TABLE ORDER (
				order_id int PRIMARY KEY,
				delivery_date DATE,
				cust_id INT,
				FOREIGN KEY(cust_id) REFERENCES customer(id) ON DELETE CASCADE );
				
				3. **ON DELETE NULL** - (can FK have null values?)
				1. CREATE TABLE ORDER (
					order_id int PRIMARY KEY,
					delivery_date DATE,
					cust_id INT,
					FOREIGN KEY(cust_id) REFERENCES customer(id) ON DELETE SET NULL
				);
				
		# 4. REPLACE
			1. Primarily used for already present tuple in a table.
			2. As UPDATE, using REPLACE with the help of WHERE clause in PK, then that row will be replaced.
			3. As INSERT, if there is no duplicate data new tuple will be inserted.
			4. REPLACE INTO student (id, class) VALUES(4, 3);
			5. REPLACE INTO table SET col1 = val1, col2 = val2;
		

# JOINING TABLES
	
		1. All RDBMS are relational in nature, we refer to other tables to get meaningful outcomes.
		2. FK are used to do reference to other table.
		
		# 3. INNER JOIN
			1. Returns a resultant table that has matching values from both the tables or all the tables.
			2. SELECT column-list FROM table1 INNER JOIN table2 ON condition1 INNER JOIN table3 ON condition2 ...;
			3. Alias in MySQL (AS)
				1. Aliases in MySQL is used to give a temporary name to a table or a column in a table for the purpose of a particular query. It works as a nickname for 
				   expressing the tables or column names. It makes the query short and neat.
				2. SELECT col_name AS alias_name FROM table_name;
				3. SELECT col_name1, col_name2,... FROM table_name AS alias_name;
				
		# 4. OUTER JOIN
			
			# 1. LEFT JOIN
				1. This returns a resulting table that all the data from left table and the matched data from the right table.
				2. SELECT columns FROM table LEFT JOIN table2 ON Join_Condition;
				
           # 2. RIGHT JOIN
				1. This returns a resulting table that all the data from right table and the matched data from the left table.
				2. SELECT columns FROM table RIGHT JOIN table2 ON join_cond;
				
		   # 3. FULL JOIN
				1. This returns a resulting table that contains all data when there is a match on left or right table data.
				2. Emulated in MySQL using LEFT and RIGHT JOIN.
				3. LEFT JOIN UNION RIGHT JOIN.
				4. SELECT columns FROM table1 as t1 LEFT JOIN table2 as t2 ON t1.id = t2.id
					UNION
					SELECT columns FROM table1 as t1 RIGHT JOIN table2 as t2 ON t1.id = t2.id;
				5. UNION ALL, can also be used this will duplicate values as well while UNION gives unique values.
				
		# 5. CROSS JOIN
				1. This returns all the cartesian products of the data present in both tables. Hence, all possible variations are reflected in the output.
				2. Used rarely in practical purpose.
				3. Table-1 has 10 rows and table-2 has 5, then resultant would have 50 rows.
				4. SELECT column-lists FROM table1 CROSS JOIN table2;
				
		# 6. SELF JOIN
				1. It is used to get the output from a particular table when the same table is joined to itself.
				2. Used very less.
				3. Emulated using INNER JOIN.
				4. SELECT columns FROM table as t1 INNER JOIN table as t2 ON t1.id = t2.id;
				
		# 7. Join without using join keywords.
				1. SELECT * FROM table1, table2 WHERE condition;
				2. e.g., SELECT artist_name, album_name, year_recordedFROM artist, albumWHERE artist.id = album.artist_id;
		

# SET OPERATIONS
	1. Used to combine multiple select statements.
	2. Always gives distinct rows.

	| Aspect                |                     JOIN                              	   			|       SET                             									 |
	|-----------------------|-----------------------------------------------------------------------|----------------------------------------------------------------------------|
	| Purpose               | Combines rows from multiple tables based on related columns. 			| Manipulates the results of SELECT queries. 								 |
	| Operation             | Retrieves data from multiple tables in a single query.       			| Operates on the result sets of SELECT queries.							 |
	| Types of Operations   | INNER JOIN, LEFT JOIN, RIGHT JOIN, FULL OUTER JOIN, CROSS JOIN, etc.  | UNION (UNION ALL), INTERSECT, EXCEPT (MINUS) 								 |
	| Result Set            | Combines columns from related tables into a single result set. 		| Combines, intersects, or finds differences between result sets.			 |
	| Usage                 | Used to consolidate data from related tables. 						| Used for combining, intersecting, or finding differences in query results. |
	| Common Scenario       | Retrieve data from a customer and order table to display customer     | Combine the results of two SELECT queries to get a complete list of        |
	|						| information along with their orders. 									|  employees from two departments											 |
	| Examples              | ```sql SELECT * FROM Customers JOIN Orders ON Customers.CustomerID 	| ```sql SELECT * FROM Employees WHERE Salary > 50000 UNION SELECT * FROM    |
	|						|	= Orders.CustomerID; ``` 											|  Contractors WHERE Rate > 50; ``` 										 |
	|-----------------------|-----------------------------------------------------------------------|----------------------------------------------------------------------------|

	
	# 3. UNION
		1. Combines two or more SELECT statements.
		2. SELECT * FROM table1 **UNION** SELECT * FROM table2;
		3. Number of column, order of column must be same for table1 and table2.
		
	# 4. INTERSECT
		1. Returns common values of the tables.
		2. Emulated.
		3. SELECT DISTINCT column-list FROM table-1 INNER JOIN table-2 USING(join_cond);
		4. SELECT DISTINCT * FROM table1 INNER JOIN table2 ON USING(id);
		
	# 5. MINUS
		1. This operator returns the distinct row from the first table that does not occur in the second table.
		2. Emulated.
		3. SELECT column_list FROM table1 LEFT JOIN table2 ON condition WHERE table2.column_name IS NULL;
		4. e.g., SELECT id FROM table-1 LEFT JOIN table-2 USING(id) WHERE table-2.id IS NULL;


# SUB QUERIES
		1. Outer query depends on inner query.
		2. Alternative to joins.
		3. Nested queries.
		4. SELECT column_list (s) FROM table_name WHERE column_name OPERATOR (SELECT column_list (s) FROM table_name [WHERE]);
		5. e.g., SELECT * FROM table1 WHERE col1 IN (SELECT col1 FROM table1);
		**6. Sub queries exist mainly in 3 clauses
			1. Inside a WHERE clause.
			2. Inside a FROM clause.
			3. Inside a SELECT clause.
		
		**7. Subquery using FROM clause
			1. SELECT MAX(rating) FROM (SELECT * FROM movie WHERE country = ‘India’) as temp;

		**8. Subquery using SELECT
			1. SELECT (SELECT column_list(s) FROM T_name WHERE condition), columnList(s) FROM T2_name WHERE Condition;
		
		**9. Derived Subquery
			1. SELECT columnLists(s) FROM (SELECT columnLists(s) FROM table_name WHERE [condition]) as new_table_name;
		**10. Co-related sub-queries
			1. With a normal nested subquery, the inner SELECT query runs first and executes once, returning values to be used by the main query. A correlated subquery,
    		   however, executes once for each candidate row considered by the outer query. In other words, the inner query is driven by the outer query.


#JOIN VS SUB-QUERIES

		|---------------------------- join --------------------------------| ------------------------- Sub queries -------------------------------|
		| 			Faster 												   | 							Slower									  |
		| Joins maximise calculation burden on DBMS                        | Keeps responsibility of calculation on user.						  |
		| Complex, difficult to understand and implement                   | Comparatively easy to understand and implement.                      |
		| Choosing optimal join for optimal use case is difficult          | Easy.                                                                |
		|------------------------------------------------------------------|----------------------------------------------------------------------|


# MySQL VIEWS
		1. A view is a database object that has no values. Its contents are based on the base table. It contains rows and columns similar to the real table.
		2. In MySQL, the View is a virtual table created by a query by joining one or more tables. It is operated similarly to the base table but does not contain any data of its own.
		3. The View and table have one main difference that the views are definitions built on top of other tables (or views). If any changes occur in the underlying table, the same changes reflected in the View also.
		4. CREATE VIEW view_name AS SELECT columns FROM tables [WHERE conditions];
		5. ALTER VIEW view_name AS SELECT columns FROM table WHERE conditions;
		6. DROP VIEW IF EXISTS view_name;
		7. CREATE VIEW Trainer AS SELECT c.course_name, c.trainer, t.email FROM courses c, contact t WHERE c.id = t.id; (View using Join clause).