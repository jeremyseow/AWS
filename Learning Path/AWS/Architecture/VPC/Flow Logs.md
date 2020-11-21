# Flow Logs
- Capture information about IP traffic going to and from network interfaces in your VPC, which can be published to CloudWatch logs or S3

- Helps you with a number of tasks
	- Diagnose overly restrictive security group rules
	- Monitor the traffic that is reaching your instance
	- Determine the direction of the traffic to and from the network interfaces

- Flow log data is collected outside the path of your network traffic 
	- You can create or delete flow logs without affecting network throughput or latency

- After a flow log is created, it can take a few minutes to begin collecting and publishing data to the chose destinations
	- Does not capture real-time log streams for your network interfaces

- Flow logs can be sent directly to a S3 bucket, which you can retrieve and analyse yourself

- Flow logs do not capture IP traffic to or from link-local addresses or AWS-reserved address

