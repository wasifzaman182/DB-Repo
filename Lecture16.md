# DB-Repo
 
# Lecture 16

# Partitioning & Sharding in DBMS (DB Optimisation)
	--> A big problem can be solved easily when it is chopped into several smaller sub-problems. That is what the partitioning technique does. It divides a
        big database containing data metrics and indexes into smaller and handy slices of data called partitions.
	
	# Partitioning
	-->	Partitioning is the process of dividing a database table into smaller tables, based on a specific criteria. For example, a table of customer orders 
		could be partitioned by order date, with each partition containing orders from a specific month or year. Partitioning can improve performance by reducing 
		the amount of data that needs to be scanned for each query. It can also improve scalability by allowing the database to be distributed across multiple 
		servers.
		
		# Vertical Partitioning
			1. Slicing relation vertically / column-wise.
			2. Need to access different servers to get complete tuples.

		# Horizontal Partitioning
			1. Slicing relation horizontally / row-wise.
			2. Independent chunks of data tuples are stored in different servers.
			
	# When Partitioning is Applied?
			1. Dataset become much huge that managing and dealing with it become a tedious task.
			2. The number of requests are enough larger that the single DB server access is taking huge time and hence the system’s response time become high.
			
	# Advantages of Partitioning
			1. Parallelism
			2. Availability
			3. Performance
			4. Manageability
			5. Reduce Cost, as scaling-up or vertical scaling might be costly.


	# Distributed Database
			1. A single logical database that is, spread across multiple locations (servers) and logically interconnected by network.
			2. This is the product of applying DB optimisation techniques like Clustering, Partitioning and Sharding.

	# Sharding
			Sharding is a type of partitioning that is typically used in distributed databases. In a sharded database, the data is divided into multiple 
			partitions and each partition is stored on a separate server. This allows the database to handle a large volume of data and traffic.
		
		# Pros
			1. Scalability
			2. Availability
		
		# Cons
			1. Complexity, making partition mapping, Routing layer to be implemented in the system, Non-uniformity that creates the necessity of Re-Sharding
			2. Not well suited for Analytical type of queries, as the data is spread across different DB instances. (Scatter-Gather problem)
