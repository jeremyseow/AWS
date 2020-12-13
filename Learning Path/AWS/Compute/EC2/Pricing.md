# Pricing

- On-demand
	- Pay for compute capacity by the hour or the second depending on which instances you run
	- No longer-term commitments or upfront payments are needed
	- You can increase or decrease your compute capacity depending on the demands of your application and only pay the specified per hourly rates for the instance you use
	- Suitable for
		- Users that prefer the low cost and flexibility of Amazon EC2 without any up-front payment or long-term commitment
		- Applications with short-term, spiky, or unpredictable workloads that cannot be interrupted
		- Applications being developed or tested on Amazon EC2 for the 1st time

- Spot
	- Allows you to request spare Amazon EC2 computing capacity for up to 90% off the On-Demand price
	- 3 types 
		- Spot block
		- Spot fleet
		- Spot instance pool
	
![[Spot Instance vs On-Demand Instance.png]]

- Savings plan
	- A flexible pricing model that offer low prices on EC2 and Fargate usage, in exchange for a commitment to a consistent amount of usage (measured in $/hour) for a 1 or 3 year term

- Reserved instances
	- Provides you with a significant discount (up to 75%) compared to On-Demand instance pricing
	- In addition, when Reserved Instances are assigned to a specific AZ, they provide a capacity reservation, giving you additional confidence in your ability to launch instances when you need them
	- Offers 2 classes
			- Standard
				- Provide you with a significant discount (up to 72%) compared to On-Demand Instance pricing,
				- Can be purchased for a 1-year or 3-year term
				- Customers have the flexibility to change the AZ, the instance size, and networking type of their Standard Reserved Instances
			- Convertible
				- Provide you with a significant discount (up to 54%) compared to On-Demand Instances
				- Can be purchased for a 1-year or 3-year term
				- Use this class ==if you need additional flexibility==, such as the ability to use different instance families, operating systems, or tenancies over the Reserved Instance term
		- You can choose between three payment options when you purchase a Standard or Convertible Reserved Instance
			- All upfront option
				- You pay for the entire Reserved Instance term with one upfront payment
				- This option provides you with the largest discount compared to On-Demand Instance pricing
			- Partial upfront option
				- You make a low upfront payment and are then charged a discounted hourly rate for the instance for the duration of the Reserved Instance term
			- No upfront option
				- Does not require any upfront payment and provides a discounted hourly rate for the duration of the term.
	- Suitable for
		- Applications with steady state usage
		- Applications that may require reserved capacity
		- Customers that can commit to using EC2 over a 1 or 3 year term to reduce their total computing costs

- Dedicated host
	- Pay for a ==physical host that is fully dedicated to running your instances==, and bring your existing per-socket, per-core, or per-VM software licenses to reduce costs
	- ==Help you meet compliance requirements==
	- Can be purchased On-Demand (hourly), or as a Reservation for up to 70% off the On-Demand price

- Dedicated Instances
	- Pay, by the hour, for instances that run on ==single-tenant hardware==