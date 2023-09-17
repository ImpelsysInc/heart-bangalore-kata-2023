# Heart Bangalore - O'Reilly Architecture Katas Sept 2023

![Team Heart Bangalore](/Diagrams/team-heart-bangalore.png)

Hello! We are the Heart Bangalore team hailing from Bangalore, India, and we are here to present our solution for the O'Reilly Architecture Katas in September 2023.

## Team Members 
 [Krishnaraj Ramakrishna](https://www.linkedin.com/in/krishnaraj-vr-8869b45/)  
[Prinjumon Kalyani](https://www.linkedin.com/in/prinjumon-km-98998121/)  
[Raghu A M](https://www.linkedin.com/in/raghu-a-m-6381b614/)  
[Sangeeth Kumar](https://www.linkedin.com/in/sangeeth-kumar-350b8349/)  
[Vishwanatha K](https://www.linkedin.com/in/visshh7/) 


## Contents
- [Introduction](#introduction)  
- [Requirements](#requirements)
    - [Business Requirments](#business-requirments)  
    - [Technical Requirements](#technical-requirements)
    - [Market Research](#market-research)
    - [Other Considerations](#other-considerations)
- [Architecture Characteristics](#architecture-characteristics) 
    - [Top 3 Characteristics](#top-3-characteristics)
    - [Implicit Characteristics](#implicit-characteristics)
    - [Other Characteristics](#other-characteristics)
- [Architecture Approach](#architecture-approach)
- [Use Journey](#use-journey)
    - [User experience (UX) design](#user-experience-ux-design)
- [Event Storming](#event-storming)
- [Context](#context)
    - [Complete Overview](#complete-overview)
    - [Context Diagram](#context-diagram)
- [Containers](#containers)
    - [Road Warrior System](#road-warrior-system)
- [Components](#components)
    - [API Application](#api-application)
    - [Batch Process](#batch-process)
- [Code](#code)
    - [Trip Service](#trip-api-service)
- [Deployment](#deployment)
- [ADRs](#adrs)

## Introduction
The Road Warrior wants to build the next generation online trip management Dashboard to allow travelers to see all of their existing reservations organized by trip either online (web) or through their mobile device.

## Requirements

### Business Requirments
**US-01:** Poll E-Mail looking for travel-related E-Mail.\
**US-02:** Filter and whitelist certain E-Mails.\
**US-03:** The system must interface with the agency’s existing airline, hotel, and car rental interface system to update travel details (delays, cancellations, updates, gate changes, etc.). Updates must be in the app within 5 minutes of an update (better than the competition).\
**US-04:** Customers should be able to add, update, or delete existing reservations manually as well.\
**US-05:** Items in the dashboard should be able to be grouped by trip, and once the trip is complete, the items should automatically be removed from the dashboard.\
**US-06:** Users should also be able to share their trip information by interfacing with standard social media sites or allowing targeted people to view your trip.\
**US-07:** Provide end-of-year summary reports for users with a wide range of metrics about their travel usage.\
**US-08:** Road Warrior gathers analytical data from users trips for various purposes - travel trends, locations, airline and hotel vendor preferences, cancellation and update frequency, and so on.\
**US-09:** Must integrate seamlessly with existing travel systems (i.e, SABRE, APOLLO).\
**US-10:** Must integrate with preferred travel agency for quick problem resolution (help me!).\
**US-11:** Must work internationally.

### Technical Requirements
**US-12:** Richest user interface possible across all deployment platforms.\
**US-13:** Users must be able to access the system at all times (max 5 minutes per month of unplanned downtime).\
**US-14:** Travel updates must be presented in the app within 5 minutes of generation by the source.\
**US-15:** Response time from web (800ms) and mobile (First-contentful paint of under 1.4 sec)\
**US-16:** Supports minimum 2 million active users/week\
**US-17:** Supports total users: 15 million (user accounts)

## Assumptions
* Actual trip bookings are done externally, and the application is only a dashboard to aggregate trips.
* Notifications are not part of the basic requirements.
* Payment integration is not required because we are not directly managing bookings.
* Revenue generation is not an initial requirement; the current requirement is to add customers to the system.
* Popular travel agencies and other system like SABRE, APOLLO are pre configured in the system
* Help me !! link only redirect to the respecitve agency site if agency information is available in the trip
* User will provide his hometown location while registering for localization
* The system is already integrated with well-known email providers such as Gmail, MSN, iCloud, and others.

## Market Research

### Market Scope
Global online travel market size - $2.3 trillion in 2023.
Online travel market growth rate is expected to grow at a CAGR of 10.3% over the forecast period 2023-2030 
(Ref:- https://www.globaldata.com/store/report/online-travel-market-analysis/ )

### Key online travel market drivers  
1.	Increasing population 
2.	Rising disposable income 
3.	Increasing use of mobile devices for online travel booking
4.	Travel globalization with cheaper and easier travel options 

### Key online travel market targeted segments
1.	Transportation (Airlines, Car Rental, Rail, Cruise, and others)
2.	Travel Accommodation (Hotels and resorts)
3.	Travel Intermediation (Online Travel Agencies, Tour Operator Websites, and Others)
4.	Personalized travel guide and recommendations

### Current Traveler booking challenges on online websites.
1.	Lack of end-to-end travel advisor platform connecting to various established travel segments based on traveller preferences. 
2.	Lack of multi-region support
3.	Lack of centralized portal for navigation challenges regarding travel related support and queries
4.	Lack of centralized portal for easy navigation to cancel or modify travel plan

### Trip aggregator portal advantages
1.	Well structured, up-to date, easy and quicker access, navigations, and content across multiple devices
2.	Trustworthy and secure website with seamless transaction options
3.	Easy, faster, less cumbersome single vendor affiliate for multiple B2B and B2C connects. 
4.	Capability to collect and store large amount of data and perform AI-ML analytics based on traveller buying patterns, different pricing strategies, new trends and opportunities. 
5.	Capability to personalize the options by providing recommendations in the form of updates or advertisements as rendered by the B2B segments

### Other Considerations 
- **Personalized Recommendations:** AI can analyze user preferences, past travel history, and behavior to provide highly personalized travel recommendations. This includes suggesting destinations, hotels, activities, and even travel itineraries tailored to individual preferences.  
- **Augmented Reality (AR):** AR apps can provide travelers with immersive experiences, such as virtual tours of destinations or navigation assistance in unfamiliar locations.  
- **AI Chatbots:** AI chatbots can handle customer inquiries, provide real-time support, and assist with last-minute changes to travel plans.

## Quality Attribute Requirements
This section outlines the Quality Attribute Requirements that exert a critical influence on the overarching architecture of the software solution.
| Id | Quality Attribute | Description |
| --------- | --------- | --------- |
| QA1 | Scalability | US-16: Supports 2 million active users/week |
| QA2 | Scalability | US-17: Supports total users: 15 million (user accounts) |
| QA3 | Performance | US-03: Updates must be in the app within 5 minutes of an update (better than the competition) |
| QA4 | Performance | US-14: Travel updates must be presented in the app within 5 minutes of generation by the source.|
| QA5 | Availability | US-13: Users must be able to access the system at all times (max 5 minutes per month of unplanned downtime). |
| QA6 | Responsiveness | US-15: Response time from web (800ms) and mobile (First-contentful paint of under 1.4 sec) |
| QA7 | Interoperability | US-03: The system must interface with the agency’s existing airline, hotel, and car rental interface system |
| QA8 | Usability | US-12: Richest user interface possible across all deployment platforms. |
| QA9 | Usability | US-11: Must work internationally. |
| QA10 | Security | US-01: Poll E-Mail looking for travel-related E-Mail.  |

## Architecture Characteristics
To ensure a successful system implementation, it's vital to prioritize key architecture characteristics. These elements guarantee reliability, availability, and responsiveness, delivering a seamless user experience.

![Architecture Characteristics](/Diagrams/architecture-characteristic.png)
*Figure: Architecture Characteristics*

## Top 3 Characteristics
### Scalability
 Scalability allows the system to accommodate a growing user base and increased data volume, ensuring that Road Warrior can scale its services as it gains more users.
### Performance
 Performance optimization is critical to meet the specified response times and deliver real-time travel updates quickly and efficiently.
### Availability
"99.99% uptime" is a High availability, with a maximum of 5 minutes per month of unplanned downtime, is essential to ensure travelers can access their reservations and updates reliably.

## Implicit Characteristics
### Feasibility (Cost/Time)
Achieving rapid time-to-market while managing development costs is a feasible goal with the selected "mini-services" architecture.
### Security
Implementing strong authentication and authorization mechanisms is vital to safeguard traveler information and data integrity. Also storing the PII data like trip information needs to be protected and handle properly due to compliance like GDPR. 
Token-based authentication (JWT) and role-based access control (RBAC) must safeguard all API access. Additional considerations encompass encrypting data at rest and during transmission, ensuring secure credential management, effectively managing sessions, implementing refresh tokens for applications, and integrating IAM for enhanced security.
### Maintainability
Ensuring clean code, documentation, and knowledge sharing within the development team are essential for long-term system maintainability.
### Observability
Implementing comprehensive monitoring and observability solutions enables efficient tracking of system performance and early issue detection for proactive problem-solving.

## Other Characteristics
### Interoperability
 Interoperability is crucial to seamlessly integrate with external travel systems and agencies, ensuring smooth data exchange and collaboration.
### Elasticity
 Elasticity enables the system to dynamically scale resources up or down in response to varying workloads, ensuring cost-efficiency and optimal performance.
### Responsiveness
 Responsiveness in the user interface is vital for providing a positive user experience, allowing travelers to quickly access and manage their travel information.
### Reliability
 Reliability is paramount to ensure that travelers receive timely travel updates and manage their reservations without disruptions or errors.

## Architecture Approach
### Architecture Style
![Architecture Style](/Diagrams/architecture-style.png)
*Figure: Architecture Style*

Based on the architecture charetrisctis we prefer to use the microservices based style.

#### Options for service granularity
![Service Granularity](/Diagrams/service-granularity.png)\
*Figure: Option for Service Granularity. Credits: Gartner*

Microservices are not the only alternative to monolithic architectures. A real-world architecture will have services at different levels of granularity. In addition to microservices, Gartner has identified two other “services” patterns: As shown in Figure, these represent points between monolith and microservice on a spectrum of options. As we move further to the right, we are gaining development agility, deployment flexibility and precision of scalability. However, we are giving up data integrity, and the complexity of the application architecture is increasing.

As a startup, Road Warrior prioritizes rapid time-to-market while seeking the benefits of modularity and scalability. Therefore, a '**mini-services**' architecture with a slightly lesser granularity than microservices is a suitable choice.

By adopting a "mini-services" architecture, Road Warrior can strike a balance between rapid development and modularity. This approach allows for quicker iterations, parallel development efforts, and the ability to release new features to the market faster while maintaining a structured and maintainable codebase.

- Miniservices are similar to microservices but have a larger scope and relaxed architectural constraints. 
- Like a microservice, a miniservice is a physically encapsulated, loosely coupled, independently deployable and scalable application component.
- Miniservices have a broader scope than microservices, often incorporating all the functionality of a given domain. Miniservices can also share backing data stores.
- Each mini-service encapsulates significant functionality, reducing development complexity.
- Services communicate via well-defined APIs (RESTful or GraphQL) for simplicity.
- Aim for independent deployment, allowing for rapid iterations and updates.
- Development teams align with mini-services, enabling parallel development.
- Implement robust testing, CI/CD, and monitoring for reliability.
- Consider transitioning to microservices as the startup grows and complexity increases.

This approach balances speed to market with modularity and maintainability.

### Scalability

- **Granular Scaling**: Mini-services allow for granular scaling of specific parts of the application to meet varying workloads efficiently.
- **Resource Efficiency**: Scalability ensures optimal resource usage, preventing over-provisioning and reducing operational costs.
- **Seamless Growth**: The architecture facilitates the seamless growth of the system as user numbers and data volume increase over time.

### Availability

- **Independent Deployment**: The architecture's emphasis on independent deployment contributes to high availability. If one mini-service experiences issues or requires maintenance, it does not necessarily impact the availability of other services.
- **Cluster setup with DR Plan**: All components must be capable of operating in cluster mode and accommodating horizontal scalability. Additionally, the application should be deployable in various regions to address Disaster Recovery (DR) and Business Continuity Planning (BCP) requirements, ensuring compliance with a 99.99% Service Level Agreement (SLA).
- **Robust Testing and CI/CD**: The inclusion of robust testing and CI/CD practices ensures that new updates can be quickly and reliably deployed, minimizing the likelihood of extended downtime.

### Performance
- **Data access Performance**: The architecture places a significant emphasis on selecting the appropriate database system to ensure optimized access and horizontal scalability, thereby meeting stringent response time requirements. One approach involves caching database data in an in-memory store to expedite access, while another option entails leveraging NoSQL databases for enhanced and optimized data retrieval.
- **Application performancee**: The strategy involves the selection of an optimized programming language and the horizontal scaling of application nodes to effectively address the demands of scale and performance. Web applications are serving content from a Content Delivery Network (CDN) for performance and utilizing an optimized native mobile application for mobile devices.
  
## Use Journey 
 ![User Journey Diagram](/Diagrams/road-warriors-workflow.png)
### User experience (UX) design
 ![Dashboard](/Diagrams/ux-dashboard.png)  
 ![Reports](/Diagrams/ux-reports.png) 
 #### More designs
- [Add Trip](/Diagrams/ux-add-trip.png)
- [Login](/Diagrams/ux-login.png)  
- [Sign Up](/Diagrams/ux-sign-up.png)
 #### Complete walkthrough
- [Adobe-XD walkthrough](https://xd.adobe.com/view/2771a735-f300-447d-b192-2e5f9d16369f-7222/?fullscreen)
 
## Event Storming

Event storming drives greater understanding and productivity by simplifying the approach and including multiple levels of stakeholders in the business. With the help of sticky notes and a willing group, you can reveal your business processes more efficiently and enjoyably.

### Identify domain events
The first step is to begin identifying events. Events are “things that happen” in a process or system. Important events trigger reactions, so understanding the causal event can help you understand how the system operates and why. Keep in mind that events are always noted in the past tense.
![Identify domain events](/Diagrams/event-storming-events.jpg)\
*Figure: Identify events*

### Connect domain events to commands
With your events outlined, you can begin to evaluate each event for its causes and consequences. In other words, ask yourself what triggered this event (e.g., users, other events, or external systems).

![Identify bounded context and aggregates](/Diagrams/event-storming-command.jpg)\
*Figure: connect domain events to commands*

### Identify bounded context and aggregates
For high-level event storming, the process can end once your team has added domain events, commands, and reactions. However, event storming can be combined with the technique of domain-driven design to define the structure of your system and send your team on the way to implementation.

![Identify bounded context and aggregates](/Diagrams/event-storming-context.jpeg)\
*Figure: bounded context and aggregates*

## Context
### Complete Overview
![Complete Overview](/Diagrams/c4-complete-overview.png)
### Context Diagram
![Complete Overview](/Diagrams/c4-system-context.png)
## Containers
### Road Warrior System
![Complete Overview](/Diagrams/c4-container-road-warrior-system.png)
## Components
### API Application
![Complete Overview](/Diagrams/c4-component-api-application.png)
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


## Code
### Trip API Service
![Complete Overview](/Diagrams/c4-code-tripservice.png)

**Handlers** - Handlers in Go are used to handle incoming HTTP requests. When a request is received, the handler processes it, performs the necessary business logic, and generates an HTTP response.

**Service** - The service class abstracts and encapsulates the core business logic for a specific domain.It defines methods and functions that represent the operations that can be performed within that domain.

**Repo** - The repository abstracts the details of how data is stored and retrieved. It provides high-level methods for performing CRUD (Create, Read, Update, Delete) operations on a specific domain entity, such as a trips, userdetails.

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
Our Krakend API Gatway uses ALB for providing public access  
 
#### CloudWatch and Metrics 
Include CloudWatch for monitoring and metrics collection. Show how it integrates with other services.  

## ADRs

- [ADR-01:Programming language for service](/ADRs/ADR-01-programming-language-for-service.md)  
- [ADR-02:Technology for web app](/ADRs/ADR-02-technology-for-web-app.md)
- [ADR-03:Technology for mobile app](/ADRs/ADR-03-technology-for-mobile-app.md)  
- [ADR-04:Framework selection for gateway](/ADRs/ADR-04-framework-selection-for-gateway.md)
- [ADR-05:Database seclection for reporting](/ADRs/ADR-05-database-seclection-for-reporting.md)
- [ADR-06:Cloud provider selection from application](/ADRs/ADR-06-cloud-provider-selection-from-application.md)
- [ADR-07:Process engine selection for batch process](/ADRs/ADR-07-process-engine-selection-for-batch-process.md)  
- [ADR-08:Transactional database selection for application](/ADRs/ADR-08-transactional-database-selection-for-application.md)
- [ADR-09:Datastore selection for barch process](/ADRs/ADR-09-datastore-selection-for-barch-process.md)
- [ADR-10:GDPR compliance](/ADRs/ADR-10-GDPR-compliance.md)

## Glossary
- **AWS** - Amazon Web Services
- **EKS** - Elastic Kubernets Cluster
- **EMR** - Elastic Map Reduce
- **S3** - Simple Storage Service
- **OTA** - Online Travel Agencies. (i.e, MakeMyTrip, Booking.com)
- **GDS** - Global Distribution System. (i.e, SABRE, APOLLO) 
- **B2B** - Business to Business
- **Agencies** - Refering to Onlnie Travel Agencies (OTA)
  
## References
- [C4 Diagrams](https://c4model.com/)
- [Event storming](https://en.wikipedia.org/wiki/Event_storming)
- [Architecture Kata Event](https://learning.oreilly.com/featured/architectural-katas/)
- [Understanding Travel APIs](https://www.altexsoft.com/blog/engineering/travel-and-booking-apis-for-online-travel-and-tourism-service-providers/)




