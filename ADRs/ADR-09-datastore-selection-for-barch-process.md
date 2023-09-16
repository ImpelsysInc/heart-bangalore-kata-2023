# Datastore selection for barch process workload

## Title
Chooseing the database engine for storing jobs db for faster access to parellel processing system.
## Status
Proposed

## Context
Since the batch processing system needs to access more than 15 Million users related job data for every 5 minues, access needs to be faster . It also need to support adding new jobs information or deleting job information at a high rate. It can also store list of users as single file using hash algorithm but the batch files need to be modified if any user changes.

## Decision

Use the S3 for storing User jobs and the files will be storing based on the User identifier ( Internal system identifier ) and the batch process ( Elastic map reduce ) can access the data parellelly using the specific folder . Using the parellel processing high volume of data can be processed.

## Alternatives Considered

- Use In memory database for Faster access
- Use Hive, Cassandra that support and parellel access
- Use Big Query


## Consequences
 
Adaption of S3 will lead to following consequences:

1. High scalablity and no worry on the downtime or maintanance.

2. Low cost

3. Scalability and robustness of the application.

Drawbacks

File operations. But due to s3 scalablity and parellel processing that can be mitigated.

## Conclusion

Based on the factors considered, we have decided to use the s3 due to low cost, scalablity and manageablity.
