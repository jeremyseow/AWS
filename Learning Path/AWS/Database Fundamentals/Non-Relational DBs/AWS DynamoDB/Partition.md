# Partition

- DynamoDB can scale infinitely large, it transparently splits your table into smaller segments or partitions
	- The partition key is used to determine which partition an item should be stored in
	- DynamoDB handles the mapping of the partition keys to the physical partitions that hold the data on their servers

- It is often helpful to be aware of how many partitions your table will have
	- Amazon does not make this number visible to customers. Not in the web console, and not through the API

- We can either get the exact number by contacting AWS Premium Support, or estimate it using a formula provided by AWS

![[Partition Formula.png]]

**Example**

Attributes|Value
--|--
Table Size|6Gb
Read Capacity Units|15000
Write Capacity Units|2000

$$
max(6Gb/10Gb, (15000/3000 + 2000/1000))
= max(0.6, (5 + 2))
= 7 partitions
$$


- Partitions can be split, and the table's number of partitions can grow but they can never be joined or reduced

- When there is a need to create new partitions, DynamoDB will start copying your data into two new partitions
	- This happens transparently
	- Eventually, the data will finish migrating to the new partitions and DynamoDB will clean up the old partition
	- Each partition will have half of the partition key space
	- DynamoDB uses a hash algorithm to choose which partition each item belongs in. That is why partition keys are sometimes called hash keys


- Issues with partitions
	- when a table is split into partitions, each partition is given an equal slice of read capacity and write capacity
		- problems can happen when your data or when your read and write traffic are not evenly distributed across all your partitions
		- When you run out of provision capacity units in a partition, DynamoDB reads and writes stop functioning in that partition. Instead you get an exception called a “Provision Throughput Exceeded Exception”
		- AWS claims that this resets every second, but it can take a few minutes or longer to get back to normal even if traffic levels drop quickly
		- AWS will provide you with a little bit of burst capacity for each of your tables
			- AWS uses the burst capacity themselves for background maintenance tasks so you cannot always rely on it. And they do not tell you how much burst capacity you have available or how much you have used
	

- Solutions
	- Increase table’s provisioned capacity
		- However, it can be very expensive, and you are increasing capacity for many partitions that do not need it
	- Choose a partition key that will balance well
		- You can auto generate an artificial partition key that will be unique for each record
			- Every partition key would include exactly record, that way the data would never get out of balance
	- The downside is that this would add complexity to your table design, and it would mean that you would have to redesign your queries and the indexes that support those queries
		- There is no value having local secondary indexes as each partition key will only return one record
		- Need to create or edit global secondary indexes

