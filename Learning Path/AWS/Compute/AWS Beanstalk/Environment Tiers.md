# Environment Tiers
- Determines how Beanstalk provisions resources based on what the application is designed to do

- Types of tier
	- Web tier
		- Suitable for applications that manages and handle HTTP requests
		- This tier will typically use the following resouces in the environment
			- Route 53
				- When an environment is created by Elastic Beanstalk, it has an associated URL
				- Using the CNAME record in Route 53, this URL is aliased to an ELB
			- Elastic load balancer (ELB)
				- For every environment, you should have at least one ELB sitting in front of your EC2 instances that is referenced by Route 53 
				- This ELB will also integrate with an autoscaling group
			- Auto scaling group
				- For every environment, you will also have an auto scaling group that will manage the capacity planning of your applications based on the load received
			- [[AWS Elastic Compute Cloud (EC2)|EC2]] instances
				- Within the environment, AWS Elastic Beanstalk will create a minimum of 1 EC2 instance to run your application, which will be a part of the auto scaling group
			- [[Security Group|Security group]]
				- Your EC2 instances will be governed by a security group, which by default will allow port 80 open to everyone
			- Host manager
				- Is installed on every EC2 instance within the environment 
				- It collates different metrics and events from the EC2 instance, which can then be reviewed from within the console or via the AWS CLI or API
				- It generates instance-level events, it monitors both the application log files and the application server itself
				- It will also patch instance components
				- It will manage the log files, allowing them to be published at S3
	- Worker tier
		- Suitable for applications that pulls data from a [[Simple Queue Service (SQS)|SQS]] queue
		- This tier will typically use the following resouces in the environment
			- SQS queue
				- If you do not already have an SQS Queue operational and configured, then as a part of the creation of the worker environment AWS Elastic Beanstalk will create one for you
			- IAM Service Role
				- To allow your EC2 instances to monitor queue activity in the SQS Queue, each EC2 instance will have an associated instance profile role which contains a section within the policy as shown
				- Auto scaling group
				- EC2 instances
					- Within the environment, AWS Elastic Beanstalk will create a minimum of 1 EC2 instance to run your application, which will be a part of the auto scaling group, and each EC2 instance in the environment will read from the same SQS Queue
				- Daemon
					- Whereas the web tier used the Host Manager to perform some key tasks for Elastic Beanstalk, instead within a worker tier a Daemon is installed on every EC2 instance to pull requests from your SQS Queue
					- It will also then send data to the application allowing it to process the message. Therefore, the instance profile role is required to ensure permissions are given to read from a queue

- It is likely that you will use the two tiers in conjunction with each other, decoupled by the use of the simple queue service, allowing each environment to scale independently of one another depending on demand through auto scaling and Elastic Load Balancing

![[Web Tier.png]]

![[Worker Tier.png]]