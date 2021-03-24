# Storage Gateway

-  Allows you to provide a gateway between your own data center's storage systems such as your SAN, NAS or DAS and Amazon S3 and Glacier

- The Storage Gateway itself can either be installed as software or physical hardware appliance that can be stored within your own data center which allows integration between your on-premise storage and that of AWS

#### Configurations

- File gateway
	- Allow you to securely store your files as objects within S3
	- Allows you to mount or map drives to an S3 bucket as if the share was held locally on your own corporate network
	- A local on-premise cache is also provisioned for accessing your most recently accessed files to optimize latency which also helps to reduce egress traffic costs




- Volume gateway
	- 2 modes
		- Stored volume gateway
			- Volumes created and configured within the storage gateway are mounted as iSCSI devices that your applications can then communicate with
				- Remain locally on-premise for very low latency data access
			- These volumes are backed by Amazon S3 as EBS snapshots
		- Cached volume gateway
			-  The primary data storage is actually on Amazon S3 rather than your own local storage solution
			-  However cache volume gateways utilize your local data storage as a buffer and the cache for recently accessed data to help maintain low latency
- Tape gateway
	- Known as Gateway VTL. Virtual Tape Library, essentially a cloud-based tape backup solution
	- Allows you again to back up your data to S3 from your own corporate data center in addition to being able to leverage the storage classes within Glacier for data archiving for a far lower cost than S3