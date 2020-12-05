# Amazon S3

- Access control
	- S3 bucket policies
		-  You can specify who can access the bucket, what time of day the can access, from which CIDR block, and by IP address

In Amazon S3, all objects are private by default. Only the object owner has permission to access these objects. However, the object owner can optionally share objects with others by creating a pre-signed URL, using their own security credentials, to grant time-limited permission to download the objects.

When you create a pre-signed URL for your object, you must provide your security credentials, specify a bucket name, an object key, specify the HTTP method (GET to download the object) and expiration date and time. The pre-signed URLs are valid only for the specified duration. Anyone who receives the pre-signed URL can then access the object

![[S3 Pre-signed URL Flow.png]]

## Querying S3
- **S3 Select** : Use SQL to filter contents of S3 to reduce amount of data transfers. Works for CSV, JSON, or Apache Parquet format. It also works with objects that are compressed with GZIP or BZIP2 (for CSV and JSON objects only)
- **Athena** : Athena can handle far more complex ad-hoc queries on data in Amazon S3, this entails an increase in operating cost as compared to S3 Select