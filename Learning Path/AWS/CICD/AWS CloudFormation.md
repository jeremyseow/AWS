# AWS CloudFormation

AWS CloudFormation provides the following Python helper scripts that you can use to install software and start services on an Amazon EC2 instance that you create as part of your stack:

cfn-init: Use to retrieve and interpret resource metadata, install packages, create files, and start services.

cfn-signal: Use to signal with a CreationPolicy or WaitCondition, so you can synchronize other resources in the stack when the prerequisite resource or application is ready.

cfn-get-metadata: Use to retrieve metadata for a resource or path to a specific key.

cfn-hup: Use to check for updates to metadata and execute custom hooks when changes are detected.