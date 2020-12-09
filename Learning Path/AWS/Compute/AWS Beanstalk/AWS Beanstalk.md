# AWS Beanstalk

-	A managed service that allows you to upload code of your web application along with environment configurations, which will then allow Elastic Beanstalk to automatically provision and deploy the appropriate and necessary resources required within AWS to make the web application operational

-	Elastic Beanstalk is compatible with the following: 
	- Packer Builder, Single Container Docker, Multicontainer Docker, Preconfigured Docker, Go, Java SE, Java with Tomcat, .NET on Windows Server with IIS, Node.js, PHP, Python, and Ruby

- Elastic Beanstalk uses [[AWS CloudFormation]] to launch the resources in your environment and propagate configuration changes
	- AWS CloudFormation supports Elastic Beanstalk application environments as one of the AWS resource types.

- Workflow

![[AWS Beanstalk Workflow.png]]

- Domain name is in the following format
	- *subdomain.region*.elasticbeanstalk.com

#### Components
- Application
	- A logical collection of Elastic Beanstalk components, including environments, versions, and environment configurations
	- It is conceptually similar to a folder
- Application version
	- Refers to a specific, labeled iteration of deployable code for a web application
	- An application version points to an Amazon S3 object that contains the deployable code
	- Applications can have many versions and each application version is unique
	- There is a limit to the number of application version
		- Use **application version lifecycle policy** to delete application version that are old, or when the number of the application version exceeds a threshold
- Environment
	-  Refers to an application version that has been deployed on to AWS resources
	-  The environment is comprised of all the resources created by Elastic Beanstalk and not just an EC2 instance with your uploaded code
	-  Each environment runs only a single application version at a time, however you can run the same version or different versions in many environments at the same time
- Environment configuration
	- A collection of parameters and settings that dictate how an environment will have its resources provisioned by Elastic Beanstalk and how these resources will behave
- Configuration template
	- A starting point for creating unique environment configurations
- [[Environment Tiers|Environment tiers]]

- [[AWS/Compute/AWS Beanstalk/Deployment Options|Deployment options]]

- [[Performance Monitoring|Monitoring]]

#### Pricing
- Beanstalk is free but any resources that are created on your application's behalf, such as EC2 instances, will be charged