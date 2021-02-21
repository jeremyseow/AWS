# Cross Region Replication (CRR)

-  By default, S3 will not copy your data across multiple regions, it has to be explicitly configured and enabled

#### Benefits

- Reduce latency of data retrieval
	- If you had multiple data centers, and one of these became unavailable in a disaster, another data center could potentially take the load and run your production environment
	- By configuring CRR to a location that is closer to your Secondary Data Center, latency in data retrieval will be kept to a minimum

- Governance and Compliance
	- Depending on specific compliance controls, there may be a requirement to store backup data across a specific distance from the source
	- By enabling CRR, you can maintain compliance whilst at the same time still have the data in the local region for optimum data retrieval latency