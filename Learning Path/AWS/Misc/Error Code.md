# Error Codes

Throttling: HTTP 502 or 429
If executing the function would cause you to exceed a concurrency limit at either the account level (`ConcurrentInvocationLimitExceeded`) or function level (`ReservedFunctionConcurrentInvocationLimitExceeded`), Lambda may return a `TooManyRequestsException` as a response

- 4XX errors
	- 403 Forbidden error
		-  Authorization failures for missing authentication token error, invalid AWS signature error, or Amazon Cognito authentication problems
-  5XX errors
	-  500 Internal server error
		-  Indicates that the server encountered an unexpected condition that prevented it from fulfilling the request
		-  A generic "catch-all" response. Usually, this indicates the server cannot find a better 5xx error code to response
	- 502 Bad gateway error
		- A server, while acting as a gateway or proxy, received an invalid response from the upstream server
	- 503 Service unavailable error ^61edb4
		- Indicates that the server is not ready to handle the request
		- Common causes are a server that is down for maintenance or that is overloaded
	- 504 Gateway timeout error
		- A server, which is currently acting as a gateway or proxy, did not receive a timely response from another server further upstream


#### AWS service errors
- General
	- CodeStorageExceededException
		- For example, if you have exceeded your maximum total code size per account
	- ResourceConflictException
		- For example, if the resource already exists
	- ServiceException
		- For example, If the AWS Lambda service encountered an internal error
	- InvalidParameterValueException
		- For example, if you provided an IAM role in the CreateFunction API which AWS Lambda is unable to assume