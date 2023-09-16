# AWS Cloud Provider

## Title
Chooseing the database engine for storing jobs db for faster access to parellel processing system.
## Status
Proposed

## Context
Since the batch processing system needs to access more than 15millions users related job data for every 5 minues, access needs to be faster . It also need to support adding new jobs information or deleting job information.

## Decision

We have decided to use the Django web framework for the development of the web application. Django provides a robust set of tools and features for building web applications quickly and efficiently. 

## Alternatives Considered

We considered other web frameworks such as Flask and Pyramid. However, we found that Django is a more mature and well-established framework with a robust set of features.

We considered other web frameworks such as Flask and Pyramid. However, we found that Django is a more mature and well-established framework with a robust set of features.

We also discussed developing the application without a web framework and using libraries like SQLAlchemy and Flask-RESTful. However, we found that Django offers broader functionality, making it a better choice for a complete web application.


## Consequences
 
The adoption of Django will lead to the following consequences:

1. Easier to develop and maintain the application due to Django’s built-in tools and features.

2. Separation of business logic and presentation layer, leading to more organized and easier to maintain code.

3. Scalability and robustness of the application.

4. Built-in security features that help protect the application against common web attacks.

5. Access to a large and active community for support.

We understand that Django has a steeper learning curve than other frameworks, but we find that it is worth the investment for the long-term benefits it provides.

## Conclusion

Based on the factors considered, we have decided to use the Django web framework for the development of the web application. We believe that Django’s features, community support, and scalability capabilities make it the best choice for building a complete web application. We will train our developers to use Django to ensure that the framework is used effectively and efficiently.