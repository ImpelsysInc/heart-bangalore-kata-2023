# Seperate datastore for barch process workload

## Title
Chooseing the database engine for storing jobs db for faster access to parellel processing system.
## Status
Proposed

## Context
Since the batch processing system needs to access more than 15 Million users related job data for every 5 minues, access needs to be faster . It also need to support adding new jobs information or deleting job information at a high rate. 

## Decision

Utilize Amazon S3 as the storage repository for user jobs, with data organization structured around the user's internal system identifier. This arrangement enables Elastic MapReduce (EMR) to access the data concurrently by targeting specific folders. Leveraging this parallel processing approach facilitates the efficient processing of large volumes of data.   
Additionally, it's possible to store a list of users as a single file to further optimize processing job performance. This approach, while increasing the complexity of modifications, is ideally suited for grouping user data based on their creation time.

## Alternatives Considered
- Use In memory database like MemSQL,Apache and Ignite VoltDB for Faster access
- Use Hive, Cassandra and other scalable database for bigdata access
- Use NoSql database like Big Query to get data at a faster pace.

## Rationale
Using this approach ensure
1. Exceptional scalability without concerns about downtime or maintenance.
2. Cost-effectiveness at its core.
3. Ensured scalability and robustness of the application.

## Consequences

S3 is an object store and related limitations. But due to s3 scalablity and parellel processing that can be mitigated.

## Conclusion

Based on the factors considered, we have decided to use the s3 due to low cost, scalablity and manageablity.
