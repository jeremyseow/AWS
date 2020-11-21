# Capacity Unit Consumption

- Read capacity unit
	- 1 read request unit represents 1 strongly consistent read request, or 2 eventually consistent read requests, for an item up to 4 KB in size
	- 2 read request units represent 1 transactional read for items up to 4 KB
	- If you need to read an item that is larger than 4 KB, DynamoDB needs additional read request units
	- The total number of read request units required depends on the item size, and whether you want an eventually consistent or strongly consistent read
	- For example, if your item size is 8 KB, you require 2 read request units to sustain 1 strongly consistent read, 1 read request unit if you choose eventually consistent reads, or 4 read request units for a transactional read request

- Write capacity unit
	- 1 write request unit represents 1 write for an item up to 1 KB in size
	- If you need to write an item that is larger than 1 KB, DynamoDB needs to consume additional write request units
	- Transactional write requests require 2 write request units to perform one write for items up to 1 KB
	- The total number of write request units required depends on the item size
	- For example, if your item size is 2 KB, you require 2 write request units to sustain 1 write request or 4 write request units for a transactional write request.