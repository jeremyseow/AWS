# ElastiCache

- Support for 2 engines
	- Memcached
		- Memcached is a widely adopted in-memory key-value store
		- It is historically the gold standard of web caching
		- ElastiCache is protocol-compliant with Memcached, and it is designed to work with popular tools that you use today with existing Memcached environments
		- ==Memcached is also multithreaded, meaning that it makes good use of larger Amazon EC2 instance sizes with multiple cores==
	- Redis
		- Redis is an increasingly popular open-source, in-memory key-value store that supports more advanced data structures, such as sorted sets, hashes, and lists
		- ==Unlike Memcached, Redis has disk persistence built in==, meaning that you can use it for long-lived data
		- ==Redis also supports replication, which can be used to achieve Multi-AZ redundancy, similar to Amazon RDS==
		- Default limit is 20 nodes per cluster

Although both Memcached and Redis appear similar on the surface, in that they are both
in-memory key stores, they are quite different in practice. Because of the replication and
persistence features of Redis, ElastiCache manages Redis more as a relational database.
Redis ElastiCache clusters are managed as stateful entities that include failover, similar to
how Amazon RDS manages database failover.
Conversely, because Memcached is designed as a pure caching solution with no persistence,
ElastiCache manages Memcached nodes as a pool that can grow and shrink, similar
to an Amazon EC2 Auto Scaling group. Individual nodes are expendable, and ElastiCache
provides additional capabilities here, such as automatic node replacement and Auto
Discovery.
Consider the following requirements when deciding between Memcached and Redis.
Use Memcached if you require one or more of the following:
■■ Object caching is your primary goal, for example, to offload your database.
■■ You are interested in as simple a caching model as possible.
■■ You plan to run large cache nodes and require multithreaded performance with the use
of multiple cores.
■■ You want to scale your cache horizontally as you grow.
Use Redis if you require one or more of the following:
■■ You are looking for more advanced data types, such as lists, hashes, and sets.
■■ Sorting and ranking datasets in memory help you, such as with leaderboards.
■■ Your application requires publish and subscribe (pub/sub) capabilities.
■■ Persistence of your key store is important.
■■ You want to run in multiple Availability Zones (Multi-AZ) with failover.
■■ You want transactional support, which lets you execute a group of commands as an
isolated and atomic operation.


#### Use case

- Amazon ElastiCache can be used to 
	- Significantly improve latency and throughput for many read-heavy application workloads (such as social networking, gaming, media sharing, and Q&A portals) 
	- Compute-intensive workloads (such as a recommendation engine) by allowing you to store the objects that are often read in the cache
	
- Not suitable for write-heavy applications as the cache goes stale at a very fast rate

- To make the application tier stateless and outsource the session information (in the case where users have to re-authenticate into the website often)
	- We can use ElastiCache to provide a shared data storage for sessions that can be accessed from any individual web server, you can abstract the HTTP sessions from the web servers themselves