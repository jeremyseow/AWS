# Deployment Options

- CodeDeploy provides two deployment type options:

	- In-place deployment
		- The application on each instance in the deployment group is stopped, the latest application revision is installed, and the new version of the application is started and validated. You can use a load balancer so that each instance is deregistered during its deployment and then restored to service after the deployment is complete
		- ==Only deployments that use the EC2/On-Premises compute platform can use in-place deployments==

	- Blue/green deployment
		- EC2/On-Premises compute platform
			- The instances in a deployment group (the original environment) are replaced by a different set of instances (the replacement environment)
			- ==If you use an EC2/On-Premises compute platform, be aware that blue/green deployments work with Amazon EC2 instances only==

		- Lambda compute platform
			- Traffic is shifted from your current serverless environment to one with your updated Lambda function versions. You can specify Lambda functions that perform validation tests and choose the way in which the traffic shift occurs
			- ==All AWS Lambda compute platform deployments are blue/green deployments==
				- You do not need to specify a deployment type.

		- ECS compute platform
			- Traffic is shifted from the task set with the original version of a containerized application in an Amazon ECS service to a replacement task set in the same service
			- The protocol and port of a specified load balancer listener are used to reroute production traffic. During deployment, a test listener can be used to serve traffic to the replacement task set while validation tests are run.

- CodeDeploy agent 
	- A software package that, when installed and configured on an instance, makes it possible for that instance to be used in CodeDeploy deployments
	- The CodeDeploy agent communicates outbound ==using HTTPS over port 443==
	- CodeDeploy agent is ==required only if you deploy to an EC2/On-Premises compute platform==
		- The agent is not required for deployments that use the Amazon ECS or AWS Lambda compute platform.