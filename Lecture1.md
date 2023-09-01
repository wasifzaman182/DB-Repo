# DB-Repo
 
#Lecture 1

#DBMS
		--> lets start what is D.

#D 
	D means data --> collection of raw bytes is called data. not understandable/ not meaningfull.
										||
										||
					When raw data is processed it become "information".
					information provides context for decsion making.

#Types of data	
	          #i) Quantitative
					The data which is in nomerical form is called Quantitative like age, weight, height etc.
			  
			  #ii) Qualitative
					The data which is in descriptive form is called Qualitative data like name,gender,hair color etc.


#Data Vs information	
			i) Data is collection of facts  while information put those facts into context.
			ii) Data is unorganized form while information is organized
			iii) Data is itself meaningless when analyaze it and interpret then it become information
			iv) Data does not depend on inforamtion while information depend on data.
			v) Data doesn't sufficent for decsion while information is.

#Database
	--> Database is an electronic space where we can store data, managed, access and updtad
	--> to store, managed, access and updtad data we need Database management system(DBMS).

#DBMS	
	--> DBMS is set of softwares which we need for access, add, update and delete data.
	--> The primary goal of DBMS is to retrive and stroe information in efficent way.
	
###################################################################################################################################################

#DBMS VS File system
	--> File processing disadvantages
	##1) Data redundancy and inconsistency
			Data redundancy and inconsistency are common issues in database management. Let's illustrate these concepts with an example:

			**Scenario**: Consider a simple database for a library. This database contains information about books, borrowers, and library branches.

			**Table 1: Books**
			| ISBN        | Title           | Author       | BranchID |
			|-------------|-----------------|--------------|----------|
			| 978-1234567 | "Introduction"  | "John Smith" | 101      |
			| 978-2345678 | "Database"      | "Jane Doe"   | 102      |
			| 978-3456789 | "Programming"   | "John Smith" | 101      |
			| 978-4567890 | "Data Science"  | "Alice Lee"  | 103      |


			Now, let's examine data redundancy and inconsistency in this example:

			1. **Data Redundancy**:
			   Data redundancy occurs when the same data is duplicated in multiple places within the database. In this example, the "Author" column in the "Books" table contains 
			   redundant data. For instance, "John Smith" appears twice as an author. If "John Smith" were to change his name, you would need to update it in multiple rows, which 
			   can lead to inconsistencies.

			   Example of redundancy:
			   - "Introduction" by "John Smith" (ISBN: 978-1234567)
			   - "Programming" by "John Smith" (ISBN: 978-3456789)

			2. **Data Inconsistency**:
			   Data inconsistency arises when there are conflicting or contradictory data values in different parts of the database. In this example, consider that "John Smith" 
			   changes his name to "John J. Smith." If you update one occurrence of his name but forget another, it leads to inconsistency.

			   Example of inconsistency (after the name change):
			   - "Introduction" by "John J. Smith" (ISBN: 978-1234567)
			   - "Programming" by "John Smith" (ISBN: 978-3456789)

			   Here, "John Smith" and "John J. Smith" are inconsistent author names for the same person.

	##2) Difficulty in accessing data
	
			Let's consider an example that illustrates some of the difficulties in accessing data in file systems:

			**Scenario**: Imagine a small business that relies on a file system to store important documents and files related to its operations.

			1. **Disorganized File Structure**:
			   
			   In this business, employees have been saving documents to the file system for years without a consistent organizational structure. Files are scattered across various folders with inconsistent naming conventions. For example:
			   
			   - Important contracts might be stored in a folder called "Contracts," but there's no uniform naming scheme, making it hard to find specific contracts quickly.
			   - Project-related documents might be saved in folders named after project codes, and the naming convention varies between projects.
			   
			   The lack of a standardized structure makes it challenging to locate specific documents efficiently.

			2. **Duplicate Files**
			3. **Search Difficulties**
			4. **Security and Access Control**
			5. **Concurrency Issues**
			6. **Backup and Recovery**
			7. **Scalability**
			8. **Version Control**

		##3) Data Isolation
				**Scenario** Imagine a shared network drive in a small office environment where multiple users have access to the same set of files and directories.

			1. **Concurrent File Access:**
                   User A and User B are both working on a project that involves modifying the same file, "ProjectReport.docx," which is stored on the network drive.
            
			2. **Data Isolation Challenge:**
				User A opens "ProjectReport.docx" and starts making changes to it.
				Simultaneously, User B also opens "ProjectReport.docx" and begins editing it without being aware that User A is working on the same file.
				Both users save their changes independently.
				
		
		##4) Integrity problem
				Integrity problems in file systems refer to situations where the data stored in files becomes corrupted, inconsistent, or inaccurate due to various reasons. 

		1. **Data Corruption**:

				  - **Example**: A hardware failure, such as a bad sector on a hard disk, can lead to data corruption in a file. For instance, a text document may contain 
									garbled or unreadable characters in some sections.
		          - **Solution**: Regular data backups and the use of error-checking mechanisms like checksums or redundancy (e.g., RAID) can help detect and recover from 
				                  data corruption.

		2. **Incomplete Writes**:

		         - **Example**: During a power outage or system crash, a write operation to a file may be interrupted, leaving the file in an incomplete or inconsistent state. 
				                For example, a database file might have a portion of a record written but not the rest.
		         - **Solution**: Journaling file systems and transactional mechanisms are used to ensure that file updates are completed in a consistent manner even after 
				                 unexpected system failures.

		3. **File System Corruption**:

		          - **Example**: The file system structure itself can become corrupted due to software bugs, disk errors, or improper shutdowns. This can result in lost files 
				                 or directories.
        		  - **Solution**: Running file system repair tools (e.g., fsck in Unix-like systems) can help identify and fix structural issues within the file system.
 
		4. **Unauthorized Access**:

				- **Example**: If unauthorized users gain access to a file or directory, they may tamper with the data, delete files, or inject malicious code, compromising the 
				              integrity of the data.
		        - **Solution**: Proper access control mechanisms, user authentication, and encryption can help prevent unauthorized access and tampering.

		5. **Virus or Malware Attacks**:

		   - **Example**: Malicious software can infect files, leading to changes or destruction of data. For instance, a virus may encrypt files and demand a ransom for 
		                  decryption.
		   - **Solution**: Regularly updated antivirus and anti-malware software can help detect and remove threats. Additionally, practicing safe computing habits and avoiding 
							suspicious downloads can reduce the risk of malware infection.

		6. **Human Errors**
		7. **Lack of Data Validation**
		8.**Concurrency Issues **:

   ##5) Atomicity problem
			Refers to the property of ensuring that a series of operations either all succeed together or fail together as a single, indivisible unit (a transaction).
			Traditional file systems do not provide the same level of support for atomicity as database systems
			
   ##6) Concurrent-access anomilies
			Consider a shared network folder where multiple users have access to a file. In this scenario, two users attempt to simultaneously modify and save changes to the 
		    same file, leading to concurrent-access anomalies.
			
   ##7) Security Problems
			Security problems in file systems refer to vulnerabilities and issues that can compromise the confidentiality, integrity, and availability of data stored within 
			the file system. These problems can result from various factors, including improper access controls, vulnerabilities, and human errors
		
		
Above all are the advantages of DBMS. 