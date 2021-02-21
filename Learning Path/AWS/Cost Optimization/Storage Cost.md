# Storage Cost

## S3

- AWS S3 offers multiple storage classes to suit your needs
	- Differences include number of AZs used to store your object data, the minimum storage duration (in days), the minimum billable object size, durability and availability percentages, and retrieval times and fees, etc

## Glacier
- An extremely low cost, long-term, durable storage solution which is often referred to as cold storage, ideally suited for long-term back up and archival requirements

[[Storage Class]]

#### Types of costs
- Storage costs
- Request costs
	- Requests can be split into the following main request types
		- PUT, COPY, POST, LIST, GET, SELECT, Lifecycle Transition
		- Both the DELETE and CANCEL requests are free
	- For Glacier, cost depends on the retrieval method
		- Expedited
		- Standard
		- Bulk
- Data retrieval costs
- Data transfer costs
	- Data transfer is free when
		- Data is transferred INTO Amazon S3 from the internet
		- Data is transferred OUT to your EC2 instances which ==reside in the same region== as the source S3 bucket in which the data is located
		- Data is transferred OUT to Amazon CloudFront
	- Cost is incurred when
		- Transferring out to the internet
		- When transferring out to other AWS services
- Features
	- Transfer acceleration
		- Data is routed through an optimized network path to Amazon S3 via CloudFront edge locations
		- Whereas normal data transfer into amazon S3 is free from the internet, with transfer acceleration, this is a cost associated per GB dependant on which edge location is used
		- There is an increased cost for any data transferred OUT of S3, either to the internet or to another region, again due to the edge location acceleration involved
	- S3 Batch operations
		- Batch operations allow you to carry out management operations across millions or even billions of your S3 Objects at the same time using a single API or by using the S3 Management Console
		- Pricing for this feature has two price points, firstly on per batch job, and secondly per million object operations performed
	- S3 and Glacier select
		- S3 and Glacier select is available with all storage classes except Glacier Deep Archive
		- Allows you to use SQL expressions to retrieve only the data that you want from your objects instead of the whole objects which could be many gigabyes in size
		- This enables you to retrieve the data faster and cheaper
		- 2 price points related to Select: data scanned (per GB) and data returned (per GB)
- Management costs
	- Amazon S3 inventory (Used for auditing and reporting for replication and encryption actions)
		- This feature is priced per million objects listed
	- Analytics, which is used to analyze access patterns to assist in ensuring you are using the right storage class for your objects
		- This feature is priced per million objects monitored per month
	- Object tagging, which is using tags allows you to categorize your storage
		- This feature is priced per 10,000 tags applied per month
- Replication costs
	- 2 modes of replications
		- Cross-Region Replication between 2 different buckets
			- There will also be the addition of the ==inter-region data transfer fees==, which will be priced upon the source region
		- Same-Region Replication between 2 different buckets
		- There are no specific costs for the use of the S3 replication feature itself, instead, you are ==simply charged for the cost for the storage class in your destination where your replicated objects will reside==
		- You will also incur costs for any COPY and PUT requests which will also be based upon the rates of the destination region
	- S3 Replication Time Control
		- S3-RTC is an advanced feature built on top of S3 replication that provides an SLA of ensuring that 99.9% of objects are replicated within 15 minutes of the start of the upload
- Data management costs
	- Versioning
		- An added cost to you as you are storing multiple versions of the same object
	- Lifecycle policies
		- Able to configure and set specific criteria that can automatically move your data from one storage class to another, or delete it from S3 altogether


## Cost Considerations
- Storage class (Priced per GB of storage)
	- You need to understand the profile of your storage, its access patterns, its criticality, availability and if latency plays a factor when accessing the data
- Data requests (Priced per 1000 requests)
- Retrieval requests (Priced per GB retrieved)
- Data Transfer (Priced per GB)
	- Once your data is in Amazon S3, what do you intend to do with it? Will it simply be kept there for cold storage, for example in Glacier or Deep Archive, or will it be shared across numerous applications and services and transferred out to different regions?
- Management Operations
- Replication
	- Depending on your design, service and resiliency needs
- Data Management controls
	- Be aware of the additional costs that are incurred when versioning is enabled on a bucket
	- Make use of lifecycle policies to automatically move or delete your data based upon your own data policies, this could lead to significant savings