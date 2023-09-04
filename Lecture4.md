# DB-Repo
 
#Lecture 4
#for visal view and example please find the the lec4visual file of codeHelp.which is related to lecture 4

# Extended ER Features
				--> Basic ER Features studied in the LEC-3, can be used to model most DB features but when complexity increases, it is better to 
				    use some Extended ER features to model the DB Schema.	
		
	**There are some features of Extended ER

	**1) Subtypes and Supertypes (Inheritance)
				--> EER models allow for the representation of generalization/specialization hierarchies, similar to inheritance in object-oriented programming.
				--> This modeling technique helps capture shared attributes and relationships among entities while allowing for specialization.
		
		**Example
				**Supertype: Person
					Attributes: PersonID (Primary Key), FirstName, LastName
				
				**Subtype 1: Student
					Additional Attributes: StudentID, EnrollmentDate
					Relationship: Enrolls In (with Course)
				
				**Subtype 2: Faculty
					Additional Attributes: FacultyID, HireDate
				    Relationship: Teaches (with Course)


			1) "Person" is the supertype, representing a general entity with common attributes like "PersonID," "FirstName," and "LastName."
			2) "Student" and "Faculty" are subtypes, specializing "Person" into more specific entities.
			3) Each subtype has additional attributes unique to its specialization. For instance, "Student" has "StudentID" and "EnrollmentDate," while "Faculty"
				has "FacultyID" and "HireDate."
			4) Each subtype also participates in specific relationships. "Student" is related to "Course" through the "Enrolls In" relationship, indicating that
       			students enroll in courses. "Faculty" is related to "Course" through the "Teaches" relationship, indicating that faculty members teach courses.

	**2) Specialization 
			1)In ER model, we may require to subgroup an entity set into other entity sets that are distinct in some way with other
			   entity sets.
			2) Specialisation is splitting up the entity set into further sub entity sets on the basis of their functionalities,specialities and features.
			3) It is a Top-Down approach.
			4) e.g., Person entity set can be divided into customer, student, employee. Person is superclass and other specialised entity sets are subclasses.
			5) We have “is-a” relationship between superclass and subclass.
			6) Depicted by triangle component.
		   ** Why Specialisation?
			1) Certain attributes may only be applicable to a few entities of the parent entity set.
			2) DB designer can show the distinctive features of the sub entities.
			3) To group such entities we apply specialisation, to overall refine the DB blueprint.
	
	**3) Generalisation
			1) It is just a reverse of Specialisation.
			2) DB Designer, may encounter certain properties of two entities are overlapping. Designer may consider to make a new generalised entity set.
    			That generalised entity set will be a super class.
			3) “is-a” relationship is present between subclass and super class.
			4) e.g., Car, Jeep and Bus all have some common attributes, to avoid data repetition for the common attributes. DB designer may consider to Generalise 
			   to a new entity set “Vehicle”.
			5) It is a Bottom-up approach.
		  ** Why Generalisation?
			1) Makes DB more refined and simpler.
			2) Common attributes are not repeated.
			4) Attribute Inheritance
			5) Both Specialisation and Generalisation, has attribute inheritance.
			6) The attributes of higher level entity sets are inherited by lower level entity sets.
			7) E.g., Customer & Employee inherit the attributes of Person.
			8) Participation Inheritance
			9) If a parent entity set participates in a relationship then its child entity sets will also participate in that relationship.
	
	**4) Aggregation
			1) How to show relationships among relationships? - Aggregation is the technique.
			2) Abstraction is applied to treat relationships as higher-level entities. We can call it Abstract entity.
			3) Avoid redundancy
