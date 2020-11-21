# VPC
- A virtual private cloud (VPC) is a virtual network dedicated to your AWS account, where you can launch your AWS resources

- It is logically isolated from other virtual networks in the AWS Cloud

- You can specify an IP address range for the VPC in the form of Classless Inter-Domain Routing (CIDR) block, for example; 10.0.0.0/16, and add [[VPC Subnet|subnets]], associate security groups, and configure route tables

- When you associate a CIDR block with your VPC, a route is automatically added to your VPC route tables to enable routing within the VPC 
		- The destination is the CIDR block and the target is _local_
		- You have a limit on the number of CIDR blocks you can associate with a VPC and number of routes you can add to a route table

- Subnet security
	- [[Security Group]]
	- [[Network Access Control List (NACL)]]
	- [[Flow Logs]]

![[Security group vs Network ACL.png]]
![[Security group and Network ACL in VPC.png]]

- Components
	- Network Interfaces

- Guide
	- https://tutorialsdojo.com/amazon-vpc/
	- https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html
