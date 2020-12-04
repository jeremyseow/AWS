# Task Placement Strategy

- A task placement strategy is an algorithm for selecting instances for task placement or tasks for termination
- Task placement strategies can be specified when either running a task or creating a new service.
- Amazon ECS supports the following task placement strategies:
	- Binpack 
		- Place tasks based on the least available amount of CPU or memory
		- This minimizes the number of instances in use.
	- Random 
		- Places tasks on instances at random yet still honors the other constraints that you specified, implicitly or explicitly
		- Specifically, it still makes sure that tasks are scheduled on instances with enough resources to run them
	- Spread
		- Place tasks evenly based on the specified value
		- Accepted values are attribute key-value pairs, instanceId, or host.