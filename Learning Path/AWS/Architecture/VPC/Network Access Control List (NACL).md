# Network Access Control List (NACL)
- Each subnet in the VPC must be associated with a NACL
	- If none is specified, it will be associated with the default NACL

- 1 subnet can only associated with only 1 NACL, however, 1 NACL can be associated with multiple subnets

- A NACL contains a numbered list of rules that is evaluated in order, starting with the lowest numbered rule
	- The default NACL is configured to allow all traffic in and out of the subnets associated with it

- NACLs do not filter traffic to or from link-local addresses or AWS-reserved address