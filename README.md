# O'Reilly Architecture Katas Sept 2023

Team submission for O'Reilly [Architecture Katas Sept 2023]

Team Members:  
[Krishnaraj Ramakrishna](https://www.linkedin.com/in/krishnaraj-vr-8869b45/)  
[Prinjumon Kalyani](https://www.linkedin.com/in/prinjumon-km-98998121/)  
[Raghu A M](https://www.linkedin.com/in/raghu-a-m-6381b614/)  
[Sangeeth Kumar](https://www.linkedin.com/in/sangeeth-kumar-350b8349/)  
[Vishwanatha K](https://www.linkedin.com/in/visshh7/) 

## Contents
- [Introduction](#introduction)  
- [Requirements](#requirements)
- [Architecture Characteristics](#architecture-characteristics) 
    - [Driving Characteristics](#driving-characteristics)
    - [Implicit Characteristics](#implicit-characteristics)
- [Architecture Approach](#architecture-approach)
    - [Goals](#goals)
- [Context](#context)  
    - [Actors](#actors)
    - [Use Cases](#use-cases)
    - [Event Storming](#event-storming)
- [Containers](#containers)
    - [Service Containers](#service-containers)
    - [API Layer](#api-layer)
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

### Busines Requirments
- Poll E-Mail looking for travel-related E-Mail.

- Filter and whitelist certain E-Mails
- The system must interface with the agency’s existing airline, hotel, and car rental interface system to update travel details (delays, cancellations, updates, gate changes, etc.). Updates must be in the app within 5 minutes of an update (better than the competition).

- Customers should be able to add, update, or delete existing reservations manually as well.

- Items in the dashboard should be able to be grouped by trip, and once the trip is complete, the items should automatically be removed from the dashboard.

- Users should also be able to share their trip information by interfacing with standard social media sites or allowing targeted people to view your trip.

- Provide end-of-year summary reports for users with a wide range of metrics about their travel usage.

- Road Warrior gathers analytical data from users trips for various purposes - travel trends, locations, airline and hotel vendor preferences, cancellation and update frequency, and so on.

### Technical Requirements
- Richest user interface possible across all deployment platforms.

- Must integrate seamlessly with existing travel 
systems (i.e, SABRE, APOLLO).

- Must integrate with preferred travel agency for 
quick problem resolution (help me!).

- Must work internationally.

- Users must be able to access the system at all times (max 5 minutes per month of unplanned downtime).

- Travel updates must be presented in the app within 5 minutes of generation by the source.

- Response time from web (800ms) and mobile (First-contentful paint of under 1.4 sec)

## Architecture Characteristics
The following section highlights the architecure characteristics we consider crucial to a successful implementation of the system.

### Driving Characteristics

### Implicit Characteristics
**Security**  



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







