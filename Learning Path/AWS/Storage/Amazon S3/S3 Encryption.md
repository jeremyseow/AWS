# S3 Encryption

![[S3 Encryption Overview.png]]

#### SSE-S3
![[SSE-S3 Encryption.png]]
![[SSE-S3 Decryption.png]]

- `'x-amz-server-side-encryption': 'AES256'`

#### SSE-KMS
![[SSE-KMS Encryption.png]]
![[SSE-KMS Decryption.png]]

- `'x-amz-server-side-encryption': 'aws:kms'`

#### SSE-C
![[SSE-C Encryption.png]]
![[SSE-C Decryption.png]]

- Customers provides the encryption keys
-  With the encryption key you provide as part of your request, Amazon S3 manages both the encryption, as it writes to disks, and decryption, when you access your objects
-  S3 does not store the encryption key you provide. Instead, it stores a randomly salted HMAC value of the encryption key in order to validate future requests
-  The salted HMAC value cannot be used to derive the value of the encryption key or to decrypt the contents of the encrypted object. ==That means, if you lose the encryption key, you lose the object==
-   You must provide encryption key information using the following request headers:
	- `x-amz-server-side-encryption-customer-algorithm`
		- This header specifies the encryption algorithm
		- ==The header value must be “AES256”==
	- `x-amz-server-side-encryption-customer-key`
		- This header provides the ==256-bit, base64-encoded encryption key== for Amazon S3 to use to encrypt or decrypt your data
	- `x-amz-server-side-encryption-customer-key-MD5`
		- This header provides the ==base64-encoded 128-bit MD5 digest of the encryption key according to RFC 1321==
		- Amazon S3 uses this header for a message integrity check to ==ensure the encryption key was transmitted without error==

#### CSE-KMS
![[CSE-KMS Encryption.png]]
![[CSE-KMS Decryption.png]]

#### CSE-C
![[CSE-C Encryption.png]]
![[CSE-C Decryption.png]]