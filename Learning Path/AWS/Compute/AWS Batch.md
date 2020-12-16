For batch computing

You can seamlessly create a cluster of compute resources which is highly scalable, taking advantage of the elasticity if AWS, coping with any level of batch processing while optimizing the distribution of the workloads. All provisioning, monitoring, maintenance and management of the clusters themselves is taken care of by AWS, meaning there is no software to be installed by yourself. 

## Components
- Jobs
Job to run: executable file, application within ECS cluster, shell script. Runs on EC2 instances as containerized applications
- Job Definitions
These define specific parameters for the jobs themselves. They dictate how the job will run and with what configuration. Some examples of these may be how many vCPUs to use for the container, which data volume should be used, which IAM role should be used, allowing access for AWS Batch to communicate with other AWS services, and mount points
- Job queues
Jobs that are scheduled are placed into a job queue until they run. It's also possible to have multiple queues with different priorities if needed. One queue could be used for on-demand EC2 instances, and another queue could be used for the spot instances. Both on-demand and spot instances are supported by AWS Batch, allowing you to optimize cost, and AWS Batch can even bid on your behalf for those spot instances. 
- Job scheduling
The Job Scheduler takes control of when a job should be run and from which Compute Environment.
- Compute Environments
These are the environments containing the compute resources to carry out the job. The environment can be defined as managed or unmanaged. A managed environment means that the service itself will handle provisioning, scaling and termination of your Compute instances based on the configuration parameters that you would enter regarding the instance type, purchase method, such as on-demand or spot. This environment is then created as an Amazon ECS Cluster. Unmanaged environments are provisioned, managed and maintained by you, which gives greater customization.