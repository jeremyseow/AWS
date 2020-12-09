- `Transform` : Specifies the version of the AWS Serverless Application Model (AWS SAM) to use. When you specify a transform, you can use AWS SAM syntax to declare resources in your template.
- `Parameter`: Contains values to pass to your template at runtime when you create or update a stack
- `Resources` : Specify the stack resources and their properties
- `Mappings`: Lists a mapping of keys and associated values that you can use to specify conditional parameter values, similar to a lookup table. You can match a key to a corresponding value by using the `Fn::FindInMap` intrinsic function in the Resources and Outputs sections.
- `Outputs` : An optional Outputs section which declares output values that you can import into other stacks (to create cross-stack references), return in response (to describe stack calls), or view on the AWS CloudFormation console
	- For example, you can output the S3 bucket name for a stack to make the bucket easier to find.
	- You can use the Export Output Values to export the name of the resource output for a cross-stack reference
	- ==For each AWS account, export names must be unique within a region==


#### Guide
- https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/template-anatomy.html