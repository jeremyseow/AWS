# Read Replica vs ElastiCache


|Read replica|ElastiCache|
|-------------|-------------|
|More up-to-date as it will continously sync with the master|Less up-to-date as query result is taken at a point in time and depends on TTL|
|More suitable for queries that changes dynamically or has dynamic elements such as NOW()|Can only cache results for queries that has been executed before, so more suitable if there are heavy queries that are executed often|
|Slower as you are reading from a database|Faster as you reading directly from RAM, but also limits the number of results you can store|
|More expensive???|Less expensive???|