# Error Codes

#### HTTP errors
- 5XX errors
	- 502 Bad gateway error
		- A server, while acting as a gateway or proxy, received an invalid response from the upstream server
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