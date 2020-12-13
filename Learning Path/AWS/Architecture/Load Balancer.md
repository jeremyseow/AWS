# Load Balancer

The nodes for a load balancer distribute requests from clients to registered targets. When cross-zone load balancing is enabled, each load balancer node distributes traffic across the registered targets in all enabled Availability Zones. When cross-zone load balancing is disabled, each load balancer node distributes traffic only across the registered targets in its Availability Zone. With Application Load Balancers, cross-zone load balancing is always enabled.

10 - When cross-zone load balancing is enabled, each of the 10 targets receives 10% of the traffic. This is because each load balancer node can route its 50% of the client traffic to all 10 targets (present in both AZs).

https://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/how-elastic-load-balancing-works.html

[[Error Code#^61edb4|503 error]] in ALB is an indicator of the target groups for the load balancer having no registered targets.