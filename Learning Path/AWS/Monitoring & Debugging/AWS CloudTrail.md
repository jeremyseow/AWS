# AWS CloudTrail

- Organization trail
	- If you have created an organization in AWS Organizations, you can also create a trail that will ==log all events for all AWS accounts in that organization==
	- Organization trails must be created in the master account, and when specified as applying to an organization, are automatically applied to all member accounts in the organization
	- ==Member accounts will be able to see the organization trail, but cannot modify or delete it==
	- ==By default, member accounts will not have access to the log files for the organization trail in the Amazon S3 bucket==

- By default, CloudTrail tracks only bucket-level actions
	- ==To track object-level actions, you need to enable Amazon S3 data events==


#### Security
- By default, CloudTrail event log files are encrypted using Amazon S3 server-side encryption (SSE)