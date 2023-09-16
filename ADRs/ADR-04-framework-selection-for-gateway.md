## Framework selection for api gateway.

### Status: Proposed

## Context
We are in the process of designing and implementing the architecture for our microservices-based application. One of the key requirements for our application is to efficiently manage and expose a set of microservices as APIs, ensuring security, rate limiting, and centralized configuration.

## Decision
As we have chosen Golang as our primary programming language, we have also decided to adopt the Krakend API Gateway as our primary solution for managing and exposing microservices through APIs.Following are the capabilities of Krakend

**Microservices Integration**: Krakend provides seamless integration with our microservices architecture, allowing us to aggregate, route, and expose multiple microservices through a unified API gateway.

**Middleware Support**: Krakend offers a wide range of built-in middleware options for handling authentication, rate limiting, caching, logging, and request/response transformations. This enables us to enforce security and operational policies consistently across all our APIs.

**Performance**: Krakend is designed for high performance and is capable of handling a large number of concurrent requests, making it suitable for our application's scalability requirements.

**Open Source and Community Support**: Krakend is an open-source project with an active community, ensuring that we have access to ongoing development, support, and documentation.

**Developer-Friendly**: Krakend's configuration is written in JSON or YAML, which is familiar to our development team and simplifies the setup and maintenance of API routes.

## Consequences
By adopting Krakend as our API gateway solution, we accept the following consequences:

Developers will need to learn and become proficient with Krakend's configuration and concepts.
We will need to ensure the availability and scalability of the Krakend infrastructure in our deployment environment.
## Alternatives
## Alternative 1: Build Custom API Gateway
**Pros**: Complete customization and control over the API gateway's behavior.  
**Cons**: Development and maintenance effort, potentially longer time to market.

## Alternative 2: Use a Different API Gateway (e.g.Kong,AWS API Gateway,Zuul,Tyk,Traefic)
**Pros**: Familiarity with existing tools, potential cost savings.  
**Cons**: May require more extensive customization, limited support for microservices-specific features.

## Decision Rationale
Krakend was chosen because it aligns with our project requirements for efficiently managing microservices-based APIs. Its microservices integration, middleware support, and developer-friendly configuration make it a strong choice for our API gateway needs. While alternatives were considered, Krakend's feature set and community support make it a well-suited solution for our application. Also On the hardware side, KrakenD is very light and consumes very low resources. For instance, the consumption pattern of the baseline (we will see this definition below) is around 100-200MB of RAM and can work on production with 0.5 vCPU. This baseline can process thousands of requests per second.
