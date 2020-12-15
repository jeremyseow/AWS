# Caching Strategies

- Lazy loading
	- Lazy loading is a caching strategy that ==loads data into the cache only when necessary==
		- When your application requests data, it first makes the request to the cache
		- If the data exists in the cache (a cache hit), it is retrieved; but if it does not or has expired (a ache miss), then the data is retrieved from your data store and then stored in the cache
	- The advantage of lazy loading is that only the requested data is cached
	- The disadvantage is that there is a cache miss penalty resulting in three trips
		- The application requests data from the cache
		- If there is a cache miss, you must query the database
		- After data retrieval, the cache is updated

- Write through
	- The write-through strategy ==adds data or updates in the cache whenever data is written to the database==
	- The advantage of write through is that the data in the cache is never stale
	- The disadvantage is that there is a write penalty because every write involves 2 trips
		- A write to the cache and a write to the database
	- Another disadvantage is that because most data is never read in many applications, the data or information that is stored in the cluster is never used
		- This storage incurs a cost for space and overhead due to the duplicate data
		- In addition, if your data is updated frequently, the cache may be updating often, causing cache churn