# Monitoring

- To closely monitor how the different processes on a DB instance use the CPU such as the percentage of the CPU bandwidth or the total memory consumed by each process to ensure application performance, use RDS enhanced monitoring

|CloudWatch logs | RDS Enhanced Monitoring|
|-------------------|----------------------------|
|Gathers metrics about CPU utilization from the hypervisor for a DB instance|Gathers metrics from an agent on the DB instance|
|Monitor the CPU Utilization of your database instance but not the % of the CPU bandwidth and total memory consumed by each database process in your RDS instance|Collects all|