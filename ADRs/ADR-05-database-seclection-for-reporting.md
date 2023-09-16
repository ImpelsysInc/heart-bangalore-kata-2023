## ADR 010: Adoption of PostgreSQL for Analytics and reporting

### Status: Proposed

## Context
We have to build a reporting  and analytics system to collect, store, and analyze user data from our applications. This data includes user interactions, events, and other relevant information. To effectively manage and analyze this data, we need to select a suitable database management system.

## Decision
After careful evaluation, we have decided to use PostgreSQL as the primary database for storing analytics records.

Current scalability can be achieved using PostgreSQL, and if the need arises to transition to a more analytical database like Redshift, this transition can be executed with relative ease and minimal effort.

This decision is based on the following considerations:

**Mature and Reliable**: PostgreSQL is a mature, open-source relational database management system known for its reliability and stability. It has a proven track record in handling large datasets.

**Scalability**: PostgreSQL offers options for horizontal and vertical scaling, enabling us to handle increasing data volumes and high query loads as our analytics system grows.

**Extensible**: PostgreSQL's extensibility allows us to add custom functions and extensions to meet specific analytical requirements. This flexibility is essential for tailoring the system to our needs.

**Community and Ecosystem**: PostgreSQL has a vibrant and active community, which ensures ongoing support, security updates, and access to a wide range of extensions and tools.

**Performance**: PostgreSQL is known for its excellent performance, especially when properly optimized. We can leverage indexing, partitioning, and other performance-enhancing features to ensure responsive analytics queries.

**Data Integrity**: PostgreSQL enforces data integrity constraints, ensuring the accuracy and reliability of our analytics data.

## Consequences
By adopting PostgreSQL as our reportying and analytics solution, we accept the following consequences:

Scaling PostgreSQL horizontally can be complex and may require expertise in database management. Managing a large and growing dataset may pose challenges.

## Alternatives
## Alternative 1: Snowflake
**Pros**: Cloud-Native, Scalability,Concurrency, and etc.    
**Cons**: Cost and complexity.

## Alternative 2: Google BigQuery
**Pros**: Serverless and Fully Managed,Scalability,Speed,Serverless Cost Model and etc.  
**Cons**: Cost for Frequent Usage and Learning Curve.  

## Alternative 2: Red shift
**Pros**: Data Warehousing, Massive Scalability, Concurrency, Integration with AWS and etc.    
**Cons**: Cost and Complexity.

## Decision Rationale
PostgreSQL can be an excellent choice for startups looking to strike a balance between cost-effectiveness, versatility, and scalability. While Redshift excels in specific use cases, PostgreSQL's open-source nature, cost-effectiveness, and adaptability make it a compelling option for startups that need a solid foundation for their database needs while staying mindful of budget constraints.

## References
PostgreSQL  

