# ELB with Auto Scaling

- For example, let's say you have an ELB configured but without any auto scaling. You will need to ensure that you manually add and remove targets based upon the demand. You will need to monitor this demand allowing you to manually add or remove instances as required

- Now let's look at the reverse. Let's assume you have EC2 auto scaling configured but no elastic load balancer. How are you going to evenly distribute traffic to your EC2 fleet?

- When you attach an ELB to an auto scaling group, the ELB will automatically detect the instances and start to distribute all traffic to the resources in the auto scaling group

- When you want to associate an application load balancer or network load balancer, you associate the auto scaling group with the ELB target group. When you attach a classic load balancer, the EC2 fleet will be registered directly with the load balancer