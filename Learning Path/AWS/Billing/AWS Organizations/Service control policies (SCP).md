# Service control policies (SCP)

- Allow you to control what services and features are accessible from within an AWS account
	- These SCPs can either be associated with the Root, OUs, or individual accounts
- Before you start using SCPs, you first need to enable them from the root account of your organization
- When an SCP is applied to any of these objects, ==its associated controls are fed down to all child objects==
![[SCP Inheritance.png]]
- ==SCP does not grant access==
	- It acts as a permission boundary that sets the maximum permission level for the objects that it is applied to
		- ==It has the overriding precedence over identity-based==
	- You will still need to configure your identity-based or resource-based policies to identities, granting permission to carry out actions within your accounts

#### Notes

- SCPs do not affect resource-based policies
	- They only affect principals managed by your accounts in your organization
	
- SCPs affect all users and roles, in addition to the root user
	- However, the root user will still be able to change its own password including MFA settings, manage root access keys, and manage x.509 keys for the root user

- If you disable SCPs in your organization, all SCPs are deleted and removed. Re-enabling SCPs again in the same organization will revert to the default SCP allowing FullAWSAccess

- The following elements are not affected by SCPs: any actions performed by the master account, SCPs do not affect service-linked roles, and managing Amazon CloudFront keys