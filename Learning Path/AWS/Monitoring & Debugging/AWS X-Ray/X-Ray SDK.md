# X-Ray SDK

- The SDK provides
	- Interceptors
		- To add to your code to trace incoming HTTP requests
	- Client handlers
		- To instrument AWS SDK clients that your application uses to call other AWS services
	- HTTP clients
		- to instrument calls to other internal and external HTTP web services

- Supports tracing for applications written in Node.js, Java, and .Net

- Instead of sending trace data directly to the X-Ray service, the SDK sends JSON segment documents to an X-Ray daemon 

- The daemon buffers segments in a queue and uploads them to X-Ray in batches