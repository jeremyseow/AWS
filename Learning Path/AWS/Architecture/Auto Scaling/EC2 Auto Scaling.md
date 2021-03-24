# EC2 Auto Scaling
 
- Automatically allows you to increase or decrease your EC2 resources to meet the demand based off of custom defined metrics and thresholds

#### Components

- Configuration
	- Launch template
		- Essentially a newer and more advanced version of the launch configuration
		- Allows you to have multiple versions of a template
			- With versioning, you can create a subset of the full set of parameters and then reuse it to create other templates or template versions
	- Launch configuration
	- Both define how an auto scaling group builds new EC2 instances
		- Which [[Amazon Machine Image (AMI)|AMI]] to use
		- Which instance type to select
		- If you'd like to use Spot Instances to help lower costs
		- If and when public IP addresses should be used for your instances
		- If any user data is required for automatic scripting on first boot
		- What storage volume configuration should be used
		- What security group should be applied
		- Etc
	- Without either the launch configuration or launch template, Auto scaling would not know what instance it was launching and to which configuration
		- You need to have your launch configuration or template defined 1st

- Auto scaling group
	- Defines the desired capacity and other limitations of the group using scaling policies and where the group should scale your resources, such as which AZ
	- Scaling policies can be used to scale out or scale in the instances
		- Alarms can be created so that auto scaling knows when to execute the policies
			- The alarm will be activated when certain metric breaches the threshold for a number of period of time
			- Eg: whenever the average CPU utilization is greater than or equal to 75% for 1 consecutive period of 5 minutes
	- Can be integrated with SNS to send notifications when alarms are triggered or when instances are started, stopped etc