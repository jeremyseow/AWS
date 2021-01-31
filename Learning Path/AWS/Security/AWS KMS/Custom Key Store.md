# Custom Key Store

- The KMS custom key store integrates KMS with [[AWS Cloud Hardware Security Module (CloudHSM) | AWS CloudHSM]] to help satisfy compliance obligations that would otherwise require the use of on-premises hardware security modules (HSMs) while providing the AWS service integrations of KMS
	- Where customers need to manage their keys in single-tenant HSMs that they exclusively control
	- KMS did not meet these requirements since it offered only the ability to store keys in shared HSMs that are managed by KMS

- AWS CloudHSM is not widely integrated with other AWS managed services

#### How it works

- With custom key store, you can configure your own CloudHSM cluster and authorize KMS to use it as a dedicated key store for your keys rather than the default KMS key store

- Then, when you create keys in KMS, you can choose to generate the key material in your CloudHSM cluster

- Your KMS customer master keys (CMKs) never leave the CloudHSM instances, and all KMS operations that use those keys are only performed in your HSMs

- In all other respects, the master keys stored in your custom key store are used in a way that is consistent with other KMS CMKs

![[Custom Key Store Overview.png]]

#### Guide
- https://aws.amazon.com/blogs/security/are-kms-custom-key-stores-right-for-you/