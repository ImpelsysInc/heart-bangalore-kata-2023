# AWS Cloud Provider

## Title
Choosing the infrastructure (public cloud provider) for Road Warriors startup
## Status
Proposed

## Context
Since the application is a startup we choose to use the cloud provider support most of the components are managed services and also that are building using opensource standards so that the migrate to other cloud are easier 

## Decision
The  leading cloud providers such are
[Google Cloud Platform](https://cloud.google.com/), 
[Amazon Web Services](https://aws.amazon.com/) 
[Azure](https://azure.microsoft.com/) 

All have most of the capabilites we are looking for the solution and support the components are managed servie. We are not looking in to cloud agnotic solution but where ever we can use with minimal effort that can be chosen. Our main goal is to get start things faster with minal effort and small team with less managment overhead but take case scalablity and monitoring aspect.

Due to experienced knowedg in AWS for the existing team we choose the AWS. Also they are the leader in this area and All the components needed are supported by this provider.

## Consequences
There is a lock-in to a certain public cloud provider. Developers have to learn usign the Platform and services if the respective know-how is not available yet. Extending to multi-cloud setup is a possibility but requires additional efforts which, in the current state of the project, do not make sense.
