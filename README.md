# O'Reilly Architecture Katas Sept 2023

## Team submission for O'Reilly [Architecture Katas Sept 2023]

## Team Members:  
- [Krishnaraj Ramakrishna](https://www.linkedin.com/in/krishnaraj-vr-8869b45/)  
- [Prinjumon Kalyani](https://www.linkedin.com/in/prinjumon-km-98998121/)  
- [Raghu A M](https://www.linkedin.com/in/raghu-a-m-6381b614/)  
- [Sangeeth Kumar](https://www.linkedin.com/in/sangeeth-kumar-350b8349/)  
- [Vishwanatha K](https://www.linkedin.com/in/visshh7/) 


## Contents
- [Introduction](#introduction)  
- [Requirements](#requirements)
    - [Business Requirments](#business-requirments)  
    - [Technical Requirements](#technical-requirements)
    - [Market Research](#[market-research) 
- [Architecture Characteristics](#architecture-characteristics) 
    - [Driving Characteristics](#driving-characteristics)
    - [Implicit Characteristics](#implicit-characteristics)
- [Use Journey](#user-journey)
    - [ux](#ux)
- [Event Storming](#event-storming)
- [Context](#context)  
- [Containers](#containers)
    - [API Layer](#api-layer)
    - [Batch-Process](#service-containers)
- [Components](#components)
    - [Identity and Access Manager](#identity-and-access-manager)
    - [Profile Manager](#profile-manager)
    - [Connections Manager](#connections-manager)
    - [Reporting and Analytics Manager](#reporting-and-analytics-manager)
- [Deployment](#deployment)
- [Cost Analysis](#cost-analysis)
- [Evaluation, Risks and Architecture Fitness](#evaluation-risks-and-architecture-fitness)  
- [ADRs](#adrs)

## Introduction
The Road Warrior wants to build the next generation online trip management Dashboard to allow travelers to see all of their existing reservations organized by trip either online (web) or through their mobile device.

## Requirements

### Business Requirments
**US-01:** Poll E-Mail looking for travel-related E-Mail. \
**US-02:** Filter and whitelist certain E-Mails \
**US-03:** The system must interface with the agency’s existing airline, hotel, and car rental interface system to update travel details (delays, cancellations, updates, gate changes, etc.). Updates must be in the app within 5 minutes of an update (better than the competition).\
**US-04:** Customers should be able to add, update, or delete existing reservations manually as well.\
**US-05:** Items in the dashboard should be able to be grouped by trip, and once the trip is complete, the items should automatically be removed from the dashboard.\
**US-06:** Users should also be able to share their trip information by interfacing with standard social media sites or allowing targeted people to view your trip.\
**US-07:** Provide end-of-year summary reports for users with a wide range of metrics about their travel usage.\
**US-08:** Road Warrior gathers analytical data from users trips for various purposes - travel trends, locations, airline and hotel vendor preferences, cancellation and update frequency, and so on.
**US-09:** Must integrate seamlessly with existing travel systems (i.e, SABRE, APOLLO).\
**US-10:** Must integrate with preferred travel agency for quick problem resolution (help me!).\

### Technical Requirements
**US-11:** Richest user interface possible across all deployment platforms.\
**US-12:** Must work internationally.\
**US-13:** Users must be able to access the system at all times (max 5 minutes per month of unplanned downtime).\
**US-14:** Travel updates must be presented in the app within 5 minutes of generation by the source.\
**US-15:** Response time from web (800ms) and mobile (First-contentful paint of under 1.4 sec)\

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
•	Transportation (Airlines, Car Rental, Rail, Cruise, and others)
•	Travel Accommodation (Hotels and resorts)
•	Travel Intermediation (Online Travel Agencies, Tour Operator Websites, and Others)
•	Personalized travel guide and recommendations

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
5.	Capability to personalize the options by providing recommendations in the form of updates or commercial advertisements as rendered by the B2B segments

## System Architecture Characteristics

To ensure a successful system implementation, it's vital to prioritize key architecture characteristics. These elements guarantee reliability, availability, and responsiveness, delivering a seamless user experience.


![Architecture Characteristics](/Diagrams/architecture-characteristic.png)
*Figure: Architecture Characteristics*

## Top 3 Characteristics
### Scalability
 Scalability allows the system to accommodate a growing user base and increased data volume, ensuring that Road Warrior can scale its services as it gains more users.

### Availability
"99.99% uptime" is a High availability, with a maximum of 5 minutes per month of unplanned downtime, is essential to ensure travelers can access their reservations and updates reliably.
### Responsiveness
 Responsiveness in the user interface is vital for providing a positive user experience, allowing travelers to quickly access and manage their travel information.

 ## Other Characteristics
### Interoperability
 Interoperability is crucial to seamlessly integrate with external travel systems and agencies, ensuring smooth data exchange and collaboration.

### Elasticity
 Elasticity enables the system to dynamically scale resources up or down in response to varying workloads, ensuring cost-efficiency and optimal performance.

### Performance
 Performance optimization is critical to meet the specified response times and deliver real-time travel updates quickly and efficiently.

### Reliability
 Reliability is paramount to ensure that travelers receive timely travel updates and manage their reservations without disruptions or errors.

## Implicit Characters
### Feasibility (Cost/Time)
Achieving rapid time-to-market while managing development costs is a feasible goal with the selected "mini-services" architecture.

### Security
Implementing strong authentication and authorization mechanisms is vital to safeguard traveler information and data integrity.

### Maintainability

Ensuring clean code, documentation, and knowledge sharing within the development team are essential for long-term system maintainability.

### Observability

Implementing comprehensive monitoring and observability solutions enables efficient tracking of system performance and early issue detection for proactive problem-solving.

## Architecture Approach
### Goals
**"Microservices are not the goal, you don't win by having microservices"** 
**A discussion regarding architecture characteristics and microservices**  
## Context
### Actors and Use Cases
### Event Storming
## Containers
### Service Containers
### API Layer
### Coupling and Architecture Quanta
**Static Coupling**
**Dynamic Coupling**
## Components
### Identity and Access Manager
### Profile Manager
### Connections Manager

**Proximity Detection**  
**Establishing Connection**  

### Reporting and Analytics Manager
### Social Media API Manager
## Deployment
The next diagram models a sample deployment of The Road Warrior system on the AWS Platform. A brief overview of the involved AWS services follows.

![AWS Infrastructure Architecture](/Diagrams/aws-infra-architecture.png)
*Figure * AWS Deployment Architecture*

## Cost Analysis
## Evaluation, Risks and Architecture Fitness  
## ADRs
## References







