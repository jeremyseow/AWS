# AWS Lambda

- A serverless compute service which has been designed to allow you to run your application code without having to manage and provision your own EC2 instances

- Lambda executes your code only when needed and scales automatically

- Natively supports the following languages
	- Node.js
	- Java
	- C#
	- Go
	- Python
	- Ruby
	- For other languages that are not supported natively, users can provide their custom runtime

#### Components

- Function
	- A script or program that runs in Lambda
	- Lambda passes invocation events to the function, which processes it and returns a response
- Runtime
	-  Lambda runtimes allow functions in different languages to run in the same base execution environment
	-  The runtime sits in-between the Lambda service and your function code, relaying invocation events, context information, and responses between the two
-  [[Lambda Layer]]
-  Version
	-  A published snapshot of your function
-  Alias
	-  Allows you to create a pointer to a specific version of your function
	-  **An alias also has its own ARN**, so you can use the ARN of the alias within configurations, such as the event source mapping, and anytime you want to change the version, just change the alias to point to a different version without changing the configuration
-  [[Event Sources]]
-  Downstream resource
	- Resources that are required during the execution of your Lambda function
	- For example, your function might call upon accessing a specific SNS topic or a SQS queue
- Log stream
	- You can add logging statements to help you identify if your code is operating as expected into a log stream
	- These log streams will essentially be a sequence of events that all come from the same function and are recorded in CloudWatch
	- In addition to log streams, Lambda also sends common metrics of your functions to CloudWatch for monitoring and alerting


#### How it works

- AWS Lambda needs to be aware of your code that you need to run
	- Write the code using the code editor provided by Lambda
	- Upload your application code in the form of one or more Lambda functions
		- Package your code and dependencies in a deployment package, then upload the deployment package to create your Lambda function
		- Use layers to manage your function's dependencies and keep your deployment package small
		- **Lambda stores code in Amazon S3 and encrypts it at rest**
		- https://docs.aws.amazon.com/lambda/latest/dg/gettingstarted-package.html
	- Configure Lambda functions to execute your code upon specific triggers from supported event sources
		- For example, a Lambda function could be triggered when an S3 event occurs, such as an object being uploaded to an S3 bucket
	- Once the trigger is activated, AWS Lambda will run your code, as per your Lambda function, using only the required compute power as defined
	- AWS records the compute time in milliseconds and the quantity of Lambda functions run to ascertain the cost of the service
	- Configure **basic function settings**
		- Description
		- Memory usage
			- Specify the amount of memory used and AWS Lambda then calculates the CPU power required based off this selection
			- Lambda bases this calculation from an instance within the general-purpose family of instances
			- 128 Mb to 10240 Mb
		- Execution timeout
			- Default value of 3 seconds and max of 900 seconds
		- Role required for AWS Lambda to assume and execute the code of your function
	- Environment variables
		- Key value pairs that allow you to incorporate variables into your function without embedding them directly into your code
		- Encrypted at rest and can be encrypted in transit as well
	- Use version and alias to manage function deployment and invocation

#### [[Concurrency]]

#### Monitoring
- AWS Lambda automatically monitors functions on your behalf, reporting metrics through Amazon CloudWatch
	- Invocations
	- Errors
	- Latency
	- DeadLetterErrors
		- This counts the number of times Lambda failed to write the dead letter queue, for example due to misconfigured resources or permission issues
	- Duration
		- How long the function runs for in milliseconds from the point of invocation to when it terminates its execution
	- Throttles
		- How many times the function was invoked and throttled due to the limit of concurrency having been reached
	- IteratorAge
		- Only used for stream-based invocations such as Amazon Kinesis. It measures in time how long Lambda took to receive a batch of records to the time of the last record written to the stream
	- ConcurrentExecutions
		- This is a combined metric for all your Lambda functions that you have running within your AWS account in addition to functions with a custom concurrency limit
		- It calculates the total sum of concurrent executions at any point in time
	- UnreservedConcurrentExecutions
		- Combined metric for all your functions in your account, and it calculates the sum of the concurrency of functions without a custom concurrency limit at any given time
- In addition to these metrics, CloudWatch also gathers log data sent by Lambda
	- You can also add custom logging statements into your function code
		- These logging statements are used to push data to CloudWatch logs automatically in addition to the managed messages that are sent by default
	- CloudWatch will automatically create two different log groups, one for each function
		- The log group name will be prefixed with *aws* and *lambda*

#### Quotas
- https://docs.aws.amazon.com/lambda/latest/dg/gettingstarted-limits.html

#### Lambda@Edge
- Lets you run Lambda functions to customize content that CloudFront delivers, executing the functions in AWS locations closer to the viewer
- The functions run in response to CloudFront events, without provisioning or managing servers
- You can use Lambda functions to change CloudFront requests and responses at the following points
	- After CloudFront receives a request from a viewer (viewer request)
	- Before CloudFront forwards the request to the origin (origin request)
	- After CloudFront receives the response from the origin (origin response)
	- Before CloudFront forwards the response to the viewer (viewer response)

![[Lambda@Edge.png]]

#### [[Best Practices]]

#### Guide

- https://docs.aws.amazon.com/lambda/latest/dg/welcome.html