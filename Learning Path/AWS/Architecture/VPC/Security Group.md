# Security Group
- Controls inbound and outbound traffic for your instances

- You can associate 1 - 5 security groups to your instances in the VPC

- If no security group is specified, the instance will be associated with a default security group

- When a security group is created, by default
	- It has no inbound rules
	- Has an outbound rule that allows all outbound traffice


- Security groups are associated with network interfaces

- Security groups do not filter traffic to or from link-local addresses or AWS-reserved address