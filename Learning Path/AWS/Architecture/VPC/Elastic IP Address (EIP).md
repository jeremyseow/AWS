# Elastic IP Address (EIP)

- When launching an EC2 instance, you can select either a private or public subnet

- If you choose the public subnet, there are 2 option to get a public IP address
	- Auto assign
	- EIP

#### Auto assign

- The instance will be launched with one of AWS's public IP addresses from their pool of availble public addresses

-  The public IP address will remain with that instance until it is stopped or terminated, at which point it will be removed from your instance and returned to the pool

- When the instance is started again, it may receive a different IP address from the pool

#### EIP

- ==If the instance needs a persistent IP address, you should use EIP==

- When you create a persistent EIP address, the IP address is associated with your account rather than an instance
	- This means you can attach an EIP address to an instance or an [[Elastic Network Interface (ENI)|ENI]], and even if you stop the instance its associated with, the same EIP will remain in place
	- You can attach EIP address to an instance only if it has 1 network interface, else you will have to attach it to a network interface

- You can also detach the EIP from an instance and re-attach it to another instance
	- ==However, do bear in mind that when you detach an EIP and it's not associated with a running instance, then you will incur a cost for it==
	- If you no longer need the EIP, you must detach it from the associated instance and release it back to AWS

- If you associate an EIP to an instance that already has a pooled public IP address, then that pooled public address will be released and put back into the pool, and your instance will take on a new EIP address

- You cannot convert an existing pooled public IP address to an EIP