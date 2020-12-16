# AWS CloudFormation

## Terminology
A **stack set** lets you create stacks in AWS accounts across regions by using a single AWS CloudFormation template. All the resources included in each stack are defined by the stack set’s AWS CloudFormation template. As you create the stack set, you specify the template to use, as well as any parameters and capabilities that the template requires.

**Change Sets** allow you to preview how proposed changes to a stack might impact your running resources

By default, CloudFormation stack operations perform with the permissions of the user performing the operation
- CloudFormation can operate using a service role; however, this must be explicitly passed as part of the stack operation
	

## Installation
AWS CloudFormation provides the following Python helper scripts that you can use to install software and start services on an Amazon EC2 instance that you create as part of your stack

`cfn-init`
- Use to retrieve and interpret resource metadata, install packages, create files, and start services

`cfn-signal`
- Use to signal with a *CreationPolicy or WaitCondition*, so you can synchronize other resources in the stack when the prerequisite resource or application is ready
	- Any issues preventing the instance from calling `cfn-signal` and sending a success/failure message to CloudFormation would cause the *CreationPolicy* to time out
	- For example
		- The user data script does not include a call to `cfn-signal`
		- The user data script fails before reaching the `cfn-signal` step
		- The instance cannot connect to the AWS CloudFormation endpoint when calling `cfn-signal`

`cfn-get-metadata`
- Use to retrieve metadata for a resource or path to a specific key

`cfn-hup`
- Use to check for updates to metadata and execute custom hooks when changes are detected