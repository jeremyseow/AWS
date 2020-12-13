# Event Sources

-  An AWS service or custom service that triggers your function
-  2 types of sources
	-  Push
		-  Services using this push model publish events in addition to invoking your Lambda function
	-  Poll
		- Lambda polls the service looking for events
		- For example, Lambda will poll the message queue for SQS
- 2 types of invocations
	- Synchronous
		- Enables you to assess the result before moving onto the next operation required
		- Maintain the order of the invocations
	- Asynchronous
		- Not waiting for the results of an invocation before moving to the next one
		- Order does not matter

-  When you manually invoke a Lambda function or when your custom-built application invokes it, you have the ability to use the *invoke* option, which allows you to specify if the function should be invoked synchronously or asynchronously. When using event sources to call and invoke your function, the invocation type is very dependent on the actual service itself
	-  [[Invoke API]]

![[Lambda Event Sources.png]]

- List of supported event sources
	- https://docs.aws.amazon.com/lambda/latest/dg/lambda-services.html#supported-event-source-s3


#### Event Source Mapping

- Configuration that links events generated from your event source to your Lambda function
- Where the event source mapping is configured and stored depends on if the event source is push or poll-based
	- Push
		- Mapping is maintained within the event source
		- Using the appropriate API calls for the event source service, you can create and configure the relevant mappings
		- For example, using the *API for S3 bucket notifications*, you can specify which events to publish within that bucket and which of your Lambda function to invoke based on those notifications
		- This will require specific access to allow your event source to invoke the function. And this access is granted through the **Lambda function policy**
	- Poll
		- Mappings are held within your Lambda function instead
		- Using the *CreateEventSourceMapping* API, you can set up the relevant event source mapping for your poll-based service
			- https://docs.aws.amazon.com/lambda/latest/dg/API_CreateEventSourceMapping.html
		- Permission is required in the **Execution role policy**
