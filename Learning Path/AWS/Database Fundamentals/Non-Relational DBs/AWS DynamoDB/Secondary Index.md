# AWS DynamoDB Secondary Index

- A data structure that contains a subset of attributes from a table, along with an alternate key to support Query operations
	- Every secondary index is associated with exactly one table, from which it obtains its data. This is called the base table for the index
	- When you create an index, you define an alternate key for the index (partition key and sort key). You also define the attributes that you want to be projected, or copied, from the base table into the index. DynamoDB copies these attributes into the index, along with the primary key attributes from the base table. You can then query or scan the index just as you would query or scan a table
	- Every secondary index is automatically maintained by DynamoDB. When you add, modify, or delete items in the base table, any indexes on that table are also updated to reflect these changes

- Differences with indexes in Relational Database
	- Each query can only use one index. If you want to query and match on two different columns, you need to create an index that can do that properly
	- When you write your queries, you need to specify exactly which index should be used for each query. It is not like a relational database that has a query analyzer, which can automatically decide which indexes to use for our query. Here, you need to be explicit and tell DynamoDB what index to use

- 2 types of secondary indexes
	- Global secondary index
		- Allows you to query across the entire table to find any record that matches a value
		- Global secondary indexes use storage space that is separate from the main table
			- You must configure provision throughput for each global secondary index, just like you do for a table
		-  You can choose attributes from the base table to include in the index. This is called projecting attributes into the index
			-  By default, all the attributes in the table are projected into the index, which uses more space and more throughput
		- You can achieve the same result by creating separate tables instead of using secondary indexes
			- However, DynamoDB keeps the indexes updated for you automatically. When you insert or modify data in the main table, DynamoDB will automatically ensure that the index receives the same updates at the same time

	- Local secondary index
		- Lives within each partition key and help you filter data within that partition
		- It is similar to global secondary indexes, except that the partition key of the local secondary index must be the same as the partition
			- This means that they are not useful unless you have a compound primary key. If you do not, then there would never be more than one item with a given partition key (as good as just using the partition key of the base table)

- Differences between the 2 indexes

Local secondary index|Global secondary index
------------------------|-------------------------
If your queries will work by limiting the results to a single partition key value|If you need to query across all partition key values
Can only be created at the same time the table is created, If you want to add a local secondary index to an existing table, or remove a local secondary index, you will need to delete the table and start over |Can be created at the same time the table is created, and can be added, changed or removed later
Share their provision throughput with the main table|Have to revision separate throughput capacity for the index
5 local secondary indexes for each table|20 global secondary indexes for each table
When you query a local secondary index, you can choose either eventual consistency or strong consistency|Only supports eventual consistency and not strong consistency

![[DynamoDB Global Secondary Index.png]]
![[DynamoDB Local Secondary Index.png]]


