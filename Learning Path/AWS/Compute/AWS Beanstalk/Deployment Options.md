# Deployment Options

- Understanding the different options that are available enables you to efficiently manage your infrastructure
	- All at once
		- Default option
		- Roll out the application to all your resources at the same time
		- Would cause a diruption to your application while the deployment is in progress
	- Rolling
		- Your resouces will be grouped into batches
		- Beanstalk will deploy the application to 1 batch at a time, and will only move on to the next batch when the current batch is completed
		- This means that for a period of time, you will have 2 different versions of the application running. However, your application will still be available because as 1 batch is being deployed to, the other batches can still handle requests
	- Rolling with addtional batch
		- Although rolling deployment prevents outage of services, availability will be reduced as at any 1 time, 1 batch will be deployed to and cannot handle requests
		- Hence, this option is the same as rolling but an addtional batch of ressources will be created
		- This will ensure 100% availability
		- Once all batches are updated, the addtional batch will be terminated
	- Immutable
		- Creates an entirely new set of resouces in parallel to existing resources
		- These new instances will be served through a temporary auto scaling group behind your ELB
		- This means that for a period of time, your environment will double in size
		- Once your new instances are deployed and have passed all the health checks the old environment would be removed and the autoscaling group updated
		- If your health checks fail for the new instances, then Elastic Beanstalk would terminate them and delete the autoscaling group and traffic would continue to be served to your original environment
	- TrafficSplitting 
		- Performs traffic-splitting deployments to canary-test your application deployments.
		- *According to TD, canary is only for Lambda*

Method|Impact of failed deployment|Zero downtime|No DNS change|Rollback process|Code deployed to
|------|------|------|------|------|------|
All at once|Downtime|No	|Yes|Manual redeploy|Existing instances
Rolling|Single batch out of service; any successful batches before failure running new application version|Yes|Yes|Manual redeploy|Existing instances
Rolling with an additional batch|Minimal if first batch fails; otherwise, similar to Rolling|Yes|Yes|Manual redeploy|New and existing instances
Immutable|Minimal|Yes|Yes|Terminate new instances|New instances
Traffic splitting|Percentage of client traffic routed to new version temporarily impacted|Yes|Yes|Reroute traffic and terminate new instances|New instances
Blue/green|Minimal|Yes|No|Swap URL|New instances