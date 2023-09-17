# DB-Repo
 
# Lecture 13

# Indexing in DBMS
	--> In database management systems, an index is a data structure that improves the speed of data retrieval operations on a database table. 
	--> It is a special table that contains a subset of data from the original table, along with pointers to the corresponding rows in the original
    	table.
	--> Speeds up operation with read operations like SELECT queries, WHERE clause etc.
	
	#  Search Key:
				Contains copy of primary key or candidate key of the table or something else.
				
	#  Data Reference:
				Pointer holding the address of disk block where the value of the corresponding key is stored.
	
	--> Indexing is optional, but increases access speed. It is not the primary mean to access the tuple, it is the secondary mean.
	--> Index file is always sorted.

	# Indexing Methods
	
			# Primary Index (Clustering Index) 
				1. A file may have several indices, on different search keys. If the data file containing the records is sequentially ordered, a
				   Primary index is an index whose search key also defines the sequential order of the file.
				2. NOTE: The term primary index is sometimes used to mean an index on a primary key. However, such usage is nonstandard and should be avoided.
				3. All files are ordered sequentially on some search key. It could be Primary Key or non-primary key.
			
			# Dense And Sparse Indices
			
				# Dense Index
					1. The dense index contains an index record for every search key value in the data file.
					2. The index record contains the search-key value and a pointer to the first data record with that search-key value.
					   The rest of the records with the same search-key value would be stored sequentially after the first record.
					3. It needs more space to store index record itself. The index records have the search key and a pointer to the actual record on the disk.
			    
				# Sparse Index
					1. An index record appears for only some of the search-key values.
					2. Sparse Index helps you to resolve the issues of dense Indexing in DBMS. In this method of indexing technique, a
					   range of index columns stores the same data block address, and when data needs to be retrieved, the block address will be fetched.
	
	--> Primary Indexing can be based on Data file is sorted w.r.t Primary Key attribute or non-key attributes.
	
	# Based on Key attribute
		1. Data file is sorted w.r.t primary key attribute.
		2. PK will be used as search-key in Index.
		3. Sparse Index will be formed i.e., no. of entries in the index file = no. of blocks in datafile.
	
	# Based on Non-Key attribute
		1. Data file is sorted w.r.t non-key attribute.
		2. No. Of entries in the index = unique non-key attribute value in the data file.
		3. This is dense index as, all the unique values have an entry in the index file.
        4. E.g., Let’s assume that a company recruited many employees in various departments. In this case, clustering indexing in DBMS should be created for all employees
			who belong to the same dept.
			
	# Multi-level Index
		1. Index with two or more levels.
		2. If the single level index become enough large that the binary search it self would take much time, we can break down indexing into multiple levels.


# Secondary Index (Non-Clustering Index)
	1. Datafile is unsorted. Hence, Primary Indexing is not possible.
	2. Can be done on key or non-key attribute.
	3. Called secondary indexing because normally one indexing is already applied.
	4. No. Of entries in the index file = no. of records in the data file.
	5. It's an example of Dense index.

# Advantages of Indexing
	1. Faster access and retrieval of data.
	2. IO is less.
	
# Limitations of Indexing
	1. Additional space to store index table
	2. Indexing Decrease performance in INSERT, DELETE, and UPDATE query.