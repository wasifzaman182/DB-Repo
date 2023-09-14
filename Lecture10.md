# DB-Repo
 
# Lecture 10

# Normalization
		Normalization is a step towards DB optimization.


# Functional Dependency 
		--> A functional dependency is a constraint that describes the relationship between two sets of attributes (columns) within a table.
		--> It specifies how the values in one set of attributes determine the values in another set of attributes.
		--> Functional dependencies are essential for maintaining the integrity of data in a relational database and for helping to design tables that minimize data redundancy 
			and anomalies.

   # Types of Functional Dependency (FD)
		# 1)Trivial FD
			-->	it's a dependency that is so obvious that it doesn't provide any new information. 
			--> A trivial functional dependency can be expressed as A → A, where A is an attribute (or a set of attributes).
			--> Essentially, this means that an attribute is functionally dependent on itself, which is not very useful in practice.
			
			**Example of a trivial functional dependency:
				--> If you have an attribute StudentID, it is trivially functionally dependent on itself: StudentID → StudentID. 
		
		# 2)Non-Trivial FD
			--> A non-trivial functional dependency is one that provides new and meaningful information about the relationships between attributes in a table.
			--> It implies that one set of attributes determines another set of attributes, and this dependency is not self-evident.

			**Example of a non-trivial functional dependency:
				--> In a table with attributes EmployeeID and EmployeeName, the functional dependency EmployeeID → EmployeeName is non-trivial. 
					It tells us that for a given EmployeeID, we can determine the corresponding EmployeeName, which is valuable information.
		
		# 3)Rules of FD (Armstrong’s axioms)
			# 1. Reflexive
					1. If ‘A’ is a set of attributes and ‘B’ is a subset of ‘A’. Then, A→ B holds.
					2. If A subset B then A → B.
			
			# 2. Augmentation
					1. If B can be determined from A, then adding an attribute to this functional dependency won’t change anything.
					2. If A→ B holds, then AX→ BX holds too. ‘X’ being a set of attributes.
			
			# 3.Transitive
					--> A transitive dependency in a relational database occurs when one attribute's value is functionally dependent on another attribute through a 
						third attribute. Let's illustrate this with a simple example:
					
						Here's a sample table:

						| StudentID | CourseID | Instructor  |
						|-----------|----------|-------------|
						| 101       | Math101  | Dr. Smith   |
						| 102       | Math101  | Dr. Smith   |
						| 103       | Bio101   | Prof. Jones |
						| 104       | Chem101  | Dr. White   |

					--> In this table, `StudentID` represents the student's ID, `CourseID` represents the course's ID, and `Instructor` represents the instructor's name for that 
						course.

					Now, let's define some functional dependencies:

					1. `StudentID → CourseID`: Each student is enrolled in a specific course, so the `CourseID` is functionally dependent on the `StudentID`.

					2. `CourseID → Instructor`: Each course is taught by a specific instructor, so the `Instructor` is functionally dependent on the `CourseID`.

					Now, let's identify a transitive dependency:

					- `StudentID → CourseID` (Already established).
					- `CourseID → Instructor` (Already established).

					From these two dependencies, we can infer a transitive dependency:

					- `StudentID → Instructor`

					--> In other words, a student's ID (e.g., `StudentID 101`) determines the instructor (e.g., `Dr. Smith`) indirectly through the course they are 
						enrolled in (e.g., `Math101`). This is an example of a transitive dependency because it relies on two functional dependencies to derive a third.
						If we know the `StudentID`, we can determine the `Instructor` without directly having that information in the table.

	** Transitive dependencies can sometimes lead to data anomalies and redundancy in a database, which is why they are typically eliminated through the process of normalization. 


# Why Normalisation?
		1. Normalization is the process of organizing data in a database to reduce redundancy and improve data integrity.
		2. It is a systematic approach to breaking down tables into smaller, more manageable tables and defining the relationships between them.
	
	**There are several reasons why normalization is important:
	  #	1. Reduced redundancy: 
			Normalization reduces the amount of duplicate data in the database. This frees up space and improves performance.

	  # 2. Improved data integrity:
			Normalization helps to ensure that the data in the database is accurate and consistent. This is because each piece of data is stored in only 
			one place, so there is no chance of it being accidentally deleted or changed.
			
	  # 3. Easier data management:
			Normalization makes it easier to update, delete, and retrieve data from the database. This is because the data is organized in a logical way.

	  # 4.	More flexibility: 
			Normalization makes the database more flexible to changes in data requirements. This is because the data is not tightly coupled together, 
			so it can be easily modified without affecting other parts of the database.


	
	# Anomalies that can occur in a database if it is not normalized
	  #	1. Insertion anomaly: 
			1. This occurs when you cannot insert a new row into the table because some of the required data is missing. 
			2. This can happen if the table contains duplicate data.
		** For example, 
			a table of employees may have a column for the employee's department. If you try to insert a new row for an employee who has not yet been 
			assigned a department, the row will not be able to be inserted.
	  
	  # 2. Deletion anomaly: 
			1. This occurs when you delete a row from the table, and some of the remaining data becomes meaningless. 
			2. This can happen if the table contains transitive dependencies.
		** For example, 
			a table of employees may have a column for the employee's manager. If you delete a row for an employee, the manager column for the 
			remaining employees will become meaningless.

	  # 3. Update anomaly: 
			1. This occurs when you update a value in one row, and the same value in another row is not updated. 
			2. This can happen if the table contains partial dependencies.
		** For example, 
			a table of employees may have a column for the employee's salary. If you update the salary for one employee, the salary for the 
			remaining employees will not be updated.


# What is Normalisation?
	1. Normalization is the process of organizing data in a database to reduce redundancy and improve data integrity. 
	2. It is a systematic approach to breaking down tables into smaller, more manageable tables and defining the relationships between them.

	# Types of Normal forms
		# 1. 1NF
			1. A table is in 1NF if all of its columns contain atomic values, meaning that they cannot be broken down into smaller pieces.
			**For example, 
			  A column of names should not contain a first name and a last name in the same cell.

		# 2. 2NF
			1. The table must be in 1NF, and all non-key attributes must be fully functionally dependent on the primary key.
			
			| ID| NAME     	 | ADDRESS        |
			|---|------------|----------------|
			| 1 | John Doe 	 | 123 Main Street|
			| 2 | Jane Doe 	 | 456 Elm Street |
			| 3 | Mary Smith | 789 Oak Street |
			
			2. This table is in 2NF because all of the non-key attributes (NAME and ADDRESS) are fully functionally dependent on the primary key (ID). 
			3. This means that the NAME and ADDRESS columns cannot be determined by any other column in the table.

			**Here is an example of a table that is not in 2NF:

			| ID      | NAME       | ADDRESS         | DEPT        |
			|---------|------------|-----------------|-------------|
			| 1       | John Doe   | 123 Main Street | Sales       |
			| 2       | Jane Doe   | 456 Elm Street  | Marketing   |
			| 3       | Mary Smith | 789 Oak Street  | Engineering |
			
			4. This table is not in 2NF because the DEPT column is not fully functionally dependent on the primary key (ID). 
			5. The DEPT column can be determined by the NAME column, even if the ID column is not unique.

			To put this table in 2NF, we would need to decompose it into two tables:

			| ID| NAME       |dep_Id |
			|---|------------|-------|
			| 1 | John Doe   |1      |
			| 2 | Jane Doe   |2      |
			| 3 | Mary Smith |3      |
			
			
			| ID| DEPT        |
			|---|-------------|
			| 1 | Sales       |
			| 2 | Marketing   |
			| 3 | Engineering |
	
		
		# 3. 3NF
		     1. A table is in 3NF if it is in 2NF and there are no transitive dependencies.
    		 2. A transitive dependency is a dependency between two columns where the second column depends on the first column, but the second column 
			    does not directly depend on the primary key.
				
			| Customer ID| Name 	  | Address         | City    | State |
			|------------|------------|-----------------|---------|-------|
			| 1 		 | John Doe   | 123 Main Street | Anytown | CA    |
			| 2 		 | Jane Doe   | 456 Elm Street  | Anytown | CA    |
			| 3          | Mary Smith | 789 Oak Street  | Anytown | CA    |
		
			3. This table is in 3NF because there are no transitive dependencies. A transitive dependency is a dependency between two columns where the 
			   second column depends on the first column, but the second column does not directly depend on the primary key.
			 
			**Here is an example of a table that is not in 3NF:

			| Customer ID | Name       | Address         | City    | State | Department  |
			|-------------|------------|-----------------|---------|-------|-------------|
			| 1           | John Doe   | 123 Main Street | Anytown | CA    | Sales       |
			| 2           | Jane Doe   | 456 Elm Street  | Anytown | CA    | Marketing   |
			| 3           | Mary Smith | 789 Oak Street  | Anytown | CA    | Engineering |
			
			4. This table is not in 3NF because the DEPARTMENT column is transitively dependent on the PRIMARY KEY (CUSTOMER ID). 
			   The DEPARTMENT column depends on the CITY column, which in turn depends on the CUSTOMER ID column.
			  
			**To put this table in 3NF, we would need to decompose it into two tables:
			customer:
			
			| Customer ID | Name       | Address        | cust_detail_id|
			|-------------|------------|----------------|---------------|
			| 1           | John Doe   | 123 Main Street| 1             |
			| 2           | Jane Doe   | 456 Elm Street | 1             |
			| 3           | Mary Smith | 789 Oak Street | 1             |
			
			Customer Details:
			
			| id | City      | Department  |
			|----|-----------|-------------|
			| 1  | Karachi   | Sales       |
			| 2  | Islamabad | Marketing   |
			| 3  | Lahore    | Engineering |

		The first table is in 3NF because there are no transitive dependencies. The second table is in 3NF because there are no transitive dependencies.

	# 4. BCNF (Boyce-Codd normal form)
		 1. Relation must be in 3NF.
		 2. A table is in BCNF if it is in 3NF and there are no partial dependencies. 
		 3. A partial dependency is a dependency between two columns where the second column depends on only part of the primary key.
		 
		 **Here is an example of a table that is not in BCNF:

		| Student ID | Name       | Department       | Major                |
		|------------|------------|------------------|----------------------|
		| 1          | John Doe   | Computer Science | Computer Engineering |
		| 2          | Jane Doe   | Biology          | Microbiology         |
		| 3          | Mary Smith | Physics          | Physics Education    |
		
		4. This table is not in BCNF because the MAJOR column is partially dependent on the DEPARTMENT column. 
		   The MAJOR column depends on the first two characters of the DEPARTMENT column, but not on the entire DEPARTMENT column.

        **To put this table in BCNF, we would need to decompose it into two tables:
		
		Student Table:
		
		| Student ID | Name 	 | dept_id|
		|------------|-----------|--------|
		| 1          | John Doe  | 1      |
		| 2 		 | Jane Doe  | 2      |
		| 3 		 | Mary Smith| 1      |
		
		Department Details Table:
	
		|id | Department 	   | Major                |
		|---|------------------|----------------------|
		|1	| Computer Science | Computer Engineering |
		|2  | Biology 		   | Microbiology         |
		|3  | Physics          | Physics Education    |
	
	The first table is in BCNF because there are no partial dependencies. The second table is in BCNF because there are no partial dependencies.

