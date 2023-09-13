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