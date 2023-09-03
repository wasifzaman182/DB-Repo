# DB-Repo
 
#Lecture 3
#you can find ER symbols as lecture2(ER symbols)

#Data Model
		 --> collection of conceptual tools for describing data. data relationship, data semantics and data consistency constraints.

#ER (Entity Relationship)
		--> it is a high level data model based on a perception of a real world that consists of basic objects, called entities and relationship among these objects.
		--> Graphical representation of real world data is called entities relationship (ER).


#Entity:
	  --> An Entitiy is a "thing" or "object" in the real world that is distinguishable from all other objects.
		**1) it has physical existance
		**2) Each student in a collage is an entity
		**3) Entity can be uniquely identified (by primary key)
		**4) 



#Entity Set
	  --> it is a set of entities of the same type that share same properties, or attributes.
	  --> e.g Student is an entity set.
	  --> e.g customer of a bank.


#Attributes
	  --> properties of an entity is call attributes.
	  --> attributes is also know as field, column 


	1. **Data Type**: Each attribute has a data type that defines the kind of data it can store. Common data types include integers, text, dates, and floating-point numbers.

	2. **Nullability**: Attributes may or may not allow null values, depending on their definition. An attribute that allows null values can have missing or undefined data for
						certain records.

	3. **Constraints**: Attributes can have constraints applied to them to enforce data integrity rules. Common constraints include primary keys, foreign keys, unique constraints, 
	                    and check constraints.

	4. **Attribute Names**: Attribute names should be meaningful and descriptive to help users understand the data they represent. For example, in a "Customers" table, 
	                        attributes might include "CustomerID," "FirstName," "LastName," "Email," and so on.

	5. **Domains**: Attributes are associated with domains, which define the set of valid values that an attribute can have. For instance, an attribute for "Age" might have a 
	                domain that restricts values to positive integers.

	6. **Composite Attributes**: In some cases, an attribute can be composed of sub-attributes. For example, an attribute for "Address" may consist of sub-attributes 
	                             like "Street," "City," "State," and "PostalCode."

	7. **Derived Attributes**: Some attributes can be derived from other attributes in the database. For instance, an attribute for "TotalPrice" in an order table can be 
	                           derived by multiplying the "Quantity" attribute by the "UnitPrice" attribute.

	8. **Multivalued Attributes**: Certain attributes can hold multiple values for a single entity. For instance, an attribute for "PhoneNumbers" in a "Contact" 
	                               table might contain multiple phone numbers for one person.

	9. **Key Attributes**: Key attributes are attributes that are part of the primary key or candidate keys of a table. They are used to uniquely identify records within the table.

#**Note will add pics of symbols related to attributes**.


#Relationship
	 --> Association between two or more entities
	 --> e.g customer has account, student has course, customer borrow loan etc.
	
	**Types of relationship
		**1) Strong relationship**
				--> A strong relationship is a type of association between two entities where the child entity (also known as the dependent or subordinate entity) is fully 
				    dependent on the parent entity (also known as the independent or owning entity).
				--> In a strong relationship, the child entity's existence is dependent on the parent entity, meaning that the child entity cannot exist without a corresponding 
				    parent entity.
				--> Strong relationships are typically represented by a solid connecting line between the parent and child entities in an ER diagram.
				
				**Example of a Strong Relationship:
                      Consider the relationship between a "Department" entity and an "Employee" entity in an organization's database. Each employee is assigned to a specific
					  department, and an employee cannot exist in the database without being associated with a department. This is a strong relationship.
					  
					 **Library Table

					**LibraryID**	 LibraryName
					1				Main Library
					2				Branch A
					3				Branch B

					 **Book Table

					BookID	Title	**LibraryID**
					101		Book 1	1
					102		Book 2	1
					103		Book 3	2
					104		Book 4	3
				
	**These relationships are often enforced by a foreign key constraint in a relational database, ensuring that the child entity is associated with a valid parent entity.

		**2) Week Relationship  **
				--> A weak relationship is a type of association between two entities where the child entity (weak entity) is not fully dependent on the parent entity 
					(strong entity). In other words, the child entity can exist independently but is often associated with the parent entity.
				--> Weak relationships are used when the child entity does not have a primary key attribute that uniquely identifies its records. Instead, it relies on a 
				    partial key, which is an attribute that, in combination with the parent entity, forms a unique identifier.
					
				**Example of a Weak Relationship:
						Consider a database for tracking invoices. Each invoice may have multiple line items, and each line item is associated with a specific invoice. 
						However, line items do not have a unique identifier on their own but depend on the combination of the invoice number and a line item number. 
						This is a weak relationship, with "Line Item" as the weak entity and "Invoice" as the strong entity.
					
					**Invoice Table
					InvoiceNumber	Date
					INV-001			2023-01-15
					INV-002			2023-01-20
					
					**Line Item Table
					InvoiceNumber	LineItemNumber	Product 	Quantity	Price
					INV-001				1			Product A		3		10.00
					INV-001				2			Product B		2		15.00
					INV-002				1			Product C		5		8.00
					INV-002				2			Product D		1		20.00
					
				**In an ER diagram, weak relationships are typically represented by a dashed connecting line between the parent and child entities, and the child entity may 
				**have a double rectangle border to indicate its weakness.


#Degree of relationships
		** 3 types of relationship
		
		**1) Unary Relationship (Degree 1):
				--> A unary relationship involves a single entity or entity set. In other words, it's a relationship where an entity relates to itself.
				Example: In an organizational hierarchy, an "Employee" entity might have a unary relationship with itself to represent the "Manager" or "Supervisor" relationship.

		**2) Binary Relationship (Degree 2):
				--> A binary relationship involves two distinct entities or entity sets. It's the most common type of relationship in ER modeling.
					Example: The relationship between "Customer" and "Order" is a binary relationship because each customer can place multiple orders, and each order is
					associated with a single customer.

		**3) Ternary Relationship (Degree 3):
				--> A ternary relationship involves three entities or entity sets. It represents a more complex relationship where three entities are interconnected.
				Example: In a university database, a ternary relationship might exist among "Student," "Course," and "Professor" entities to represent which students are 
						enrolled in which courses taught by which professors.


#Mapping Cardinality
		** 4 types of Cardinality
		**1) One-to-One (1:1) Relationship:
				--> In a one-to-one relationship, one record in the first entity is associated with only one record in the second entity, and vice versa.
				-->	This type of relationship is relatively rare in database design and is typically used when there is a strong reason to separate certain attributes into a 
					separate entity.
				** Example: An employee may have only one office, and each office is assigned to only one employee.
				
		**2) One-to-Many (1:N) Relationship:
				--> In a one-to-many relationship, one record in the first entity is associated with zero, one, or many records in the second entity, but each record in the 
					second entity is associated with only one record in the first entity.
				--> This is the most common type of relationship in database design.
				** Example: A customer can place multiple orders, but each order is placed by only one customer.
				
		**3) Many-to-One (N:1) Relationship:
				--> A many-to-one relationship is essentially the reverse of a one-to-many relationship. It means that many records in the first entity are associated with one 
					record in the second entity.
				** Example: Multiple students may belong to the same class, but each class is taught by one teacher.
				
		**4) Many-to-Many (M:N) Relationship:
				--> In a many-to-many relationship, multiple records in the first entity can be associated with multiple records in the second entity, and vice versa.
				--> This type of relationship typically requires the introduction of an intermediate or junction table (also known as an associative entity) to resolve the 
					many-to-many relationship.
				** Example: Students can enroll in multiple courses, and each course can have multiple students. An intermediate table, such as "Enrollment," is used to link 
				**   students and courses.


#Participation constraints 
			--> In ER modeling define whether the participation of entities in a relationship is mandatory or optional.
			** There are two main types of participation constraints
			
			**1) Mandatory Participation (Total Participation):
					--> In a relationship with mandatory participation, every entity in the relationship is required to participate. This means that there must 
						be at least one occurrence of each participating entity for each instance of the relationship.
					--> Mandatory participation is often represented by a solid line connecting the entity to the relationship in an ER diagram.
					**Example: In a "Department" and "Employee" relationship, if the participation of employees in departments is mandatory, it means that 
								**every employee must belong to a department. There cannot be employees without a department.

			**2) Optional Participation (Partial Participation):
					--> In a relationship with optional participation, entities may choose to participate in the relationship, but it is not mandatory. 
						Some entities may be related, while others may not be.
					--> Optional participation is often represented by a dashed or dotted line connecting the entity to the relationship in an ER diagram.
					**Example: In a "Customer" and "Order" relationship, if the participation of customers in orders is optional, it means that a customer 
								** can place an order, but there can also be customers who have not placed any orders.

