# Route Table vs NACL vs Security Group

Whereas security group rules provide only the capability to allow traffic, network ACL
rules support the ability to allow specific types of traffic and to deny specific traffic.
However, unlike security groups, network ACLs are stateless and do not track connections
and their replies. This means that to allow for a particular traffic flow, both
inbound and outbound rules must allow it for that network ACL

Security groups are used with Amazon EC2 instances, acting as stateful
firewalls. They provide only rules that allow traffic. In comparison, network ACLs
allow traffic between subnets and are stateless. They can allow or deny specific types of
traffic.

Because security groups are stateful,
you are not required to set the outbound rules—the replies to the inbound request are automatically
allowed.