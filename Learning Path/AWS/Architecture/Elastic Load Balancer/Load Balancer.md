#### Network Load Balancer
This is the distribution of traffic based on network variables, such as IP address and destination ports. It is layer 4 (TCP) and below and is not designed to take into consideration anything at the application layer such as content type, cookie data, custom headers, user location, or the application behavior. Has an IP address, static/elastic.
Protocol listener: TCP, UDP, TLS

#### Application Load Balancer
This is the distribution of requests based on multiple variables, from the network layer to the application layer. It is context-aware and can direct requests based on any single variable as easily as it can a combination of variables. Applications are load balanced based on their peculiar behavior and not solely on server (operating system or virtualization layer) information. This is feature fulled Layer-7 load balancer, HTTP and HTTPS listeners only. Provides the ability to route HTTP and HTTPS traffic based upon rules, host based or path based.
Protocol listener: HTTP, HTTPS, gRPC