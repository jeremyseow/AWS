# CodeDeploy Agent

The CodeDeploy agent is a software package that, when installed and configured on an instance, makes it possible for that instance to be used in CodeDeploy deployments. The CodeDeploy agent archives revisions and log files on instances. The CodeDeploy agent cleans up these artifacts to conserve disk space. You can use the :max_revisions: option in the agent configuration file to specify the number of application revisions to the archive by entering any positive integer. CodeDeploy also archives the log files for those revisions. All others are deleted, except for the log file of the last successful deployment.

https://docs.aws.amazon.com/codedeploy/latest/userguide/codedeploy-agent.html