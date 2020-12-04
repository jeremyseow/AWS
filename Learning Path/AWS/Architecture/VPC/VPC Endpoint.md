# VPC Endpoint

- A VPC endpoint enables you to privately connect your VPC to supported AWS services and VPC endpoint services powered by AWS PrivateLink without requiring an internet gateway, NAT device, VPN connection, or AWS Direct Connect connection

- Instances in your VPC do not require public IP addresses to communicate with resources in the service

- Traffic between your VPC and the other service does not leave the Amazon network


#### Components

- VPC endpoint 
	- The entry point in your VPC that enables you to connect privately to a service. The following are the different types of VPC endpoints
		- Gateway endpoint
		- Interface endpoint
		- Gateway load balancer endpoint


#### Use cases

- S3 is not part of your VPC, unlike your EC2 instances, EBS volumes, ELBs, and other services which typically reside within your private network
- An EC2 instance needs to have access to the Internet, via the Internet Gateway or a NAT Instance/Gateway in order to access S3. Alternatively, you can also create a VPC endpoint so your private subnet would be able to connect to S3

![[VPC Endpoint Overview.png]]