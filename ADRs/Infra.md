## Deployment
The deployment of The Road Warrior system on the AWS platform is outlined below,
with a concise overview of the AWS services involved.

![AWS Infrastructure Architecture](/Diagrams/aws-infra-architecture.png)
*Figure:* AWS Infrastructure Architecture  
#### Regions 
 Regions are geographic areas that contain data centers. Also helps to enable DR/BCP.  
#### Availability Zones 
Within each region, indicate the availability zones (AZs) that your resources span. AZs are physically separate data centers with redundant power, cooling, and networking.  
#### VPC (Virtual Private Cloud)  
Virtual Private Cloud(s) in use. A VPC provides a private network for your AWS resources.  
####  Subnets    
Subnets are subdivisions of your VPC and can be public or private.  
#### EC2 Instances    
EC2 instances (virtual servers) within your subnets. Specify their instance types and roles (e.g., web server, database server). 
#### RDS (Relational Database Service)    
PostgreSQL used as database engines, storage, and replication if applicable. 
Can enable read replica and table partition for higher scalablity   
#### Amazon Elastic MapReduce (EMR)    
It simplifies the process of processing and analyzing vast amounts of data using popular frameworks like Apache Hadoop, Apache Spark, Apache Flink, Apache Hive, Apache HBase, and more.
We use combination of Flink and EMR for batch processing
#### AWS Amplify   
Simplifies the process of building full-stack web and mobile applications.
It provides developers with a set of libraries, a command-line interface (CLI), and a set of back-end services to streamline the development and deployment of cloud-powered applications.  
#### S3 Buckets  
Represent Amazon S3 buckets for object storage. 
Indicate if they are used for static assets, backups, or other purposes.  
 Additionally, S3 serves as a repository for batch process job details and processed data. 
 It can also function as a data lake, housing report data and trip data for future analytical purposes.
#### Application Load Balancers  
Application Load Balancers for distributing incoming traffic across multiple instances or containers. 
Our API Gatway uses ALB for providing public access  
#### API Gateway 
API Gateway services that manage and secure your APIs.  
#### CloudWatch and Metrics 
Include CloudWatch for monitoring and metrics collection. Show how it integrates with other services.  
