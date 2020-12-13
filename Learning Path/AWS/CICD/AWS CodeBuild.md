# AWS CodeBuild





- With the Local Build support for AWS CodeBuild, you just specify the location of your source code, choose your build settings, and CodeBuild runs build scripts for compiling, testing, and packaging your code

- You can use the AWS CodeBuild agent to test and debug builds on a local machine

- By building an application on a local machine you can
	- Test the integrity and contents of a buildspec file locally
	- Test and build an application locally before committing
	- Identify and fix errors quickly from your local development environment

- It is not possible to SSH into the CodeBuild Docker container

- You cannot freeze the CodeBuild process but you can stop it

- CodeBuild scales automatically, you do not have to do anything for scaling or for parallel builds