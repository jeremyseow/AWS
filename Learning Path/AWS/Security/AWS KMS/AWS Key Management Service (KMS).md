# AWS Key Management Service (KMS)

- It is a managed service used to store and generate encryption keys that can be used by other AWS services and applications to encrypt your data

- A customer master key (CMK) is a logical representation of a master key in AWS KMS
	- In addition to the master key's identifiers and other metadata, including its creation date, description, and key state, ==a CMK contains the key material used to encrypt and decrypt data==
	- When you create a CMK, by default, AWS KMS generates the key material for that CMK. However, you can choose to create a CMK without key material and then import your own key material into that CMK
- Administrators at AWS do not have access to your keys within KMS and they cannot recover your keys for you should you delete them
- It is **region** locked

- You can encrypt up to 4 kilobytes (4096 bytes) of arbitrary data such as an RSA key, a database password, or other sensitive information
- For anything over 4 KB, you may want to look at envelope encryption
	- When you encrypt data directly with AWS KMS it must be transferred over the network. Envelope encryption reduces the network load since only the request and delivery of the much smaller data key go over the network