### Batch Process
![Complete Overview](/Diagrams/c4-component-batch-processor.png)
#### Batch Process sequence diagram
![Complete Overview](/Diagrams/batch-process-sequnce-diagram.png)
#### Batch prcess workflow considerations

Refer ADR-07 and ADR-09 for process engine and job datastore selection

#### Workflow
1. Kubernet Cluster (AWS EKS) support batch processing and scheduling [https://kubernetes.io/docs/concepts/workloads/controllers/job/] using that it can start jobs in a container which schedule the actual batch proccessing job for trip data of users.
2. Job Scheduler get the latest user data based on the pervious sync time stored in the db and user creation and modification time. It update the latest user data in to batch db based on user. It also start the Elastic Map Reduce(EMR) cluster with Flink. 
3. Once EMR with Flink started, It get jobs from Jobs DB and start aggregating trips data based on reservation for a given user. It also generate necessary reporting facts and dimentions. Once the job is completed it store the trip data and reporting summary in csv format in S3. Once that is completed, same data will be loaded in to transactional and reporting DB using the loadfile command for efficient loading of data into database.
   
