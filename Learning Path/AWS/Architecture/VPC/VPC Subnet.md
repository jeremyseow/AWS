# VPC Subnet
- A subnet is a range of IP addresses in your VPC. You can launch AWS resources into a specified subnet
	- To protect the AWS resources in each subnet, you can use multiple layers of security, including security groups and network access control lists (ACL)

- You can add 1 or more subnets in each [[Availability Zone|AZ]] of your VPC's [[Region]]
	- Specify a CIDR block for each subnet, which is a subset of your VPC's CIDR block
	- A CIDR block must not overlap with any exist CIDR block that is associated with the VPC
	- The 1st 4 and the last IP addresses in each subnet CIDR block are not usable and cannot be assigned to an instance
	- You cannot change the size of an existing CIDR block

- Types of subnets
	- Public subnet
		- Has an internet gateway
		- Public subnets have a ==route table entry that forwards internet-bound traffic to an internet gateway==
		- For resources that must be connected to the internet
	- Private subnet
		- Does not have an internet gateway
		- Private subnets do not have a direct route to the internet
			- Instead, these subnets have a ==route table entry that forwards internet-bound traffic through a NAT gateway or NAT instance==
		- For resources that won't be connected to the internet
	- VPN-only subnet
		- Has a virtual private gateway