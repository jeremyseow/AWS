# Concurrency

- The number of instances that serve requests at a given time
- When your function is invoked, Lambda allocates an instance of it to process the event
- When the function code finishes running, it can handle another request. If the function is invoked again while a request is still being processed, another instance is allocated, which increases the function’s concurrency
- Types of concurrency
	- Unreserved concurrency
		- This limit is at the **account level**, so it applies to all the Lambda functions that you have within a single region
		- Default value is 1000, which means you can have 1000 occurrences of Lambda functions running at once
		- You can raise your case to the AWS Support Center to get this soft limit increase for your account
	- Reserved concurrency
		- **Reserves a pool of instances from the unreserved account concurrency**
		- This limit is at the **function level**
		- **The reserved amount is deducted from the unreserved limit**, which means that the other functions will have to share the remaining instances
		- This ensures that your function will continue to run even if other functions have a surge in requests. On the other hand, it also limit the concurrency of your function so that it does not scale out of control
		- **The unreserved concurrency cannot go below 100**, which mean that if the unreserved concurrency limit is 1000, you can only set a concurrency execution limit of 900 to a function or spreaded across multiple functions
	- Provisioned concurrency
		- Lambda service will initialize the requested number of execution environments so they can be ready to respond to invocations
		- **Counts towards a function's reserved concurrency and Regional quotas**
		- If the amount of provisioned concurrency on a function's versions and aliases adds up to the function's reserved concurrency, all invocations run on provisioned concurrency

#### How it works
When you invoke a Lambda function, the invocation is routed to an execution environment to process the request. When a function has not been used for some time, when you need to process more concurrent invocations, or when you update a function, new execution environments are created. The creation of an execution environment takes care of installing the function code and starting the runtime. Depending on the size of your deployment package, and the initialization time of the runtime and of your code, this can introduce latency for the invocations that are routed to a new execution environment. This latency is usually referred to as a “cold start”. For most applications this additional latency is not a problem. For some applications, however, this latency may not be acceptable. When you enable Provisioned Concurrency for a function, the Lambda service will initialize the requested number of execution environments so they can be ready to respond to invocations (will not encounter "cold start")

- https://aws.amazon.com/blogs/aws/new-provisioned-concurrency-for-lambda-functions/