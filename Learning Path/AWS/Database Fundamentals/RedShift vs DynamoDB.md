# RedShift vs DynamoDB

- DynamoDB is not meant for analytical-type queries
	- It is meant for simple queries and key-value pair data, which is more transactional based
	- You can query based on only the partition and sort key in DynamoDB