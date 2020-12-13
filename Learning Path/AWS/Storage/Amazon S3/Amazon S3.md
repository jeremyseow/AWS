# Amazon S3

- Fully managed **object-based storage** that is high available, highly durable, very cost effective, and widely accessible

- Min file size = 0b, max file dize = 5Tb

- Objects stored in S3 have a durability of 11 nines (99.999999999%)
	- Probability of maintaining your data without it being lost through corruption, degradation of data, or other unknown potential damaging effects
	
-	The availability of S3 data objects is currently four nines (99.99%)
	- Enables you to access your stored data
	
- Amazon S3 does not currently support object locking for concurrent updates

- S3 Object Lock
	- Object locking is different from the S3 Object Lock feature
	- With S3 Object Lock, you can store objects using a write-once-read-many (WORM) model and prevent an object from being deleted or overwritten for a fixed amount of time or indefinitely

#### Component
- Bucket
	- Bucket name must be completely unique, globally across all other S3 buckets that exist and it must be DNS-compliant
	- After you create the bucket you cannot change the name
	- The bucket name is visible in the URL that points to the objects that you’re going to put in your bucket
	- By default, you can create up to 100 within each AWS account but this can be increased if requested through AWS
	- You cannot delete an S3 bucket using the Amazon S3 console if the bucket contains 100,000 or more objects
	- You cannot delete an S3 bucket using the AWS CLI if versioning is enabled
- Object
	- Are private by default, need to grant permissions to other users
	- Consists of a file and optionally any metadata that describes the file
- Key
	- A unique identifier for an object in a bucket

#### [[Storage Class|Storage class]]

#### Access control
- S3 bucket policies
	-  You can specify who can access the bucket, what time of day the can access, from which CIDR block, and by IP address
-  ACL
	-  Each bucket and object has an ACL attached to it as a subresource
	-  It defines which AWS accounts or groups are granted access and the type of access
	-  When a request is received against a resource, S3 checks the corresponding ACL to verify that the requester has the necessary access permissions
-  IAM


In Amazon S3, all objects are private by default. Only the object owner has permission to access these objects. However, the object owner can optionally share objects with others by creating a pre-signed URL, using their own security credentials, to grant time-limited permission to download the objects.

When you create a pre-signed URL for your object, you must provide your security credentials, specify a bucket name, an object key, specify the HTTP method (GET to download the object) and expiration date and time. The pre-signed URLs are valid only for the specified duration. Anyone who receives the pre-signed URL can then access the object

![[S3 Pre-signed URL Flow.png]]


#### Cross-origin resource sharing (CORS)

- Defines a way for client web applications that are loaded in one domain to interact with resources in a different domain

- For a bucket to allow access to its resources from another bucket, create a CORS configuration to allow cross-origin requests