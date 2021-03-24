VPC - VPC : VPC Peering
On-premise - VPC: AWS Direct Connect, VPN, Transit Gateway on VPC side to connect both

![[Pasted image 20210227162211.png]]

#### AWS Transit Gateway
AWS Transit Gateway provides a hub and spoke design for connecting VPCs and on-premises networks. You can attach all your hybrid connectivity (VPN and Direct Connect connections) to a single Transit Gateway consolidating and controlling your organization’s entire AWS routing configuration in one place. It also controls how traffic is routed among all the connected spoke networks using route tables. This hub and spoke model simplifies management and reduces operational costs because VPCs only connect to the Transit Gateway to gain access to the connected networks.

#### AWS CloudHub
Mini Transit Gateway for VPNs only. Simpler to setup