# Security Group

- Controls inbound and outbound traffic for your instances
	-  You can specify allow rules, but not deny rules
		-  If there is a rule in there, then it's considered allowed, if there's no rule, then all traffic is dropped by default

- There is no rule number with the security group
	- All the rules within the security group will be assessed before a decision is made on the action

- You can associate 1 - 5 security groups to your instances in the VPC

- If no security group is specified, the instance will be associated with a default security group

- When a security group is created, by default
	- It has no inbound rules
	- Has an outbound rule that allows all outbound traffice

- Security groups are associated with network interfaces

- Security groups do not filter traffic to or from link-local addresses or AWS-reserved address