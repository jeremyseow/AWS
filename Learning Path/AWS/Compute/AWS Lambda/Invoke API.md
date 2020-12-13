# Invoke API

- AWS Lambda supports synchronous and asynchronous invocation of a Lambda function. You can control the invocation type only when you invoke a Lambda function manually or through a custom-built application (referred to as on-demand invocation)

- When you use AWS services as a trigger, the invocation type is predetermined for each service. You have no control over the invocation type that these event sources use when they invoke your Lambda function

- In the Invoke API, you have 3 options to choose from for the InvocationType:

	- `RequestResponse` (default) 
		- Invoke the function synchronously
		- Keep the connection open until the function returns a response or times out
		- The API response includes the function response and additional data

	- `Event` 
		- Invoke the function asynchronously
		- Send events that fail multiple times to the function’s dead-letter queue (if it’s configured)
		- The API response only includes a status code

	- `DryRun` 
		- Validate parameter values and verify that the user or role has permission to invoke the function


#### Guide
- https://docs.aws.amazon.com/lambda/latest/dg/API_Invoke.html