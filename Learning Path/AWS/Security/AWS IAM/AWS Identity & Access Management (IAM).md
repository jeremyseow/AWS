# AWS Identity & Access Management (IAM)

If you have resources which are running inside AWS, that needs programmatic access to various AWS services, then the best practice is to always use IAM roles. However, for applications running outside of an AWS environment, these will need access keys for programmatic access to AWS resources. For example, monitoring tools running on-premises and third-party automation tools will need access keys.

Access keys are long-term credentials for an IAM user or the AWS account root user. You can use access keys to sign programmatic requests to the AWS CLI or AWS API (directly or using the AWS SDK).


In order to use the AWS SDK for your application, you have to create your credentials file first at `~/.aws/credentials` for Linux servers or at `C:\Users\USER_NAME\.aws\credentials` for Windows users and then save your access keys.

#### Using Identity Store with IAM
*Applies if your company identity store is not compatible with SAML 2.0, i.e. LDAP, Active Directory, etc.*

![[VPC IAM non-SAML.png]]

To get temporary security credentials, the identity broker application calls either `AssumeRole` or `GetFederationToken` to obtain temporary security credentials, depending on how you want to manage the policies for users and when the temporary credentials should expire. The call returns temporary security credentials consisting of an AWS access key ID, a secret access key, and a session token. The identity broker application makes these temporary security credentials available to the internal company application. The app can then use the temporary credentials to make calls to AWS directly. The app caches the credentials until they expire, and then requests a new set of temporary credentials.

#### [[IAM Policy Simulator]]

#### Guide

- https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_evaluation-logic.html