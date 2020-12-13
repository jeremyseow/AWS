# API Gateway

- Enables developers to create, publish, maintain, monitor, scale, and secure APIs

- Allows creating, deploying, and managing a RESTful API to expose backend HTTP endpoints, Lambda functions, or other AWS services

- All of the APIs created with Amazon API Gateway expose HTTPS endpoints only. Amazon API Gateway does not support unencrypted (HTTP) endpoints
	- If you use HTTP, you will get Connection refused error

- By default, Amazon API Gateway assigns an internal domain to the API that automatically uses the Amazon API Gateway certificate. When configuring your APIs to run under a custom domain name, you can provide your own certificate for the domain

#### CloudWatch Metrics
- Monitor the `IntegrationLatency` metrics to measure the responsiveness of the backend.
- Monitor the `Latency` metrics to measure the overall responsiveness of your API calls.
 - Monitor the `CacheHitCount` and `CacheMissCount` metrics to optimize cache capacities to achieve a desired performance.

#### Components
- API deployment
	- A point-in-time snapshot


#### Cache

- To invalidate caching for the API clients to get the most recent responses, use the `Header Cache-Control: max-age=0`