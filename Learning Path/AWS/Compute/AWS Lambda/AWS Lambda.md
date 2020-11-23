# AWS Lambda
Below are some of the best practices in working with AWS Lambda Functions:

 – Separate the Lambda handler (entry point) from your core logic.

 – Take advantage of Execution Context reuse to improve the performance of your function

 – Use AWS Lambda Environment Variables to pass operational parameters to your function.

 – Control the dependencies in your function’s deployment package.

 – Minimize your deployment package size to its runtime necessities.

 – Reduce the time it takes Lambda to unpack deployment packages

 – Minimize the complexity of your dependencies

 – Avoid using recursive code