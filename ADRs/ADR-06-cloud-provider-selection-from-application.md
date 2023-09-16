# AWS Cloud Provider

## Title
Choosing the infrastructure (public cloud provider) for Road Warriors startup
## Status
Proposed

## Context
Given that the application is a startup, we opted to utilize a cloud provider that offers predominantly managed services. These services are constructed using open-source standards, making it more straightforward to migrate to other cloud platforms in the future. 

## Decision
The  leading cloud providers such are
[Google Cloud Platform](https://cloud.google.com/), 
[Amazon Web Services](https://aws.amazon.com/) 
[Azure](https://azure.microsoft.com/) 

All these providers possess the majority of the capabilities we require for our solution, and they provide support through managed services. We are not specifically seeking a cloud-agnostic solution, but rather selecting whichever option requires minimal effort for seamless integration. Our primary objective is to expedite the startup process with a small team, minimizing management overhead, while still ensuring scalability and robust monitoring capabilities.

Due to the existing team's expertise in AWS, we opted for this cloud provider. Additionally, AWS is a leader in the field, and it offers support for all the necessary components we require for our project.

## Consequences
There is a level of dependency on a particular public cloud provider, which means developers may need to acquire skills related to that specific platform and its services if they are not already familiar. While the option to expand to a multi-cloud setup exists, it would demand additional resources and efforts that may not be justifiable at the current stage of the project.
