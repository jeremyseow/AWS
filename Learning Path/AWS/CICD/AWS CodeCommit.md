# AWS CodeCommit
- A fully-managed source control service that hosts secure Git-based repositories

- The AWS CodeCommit Console lets you visualize your code, pull requests, commits, branches, tags and other settings

- If you add AWS tags to repositories, you can setup notifications to email users about events, such as another user commenting on the code

- You can create triggers based on events, such as a push, will trigger actions, such as emails
	- You can create up to 10 triggers so Amazon SNS or [[AWS Lambda]] for each repository

- You can push your files to 2 repositories at the same time

- Components
	- Repository
		- Where you securly store code and files for your project
		- Where you store the project history as well
	- File
		- A version-controlled, self-contained piece of information available to users of the repository and branch where the file is stored
	- Branch
		- Pointers or references to a commit
		- You can use branches to separate work on different versions of files without impacting work on other branches
	-	Commit
		-	Snapshot of the contents in the repository and any changes
		-	Information such as the author, date and time, and the changes made are    included in the commit
	- Pull request
		- Allows repository users to review, comment on, approve, and merge code changes from one branch to another
	- Approval rule
		- Used to designate users to approve a pull request before the commit is merged

- Security
	- Files are transferred to and from repositories using 
		- HTTPS
			- Static username and password are generated
		- SSH
			- Use public and private keys
	- repositories are automatically encrypted at rest through AWS KMS
	- Temporary access to repositories can be given through SAML, Federation, Cross-account access, Amazon Cognito

- Availability
	- repositories are stored in S3 and DynamoDB

- Monitoring
	- CodeCommit uses IAM to control and monitor who can access your data, as well as how, when, where they can access it
	- CodeCommit monitors your repositories via CloudWatch and CloudTrail
	- Can use SNS to receive notifications about events impacting the repositories

- Pricing

- Limits
	- 1000 repositories by default, can request for more
	- A single blob in a repository cannot be more than 2Gb
	- A single commit should not be more than 20Mb
	- A single file should not be more than 6Mb

- Commands
	- To copy a remote respository to your local computer
		- git clone
	- To connect to the respository after the name is changed
		- git remove set-url \<URL>
	- To push changes to repository
		- git push \<remote-name> \<branch-name>
	- To pull changes from repository
		- git pull \<remote-name> \<branch-name>
	- To create a new commit on a branch
		- git commit -m \<message>
		- AWS CLI command: create-commit
	- To create a new branch in local repository
		- git checkout -b \<new-branch-name>
		- AWS CLI command: create-branch
	- To review changes in a pull request and resolve merge conflicts
		- git diff
	- To merge a pull request
		- git merge