# IAM Policy Simulator

- The IAM policy simulator evaluates the policies that you choose and determines the effective permissions for each of the actions that you specify

- The simulator uses the ==same policy evaluation engine that is used during real requests to AWS services.== But the simulator differs from the live AWS environment in the following ways:
	- The simulator ==does not make an actual AWS service request, so you can safely test requests that might make unwanted changes to your live AWS environment==
	- Because the simulator does not simulate running the selected actions, it cannot report any response to the simulated request. The only result returned is whether the requested action would be allowed or denied
	- If you edit a policy inside the simulator, these changes affect only the simulator. The corresponding policy in your AWS account remains unchanged


#### Use case

- Test policies that are attached to IAM users, groups, or roles in your AWS account. If more than one policy is attached to the user, group, or role, you can test all the policies, or select individual policies to test. You can test which actions are allowed or denied by the selected policies for specific resources.

- Test policies that are attached to AWS resources, such as Amazon S3 buckets, Amazon SQS queues, Amazon SNS topics, or Amazon S3 Glacier vaults.

- If your AWS account is a member of an organization in AWS Organizations, then you can test the impact of service control policies (SCPs) on your IAM policies and resource policies.

- Test new policies that are not yet attached to a user, group, or role by typing or copying them into the simulator. These are used only in the simulation and are not saved. Take note that you cannot type or copy a resource-based policy into the simulator. To use a resource-based policy in the simulator, you must include the resource in the simulation and select the checkbox to include that resource’s policy in the simulation.

- Test the policies with selected services, actions, and resources. For example, you can test to ensure that your policy allows an entity to perform the `ListAllMyBuckets, CreateBucket, and DeleteBucket` actions in the Amazon S3 service on a specific bucket.

- Simulate real-world scenarios by providing context keys, such as an IP address or date, that are included in Condition elements in the policies being tested.

- Identify which specific statement in a policy results in allowing or denying access to a particular resource or action.