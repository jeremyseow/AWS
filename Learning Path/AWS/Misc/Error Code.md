# Error Codes

Throttling: HTTP 502 or 429
If executing the function would cause you to exceed a concurrency limit at either the account level (`ConcurrentInvocationLimitExceeded`) or function level (`ReservedFunctionConcurrentInvocationLimitExceeded`), Lambda may return a `TooManyRequestsException` as a response

- 4XX errors
	- 403 Error
		-  Authorization failures for missing authentication token error, invalid AWS signature error, or Amazon Cognito authentication problems
- 5XX errors
	- 502 Bad gateway error
		- A server, while acting as a gateway or proxy, received an invalid response from the upstream server
	- 504 Gateway timeout error
		- A server, which is currently acting as a gateway or proxy, did not receive a timely response from another server further upstream