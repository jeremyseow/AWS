# Storage Class

- S3 Storage Classes can be configured at the object level and a single bucket can contain objects stored across storage classes

- S3 Lifecycle policies can automatically transition objects between storage classes without any application changes

- Types of storage classes can be classified into 4 access tiers
	- Frequent access 
		- S3 Standard
			- High durability, availability, and performance and low latency and high throughput
			- Suitable for frequently accessed data
				-  Such as cloud applications, dynamic websites, content distribution, mobile and gaming applications, and big data analytics
	-  Infrequent access
		-  S3 Standard-Infrequent Access (S3 Standard-IA)
			-  Offers the high durability, high throughput, and low latency of S3 Standard, with a low per GB storage price and per GB retrieval fee
			-  Suitable for data that is accessed less frequently, but requires rapid access when needed
				-  Such as long-term storage, backups, and as a data store for disaster recovery files
		-  S3 One Zone-Infrequent Access (S3 One Zone-IA)
			-  Offers the high durability, high throughput, and low latency of S3 Standard, with a low per GB storage price and per GB retrieval fee
			-  However, it has **lower availability** because unlike other S3 Storage Classes, which store data in a minimum of 3 AZs, S3 One Zone-IA stores data in a **single AZ and costs 20% less than S3 Standard-IA**
			-  Ideal for customers who want a lower-cost option for infrequently accessed data but do not require the availability and resilience of S3 Standard or S3 Standard-IA
				-  Such as storing secondary backup copies of on-premises data or easily re-creatable data, or data that is replicated from another AWS Region using S3 Cross-Region Replication
	-  Archive
		-  S3 Glacier
			-  Secure, durable, and low-cost storage class for data archiving
			-  You can reliably store any amount of data at costs that are competitive with or cheaper than on-premises solution
			-  3 retrieval options
				-  Expedited
					-  Allow you to quickly access your data when occasional urgent requests for a subset of archives are required
					-  For all but the largest archives (250+ Mb), data accessed using Expedited retrievals are typically made available within 1–5 minutes
					-  There are two types of Expedited retrievals
						-  On-Demand requests are similar to EC2 On-Demand instances and are available most of the time
						-  Provisioned requests are guaranteed to be available when you need them
				-  Standard
					-  Standard retrievals typically complete within 3–5 hours
					-  This is the default option for retrieval requests that do not specify the retrieval option
				-  Bulk
					-  S3 Glacier’s lowest-cost retrieval option, which you can use to retrieve large amounts, even petabytes, of data inexpensively in a day
					-  Bulk retrievals typically complete within 5–12 hours
	-  Deep archive
		-  S3 Glacier Deep Archive
			-  Lowest-cost storage class and supports long-term retention and digital preservation for data that may be accessed once or twice in a year
				-  Suitable for
					-  Highly-regulated industries, such as the Financial Services, Healthcare, and Public Sectors — that retain data sets for 7-10 years or longer to meet regulatory compliance requirements
					-  Backup and disaster recovery use cases
			- S3 Glacier Deep Archive also offers a bulk retrieval option, where you can retrieve petabytes of data within 48 hours.
	-  Special classes
		-  S3 Intelligent-tiering
			-  Designed to optimize costs by automatically moving data to the most cost-effective access tier, without operational overhead
			-  Objects uploaded or transitioned to S3 Intelligent-Tiering are automatically stored in the Frequent Access tier. S3 Intelligent-Tiering works by monitoring access patterns and then moving the objects that have not been accessed in 30 consecutive days to the Infrequent Access tier. Once you have activated one or both of the archive access tiers, S3 Intelligent-Tiering will automatically move objects that haven’t been accessed for 90 consecutive days to the Archive Access tier and then after 180 consecutive days of no access to the Deep Archive Access tier. If the objects are accessed later, S3 Intelligent-Tiering moves the objects back to the Frequent Access tier
				-  These tiers are part of the intelligent tiering class itself and are separate from existing classes
			-  Suitable for data sets with unknown storage access patterns, like new applications, or unpredictable access patterns, like data lakes
		-  S3 Outposts

![[S3 Storage Classes.png]]
