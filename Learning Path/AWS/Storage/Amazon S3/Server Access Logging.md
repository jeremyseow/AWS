# Server Access Logging

- When server-access logging is enabled on a bucket it captures details of requests that are made to that bucket and its objects

- Server-access logging, however, is not guaranteed and is conducted on a best-effort basis by S3
	- The logs themselves are collated and sent every few hours, or potentially sooner
	- There is no hard and fast rule that dictates that every request will be captured and that you will receive a log for a specific request within a set time frame

- Disabled by default

- When enabled
	- Need to set the target bucket
		- Used to store any logs created by enabling server access logging on your source bucket, which must be in the same region
	- Optionally, you can add a target prefix that S3 will add to the logs from your source bucket