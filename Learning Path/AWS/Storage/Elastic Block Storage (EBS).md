# Elastic Block Storage (EBS)

- AZ-locked
- To move between AZ and regions, must create a snapshot and create new volume from snapshot in the targeted AZ/region

#### Encryption
- To encrypt a EBS volume, you must create a snapshot, then encrypt snapshot, then restore encrypted volume
- Once encrypted/unencrypted, you can't change the type
- Setting by **region**

#### Attaching volume
- After you attach an Amazon EBS volume to your instance, it is exposed as a block device
	- Does not contain any partition or file system
- You need to login to the instance and then format the EBS volume with any file system, and then mount the volume for it to be usable
- After you make the EBS volume available for use, you can access it in the same ways that you access any other volume


#### Detaching volume
- If an EBS volume is the root device of an instance, you must stop the instance before you can detach the volume. You cannot unmount the root volume on a running instance
- If not, you can detach an Amazon EBS volume from an instance explicitly or by terminating the instance. However, if the instance is running, you must first unmount the volume from the instance.