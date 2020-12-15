# Elastic Block Storage (EBS)

- Offers persistent and durable block level storage

- ==Provides *[[Storage Concepts#^34ecc5|read-after-write consistency]]* for all operations==

- AZ-locked
	- To move between AZ and regions, must create a snapshot and create new volume from snapshot in the targeted AZ/region

- Provide point-in-time backup snapshots of the entire volume as and when you need to
	- You can manually invoke a snapshot of your volume at any time, or create some code to perform this automatically on a scheduled basis
	- The snapshots themselves are then stored on [[Amazon S3]] for long-term durability
	- The snapshots are incremental
		- Each snapshot will only copy data that has changed since the previous snapshot was taken
	- If access to the EBS volume is lost, you can recreate the data volume from an existing snapshot and then attach that volume to a new EC2 instance
	- It is possible to copy a snapshot from one region to another

- Your EBS volume is only available in a single [[Availability Zone|AZ]]
	- However, you can recreate the volume from your previous snapshot, which is accessible from all AZs within that region, and attach it to another instance in another AZ

- 2 ways to scale up your volume
	- Modifying the volume within the console or via the AWS CLI
		- Once the volume has been increased, you would then need to extend the filesystem on the OS of the EC2 instance to see the new volume
	- Creating a snapshot of your existing volume and then creating a new volume from that snapshot with an increased capacity size


#### Security

- Amazon EBS works with AWS KMS to encrypt and decrypt your EBS volume
	- Uses AES-256
	- Only available on selected instance types
	
- You can encrypt both the boot and data volumes of an EC2 instance

- To encrypt a EBS volume, you must create a snapshot, then encrypt snapshot, then restore encrypted volume
	- Once encrypted/unencrypted, ==you cannot change the type==
	- ==Setting by region==

- When you create an encrypted EBS volume and attach it to a supported instance type, ==the following types of data are encrypted==
	- Data at rest inside the volume
	- All data moving between the volume and the instance
	- All snapshots created from the volume
	- All volumes created from those snapshots

- Encryption by default
	- Encryption by default is a Region-specific setting. ==If you enable it for a Region, you cannot disable it for individual volumes or snapshots in that Region==
	- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSEncryption.html


#### Monitoring

- AWS CloudTrail event logs for 'CreateVolume' aren't available for EBS volumes created during an EC2 launch.


#### [[AWS/Storage/EBS/Best Practices|Best Practices]]
