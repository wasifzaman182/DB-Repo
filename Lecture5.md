# DB-Repo
 
#Lecture 5

#setps to Create ER diagram
	**1) identify entities set
	**2) identify attributes and their types
	**3) identify Relationship and constraints(Mapping, participation)

#Home work
		**1) Online food delivery DB
		**2) university DB
		

#let complete the home work
	
		##Online food delivery DB
			
			**identify entities set
					1) customer 
					2) payment
					3) shop
					4) items
					5) review
					6) order
					
					
				customer  order items --> M :N
				customer pay payment  --> M:N
				customer give review  --> M:N
				shop add item        --> M:N
				customer can order  --> M:N
				
			
			**identifying attributes and their types
				1) customer
						--> cust id(pk), name(composit), address(composit), phone no
				2) items
						-->  itemsName
				3) payment 
						--> amount, amountRecived, card/cash
				4) shop	
						--> shop name, shop id(pk), startDate,phoneno,address(composit)
				5) review
						--> reviewFromcustomer, stars
				6) order	
						--> orderno, orderDate,status
						
			** identifying Relationship and constraints(Mapping and participation)
					Will add ER diagram in pdf formatt/ or image.


		##University DB ER
			**Identifying entities sets
					1) Student
					2) courses
					3) fee
					4) semester
					5) department
					6) staff
					7) payment
					8) salary
			
			
				student enroll semester  	M:N
				student take courses		M:N
				student pay fee				M:N
				student do payment			M:N 
				staff belongs department    M:N
				staff teachs courses		M:N
				salary paid staff			M:N
				
				
			**Identifying attributes add their types
				1) student 
						--> student id(PK), name(composit), address(composit), contactno(Multivalue),email
				2) courses	
						--> course id(PK), name, registrationDate,endDate(derived)
				3) fee	
					   --> amount, status, submitedDate
				4) semester	
					   --> startdate,endDate(derived),semesterNo
				5) department
					   --> departmentName,joinedDate
				6)staff	
					   --> staffid(PK), name, contactno(Multivalue), email,address(Multivalue),experience(derived),totalExperice
				7) payment (week relation with student)
					  --> amount, paymentNo,paymentDate
				8) salary	 (week relation with staff)
					  --> status, transferDate
					