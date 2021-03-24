VPC endpoint -  Enables private connections between your VPC and supported AWS services. Can attach endpoint policy (controls access to service, modify route table)
- Endpoint Policy: Controls access to the service to which you are connecting. You can modify the endpoint policy attached to your endpoint and add or remove the route tables used by the endpoint. An endpoint policy does not override or replace IAM user policies or service-specific policies (such as S3 bucket policies). It is a separate policy for controlling access from the endpoint to the specified service. e.g. to control access to trusted s3, create endpoint policy for s3 buckets

VPC Gateway Endpoint - For S3 and Dynamo
VPC Interface Endpoint - For general AWS services except S3 and Dynamo
NAT Gateway - Put in public subnets, for private subnets to gain access to the internet
Customer Gateway - Put in client side, talk to Virtual Private Gateway in AWS side for VPN connection