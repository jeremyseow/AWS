# Elastic File System (EFS)

- A fully managed, highly available and durable service that allows you to create shared file systems that can easily scale to petabytes in size with low latency access

- It uses standard operating system APIs, so any application that is designed to work with standard operating system APIs will work with EFS
	- It supports both NFS versions 4.1 and 4.0 and uses standard file system semantics such as strong consistency and file locking

- It is replicated across availability zones in a single region making EFS a highly reliable storage service

- Can be accessed by multiple instances, it makes it a very good storage option for applications that scale across multiple instances allowing for parallel access of data

- EFS is regional, and so any application deployments that span across multiple availability zones can all access the same file systems providing a level of high availability of your application storage layer

#### Storage Class
- There are currently 2 different storage classes
	- EFS Standard (default storage used)
	- EFS Infrequent Access (EFS-IA)

|Standard|Infrequent Access|
|----------|-------------------|
|Can be accessed anytime|An increased first-byte latency impact when both reading and writing data|
|Charged on the amount of storage space used per month|Charged for the amount of storage space used, which is cheaper than Standard. But you are also charged for each read and write operation|
|Same level of availability and durability|Same level of availability and durability|

- EFS also offers lifecycle management and when enabled, EFS will automatically move data between the Standard storage class and the EFS-IA storage class
	- This process occurs when a file has not been read or written to for a set period of days, which is configurable, and your options for this period range include 14, 30, 60, or 90 days
	- Each time the file is accessed again, the timer is reset, and it is moved back to the Standard storage class
	- The only exceptions to data not being moved to the IA storage class is for any files that are below 128Kb in size and any metadata of your files, which will all remain in the Standard storage class

#### Throughput Mode
- There are 2 modes of throughput
	- Burst (default mode)
	- Provisioned

|Burst|Provisioned|
|------|------------|
|Suitable for consistent activities|Suitable for random period of high activities or if your file system is small but required high throughput|
|Amount of throughput scales as your file system grows, baseline rate of 50 KB/s per GB for Standard class|Allows you to burst above your allocated allowance, which is based upon your file system size|
|Does not incur any additional charges|Incur additional charges where you will need to pay for any bursting above the default capacity allowed from the standard bursting throughput|
