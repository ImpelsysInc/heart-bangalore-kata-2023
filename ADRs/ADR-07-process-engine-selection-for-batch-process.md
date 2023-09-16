# Process engine selection for batch process.md

## Title
Chooseing the batch processing engine 
## Status
Proposed

## Context
Since the application need to process more than 15 Million users trip data with in 5 minutes, we have to chose an efficient parellel processing system that can meet the need. Also it is a startup a managed solution should be ideal and later it can move to other cloud providers.

## Decision

Flink is chosen becase of much faster performnace, inmemobry, support both stream and batch using sigle code base , multipel programing support, AWS support etc. and it solve our problem

## Rationale
EMR with Flink is cooosen considering the performnace even the Spark has more communicty and connector (source/sink) support.


## Alternatives Considered

Map reduce related framework wold be ideal. Comparied to Hadoop inmemory processing engnies like SPARK or Flink will be ideal for our scenario.
AWS already supporting managed service for Flink and SPARk
EMR with Flink is cooosen considering the performnace even the Spark has more communicty and connector (source/sink) support.



![Spart vs Flink](/Diagrams/spark-vs-flink.png)
*Figure: Spart vs Flink*

## Consequences
There is a learning curve and complexity associated with parellel processing frameworks. But using managed services some of the aspect can be mitigated. But for any optimization of the workflows a deep understanding is needed. 
