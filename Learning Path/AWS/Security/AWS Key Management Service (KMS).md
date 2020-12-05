# AWS Key Management Service (KMS)

- A customer master key (CMK) is a logical representation of a master key in AWS KMS
	- In addition to the master key's identifiers and other metadata, including its creation date, description, and key state, ==a CMK contains the key material used to encrypt and decrypt data==
	- When you create a CMK, by default, AWS KMS generates the key material for that CMK. However, you can choose to create a CMK without key material and then import your own key material into that CMK