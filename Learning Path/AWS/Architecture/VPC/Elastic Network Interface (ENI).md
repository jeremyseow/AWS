# Elastic Network Interface (ENI)

- Logical virtual network cards within your VPC, that you can create, configure, and attach to your EC2 instances

- The configuration is bound to the ENI and not the instance that it is attached to
	- ==You can detach your ENI from one instance, and reconnect it to another instance and the configuration of that ENI would move with it==
	- For example, a private IP address or an elastic IP address or it's MAC address
	- All traffic originating from and being sent to an ENI can be captured using VPC flow logs
	- Quantity of interfaces is dependent on the EC2 instance type

- When you create an instance your EC2 instance comes configured with a primary network interface that is already bound to your instance
	- ==This can't be removed or detached==
	- Labeled Eth0

- Useful for when you need your instances to have multiple network interfaces
	- For example, you may want your instance to be conncted to different subnets
	