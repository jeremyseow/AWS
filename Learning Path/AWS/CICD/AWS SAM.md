# AWS SAM

- An open-source framework for building serverless applications

- It provides shorthand syntax to express functions, APIs, databases, and event source mappings

- SAM supports the following resource types:

	- AWS::Serverless::Api
		- This creates a collection of Amazon API Gateway resources and methods that can be invoked through HTTPS endpoints
		- It is useful for advanced use cases where you want full control and flexibility when you configure your APIs
	- AWS::Serverless::Application
	- AWS::Serverless::Function
		- This resource creates a Lambda function, IAM execution role, and event source mappings that trigger the function
	- AWS::Serverless::HttpApi
	- AWS::Serverless::LayerVersion
	- AWS::Serverless::SimpleTable
		- This creates a DynamoDB table with a single attribute primary key
		- It is useful when data only needs to be accessed via a primary key
	- AWS::Serverless::StateMachine

- "Transform" section of CloudFormation
	- Lets you locally build, test, debug serverless application
	- `sam package` == `aws cloudformation package`: Packages the artifact
	- `sam deploy` == `aws cloudformation deploy`: Deploys the artifact
	- `sam publish`: Publishes application to AWS Serverless Application repository

- After you deploy a SAM template to  CloudFormation, the `AWS::Serverless transform` is executed and an CloudFormation-supported template is generated
	- CloudFormation processes transformations by creating a change set, which generates a CloudFormation supported template
	- This template is saved by CloudFormation and can be downloaded using the `get-stack-template` AWS CLI command but you ==cant get the original template anymore==