Overview of Syntax

- `AWS::Serverless::Api` : API Gateway
- `AWS::Serverless::Application`: Serverless application from the AWS Serverless Application Repository or from an Amazon S3 bucket as a nested application.
- `AWS::Serverless::Function`: Lambda function. You can describe any event source that you want to attach to the Lambda function—such as Amazon S3, Amazon DynamoDB Streams, and Amazon Kinesis Data Streams.
- `AWS::Serverless::LayerVersion`: Lambda layer version that contains library or runtime code needed by a Lambda function. When a serverless layer version is transformed, AWS SAM also transforms the logical ID of the resource so that old layer versions are not automatically deleted by AWS CloudFormation when the resource is updated.
- `AWS::Serverless::SimpleTable`: This resource type provides simple syntax for describing how to create DynamoDB tables.