# AWS Cloud Provider

## Title
Choosing the transcational database for the application
## Status
Proposed

## Context
Since the application need to store trip data for more than 15Million users and serve the data with in 800Milliseconds. the db should support that scalablity

## Decision


We chose to use Posgresql for its Scalablity, Performance, Opensource support

Posgresql can be scaled using read replicas for read scaliablity and also sharding or partitioning.


We aslo use PosgreSQL Auroa for management and faster scalablity and peroformance

## Consequences
For better scale to handle more than 100Million users we should look for database like cansandara or alternative like

Options to use elasticsearch with cluster mode for search and listing scaling and capablites.

Transactional Databases
Usage

Recommended database

Comments

Less than 100Million Records or 100GB of data 

Mysq l/ PostgreSQL

Mysql can also support more than 1Billion if designed properly.

More than 100Million or Above 100GB

Casandra or Scylla db(similar to Cassandra),  Google Cloud Spanner

Regular dataset can be in MySQL and Move large tables like subscriptions or Class to Casandra

Search and Frontend Views

ElasticSearch