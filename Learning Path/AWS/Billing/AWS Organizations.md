# AWS Organizations

- As businesses expand their footprint on AWS and utilize more services to build and deploy their applications, it will soon become apparent that multiple AWS accounts are required to manage the environment and infrastructure effectively

- However, it is difficult to manage multiple accounts as separate entities
	- The more accounts you have, the more distributed your environment becomes and the associated security risks and exposures increase and multiply

- AWS Organizations provide a means of centrally managing and categorizing multiple AWS accounts that you own, bringing them together into a single organization, which helps to maintain your AWS environment from a security, compliance, and account management perspective

#### Components
![[AWS Organizations Components.png]]
- Organizations
	- Serves to form a hierarchical structure of multiple AWS accounts
	- You could think of an organization as a family tree which provides a graphical view of your entire AWS account structure
	
- Root
	- A container that resides at the top of your Organization
	- All of your AWS accounts and OUs will sit underneath this Root
	- Within any Organization, there will only be 1 Root object
	
- Organizational units (OU)
	- Simply containers that allow you to group together specific AWS accounts
	- An OU can connect directly below the Root or even below another OU (which can be nested up to 5 times)
	
- Accounts
	- Your AWS accounts that you use and create to be able to configure and provision AWS resources
	- Each of your AWS accounts has a 12 digit account number
	
- Service control policies (SCP)
	- Allow you to control what services and features are accessible from within an AWS account
		- These SCPs can either be associated with the Root, OUs, or individual accounts
	- Before you start using SCPs, you first need to enable them from the root account of your organization
	- When an SCP is applied to any of these objects, ==its associated controls are fed down to all child objects==
	- ==SCP does not grant access==
		- It acts as a permission boundary that sets the maximum permission level for the objects that it is applied to
			- ==It has the overriding precedence over identity-based and resource-based policies==
		- You will still need to configure your identity-based or resource-based policies to identities, granting permission to carry out actions within your accounts

- *Master account*
	-  A master account is just a standard AWS account that you have chosen to create the AWS Organizations
		-  ==It is best practice to use this AWS account solely as a master account==, and not to use it to provision any other resources such as EC2 instances, etc
		-  This allows you to restrict access to the master account at a greater level
		-  The few users who need access to it, the better, and you need to do this because ==the master account carries certain administrative level capabilities== such as being able to create additional AWS accounts within your organization, invite other accounts to join your organization, remove AWS accounts from your organization, and apply security features via policies to different levels within your organization

#### Benefits

-  Centrally manage multiple Accounts from a master account
	-  You can start by inviting your existing accounts to an Organization and then create new accounts directly from the master account

- Greater control of your AWS environment
	- Using SCPs, administrators of the master account gain powerful control over which services, features, or even specific API calls, that an IAM user within those accounts can use, ==regardless of the user’s identity-based or resource-based permissions==

- Consolidated Billing
	- The master account of your AWS Organization can be used to consolidate the billing and costs from all member AWS accounts
	- This allows for greater overall cost management across your individual AWS accounts

- Categorization and grouping of accounts
	- By leveraging OUs, you can segregate and group specific AWS accounts together, applying different SCPs associated to each OU
	- For example, you may have a number of AWS accounts that must not have the ability to access any AWS Analytical services
		- In this case, you could place these accounts into a single OU and assign an SCP that denies this functionality