# X-Ray Daemon

- A software application that collects all the local trace data and batches the information up and periodically sends it over to the internet to the AWS X-Ray service

- The daemon by default listens on port 2000 for UDP connections

- The AWS X-Ray daemon is currently available for Linux, OSX, and Windows operating systems

- AWS X-Ray service has an API endpoint which is used to receive the collected telemetry as delivered from the AWS X-Ray daemon