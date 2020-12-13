# AWS RDS

- [[Monitoring]]
- Use ==Transparent Data Encryption (TDE)== to encrypt stored data on your DB instances running Microsoft SQL Server to encrypts data before write and decrypt data during read


The automated backup feature of Amazon RDS enables point-in-time recovery for your database instance. Amazon RDS will backup your database and transaction logs and store both for a user-specified retention period. If it’s a Multi-AZ configuration, backups occur on the standby to reduce I/O impact on the primary. Automated backups are limited to a single AWS Region while manual snapshots and Read Replicas are supported across multiple Regions.