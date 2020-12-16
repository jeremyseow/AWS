# AWS CloudTrail

- ==All actions in your AWS account are composed of API calls, regardless of the origin (the AWS Management Console or programmatic/scripted actions)==

- As you create resources in your account, API calls are being made to AWS services in different regions around the world

- AWS CloudTrail is a fully managed service that continuously monitors and records API calls and stores them in Amazon S3
	- You can use these logs to troubleshoot and resolve operational issues, meet and verify regulatory compliance, and monitor or alarm on specific events in your account
	
- CloudTrail supports most AWS services, making it easy for IT and security administrators to analyze activity in accounts

- ==IT auditors can also use log files as compliance aids==

- CloudTrail helps answer the following five key questions about monitoring access:
	- Who made the API call?
	- When was the API call made?
	- What was the API call?
	- Which resources were acted upon in the API call?
	- Where was the origin of the API call?

- By default, CloudTrail stores the CloudTrail event history for 90 days

- Organization trail
	- If you have created an organization in AWS Organizations, you can also create a trail that will ==log all events for all AWS accounts in that organization==
	- Organization trails must be created in the master account, and when specified as applying to an organization, are automatically applied to all member accounts in the organization
	- ==Member accounts will be able to see the organization trail, but cannot modify or delete it==
	- ==By default, member accounts will not have access to the log files for the organization trail in the Amazon S3 bucket==

- By default, CloudTrail tracks only bucket-level actions
	- ==To track object-level actions, you need to enable Amazon S3 data events==


#### Security
- By default, CloudTrail event log files are encrypted using Amazon S3 server-side encryption (SSE)