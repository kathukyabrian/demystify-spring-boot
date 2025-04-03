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

[Web Server vs Application Server vs Servlet Container](https://pathum-liyanagama.medium.com/java-servlet-container-vs-application-server-vs-web-server-7471f89402ac)

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
### Recommendations
- use constructor injection to wire up dependencies
    - if a bean has more than 1 constructor, you will need to mark the one you want spring to use with *@Autowired*
- use @ComponentScan to find beans
    - all app components - @Component, @Service, @Repository, @Controller are automatically registered as beans

## @SpringBootApplication Annotation
- enables 3 features
    1. auto-configuration(**@EnableAutoConfiguration**)
    2. component scan(**@ComponentScan**)
    3. ability to define extra configuration on the application class(**@SpringBootConfiguration**)


## Application Availability
### Liveness State
- tells whether an application's internal state allows it to work correctly or recover by itself if it is currently failing.
- broken liveness state means that the application is in a state that it cannot recover from and infra should restart the application
- internal state of a spring boot application is mostly represented by **ApplicationContext**.
- if the **ApplicationContext** has started successfully, spring boot assumes that the application is in a valid state.

### Readiness State
- tells whether an application is ready to handle traffic
- a failing readiness state tells the platform that is should not route traffic to the application for now.
- typically happens during startup, while **CommandLineRunner** and **ApplicationRunner** components are being processed, or at any time if the application decides that it is **too busy for additional traffic**.


## Using ApplicationRunner and CommandLineRunner
- if you need some code to run once the **SpringApplication** has started you can implement the **ApplicationRunner** or **CommandLineRunner** interfaces 
    - both interfaces work the same way 
    - offer a single *run()* - it is called just before *SpringApplication.run(…​)*

-  **This contract is well suited for tasks that should run after application startup but before it starts accepting traffic.**

## Application Exit
- each SpringBootApplication registers a shut down hook with the JVM to ensure that the ApplicationContext closes gracefully on exit
- all the standard spring lifecycle callbacks can be used e.g
    - DisposableBean interface
    - @PreDestroy
- in addition, beans may implement the **org.springframework.boot.ExitCodeGenerator** interface if they wish to return a specific exit code when ```SpringApplication.exit()``` is called


## Externalized Configuration
- spring boot lets you externalize your config so that you are able to work with the same application code in different environments
- examples of external configuration sources:
    - Java properties files
    - YAML files
    - environment variables
    - command-line arguments

- property values can be
    - **injected directly into your beans** using the **@Value** annotation
    - accessed through Spring's **Environment** abstraction
    - bound to structured objects through **@ConfigurationProperties**

- spring boot uses the following property order - later property sources can override earlier ones
    1. Default properties - specified by setting ```SpringApplication.setDefaultProperties```
    2. ```@PropertySource``` annotations on your @Configuration classes
    3. config data such as application.properties
    4. RandomValuePropertySource that has properties only in random.*
    5. OS env variables
    6. Java System Props - System.getProperties
    7. JNDI attributes from java:comp/env
    8. ServletContext init params
    9. ServletConfig init params
    10. Properties from SPRING_APPLICATION_JSON
    11. Command line arguments
    12. properties attributes on your tests
    13. @DynamicPropertySource annotations in your tests
    14. @TestPropertySource in your tests
    15 Devtools global settings properties

- config data files are considered in the following order
    - Application Properties file packaged inside your jar - application.properties and YAML variants
    - Profile-specific application properties packaged inside your jar 
    - Application properties outside your jar
    - Profile-specific application properties outside your jar

### External Application Properties
- spring boot will automatically find and load application.properties and application.yaml files from the following locations when your application starts
    - from the classpath
        1. classpath root
        1. classpath /config package
    - from the current directory
        1. current directory
        1. the config subdirectory in the current directory
        1. immediate child directories of the config directory

- you can override the name of the config using
    ```spring.config.name=myproject```

- you can also refer to an explicit file location using 
    ```spring.config.location=optional:classpath:/default.properties,\optional:classpath:/override.properties```
    - this allows comma separated list of one or more locations to check
    - optional prefix means that you do not mind if the locations do not exist

### WildCard Locations
- eg /config/* - this will load all config files in the config folder

### Configuration Trees
- usecase example: Kubernetes
- 2 options
    1. single file contains a complete set of properties
    2. multiple files are written to a directory tree - filename becomes the key and the contents become the value
- for case 1 - you can import the file using **spring.config.import**
- for case 2 - you need **configtree:** prefix so that spring boot knows it needs to expose all file as properties

- example
    - /etc
        - /config
            - /myapp
                - username
                - password

- username would be a config value and password would be a secret
- to import these props you can add the following to application.properties
```spring.config.import=optional:configtree:/etc/config/``` 

### Property Placeholders
```
app.name=MyApp
app.description=${app.name} is a Spring Boot application written by ${username:Unknown}
```

### Configuring Random Values
```
my.secret=${random.value}
my.number=${random.int}
my.bignumber=${random.long}
my.uuid=${random.uuid}
my.number-less-than-ten=${random.int(10)}
my.number-in-range=${random.int[1024,65536]}
```
- The random.int* syntax is OPEN value (,max) CLOSE where the OPEN,CLOSE are any character and value,max are integers. If max is provided, then value is the minimum value and max is the maximum value (exclusive).

## Profiles
- it is possible to segregate parts of your app config and make it available only in certain environments
- any **@Component**, **@Configuration** or **@ConfigurationProperties** can be **marked with @Profile** to limit when it is loaded
- to specify active profiles use below env variable
```
spring.profiles.active=dev,hsqldb
```

## Logging
- spring boot uses **commons logging** for all internal logging but leaves the underlying log implementation open
- default configurations are provided for
    - java util logging
    - log4j2
    - logback
- loggers are pre-configured to use console output with optional file output also available
- by default, if you use **starters**, **logback** is used 

### Log Format
```
2024-03-21T10:10:12.859Z  INFO 34208 --- [myapp] [           main] o.s.b.d.f.logexample.MyApplication       : Starting MyApplication using Java 17.0.10 with PID 34208 (/opt/apps/myapp.jar started by myuser in /opt/apps/)
2024-03-21T10:10:12.866Z  INFO 34208 --- [myapp] [           main] o.s.b.d.f.logexample.MyApplication       : No active profile set, falling back to 1 default profile: "default"
2024-03-21T10:10:14.323Z  INFO 34208 --- [myapp] [           main] o.s.b.w.embedded.tomcat.TomcatWebServer  : Tomcat initialized with port 8080 (http)
2024-03-21T10:10:14.348Z  INFO 34208 --- [myapp] [           main] o.apache.catalina.core.StandardService   : Starting service [Tomcat]
2024-03-21T10:10:14.348Z  INFO 34208 --- [myapp] [           main] o.apache.catalina.core.StandardEngine    : Starting Servlet engine: [Apache Tomcat/10.1.19]
2024-03-21T10:10:14.426Z  INFO 34208 --- [myapp] [           main] o.a.c.c.C.[Tomcat].[localhost].[/]       : Initializing Spring embedded WebApplicationContext
2024-03-21T10:10:14.428Z  INFO 34208 --- [myapp] [           main] w.s.c.ServletWebServerApplicationContext : Root WebApplicationContext: initialization completed in 1491 ms
2024-03-21T10:10:15.041Z  INFO 34208 --- [myapp] [           main] o.s.b.w.embedded.tomcat.TomcatWebServer  : Tomcat started on port 8080 (http) with context path ''
2024-03-21T10:10:15.061Z  INFO 34208 --- [myapp] [           main] o.s.b.d.f.logexample.MyApplication       : Started MyApplication in 2.782 seconds (process running for 3.145)
```

- structure
    - date and time
    - log level
        - ERROR
        - WARN
        - INFO
        - DEBUG
        - TRACE
    - process ID
    - \--- separator 
    - application name: optional
        - only if ```spring.application.name``` is set
        - if ```spring.application.name``` is set and you do not want it to be shown in the logs use ```logging.include-application-name = false```
    - thread name
    - correlation id
        - if tracing is enabled
    - logger name
        - source class name
    - log message 

### File Output
- by default logs to console
- if you want to log to a file use either:
    - ```logging.file.name```
    - ```logging.file.path```

|logging.file.name|logging.file.path|example|description|
|---|---|---|---|
|none|none||console only logging|
|specific file|none|my.log|writes to my.log - can be absolute path or current directory|
|none|specific directory|/var/log|writes spring.log to /var/log/|

- log files rotate when they reach 10mb

### File Rotation
- if you are using logback, you can fine-tune rotation files using config files, else you need to configure rotation by yourself e.g using log4j2.xml
- properties supported

|name|description|
|---|---|
|logging.logback.rollingpolicy.file-name-pattern|filename pattern used to create log archives|
|logging.logback.rollingpolicy.clean-history-on-start|if log archive cleanup should occur when the application starts|
|logging.logback.rollingpolicy.max-file-size|maximum size of log before it is archived|
|logging.logback.rollingpolicy.total-size-cap|maximum amount of size log archives can take before being deleted|
|logging.logback.rollingpolicy.max-history|maximum number of archive log files to keep (defaults to 7)|

### Log Levels
- logging level can be set as follows
    - ```logging.level.<logger-name>=<level>```
- level
    - TRACE
    - DEBUG
    - INFO
    - WARN
    - ERROR
    - FATAL
    - OFF

### Log Groups
- help group related loggers together

```
logging.group.tomcat=org.apache.catalina,org.apache.coyote,org.apache.tomcat

logging.level.tomcat=trace
```

- predefined logging groups

|name|loggers|
|---|---|
|web|org.springframework.core.codec, org.springframework.http, org.springframework.web, org.springframework.boot.actuate.endpoint.web, org.springframework.boot.web.servlet.ServletContextInitializerBeans|
|sql|org.springframework.jdbc.core, org.hibernate.SQL, org.jooq.tools.LoggerListener|

### Custom Log Configuration
- the various logging systems can be activated by including the appropriate libraries on the classpath and can be configured by providing a suitable configuration file in
    - root of classpath
    - location specified by ```logging.config```
- you can force Spring Boot to use a particular logging system by using the ```org.springframework.boot.logging.LoggingSystem``` system property. 
- the value should be the fully qualified class name of a LoggingSystem implementation. 
- you can also disable Spring Boot’s logging configuration entirely by using a value of none.
- depending on your logging system, the following files are loaded:

|Logging System|Customization|
|---|---|
|logback|logback-spring.xml or logback-spring.groovy or logback.xml or logback.groovy|
|log4j2|log4j2-spring.xml or log4j2.xml|
|java util logging|logging.properties|




## Aspect Oriented Programming
[Aspect Oriented Programming in Spring](https://docs.spring.io/spring-framework/reference/core/aop-api.html)
- AOP complements OOP by providing another way of thinking about program structure
- key unit of modularity in *OOP* is a **class** - whereas in *AOP* it is an **aspect**
- aspects enable the modularization of concerns(e.g transaction management) that cut across multiple types and objects(crosscutting concerns)
- used in the spring framework to
    - provide declarative enterprise services
    - let users implement custom aspects 

### Concepts
> Aspect - modularization of a concern that cuts across multiple classes

> Join Point - a point during the execution of a program e.g execution of a method or handling of an exception

> Advice - action taken by an aspect at a particular join point

> Pointcut - a predicate that matches join points - advice is associated with a pointcut expression and runs at any joint point matched by the pointcut. (**AspectJ**)

> Introduction - declaring additional methods of fields on behalf of a type 

> Target Object - an object being advised by 1 or more aspects

> AOP Proxy - object created by AOP framework in order to implement the aspect contracts

> Weaving - linking aspects with other app types or objects to create an advised object

### Advice Types
- **Before** Advice - runs before a join point but does not have ability to prevent execution flow proceeding to the join point
- **After Returning** Advice - to be run after a join point completes normally
- **After Throwing** Advice -  to be run if a method exits by throwing an exception
- **After(finally)** Advice - to be run regardless of the means by which a join point exits (normal or exceptional return).
- **Around** Advice -  surrounds a join point such as a method invocation. This is the most powerful kind of advice. Around advice can perform custom behavior before and after the method invocation. It is also responsible for choosing whether to proceed to the join point or to shortcut the advised method execution by returning its own return value or throwing an exception.


## Testing
- spring boot provides a number of utilities to help when testing your application
- provided by 2 modules
    - spring-boot-test - core items
    - spring-boot-test-autoconfigure - supports autoconfiguration
- most developers use **spring-boot-starter-test** which imports
    - spring boot test modules
    - junit
    - jupiter
    - assertJ
    - hamcrest
    - other useful libraries

### Dependencies
- **Junit5** - de-facto standard for unit testing Java apps
- **Spring Test and Spring Boot Test** - utilities and intergration testing support for spring boot applications
- **AssertJ** - fluent assertion library
- **Hamcrest** - library of matcher objects - constraints or predicates
- **Mockito** - Java mocking framework
- **JSONAssert** - an assertion library for JSON
- **JSONPath** - XPath for JSON
- **Awaitility** - library for testing async systems 

### Testing Spring Applications
- one major advantage of dependency injection is that it makes your code easier to unit test 
- often you need to move beyond unit testing and start intergration testing


# Data
## SQL Databases
- options
    - direct jdbc access using jdbcClient or jdbcTemplate
    - object relation mapping such as Hibernate

## Configuring a DataSource
### Embedded Database Support
- spring boot can autoconfigure
    - h2
    - hsql
    - derby
- you need not provide connection urls - you  only need to include a build dependency to the embedded database.
- if there are multiple embedded databases on the classpath, set the ```spring.datasource.embedded-database-connection``` configuration property to control which one is used
- setting the property to none disables auto-configuration of an embedded database

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-jpa</artifactId>
</dependency>
<dependency>
    <groupId>org.hsqldb</groupId>
    <artifactId>hsqldb</artifactId>
    <scope>runtime</scope>
</dependency>
```

### Connection to a Production Database
```yaml
spring:
  datasource:
    url: "jdbc:mysql://localhost/test"
    username: "dbuser"
    password: "dbpass"
```

### Connection Pools
- database operation
    1. The application uses a database driver to open a connection.
    1. A network socket is opened to connect the application and the database.
    1. The user is authenticated.
    1. The operation completes and the connection may be closed.
    1. The network socket is closed.

- for small projects, opening and closing a connection are not expensive enough to warrant worrying about.
- as your application scales up, the constant opening and closing of connections becomes more expensive and can begin to impact your application's performance.
- it makes sense to find a way of keeping connections open and passing them from operation to operation as they’re needed, rather than opening and closing a brand new connection for each operation.
- database connection pooling is a way to reduce the cost of opening and closing connections by maintaining a “pool” of open connections that can be passed from database operation to database operation as needed. 

### How Spring Boot Does Connection Pooling
- algorithm
    - prefer HikariCP for its performance and concurrency
    - Tomcat pooling Datasource
    - Commons DBCP2 
    - Oracle UCP

- if you use **spring-boot-starter-jdbc** or **spring-boot-starter-jpa** you automatically get HikariCP

- if you want to bypass the algorithm, you can explicitly specify your connection pool using ```spring.datasource.type```

## JPA and Spring Data JPA
- Java Persistence API - lets you map objects to relational databases
- spring-boot-starter-data-jpa provides a quick way to get started - it provides the following dependencies
    - hibernate - most popular JPA implementations
    - spring-data-jpa - helps you implement JPA-based repositories
    - spring-orm - core ORM support from the spring framework

### Entity Classes
- entity scanning is used 
    - @Entity
    - @Embeddable
    - @MappedSuperclass

### Spring Data JPA Repositories
- interfaces that you can define to access data

### Concept
- central interface is **Repository** - takes the domain class to manage and identifier type of the domain class as the type arguments
- **CrudRepository** and **ListCrudRepository** interfaces provide CRUD functionality for the entity class being mapped
- **PagingAndSortingRepository** and **ListPagingAndSortingRepository** ease paginated access to entities
- difference between the list and none list repos
    - non list return iterables
    - list return lists

### Defining Repository Interfaces
- you need to define a domain class-specific repository interface
- the interface must extend __Repository__ and be typed to the domain class and an ID type

#### CRUD repository
- gives you methods for CRUD functions
- ListCrudRepository also exists and it returns a List for what CrudRepository would return an Iterable
- if you are using a reactive store, use ReactiveCrudRepository or RxJava3CrudRepository
- additionally, you can extend PagingAndSortingRepository, ReactiveSortingRepository, RxJava3SortingRepository or CoroutineSortingRepository if you need methods that allowing sorting
- you can define your own base interface to inherit from. such an interface must be annotated with __@NoRepositoryBean__. this prevents spring data from creating an instance of it directly

```java
@NoRepositoryBean
interface MyBaseRepository<T, ID> extends Repository<T, ID> {

  Optional<T> findById(ID id);

  <S extends T> S save(S entity);
}

interface UserRepository extends MyBaseRepository<User, Long> {
  User findByEmailAddress(EmailAddress emailAddress);
}
```

### Configuration
#### Bootstrap Mode
- spring data jpa repositories are default spring beans 
  - singleton scoped
  - eagerly initialized
- during startup, they already interact with the JPA entity manager for verification and metadata analysis purposes.
- spring supports the initialization of the jpa EntityManagerFactory in a background thread because the process takes time
- to make use of that, we need to make sure that jpa repositories are initialized as late as possible
- following values are allowed for bootstrap mode
##### Default
- instantiated eagerly unless explicitly annotated with @Lazy
##### Lazy
- causes lazy initialization proxies to be created to be injected into client beans
- repository instances will be initialized and verified on demand
##### Deffered
- same as __lazy__ but triggering repository initialization in response to an __ContextRefreshedEvent__ so that repositories are verified before the application has completely started.

### Persisting Entities
- entities can be saved with the CrudRepository.save() method
- if the entity has not yet been persisted, jpa saves the entity with a call to *entityManager.persist()*, otherwise it calls the *entityManager.merge()* method

#### How JPA detects new entities
- __version property and id property detection__
  - first checks presence of a version property of non-primitive type, if there is, the entity is considered new if the value of that property is set to *null*
  - if there is no version property, it proceeds to check id property, if the identifier is null, then the entity is assumed to be new.
- __implementing Persistable__ 
  - if an entity implements Persistable, jpa delegates the detection to the __isNew()__ method of the entity
- __implementing EntityInformation__
  -  you can customize the EntityInformation abstraction used in the SimpleJpaRepository implementation by creating a subclass of JpaRepositoryFactory and overriding the getEntityInformation(…) method accordingly. 
  -  you then have to register the custom implementation of JpaRepositoryFactory as a Spring bean. Note that this should be rarely necessary.

### Defining Query Methods
