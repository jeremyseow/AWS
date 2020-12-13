# Simple Queue Service (SQS)

- A fully managed service offered by AWS that works seamlessly with serverless systems, mock services, and any distributed architecture, allowing delivery of messages between components

- SQS has a message size limit of 256 KB
	- Use Amazon SQS Extended Client Library for Java for storing and consuming messages up to 2 GB

- You can retrieve up to 10 messages at a time
	- You cannot specify which messages to retrieve

#### Component
- Queue
	- Managed by SQS and is managed across several SQS servers for resiliency
- Producer
	- Sends messages to the queue
- Consumer
	- Processes messages in the queue

#### Settings
- Visibility timeout
	- Default time is 30 seconds, min is 0 seconds and max is 12 hours
	- To prevent other consumers from receiving and processing the same message
	- The value of your visibility timeout should be longer than it takes for your consumers to process your messages
	- Use `ChangeMessageVisibility` action to extend a message's visibility timeout
	- https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-visibility-timeout.html

- Retention period
	- SQS automatically deletes messages that have been in a queue for more than the maximum message retention period
	- The default message retention period is 4 days, min is 60 seconds and max is 14 days
	- Use `SetQueueAttributes` action action to change the retention period

#### How it works
1. Producers send messages to queue
2. SQS service stores the message across several SQS servers for resiliency within the specified queue
3. Consumer will then process the message. At this point, the message is retrieved from the queue and is then marked as being processed by activating the **visibility timeout** on the message
4. After the consumer has finished processing, it will send a delete request to SQS to delete the message
	- If the **visibility timeout** expires and SQS does not receive the request to delete the message, the message will become available again in the queue for other consumers to process
	- This message will then appear as a new message to the queue

#### Queue types
- Standard 
	- Default configuration
- First-in-first-out (FIFO)
	- The message group ID is the tag that specifies that a message belongs to a specific message group. Messages that belong to the same message group are always processed one by one, in a strict order relative to the message group (however, messages that belong to different message groups might be processed out of order)



#### Guide

- https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-basic-architecture.html


#### Use case
When you invoke a function synchronously, Lambda runs the function and waits for a response. Queues are generally used with asynchronous invocations since queues implement the decoupling feature of various connected systems. It does not make sense to use queues when the calling code will wait on it for a response.