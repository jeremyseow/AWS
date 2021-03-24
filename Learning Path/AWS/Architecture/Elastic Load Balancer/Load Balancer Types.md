# Load Balancer Types


#### Application Load Balancer (ALB)

- Operates at layer 7, the application layer, of the OSI model

- Allows the analysis of the HTTP header to direct traffic

- Supports HTTP, HTTPS, FTP, SMTP, gRPC and NFS etc

-  Cross-zone load balancing always enabled

This is the distribution of requests based on multiple variables, from the network layer to the application layer. It is context-aware and can direct requests based on any single variable as easily as it can a combination of variables. Applications are load balanced based on their peculiar behavior and not solely on server (operating system or virtualization layer) information. This is feature fulled Layer-7 load balancer, HTTP and HTTPS listeners only. Provides the ability to route HTTP and HTTPS traffic based upon rules, host based or path based.
Protocol listener: HTTP, HTTPS, gRPC


#### Network Load Balancer (NLB)

- Operates at layer 4, the transport layer, of the OSI model

- Directs traffic based on TCP or UDP protocols

- Supports TCP, UDP, DNS and TLS etc

- Able to process millions of requests per second, making the NLB a great choice if you need ultra high performance for your application

- Also if your application logic requires a static IP address, then the NLB will need to be your choice of elastic load balancer

- Cross-zone load balancing can be enabled or disabled

This is the distribution of traffic based on network variables, such as IP address and destination ports. It is layer 4 (TCP) and below and is not designed to take into consideration anything at the application layer such as content type, cookie data, custom headers, user location, or the application behavior. Has an IP address, static/elastic.
Protocol listener: TCP, UDP, TLS



#### Classic Load Balancer

- Does not offer as wide a range of features as the other load balancers

- It is considered best practice to use the ALB over this classic load balancer unless you have an existing application running in the EC2-Classic network
	- Any AWS account created after the 12th of April 2013 will not support EC2-Classic
	- Offers the following which the ALB does not
		- It supports EC2-Classic
		- It supports TCP and SSL listeners
		- It supports for sticky sessions using application-generated cookies

- Supports TCP, SSL/TLS, HTTP, and HTTPS protocols

- Cross-zone load balancing can either be enabled or disabled

#### Gateway Load Balancer

#### Comparison
- https://aws.amazon.com/elasticloadbalancing/features/#compare