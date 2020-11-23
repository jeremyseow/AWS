# Amazon S3

- Access control
	- S3 bucket policies
		-  You can specify who can access the bucket, what time of day the can access, from which CIDR block, and by IP address


In Amazon S3, all objects are private by default. Only the object owner has permission to access these objects. However, the object owner can optionally share objects with others by creating a pre-signed URL, using their own security credentials, to grant time-limited permission to download the objects.

When you create a pre-signed URL for your object, you must provide your security credentials, specify a bucket name, an object key, specify the HTTP method (GET to download the object) and expiration date and time. The pre-signed URLs are valid only for the specified duration. Anyone who receives the pre-signed URL can then access the object

![[S3 Pre-signed URL Flow.png]]