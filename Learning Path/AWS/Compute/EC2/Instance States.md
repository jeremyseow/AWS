# Instance States

- Start
	-  Run your instance normally. You are continuously billed while your instance is running
- Stop
	-  Performs a normal instance shutdown, you may restart it again anytime
	-  All EBS volumes remain attached, but data in instance store volumes are deleted
	-  You won’t be charged for usage while instance is stopped
	-  You can attach or detach EBS volumes
	-  You can also create an AMI from the instance, and change the kernel, RAM disk, and instance type while in this state.
- Terminate
	-  Performs a normal shutdown and gets deleted
	-  You won’t be able to restart an instance once you terminate it
	-  The root device volume is deleted by default, but any attached EBS volumes are preserved by default
	-  Data in instance store volumes are deleted
	-  To prevent accidental termination, enable termination protection.