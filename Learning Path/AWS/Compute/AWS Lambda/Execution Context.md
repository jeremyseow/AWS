# Execution Context

- The execution context is a temporary runtime environment that initializes any external dependencies of your Lambda function code, such as database connections or HTTP endpoints

- This affords subsequent invocations better performance because there is no need to “cold-start” or initialize those external dependencies

- After a Lambda function is executed, AWS Lambda maintains the execution context for some time in anticipation of another Lambda function invocation. In effect, the service freezes the execution context after a Lambda function completes, and thaws the context for reuse, if AWS Lambda chooses to reuse the context when the Lambda function is invoked again. This execution context reuse approach has the following implications:
	- Any declarations in your Lambda function code (outside the handler code, see Programming Model) remains initialized, providing additional optimization when the function is invoked again
		- For example, if your Lambda function establishes a database connection, instead of reestablishing the connection, the original connection is used in subsequent invocations
		- It is recommended to add logic in your code to check if a connection exists before creating one.
	- Each execution context provides 512 MB of additional disk space in the */tmp* directory
		- The directory content remains when the execution context is frozen, providing transient cache that can be used for multiple invocations
		- You can add extra code to check if the cache has the data that you stored.
	- Background processes or callbacks initiated by your Lambda function that did not complete when the function ended resume if AWS Lambda chooses to reuse the execution context
		- You should make sure any background processes or callbacks (in case of Node.js) in your code are complete before the code exits.