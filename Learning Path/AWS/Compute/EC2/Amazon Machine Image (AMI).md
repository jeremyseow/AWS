# Amazon Machine Image (AMI)

- A template that contains a software configuration (for example, an operating system, an application server, and applications)
- From an AMI, you launch 1 or more instances, which is a copy of the AMI running as a virtual server in the cloud

![[AMI Overview.png]]


- There are 3 sources of AMI
	- AWS AMI
	- Community AMI
		- Members of the AWS developer community have published their own custom AMIs
	- Custom AMI
		- You can create your own custom AMIs


- All AMIs are categorized as either 
	- Backed by Amazon EBS
		- The root device for an instance launched from the AMI is an Amazon EBS volume
	- Backed by instance store
		- The root device for an instance launched from the AMI is an instance store volume created from a template stored in Amazon S3

	- [[Storage#Root device volume|Differences between each type of AMI]]