# Network Address Translation (NAT) Gateway

- Allows instances within a private subnet access to the Internet, but the NAT gateway itself will block all incoming initiations from the Internet

- NAT gateway itself is managed by AWS so you don't have to provision the instance itself
	- You simply create the NAT gateway, specify what subnet it should reside in, and associate an Elastic IP address, and AWS will manage all other configuration
	- Because it is managed by default, AWS will set up multiple NAT gateways for resiliency, but you'll only see the one NAT gateway within your account with the associated ID
	- However, if you have multiple public subnets in different AZs, you will need to set up another NAT gateway within that subnet as well
		- AWS will not automatically deploy a NAT gateway within each of your public subnets

- NAT gateway sits within the public subnet
	- It has to have a public IP address in the form of an EIP which is an Elastic IP address, and this is assigned to the instance itself

- We need to update the route table of our private subnet to include a route to the NAT gateway

![[Route Table for NAT.png]]