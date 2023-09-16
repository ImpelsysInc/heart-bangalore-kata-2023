# Transactional database selection for application

## Title
Choosing the transcational database for the application
## Status
Proposed

## Context
Since the application need to store trip data for more than 15 Million users and serve the data with in 800Milliseconds. the db should support that scalablity

## Decision

We chose to use Posgresql for its Scalablity, Performance, Opensource support
Posgresql can be scaled using read replicas for read scaliablity and also sharding or partitioning for further scalablity.
We aslo use PosgreSQL Auroa for management and faster scalablity and peroformance

## Rationale

After analyzing and comparing the features of both PostgreSQL and MySQL, we have come to the conclusion that PostgreSQL is the better option because of the following reasons:

1. **Advanced features:**  PostgreSQL has a wide range of advanced features like JSON support, full-text search, and spatial data management, which are essential for our project.

2. **Performance:**  PostgreSQL has a proven track record of excellent performance capabilities, which will ensure that our project runs smoothly without any performance issues.

3. **Community support:**  PostgreSQL has a large and active community that provides regular updates and support, making it easier to resolve any issues that arise during the project development phase.

4. **Scalability:**  PostgreSQL is highly scalable, and it can handle large amounts of data with ease, which will be essential for our project.

5. **Security:**  PostgreSQL has a robust security mechanism that will ensure that our project data is secure at all times, and it meets all our organization's security requirements.


## Alternatives Considered

The other option that we considered was MySQL. MySQL is also a highly capable database management system, but it lacks some of the advanced features that PostgreSQL offers, and its performance capacity is not as good as that of PostgreSQL.

For hyper scalablity following are good options
- Casandra or Scylla db(similar to Cassandra)  - 
- Google Cloud Spanner 

We are not considering Oracle or SQL Server due to properiery database.

![Architecture Characteristics](/Diagrams/relational-database-comparision.webp)

## Conclusion

Based on our analysis, we have decided to use PostgreSQL as the preferred database management system for our upcoming project. This decision has been made after careful consideration, and we believe that it will help us achieve our project goals efficiently and effectively.
