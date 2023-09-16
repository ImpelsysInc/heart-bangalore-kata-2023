# AWS Cloud Provider

## Title
Chooseing the batch processing engine 
## Status
Proposed

## Context
Since the application need to process more than 15Million users trip data with in 5 minutes, we have to chose an efficient parellel processing system that can meet the need. Also it is a startup a managed solution should be ideal and later it can move to other cloud providers.

## Decision
Map reduce related framework wold be ideal. Comparied to Hadoop inmemory processing engnies like SPARK or Flink will be ideal for our scenario.

AWS already supporting managed service for Flink and SPARk

EMR with Flink is cooosen considering the performnace even the Spark has more communicty and connector (source/sink) support.

## Consequences
There is a learning curve and complexity associated with parellel processing frameworks. But using managed services some of the aspect can be mitigated. But for any optimization of the workflows a deep understanding is needed. 
