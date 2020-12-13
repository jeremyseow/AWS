# Best Practices

If your traffic is read-heavy, consider using a caching service such as DynamoDB Accelerator (DAX). DAX is a fully managed, highly available, in-memory cache for DynamoDB that delivers up to a 10x performance improvement—from milliseconds to microseconds—even at millions of requests per second

If you have globally dispersed users, consider using global tables. With global tables, you can specify the AWS Regions where you want the table to be available. This can significantly reduce latency for your users. So, reducing the distance between the client and the DynamoDB endpoint is an important performance fix to be considered

Time To Live (TTL) for DynamoDB allows you to define when items in a table expire so that they can be automatically deleted from the database. TTL is provided at no extra cost as a way to reduce storage usage and reduce the cost of storing irrelevant data without using provisioned throughput. With TTL enabled on a table, you can set a timestamp for deletion on a per-item basis, allowing you to limit storage usage to only those records that are relevant.