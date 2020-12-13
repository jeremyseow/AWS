# DynamoDB Streams
- An optional feature that captures data modification events in DynamoDB tables

- Each event is represented by a stream record, which includes the following information
	- A new item is added to the table
		- An image is captured of the entire item, including all its attributes
	- An item is updated
		- Before and after images of any attributes of the item that are modified will be captured
	- An item is deleted
		- An image of the entire item before it is deleted is captured
	- Each stream record also contains the name of the table, event timestamp, and other metadata

- Stream records are organized into shards, which acts as a container for multiple stream records, and contains information required for accessing and iterating through these records

- **Stream records have a lifetime of 24 hours**, after which they will be removed from the stream

- Data expired using a TTL will appear as an event in your DynamoDB streams

![[DynamoDB Stream.png]]
