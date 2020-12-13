# AWS Elastic Compute Cloud (EC2)

- Provides scalable computing capacity in AWS 

- Eliminates your need to invest in hardware up front, so you can develop and deploy applications faster

#### Component

- Instance
	- A virtual server in the cloud
	- Its configuration at launch is a copy of the AMI that you specified when you launched the instance
	- You can launch different types of instances from a single AMI
	- After you launch an instance, it looks like a traditional host, and you can interact with it as you would any computer. ==You have complete control of your instances==
		- You can use `sudo` to run commands that require root privileges
	- Your AWS account has a limit on the number of instances that you can have running
		- https://aws.amazon.com/ec2/faqs/#how-many-instances-ec2
- [[Amazon Machine Image (AMI)]]
- Instance types
	- https://aws.amazon.com/ec2/instance-types/
- [[Instance States]]
- Key pairs
	- Secure login information for your instances using key pairs (AWS stores the public key, and you store the private key in a secure place)
- [[Storage]]
- Firewall
	- Enables you to specify the protocols, ports, and source IP ranges that can reach your instances using security groups
- Elastic IP addresses
	-  A static IPv4 address designed for dynamic cloud computing
		-  With it, you can mask the failure of an instance or software by rapidly remapping the address to another instance in your account
		-  An Elastic IP address is for use in a specific region only
		-  By default, all AWS accounts are limited to 5 Elastic IP addresses per region, because public (IPv4) internet addresses are a scarce public resource
- Tags
	- Metadata that you can create and assign to your EC2 resources
- Instance metadata
	- http://169.254.169.254/latest/meta-data/ from within a running instance
	- Not encrypted
- Instance user date
	- http://169.254.169.254/latest/user-data from within a running instance
	- You can pass two types of user data to EC2: shell scripts and cloud-init directives
	- Limited to 16 KB
	- Not encrypted
- [[VPC]]


#### Placement groups

- You can launch or start instances in a placement group, which determines how instances are placed on the underlying hardware
	- Cluster 
		- Clusters instances into a low-latency group in a single AZ
		- Recommended for applications that benefit from low network latency, high network throughput, or both, and if the majority of the network traffic is between the instances in the group
	- Spread
		- Spreads instances across underlying hardware
		- Recommended for applications that have a small number of critical instances that should be kept separate from each other
		- A spread placement group can span multiple AZs, and you can have a maximum of 7 running instances per AZ per group

- The name you specify for a placement group must be unique within your AWS account for the region

- You can’t merge placement groups

- An instance can be launched in 1 placement group at a time; it cannot span multiple placement groups

- Instances with a tenancy of host cannot be launched in placement groups

#### Security
- Only 1 role can be assigned to an EC2 instance at a time, and all applications on the instance share the same role and permissions

- EC2 instances use **instance roles**, AWS CLI uses **roles**

- Use [[AWS Identity & Access Management (IAM)]] to control access to your AWS resources, including your instances
	- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/security-iam.html

- Restrict access by only allowing trusted hosts or networks to access ports on your instance using [[Security Group]]
	- For example, you can restrict SSH access by restricting incoming traffic on port 22
	- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-security-groups.html

- Review the rules in your security groups regularly, and ensure that you apply the ==principle of least privilege==
	- You can also create different security groups to deal with instances that have different security requirements

- Disable password-based logins for instances launched from your AMI
	- Passwords can be found or cracked, and are a security risk

![[EC2 Role.png]]

#### Monitoring

- CPU utilization, Network utilization, Disk performance, Disk Reads/Writes using EC2 metrics
- Memory utilization, disk swap utilization, disk space utilization, page file utilization, log collection using a monitoring agent/CloudWatch Logs
- ==By default, your instance is enabled for basic monitoring==
- You can optionally enable detailed monitoring
	- After you enable detailed monitoring, the Amazon EC2 console displays monitoring graphs with a 1-minute period for the instance
- Basic monitoring
	- Data is available automatically in **5-minute periods at no charge**
- Detailed monitoring
	- Data is available in **1-minute periods for an additional cost**
	- To get this level of data, you must specifically enable it for the instance. For the instances where you’ve enabled detailed monitoring, you can also get aggregated data across groups of similar instances

- To enable detailed monitoring for an existing instance through CLI
	- `aws ec2 monitor-instances --instance-ids i-1234567890abcdef0`
- To enable detailed monitoring when launching an instance through CLI
	- `aws ec2 run-instances --image-id ami-09092360 --monitoring Enabled=true...`
- To turn off detailed monitoring through CLI
	- `aws ec2 unmonitor-instances --instance-ids i-1234567890abcdef0`

#### [[Pricing]]
