- Configuration Item (CI): JSON with configuration information, relationship information, and other metadata of a resource
- Configuration History: Set of all CIs for a resource's history
	- Delivered every 6 hrs
- Configuration Streams: SNS topic to analyse data
- Configuration Snapshots: Point in time snapshot of resources in a **region**
- Configuration Recorder: Records changes and generates CI
- Config Rules: Enforce controls for resources. Change is sent to Lambda and evaluated against rules. **Does not stop service**. e.g: Check if RDS/EBS is encrypted

When a resource changes:
- Record CI of related resources
- Send CI to configuration stream