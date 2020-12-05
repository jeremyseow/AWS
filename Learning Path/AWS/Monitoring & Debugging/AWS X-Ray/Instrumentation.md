# Instrumentation

- To instrument X-Ray with the following services
	- Docker application hosted on an ECS cluster
		- Create a Docker image that runs the X-Ray daemon, upload it to a Docker image repository, and then deploy it to your Amazon ECS cluster
		- In addition, you also have to configure the port mappings and network mode settings in your task definition file to allow traffic on UDP port 2000
	- EC2 instances
		- Manually installing the X-Ray daemon to the instances via a user data script
	- Elastic Beanstalk
		- X-Ray daemon is already built-in in Elastic Beanstalk
		- Enable it by adding the *xray-daemon.config* configuration file to folder *ebextensions* or through console settings
	- Lambda
		- X-Ray automatically runs in the background when you enable tracing for your functions