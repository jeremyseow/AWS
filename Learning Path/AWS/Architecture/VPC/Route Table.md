# Route Table

- A route table contains a set of rules, called routes, that are used to determine where network traffic is directed

- Each subnet in your VPC must and can only be associated with 1 route table at a time, but you can associate multiple subnets with the same route table
	- The table controls the routing for the subnet

- Every subnet that is created is automatically associated with the main route table of the VPC, created by AWS
	- You can change the association, and you can edit the main route table

- The default limit of number of route tables per VPC is 200