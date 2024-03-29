# Spring Boot
- helps you create stand-alone, production-grade spring based applications
- take opinionated view of the spring platform and third party libraries - **get started with minimum fuss**

## Primary Goals
- provide a radically faster and widely accessible **getting-started experience**
- be opinionated out of the box but get out of the way quickly as requirements start to diverge from the defaults - **switch easily to other options**
- provide a range of **non-functional features** that are common to large projects e.g
    - embedded servers
    - security metrics
    - health checks
    - externalized configurations
- absolutely no **code generation**

## Servlet Containers
- a servlet container(aka web container/servlet engine) is a component that provides a runtime environment for executing Java Servlets and Java Server Pages
- handles the lifecycle of servlets, manages incoming HTTP requests and generates responses
- spring boot supports:
    - Apache Tomcat
        - stable
    - Eclipse Jetty
        - lightweight
    - Redhat Undertow
        - non-blocking 

## Starters
- starters are a set of convenient dependency descriptors that you can include in your application

|Name|Description|
|---|---|
|spring-boot-starter|core starter includes auto-configuration support, logging and yaml|
|spring-boot-starter-activemq|JMS messaging using Apache ActiveMQ|
|spring-boot-starter-amqp|Spring AMQP and Rabbit MQ|
|spring-boot-starter-aop|Aspect-oriented programming with Spring AOP and AspectJ|
|spring-boot-starter-artemis|JMS messaging using Apache Artemis|
|spring-boot-starter-batch|Spring Batch|
|spring-boot-starter-cache|Spring Framework’s caching support|
|spring-boot-starter-data-cassandra|Cassandra distributed database and Spring Data Cassandra|
|spring-boot-starter-data-cassandra-reactive|Cassandra distributed database and Spring Data Cassandra Reactive|
|spring-boot-starter-data-couchbase|Couchbase document-oriented database and Spring Data Couchbase|
|spring-boot-starter-data-couchbase-reactive|Couchbase document-oriented database and Spring Data Couchbase Reactive|
|spring-boot-starter-data-elasticsearch|Elasticsearch search and analytics engine and Spring Data Elasticsearch|
|spring-boot-starter-data-jdbc|Spring Data JDBC|
|spring-boot-starter-data-jpa|Spring Data JPA with Hibernate|
|spring-boot-starter-data-ldap|Spring Data LDAP|
|spring-boot-starter-data-mongodb|MongoDB document-oriented database and Spring Data MongoDB|
|spring-boot-starter-data-mongodb-reactive|MongoDB document-oriented database and Spring Data MongoDB Reactive|
|spring-boot-starter-data-neo4j|ne04j graph database and spring data neo4j|
|spring-boot-starter-data-r2dbc|Using Spring Data R2DBC|
|spring-boot-starter-data-redis|Using Redis key-value data store with Spring Data Redis reactive and the Lettuce client|
|spring-boot-starter-data-redis-reative|Using Redis key-value data store with Spring Data Redis reactive and the Lettuce client|
|spring-boot-starter-data-rest|Exposing Spring Data repositories over REST using Spring Data REST and Spring MVC|
|spring-boot-starter-freemarker|Building MVC web applications using FreeMarker views|
|spring-boot-starter-graphql|Building GraphQL applications with Spring GraphQL|
|spring-boot-starter-groovy-templates|Building MVC web applications using Groovy Templates views|
|spring-boot-starter-hateoas|Building hypermedia-based RESTful web application with Spring MVC and Spring HATEOAS|
|spring-boot-starter-integration|Spring Integration|
|spring-boot-starter-jdbc|Using JDBC with the HikariCP connection pool|
|spring-boot-starter-jersey|Building RESTful web applications using JAX-RS and Jersey. An alternative to spring-boot-starter-web|
|spring-boot-starter-jooq|Using jOOQ to access SQL databases with JDBC. An alternative to spring-boot-starter-data-jpa or spring-boot-starter-jdbc|
|spring-boot-starter-json|Reading and writing json|
|spring-boot-starter-mail|Java Mail and Spring Framework’s email sending support|
|spring-boot-starter-mustache|Building web applications using Mustache views|
|spring-boot-starter-oauth2-authorization-server|Spring Authorization Server features|
|spring-boot-starter-oauth2-client|Spring Security’s OAuth2/OpenID Connect client features|
|spring-boot-starter-oauth2-resource-server|Spring Security’s OAuth2 resource server features|
|spring-boot-starter-pulsar|Spring for Apache Pulsar|
|spring-boot-starter-pulsar-reactive|Spring for Apache Pulsar Reactive|
|spring-boot-starter-quartz|Quartz scheduler|
|spring-boot-starter-rsocket|Building RSocket clients and servers|
|spring-boot-starter-security|Using Spring Security|
|spring-boot-starter-test|Testing Spring Boot applications with libraries including JUnit Jupiter, Hamcrest and Mockito|
|spring-boot-starter-thymeleaf|Building MVC web applications using Thymeleaf views|
|spring-boot-starter-validation|Java Bean Validation with Hibernate Validator|
|spring-boot-starter-web|Building web, including RESTful, applications using Spring MVC. Uses Tomcat as the default embedded container|
|spring-boot-starter-web-services|Using Spring Web Services|
|spring-boot-starter-webflux|Building WebFlux applications using Spring Framework’s Reactive Web support|
|spring-boot-starter-websocket|Building WebSocket applications using Spring Framework’s MVC WebSocket support|

- Spring Boot also includes the following starters that can be used if you want to exclude or swap specific technical facets:

|Name|Description|
|---|---|
|spring-boot-starter-jetty|Using Jetty as the embedded servlet container. An alternative to spring-boot-starter-tomcat|
|spring-boot-starter-log4j2|Using Log4j2 for logging. An alternative to spring-boot-starter-logging|
spring-boot-starter-logging|Logging using Logback. Default logging starter|
|spring-boot-starter-reactor-netty|Using Reactor Netty as the embedded reactive HTTP server.|
|spring-boot-starter-tomcat|Using Tomcat as the embedded servlet container. Default servlet container starter used by spring-boot-starter-web|
|spring-boot-starter-undertow|Using Undertow as the embedded servlet container. An alternative to spring-boot-starter-tomcat|

## Spring Beans and Dependency Injection
