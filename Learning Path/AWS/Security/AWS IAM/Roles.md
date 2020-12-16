# Types of Roles

- AWS Service Role
	- This role would be ==used by other services that would assume the role to perform specific functions== based on a set of permissions associated with it
	- Some examples of AWS Service Role would be Amazon EC2, AWS Directory Services, and AWS Lambda, etc 
	- Once you have selected your service role, you would then need to attach a policy with the required permissions, and set a role name to complete its creation

- AWS Service-Linked Role
	- These are very specific roles that are associated to certain AWS services
	- ==They are pre-defined by AWS, and the permissions cannot be altered in any way, as they are set to perform a specific function==
	- Examples of these AWS Service-Linked Roles are Amazon Lex-Bots, and Amazon Lex-Channels
	- Once you have selected your service-linked role, you simply need to assign it a name and complete the creation

- Cross-Account Access
	- ==Providing access between AWS accounts that you own, and providing access between an account that you own and a third party AWS account==
	- The trusting account is the account that has the resources that need to be accessed
	- The trusted account contains the users that need to access the resources in the trusting account
	- A role is created in the trusting account. A trust is then established with the role by entering the AWS acount number of the trusted account
	- Permissions are then applied to the role via policies
	- And the ==group of users in the trusted account then need to have permissions to allow them to assume the role in the trusting account==

- Identity Provider Access Role
	- This role type offers three different options
		- Grant access to web identity providers
			- This is used to create a trust for users using Amazon Cognito, Amazon, Facebook, Google, or any other open ID connect provider
		- Grant web single sign on to SAML providers
			- This allows access for users coming from a SAML provider, which stands for Security Assertion Markup Language
		- Grant API access to SAML providers