# VPC Endpoint

- A VPC endpoint enables you to privately connect your VPC to supported AWS services and VPC endpoint services powered by AWS PrivateLink without requiring an internet gateway, NAT device, VPN connection, or AWS Direct Connect connection
	- PrivateLink allows a private and secure connection between VPCs, AWS services, and on-premises applications, via the AWS internal network

- Instances in your VPC do not require public IP addresses to communicate with resources in the service

- Traffic between your VPC and the other service does not leave the Amazon network


#### Components

- VPC endpoint 
	- The entry point in your VPC that enables you to connect privately to a service. The following are the different types of VPC endpoints
		- Gateway endpoint
			- Is a target that is used within your route tables to allow you to reach supported services
			- Only works with IPv4
		- Interface endpoint
			- Essentially ENIs that are placed within a subnet that act as a target for any traffic that is being sent to a supported services and operates through the use of PrivateLink
			- When an interface endpoint is configured within your chosen subnet, the service that it is associated with is not able to initiate a connection through to your VPC, ==communication across this interface has to originate from within your VPC first before a response can be made by the service==
		- Gateway load balancer endpoint


#### Use cases

- S3 is not part of your VPC, unlike your EC2 instances, EBS volumes, ELBs, and other services which typically reside within your private network
	- An EC2 instance needs to have access to the Internet, via the Internet Gateway or a NAT Instance/Gateway in order to access S3. Alternatively, you can also create a VPC endpoint so your private subnet would be able to connect to S3

![[VPC Endpoint Overview.png]]