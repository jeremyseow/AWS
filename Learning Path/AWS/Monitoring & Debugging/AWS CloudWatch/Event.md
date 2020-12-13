# Event

- Deliver near real-time stream of system events that describe changes in AWS resources

- CloudWatch Events becomes aware of operational changes as they occur

- Events respond to these operational changes and take corrective action as necessary, by sending messages to respond to the environment, activating functions, making changes, and capturing state information

- You can also use CloudWatch Events to schedule automated actions that self-trigger at certain times using cron or rate expressions
	- https://docs.aws.amazon.com/AmazonCloudWatch/latest/events/ScheduledEvents.html

- Support services
	- https://docs.aws.amazon.com/AmazonCloudWatch/latest/events/EventTypes.html

#### Components

- Event
	- An event indicates a change in your AWS environment
	- AWS resources can generate events when their state changes
	- For example
		- Amazon EC2 generates an event when the state of an EC2 instance changes from pending to running
		- Amazon EC2 Auto Scaling generates events when it launches or terminates instances
		- AWS CloudTrail publishes events when you make API calls
		- You can generate custom application-level events and publish them to CloudWatch Events
		- You can also set up scheduled events that are generated on a periodic basis

- Rule
	- A rule matches incoming events and routes them to targets for processing
	- A single rule can route to multiple targets, all of which are processed in parallel
	- Rules are not processed in a particular order
		- This enables different parts of an organization to look for and process the events that are of interest to them
	- A rule can customize the JSON sent to the target, by passing only certain parts or by overwriting it with a constant

- Target
	- A target processes events
	- Targets can include Amazon EC2 instances, AWS Lambda functions, Kinesis streams, Amazon ECS tasks, Step Functions state machines, Amazon SNS topics, Amazon SQS queues, and built-in targets
	- A target receives events in JSON format
	- ==A rule's targets must be in the same Region as the rule==