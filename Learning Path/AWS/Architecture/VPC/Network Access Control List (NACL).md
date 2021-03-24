# Network Access Control List (NACL)

- Each subnet in the VPC must be associated with a NACL
	- If none is specified, it will be associated with the default NACL
	- By default, it allows all inbound and outbound IPv4 traffic and, if applicable, IPv6 traffic

- You can create a custom NACL and associate it with a subnet
	- By default, each custom NACL denies all inbound and outbound traffic until you add rules
	
- 1 subnet can only associated with only 1 NACL, however, 1 NACL can be associated with multiple subnets
	- When you associate a NACL with a subnet, the previous association is removed

- A NACL contains a numbered list of rules that is evaluated in order, starting with the lowest numbered rule
	- The highest number that you can use for a rule is 32766
	- Recommended to create rules in increments (for example, increments of 10 or 100) so that you can insert new rules where you need to later on

- NACLs do not filter traffic to or from link-local addresses or AWS-reserved address

- NACLs are stateless, which means that responses to allowed inbound traffic are subject to the rules for outbound traffic (and vice versa)

![[NACL Example.png]]