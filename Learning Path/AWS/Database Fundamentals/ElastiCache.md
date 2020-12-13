# ElastiCache

- Support for 2 engines
	- Memcached
	- Redis


#### Use case

- Amazon ElastiCache can be used to 
	- Significantly improve latency and throughput for many read-heavy application workloads (such as social networking, gaming, media sharing, and Q&A portals) 
	- Compute-intensive workloads (such as a recommendation engine) by allowing you to store the objects that are often read in the cache
	
- Not suitable for write-heavy applications as the cache goes stale at a very fast rate

- To make the application tier stateless and outsource the session information (in the case where users have to re-authenticate into the website often)
	- We can use ElastiCache to provide a shared data storage for sessions that can be accessed from any individual web server, you can abstract the HTTP sessions from the web servers themselves