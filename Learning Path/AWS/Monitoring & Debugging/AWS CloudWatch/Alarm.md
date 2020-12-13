# Alarm

-  CloudWatch watches a single metric over a specified time period, and performs one or more specified actions, based on the value of the metric relative to a threshold over time
	-  Alarm states
		-  OK
			- The metric or expression is within the defined threshold
		- ALARM
			- The metric or expression is outside of the defined threshold
		- INSUFFICIENT DATA 
			- The alarm has just started, the metric is not available, or not enough data is available for the metric to determine the alarm state
			
	- When creating an alarm, you need to specify 3 settings
		- Period
			- Length of time to evaluate the metric
			- When creating an alarm, ==select a period that is >= to the metric's resolution==
				- For example, basic monitoring for Amazon EC2 provides metrics for your instances every 5 minutes
				- When setting an alarm on a basic monitoring metric, select a period of at least 300 seconds (5 minutes)
		- Evaluation period
			- Number of most recent periods, or data points, to evaluate when determining alarm state
		- Datapoints to alarm
			-  Number of data points within the *Evaluation period* that must be breaching to cause the alarm to go to the ALARM state
			-  The breaching data points ==do not have to be consecutive==, they just must all be within the last number of data points equal to *Evaluation period*
			-  If you want the data points to be consecutive, just set *Datapoints to alarm* the same as *Evaluation period*
			
	-  For each alarm, you can specify CloudWatch to treat missing data points as any of the following
		-  Missing
			-  The alarm does not consider missing data points when evaluating whether to change state 
			- Default option
		- NotBreaching
			- Missing data points are treated as being within the threshold
		- Breaching
			- Missing data points are treated as breaching the threshold
		- Ignore
			- The current alarm state is maintained