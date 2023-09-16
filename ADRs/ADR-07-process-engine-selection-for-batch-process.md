# Process engine selection for batch process.md

## Title
Chooseing the processing engine to fetch and process trip data for users
## Status
Proposed

## Context
Given the necessity to handle data from over 15 million users' trips within a 5-minute timeframe, it's crucial to opt for a highly efficient parallel processing system. Considering the startup nature of the project, an optimal choice would be a managed solution. Choosing  the opensoruce related technology alows to move to other cloud providers.

## Decision
Use AWS Elastic Map Reduce (EMR) with Flink as the processing engline

## Rationale

Advantages of EMR 

- **Scalability**: EMR allows you to easily scale your cluster up or down to handle varying workloads. 
- **Managed Service**: EMR is a fully managed service, which means AWS takes care of cluster provisioning, configuration, monitoring, and maintenance. 
- **Broad Ecosystem Compatibility**: EMR supports various big data processing frameworks, including Apache Hadoop, Apache Spark, Flink,  Apache Hive, Apache HBase, and more.
- **Integration with AWS Services**: EMR seamlessly integrates with other AWS services like S3, DynamoDB, Redshift, and Glue.
- **Cost-Effective**: AWS offers various pricing options for EMR, including on-demand, spot instances, and reserved instances. 
- **Security**: EMR provides robust security features, including encryption at rest and in transit, integration with AWS Identity and Access Management (IAM), and support for Virtual Private Cloud (VPC) configurations. You can also implement fine-grained access control using security groups and network ACLs.
- **Elasticity**: EMR can automatically resize clusters based on your workload demands, ensuring that you have the right amount of resources available when needed and minimizing costs during idle periods.

EMR with Flink is cooosen considering the performnace inmemobry, support both stream and batch using sigle code base , multipel programing support 

## Alternatives Considered

For our workload, a MapReduce-related framework might not be the most suitable choice. In contrast, in-memory processing engines like Spark or Flink appear to be the ideal candidates for our scenario. AWS already provides managed services for both Flink and Spark.

In our case, we've opted for EMR with Flink due to its performance advantages, even though Spark enjoys a larger community and offers more extensive support for connectors (both source and sink).

![Spart vs Flink](/Diagrams/spark-vs-flink.png)
*Figure: Spart vs Flink*

## Consequences
There is a learning curve and complexity associated with parellel processing frameworks. But using managed services some of the aspect can be mitigated. But for any optimization of the workflows a deep understanding is needed. 
