# AWS DynamoDB

- A fully managed NoSQL database service
	- No database administration, no servers to manage, scalable and resilient
	- Schema-less

- 

#### Components
- Table
	- A collection of items
	- Schema-less
	- There is an initial limit of 256 tables per region

- Item
	- A collection of attributes
	- Can be thought of as a row
	- DynamoDB uses primary keys to uniquely identify each item in a table and secondary indexes to provide more querying flexibility
	- Each table can contain 0 or more items

- Attribute
	- A fundamental data element
	- DynamoDB supports nested attributes up to 32 levels deep

- Primary key
	- Uniquely identifies each item in a table
	- Is made up of 
		- Partition key (hash key)
		- And optionally, sort key (range key)
	- Must be of [[AWS DynamoDB#^178017|scalar type]]
	- If the primary key is made up of only the partition key, then no 2 items can have the same partition key
	- If the sort key is defined, the composite primary key must be unique
		- The partition key will go through a hash function and the output will be used to determine the [[Partition|partition]] that the item will be stored
		- Items with the same partition keys will be stored together, in sorted order by the sort key

- [[Secondary Index|Secondary Index]]

- [[DynamoDB Streams]]

#### Data types for attributes
- Scalar types ^178017
	- Can represent exactly 1 value
	- Types include number, string, binary, Boolean, and null
- Document types
	- Can represent complex structures with nest attributes, such as JSON
	- Types include list and map
- Set types
	- Can represent multiple scalar values
	- Types include number set, string set, binary set


#### Throughput management
- 

#### [[Commands]]

#### Guide
- https://tutorialsdojo.com/amazon-dynamodb/
- https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Introduction.html?shortFooter=true