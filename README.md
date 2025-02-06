# Spring Boot Interview Questions and Answers

## Core Concepts

### 1. What is Spring Boot?
Spring Boot is a project built on top of the Spring Framework that provides a simpler and faster way to set up, configure, and run applications.

### 2. What are the advantages of Spring Boot?
- Provides opinionated 'starter' dependencies
- Automatic configuration
- Embedded server support
- Microservices support
- No XML configuration required
- Production-ready features

### 3. What is Spring Boot Autoconfiguration?
Autoconfiguration automatically configures a Spring application based on dependencies present on the classpath.

### 4. What is a Spring Boot Starter?
Starters are dependency descriptors that combine multiple related dependencies into a single dependency, simplifying project setup.

### 5. Explain Spring Boot Actuator.
Actuator provides production-ready features like health checks, metrics, and monitoring for Spring Boot applications.

## Configuration

### 6. What are different ways to configure a Spring Boot application?
- application.properties/application.yml
- Command-line arguments
- Environment variables
- @Configuration classes
- Cloud config server

### 7. What is the default port of Spring Boot application?
The default port is 8080. It can be changed using server.port property.

### 8. How to disable a specific auto-configuration?
Use @EnableAutoConfiguration(exclude={DataSourceAutoConfiguration.class}) annotation.

### 9. What is Spring Boot DevTools?
DevTools provides development-time features like automatic restart and live reload.

### 10. How to change the server port in Spring Boot?
Add server.port=desired_port_number in application.properties.

## Dependencies and Build

### 11. What is the importance of spring-boot-starter-parent?
It provides dependency management and default configurations for Spring Boot applications.

### 12. What is the minimum Spring Boot configuration needed?
- spring-boot-starter-parent as parent
- spring-boot-starter dependency
- @SpringBootApplication annotation
- Main class with main method

### 13. What is Spring Initializr?
A web tool that generates Spring Boot project structure with selected dependencies.

### 14. What are profiles in Spring Boot?
Profiles provide a way to segregate parts of application configuration and make it available only in certain environments.

### 15. How to activate a profile in Spring Boot?
- Using spring.profiles.active property
- @Profile annotation
- Command line argument

## Annotations

### 16. What is @SpringBootApplication?
Combines @Configuration, @EnableAutoConfiguration, and @ComponentScan annotations.

### 17. Explain @RestController vs @Controller
@RestController combines @Controller and @ResponseBody, used for RESTful web services.

### 18. What is @RequestMapping?
Maps HTTP requests to handler methods in controllers.

### 19. What is @Value annotation?
Injects values from properties files into variables.

### 20. What is @ConfigurationProperties?
Binds external configuration properties to a Java class.

## Database and JPA

### 21. How to configure database in Spring Boot?
Add database properties in application.properties and include appropriate starter dependency.

### 22. What is Spring Data JPA?
Provides repository support for the Java Persistence API (JPA).

### 23. What is @Repository annotation?
Indicates the class is a repository, a mechanism for encapsulating storage and retrieval behavior.

### 24. Explain different types of spring data repositories.
- CrudRepository
- JpaRepository
- PagingAndSortingRepository
- MongoRepository

### 25. How to implement custom queries in Spring Data JPA?
- Using @Query annotation
- Method name conventions
- QueryDSL
- Specifications

## Security

### 26. How to implement security in Spring Boot?
Add spring-boot-starter-security dependency and configure WebSecurityConfigurerAdapter.

### 27. What is the default security configuration?
- Form-based authentication
- Basic HTTP authentication
- Default login page
- CSRF protection enabled

### 28. How to disable security for specific URLs?
Use antMatchers() in security configuration to exclude paths.

### 29. What is JWT?
JSON Web Token used for secure transmission of information between parties.

### 30. How to implement OAuth2 in Spring Boot?
Use spring-security-oauth2-autoconfigure dependency and configure OAuth2 properties.

## Testing

### 31. What is @SpringBootTest?
Annotation for Spring Boot integration tests.

### 32. What is @WebMvcTest?
For testing Spring MVC controllers with a subset of the Spring configuration.

### 33. What is @DataJpaTest?
For testing JPA repositories.

### 34. How to test REST APIs?
Use TestRestTemplate or MockMvc.

### 35. What is @MockBean?
Creates and injects a Mockito mock for a bean in the application context.

## Microservices

### 36. What is Spring Cloud?
Provides tools for common patterns in distributed systems.

### 37. What is Netflix Eureka?
Service registry for microservices architecture.

### 38. What is Ribbon?
Client-side load balancer.

### 39. What is Feign Client?
Declarative REST client for microservices communication.

### 40. What is Circuit Breaker?
Pattern to prevent cascading failures in distributed systems.

## Logging and Monitoring

### 41. What is the default logging framework in Spring Boot?
Logback is the default logging framework.

### 42. How to change logging level in Spring Boot?
Using logging.level.* property in application.properties.

### 43. What are different logging levels?
TRACE, DEBUG, INFO, WARN, ERROR, FATAL

### 44. How to configure external logging configuration?
Using logback.xml or log4j2.xml file.

### 45. How to monitor Spring Boot applications?
Using actuator endpoints and tools like Prometheus, Grafana.

## Deployment

### 46. How to deploy Spring Boot application?
- JAR file deployment
- WAR file deployment
- Docker containerization
- Cloud platforms

### 47. What is the difference between JAR and WAR?
JAR contains embedded server, WAR needs external server.

### 48. How to enable HTTPS in Spring Boot?
Configure SSL properties in application.properties.

### 49. How to deploy to Docker?
Use Dockerfile and docker-compose for containerization.

### 50. How to deploy to cloud platforms?
Use platform-specific configurations (AWS, Azure, GCP).

## Advanced Concepts

### 51. What is Spring Boot Admin?
UI application for managing and monitoring Spring Boot applications.

### 52. What is CommandLineRunner?
Interface to run specific code when application starts.

### 53. What is @Conditional annotation?
Controls conditional configuration based on various factors.

### 54. What is Spring Boot Batch?
Framework for batch processing in Spring Boot.

### 55. What is Spring Boot Cache?
Provides caching support through various providers.

## Exception Handling

### 56. How to handle exceptions in Spring Boot?
Use @ControllerAdvice and @ExceptionHandler annotations.

### 57. What is @ResponseStatus?
Marks exception with specific HTTP status code.

### 58. How to create custom error pages?
Create error.html or implementing ErrorController.

### 59. What is the default error handling mechanism?
WhitelabelErrorView for browser clients, JSON response for REST clients.

### 60. How to disable default error handling?
Set server.error.whitelabel.enabled=false.

## Validation

### 61. How to implement validation?
Use spring-boot-starter-validation and annotation-based validation.

### 62. What are common validation annotations?
@NotNull, @Size, @Min, @Max, @Email, etc.

### 63. How to handle validation errors?
Use BindingResult parameter in controller methods.

### 64. What is @Valid annotation?
Triggers validation of an object.

### 65. How to create custom validators?
Implement Validator interface or create custom constraint annotations.

## Scheduling

### 66. How to enable scheduling?
Use @EnableScheduling annotation.

### 67. What is @Scheduled annotation?
Marks a method to be executed periodically.

### 68. What are cron expressions?
Define complex scheduling patterns.

### 69. How to configure async execution?
Use @EnableAsync and @Async annotations.

### 70. How to configure thread pool?
Configure ThreadPoolTaskExecutor bean.

## Performance

### 71. How to improve Spring Boot performance?
- Use appropriate JVM settings
- Enable caching
- Optimize database queries
- Use async processing
- Profile and monitor application

### 72. What is lazy initialization?
Delays bean creation until needed.

### 73. How to implement caching?
Use @Cacheable, @CachePut, @CacheEvict annotations.

### 74. What is connection pooling?
Manages database connections for better performance.

### 75. How to implement pagination?
Use PagingAndSortingRepository or Pageable parameter.

## Miscellaneous

### 76. What are Spring Boot starters for testing?
spring-boot-starter-test includes JUnit, Mockito, AssertJ.

### 77. How to customize banner in Spring Boot?
Create banner.txt file or configure Banner interface.

### 78. What is Spring Boot Actuator info endpoint?
Displays arbitrary application info.

### 79. How to customize error messages?
Use messages.properties or implement MessageSource.

### 80. What is Spring Boot Developer Tools?
Provides additional development-time features.

## Data Handling

### 81. How to handle file upload?
Use MultipartFile and appropriate controller methods.

### 82. How to implement WebSocket?
Use spring-boot-starter-websocket and @EnableWebSocket.

### 83. How to work with MongoDB?
Use spring-boot-starter-data-mongodb.

### 84. How to implement Redis caching?
Use spring-boot-starter-data-redis.

### 85. How to work with multiple databases?
Configure multiple DataSource beans.

## REST APIs

### 86. What is Richardson Maturity Model?
Defines maturity levels of RESTful services.

### 87. How to version REST APIs?
- URL versioning
- Header versioning
- Content negotiation
- Parameter versioning

### 88. How to secure REST APIs?
- Basic authentication
- OAuth2
- JWT
- API keys

### 89. How to implement CORS?
Use @CrossOrigin or configure CorsRegistry.

### 90. How to handle API documentation?
Use Swagger/OpenAPI with SpringFox or SpringDoc.

## Messaging

### 91. How to implement JMS?
Use spring-boot-starter-activemq or spring-boot-starter-artemis.

### 92. How to work with RabbitMQ?
Use spring-boot-starter-amqp.

### 93. How to implement Kafka?
Use spring-kafka dependency.

### 94. What is Spring Integration?
Framework for enterprise integration patterns.

### 95. How to implement WebFlux?
Use spring-boot-starter-webflux for reactive programming.

## Best Practices

### 96. What are coding best practices?
- Follow proper package structure
- Use appropriate annotations
- Implement proper exception handling
- Write unit tests
- Use proper logging

### 97. What are configuration best practices?
- Use YAML over properties when possible
- Externalize configurations
- Use profiles effectively
- Secure sensitive information

### 98. What are security best practices?
- Keep dependencies updated
- Implement proper authentication
- Use HTTPS
- Validate inputs
- Handle errors securely

### 99. What are testing best practices?
- Write unit tests
- Use integration tests
- Mock external dependencies
- Test error scenarios
- Use proper assertions

### 100. What are deployment best practices?
- Use CI/CD pipelines
- Implement proper monitoring
- Use container orchestration
- Implement proper logging
- Use blue-green deployment