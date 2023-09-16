### Batch Process
![Complete Overview](/Diagrams/c4-component-batch-processor.png)
#### Batch Process sequence diagram
![Complete Overview](/Diagrams/batch-process-sequnce-diagram.png)
#### Batch prcess workflow considerations

Refer ADR-07 and ADR-09 for process engine and job datastore selection

#### Workflow

1. Within the Kubernetes Cluster (AWS EKS), support is provided for batch processing and scheduling, as outlined in the Kubernetes documentation[https://kubernetes.io/docs/concepts/workloads/controllers/job/]. This functionality allows for the initiation of jobs within a container, which in turn schedules the actual batch processing job for user trip data.
2. The Job Scheduler retrieves the most recent user data based on the previously stored synchronization time in the database, taking into account user creation and modification timestamps. It updates the latest user data in the batch database on a per-user basis. Additionally, it initiates the Elastic MapReduce (EMR) cluster featuring Flink.
3. Once the EMR cluster with Flink is up and running, it retrieves jobs from the Jobs Database and commences the aggregation of trip data based on reservations for individual users. This process also involves the generation of necessary reporting facts and dimensions. Upon job completion, the trip data and reporting summary are stored in CSV format within an S3 bucket. Following this, the same dataset is loaded into both the transactional and reporting databases using the "loadfile" command, ensuring efficient data ingestion into the database systems
