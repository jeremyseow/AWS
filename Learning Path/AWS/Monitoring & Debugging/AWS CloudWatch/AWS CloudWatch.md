# AWS CloudWatch

- A service that that monitors AWS resources and the applications you run on AWS in real time

- You can use CloudWatch to collect and track metrics, which are variables you can measure for your resources and applications

- CloudWatch is ==basically a metrics repository==
	- An AWS service, such as EC2, puts metrics into the repository, and you retrieve statistics based on those metrics
	- If you put your own custom metrics into the repository, you can retrieve statistics on these metrics as well
	
- You can use metrics to calculate statistics and then present the data graphically in the CloudWatch console

![[CloudWatch Overview.png]]

#### Monitoring
- The basic monitoring data is available automatically in a 5-minute interval and detailed monitoring data is available in a 1-minute interval for EC2

- Using high-resolution custom metric, your applications can publish metrics to CloudWatch with 1-second resolution

- You can alert with High-Resolution Alarms, as frequently as 10-second periods. High-Resolution Alarms allow you to react and take actions faster and support the same actions available today with standard 1-minute alarms
	 - https://aws.amazon.com/blogs/aws/new-high-resolution-custom-metrics-and-alarms-for-amazon-cloudwatch/


#### Component
- Namespace
	- A container for CloudWatch metrics
	- There is no default namespace
	- Uses the following naming convention: AWS/*service*
- Metric
	- Represents a time-ordered set of data points that are published to CloudWatch
	- Exists only in the region in which they are created
	- Cannot be deleted, but expires after 15 months if no new data is published to them
		- As new data points come in, data older than 15 months is dropped
	- Each data point must be marked with a timestamp
		- The timestamp can be up to 2 weeks in the past and 2 hours unto the future
		- If you do not provide a timestamp, CloudWatch creates a timestamp based on the time the data point was received
- Dimension
	- A name-value pair that uniquely identifies a metric
	- You can assign up to 10 dimensions to a metric
- Statistic
	- Metric data aggregation over specified periods of time
	- A period is the length of time associated with a specific statistic
		- The default value is 60 seconds
	- CloudWatch aggregates statistics according to the period length that you sepcify when retrieving statistics
- Value
	- The measurement for the data point
- Unit
	- Unit of measurement used to label your data. This offers a better understanding of what the value represents
	- Example units include Bytes, Seconds, Count, and Percent. If you do not specify a unit in CloudWatch, your data point units are designated as None

#### Retention period
- CloudWatch stores this data based on the retention period, which is the length of time to keep data points available
- Data points are stored in CloudWatch based on how often the data points are published
	- Data points with a published frequency less than 60 seconds are available for 3 hours (high-resolution, custom metrics)
	- Data points with a published frequency of 60 seconds (1 minute) are available for 15 days (standard resolution)
	- Data points with a published frequency of 300 seconds (5 minutes) are available for 63 days
	- Data points with a published frequency of 3,600 seconds (1 hour) are available for 455 days (15 months)

#### [[Alarm]]

#### [[Event]]

#### Guide
- https://tutorialsdojo.com/amazon-cloudwatch/