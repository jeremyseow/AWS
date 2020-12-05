# AWS Elastic Compute Cloud (EC2)

- only one role can be assigned to an EC2 instance at a time, and all applications on the instance share the same role and permissions

- EC2 instances use **instance roles**, AWS CLI uses **roles**


![[EC2 Role.png]]

#### Monitoring

- **By default, your instance is enabled for basic monitoring**
- You can optionally enable detailed monitoring
	- After you enable detailed monitoring, the Amazon EC2 console displays monitoring graphs with a 1-minute period for the instance
- Basic monitoring
	- Data is available automatically in **5-minute periods at no charge**
- Detailed monitoring
	- Data is available in **1-minute periods for an additional cost**
	- To get this level of data, you must specifically enable it for the instance. For the instances where you’ve enabled detailed monitoring, you can also get aggregated data across groups of similar instances