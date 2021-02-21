# Connecting to VPC

## VPN

## Direct connect

## VPC peering

- Allows 2 VPCs to be able to communicate with each other
	-  VPCs might be in the same region to they might be in different regions

-  The peering connection itself here that links the two VPCs is actually run and hosted on the AWS infrastructure

- Peering connection is a one-to-one connection only
	- So, if we had a third VPC down here, call this one VPC-3, again this had additional resources in as well and you had a VPC peering connection between two and three, resources in VPC-1 could not go from VPC-1 and then through VPC-2 to get through to VPC-3. That simply is not allowed as it's a one-to-one connection only. If you wanted VPC-1 to connect to VPC-3, then you'd have to set up a separate VPC peering connection between one and three

- Each VPC cannot have an IP address overlap between them
	- The CIDR blocks cannot overlap because the route table of each VPC will have a entry for its own CIDR block to be routed locally with the VPC

#### Process
Now VPC-1 is going to be known as the requester and VPC-2 is going to be known as the accepter
1. Now the owner of VPC-1 needs to send a VPC peering request to the owner of VPC-2
2. If the VPC accepter is happy with that peering connection, then an acknowledgement and acceptance of that request is sent back to the requester and that's the second stage and this creates the peering connection between the two
3. At this stage, each VPC needs to update their routing tables to allow the traffic from VPC-1 to get to the destination of VPC-2
4. Update the rules of the security groups of the resources to allow the correct resources, ports and protocols to communicate with each other

## Transit gateway

- Serves as a central hub for all your VPC connections, whether it's over Direct Connect, VPN, or peering connection

- For each VPC or remote location that we want to allow to talk to each other, all we need to do is to create a single connection to the Transit Gateway, so one from each of the VPCs and also one each from the remote locations as well

- All the routing is managed centrally within that hub and when any new remote locations or VPCs are created, all you need to do is to connect it to the AWS Transit Gateway and each of these new VPCs can then communicate with the entire rest of your infrastructure

- Allows you to centralize all your monitoring as well for your network traffic and connectivity

![[Transit Gateway Overview.png]]