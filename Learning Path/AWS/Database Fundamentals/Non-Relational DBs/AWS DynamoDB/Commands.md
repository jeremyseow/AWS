# Commands

- To create, update, or delete an item in a DynamoDB table, use one of the following operations:
	- PutItem
	- UpdateItem
	- DeleteItem

- For each of these operations, you need to specify the entire primary key, not just part of it. For example, if a table has a composite primary key (partition key and sort key), you must supply a value for the partition key and a value for the sort key.

-  To return the number of write capacity units consumed by any of these operations, set the ReturnConsumedCapacity parameter to one of the following:

	- TOTAL — returns the total number of write capacity units consumed.
	- INDEXES — returns the total number of write capacity units consumed, with subtotals for the table and any secondary indexes that were affected by the operation.
	- NONE — no write capacity details are returned. (This is the default.)


To read data from a table, you use operations such as GetItem, Query, or Scan. DynamoDB returns all of the item attributes by default. To get just some, rather than all of the attributes, use a projection expression.

A projection expression is a string that identifies the attributes you want. To retrieve a single attribute, specify its name. For multiple attributes, the names must be comma-separated.

Using condition expressions is incorrect because this is primarily used to determine which items should be modified for data manipulation operations such as PutItem, UpdateItem, and DeleteItem calls.

Using expression attribute names is incorrect because this is a placeholder that you use in a projection expression, as an alternative to an actual attribute name. An expression attribute name must begin with a #, and be followed by one or more alphanumeric characters.

Using filter expressions is incorrect because it simply determines which items (and not the attributes) within the Query results should be returned to you. All of the other results are discarded. Take note that the scenario says that you have to fetch specific attributes and not specific items.

 