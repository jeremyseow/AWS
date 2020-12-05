# IAM certificate store vs ACM vs CloudFront

- It is recommended that to use ACM to provision, manage, and deploy your server certificates for regions that support ACM
- In unsupported Regions, you must use IAM as a certificate manager
- If you got your certificate from a third-party CA, import the certificate into ACM or upload it to the IAM certificate store

|IAM certificate store|ACM|CloudFront|
|---------------------|-----|-----------|
|you can request a certificate or deploy an existing ACM or external certificate to AWS resources| IAM securely encrypts your private keys and stores the encrypted version in IAM SSL certificate storage|sas|
|you can use ACM to manage server certificates from the console or programmatically|IAM supports deploying server certificates in all Regions. you cannot manage your certificates from the IAM Console|dsd|
|Certificates provided by ACM are free and automatically renew|ou must obtain your certificate from an external provider for use with AWS. You cannot upload an ACM certificate to IAM|You would also not be able to export the certificate that you have loaded in CloudFront nor assign them to your EC2 or ELB instances as it would be tied to a single CloudFront distribution|
