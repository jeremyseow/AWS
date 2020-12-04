# Amazon S3

- Fully managed **object-based storage** that is high available, highly durable, very cost effective, and widely accessible
- Min file size = 0b, max file dize = 5Tb
- Objects stored in S3 have a durability of 11 nines (99.999999999%)
	- Probability of maintaining your data without it being lost through corruption, degradation of data, or other unknown potential damaging effects
-	The availability of S3 data objects is currently four nines (99.99%)
	- Enables you to access your stored data

#### Component
- Bucket
	- Bucket name must be completely unique, globally across all other S3 buckets that exist and it must be DNS-compliant
	- After you create the bucket you cannot change the name
	- The bucket name is visible in the URL that points to the objects that you’re going to put in your bucket
	- By default, you can create up to 100 within each AWS account but this can be increased if requested through AWS
	- You cannot delete an S3 bucket using the Amazon S3 console if the bucket contains 100,000 or more objects
	- You cannot delete an S3 bucket using the AWS CLI if versioning is enabled

#### [[Storage Class|Storage class]]

#### Access control
- S3 bucket policies
	-  You can specify who can access the bucket, what time of day the can access, from which CIDR block, and by IP address


In Amazon S3, all objects are private by default. Only the object owner has permission to access these objects. However, the object owner can optionally share objects with others by creating a pre-signed URL, using their own security credentials, to grant time-limited permission to download the objects.

When you create a pre-signed URL for your object, you must provide your security credentials, specify a bucket name, an object key, specify the HTTP method (GET to download the object) and expiration date and time. The pre-signed URLs are valid only for the specified duration. Anyone who receives the pre-signed URL can then access the object

![[S3 Pre-signed URL Flow.png]]