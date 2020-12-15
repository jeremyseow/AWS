# Storage

- There are 2 types of storage
	- Instance store volumes
		- Physically reside on the same host that provides your EC2 instance itself, acting as local disc drives, allowing you to store data locally to that instance
		- Used for temporary data that is deleted when you stop, hibernate, or terminate your instance
		- However, if your instance was simply rebooted, your data would remain intact
		- The size of your volumes will increase as you increase the EC2 instance size
		- Provided as a part of the EC2 service, hence, they effectively have the same security mechanisms provided by EC2 (IAM policies etc)
		- Pros
			- Storage used is included in the price of the EC2 instance, so no addtional storage cost
			- ==The IOPS is higher than EBS==
		- Cons
			- Not all instance types support instance store volumes
			- You must enable the volumes when you launch an Amazon EC2 instance, as you ==cannot add instance store volumes to an Amazon EC2 instance once it has been launched==
			
	- [[Elastic Block Storage (EBS)]]
		- Persistant storage
		- Network attached to the instance instead of directly attached like instance store volumes
			- Although the EC2 instance treats the EBS volume as a local disk, the underlying host machine ==reads and writes to the EBS volume over the network==
			- To maintain peak performance for this connection, you can use EBS-optimized instance types. ==EBS-optimized instances reserve dedicated network bandwidth specifically for traffic to the EBS volume==
		- A single EBS volume can only ever be attached to a single EC2 instance but multiple EBS volumes can be attached to a single instance
		- Decoupled from the underlying physical host running the instance
			- Enables you to persist data even if your instance is no longer running on the physical host


#### Root device volume

- Contains the [[Amazon Machine Image (AMI)|AMI]] used to boot the instance
	- Instance store-backed instances
		- Any data is deleted when the instance is terminated or if it fails
			- ==Instance store-backed instances do not support the *Stop* action==
	- EBS-backed instances
		- An EBS-backed instance can be stopped and later restarted without affecting data stored in the attached volumes
		- When in a stopped state, you can modify the properties of the instance, change its size, or update the kernel it is using, or you can attach your root volume to a different running instance for debugging or any other purpose
		- By default, the root device volume for an AMI backed by Amazon EBS is deleted when the instance terminates
- Significant differences in what you can do with each type of AMI
	- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ComponentsAMIs.html#storage-for-the-root-device

![[Differences between EBS and Instance Volume.png]]


#### Attaching volume
- After you attach an Amazon EBS volume to your instance, it is exposed as a block device
	- ==Does not contain any partition or file system==
- You need to login to the instance and then format the EBS volume with any file system, and then mount the volume for it to be usable
- After you make the EBS volume available for use, you can access it in the same ways that you access any other volume


#### Detaching volume
- If an ==EBS volume is the root device of an instance==, you must stop the instance before you can detach the volume. You cannot unmount the root volume on a running instance
- If not, you can detach an Amazon EBS volume from an instance explicitly or by terminating the instance. However, if the instance is running, you must first unmount the volume from the instance.