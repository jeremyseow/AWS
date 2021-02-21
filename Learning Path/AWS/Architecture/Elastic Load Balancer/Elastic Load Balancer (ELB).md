# Elastic Load Balancer (ELB)

- By default, the ELB is highly available as this is a managed service provided by AWS

- Help manage and control the flow of inbound requests destined to a group of targets by distributing these requests evenly across the targeted resource group
	- These targets could be a fleet of EC2 instances, Lambda functions, a range of IP addresses, or even Containers
	- The targets defined within the ELB could be situated across different AZs or within a AZ

#### Schemes

- Internet facing
	- Accessible via the Internet and so have a public DNS name that can be resolved with public IP address, in addition to an internal IP address as well
	- Allows the ELB to serve incoming requests from the Internet before distributing and routing the traffic to your target groups
	- When your Internet-facing ELB communicates with its target group, it will only use the internal IP address, meaning that your target group does not need public IP addresses
	
- Internal facing
	- Only has an internal IP address
	- Can only serve requests that originate from within your VPC itself
	- For example, you might have an internal load balancer sitting between your web servers in the public subnet and your application servers in the private subnet

#### Components

- Listener
	- A process that checks for connection requests, using the protocol and port that you have configured

- Rule
	- Associated to each listener that you have configured within your ELB
	- Defines how an incoming request gets routed to which target group
	- Each listener can contain one or more rules, and each rule can contain more than one condition, and all conditions in the rule equal a single action

- Target group
	- A group of resources that you want your ELB to route requests to
	- You can configure your ELB with a number of different target groups, each associated with a different listener configuration and associated rules

- Health check
	-  Allows the ELB to contact each target using a specific protocol to receive a response. If no response is received within a set of thresholds, then the ELB will mark the target as unhealthy and stop sending traffic to that target

- Node
	- During the creation process of your ELBs, you're required to define which AZ you'd like your ELB to operate within
	- For each AZ selected, an ELB node will be placed within that AZ
	- As a result, you need to ensure that you have an ELB node associated to any AZ for which you want to route traffic to
	- Without the AZ associated, the ELB will not be able to route traffic to any targets within that AZ, even if they are defined within the target group
	- This is because the nodes are used by the ELB to distribute traffic to your target groups

- Cross-zone load balancing
	- Depending on which ELB option you select, you may have the option of enabling and implementing Cross-zone load balancing within your environment
	- Regardless of how many targets are in an associated AZ, the ELBs would distribute all incoming traffic evenly between all targets, ensuring each target across the AZ have an even distribution
	
![[Cross-Zone Disabled.png|600]]

![[Cross-Zone Enabled.png|600]]