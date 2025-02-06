# Spring Boot Interview Questions and Answers

[Previous content remains the same through question 5...]

## Configuration

### 6. What are different ways to configure a Spring Boot application?
Spring Boot provides multiple flexible options for configuring your application, each serving different needs and use cases. Understanding these options helps you choose the most appropriate approach for your specific requirements.

1. Application Properties Files:
   The most common approach is using application.properties or application.yml files. These files can be placed in different locations with different precedence:

   ```properties
   # application.properties example
   server.port=8080
   spring.datasource.url=jdbc:mysql://localhost:3306/mydb
   spring.jpa.hibernate.ddl-auto=update
   ```

   ```yaml
   # application.yml example
   server:
     port: 8080
   spring:
     datasource:
       url: jdbc:mysql://localhost:3306/mydb
     jpa:
       hibernate:
         ddl-auto: update
   ```

2. Command-line Arguments:
   You can override properties when starting the application:
   ```bash
   java -jar myapp.jar --server.port=8081
   ```

3. Environment Variables:
   System environment variables can be used for configuration:
   ```bash
   export SERVER_PORT=8081
   ```
   Spring Boot automatically converts environment variables from uppercase underscore format to lowercase dot format.

4. @Configuration Classes:
   Java-based configuration provides type-safe configuration:
   ```java
   @Configuration
   public class DatabaseConfig {
       @Bean
       public DataSource dataSource() {
           HikariDataSource dataSource = new HikariDataSource();
           dataSource.setJdbcUrl("jdbc:mysql://localhost:3306/mydb");
           dataSource.setUsername("user");
           dataSource.setPassword("password");
           return dataSource;
       }
   }
   ```

5. Cloud Config Server:
   For distributed systems, Spring Cloud Config Server provides centralized configuration:
   ```yaml
   spring:
     cloud:
       config:
         uri: http://config-server:8888
         label: master
   ```

The order of precedence (from highest to lowest) is:
1. Command-line arguments
2. Java System properties
3. OS environment variables
4. Application properties files
5. @Configuration classes

### 7. What is the default port of Spring Boot application and how to customize it?
Spring Boot applications by default run on port 8080, but this can be easily customized in several ways to suit your needs.

Ways to change the port:

1. Using application.properties:
   ```properties
   server.port=8081
   ```

2. Using application.yml:
   ```yaml
   server:
     port: 8081
   ```

3. Using environment variable:
   ```bash
   export SERVER_PORT=8081
   ```

4. Programmatically:
   ```java
   @SpringBootApplication
   public class MyApplication {
       public static void main(String[] args) {
           SpringApplication app = new SpringApplication(MyApplication.class);
           app.setDefaultProperties(Collections.singletonMap("server.port", "8081"));
           app.run(args);
       }
   }
   ```

Special port values:
- 0: Random port (useful for testing)
- -1: Disable HTTP connector

Example for random port in tests:
```java
@SpringBootTest(webEnvironment = SpringBootTest.WebEnvironment.RANDOM_PORT)
class MyApplicationTests {
    @LocalServerPort
    private int port;

    @Test
    void contextLoads() {
        // Test using dynamic port
    }
}
```

### 8. How to disable specific auto-configuration?
Spring Boot's auto-configuration can be selectively disabled when you need more control over your application's configuration. There are several ways to achieve this:

1. Using @EnableAutoConfiguration exclude:
   ```java
   @SpringBootApplication(exclude = {DataSourceAutoConfiguration.class})
   public class MyApplication {
       public static void main(String[] args) {
           SpringApplication.run(MyApplication.class, args);
       }
   }
   ```

2. Using properties file:
   ```properties
   spring.autoconfigure.exclude=org.springframework.boot.autoconfigure.jdbc.DataSourceAutoConfiguration
   ```

3. Multiple exclusions:
   ```java
   @EnableAutoConfiguration(exclude = {
       DataSourceAutoConfiguration.class,
       HibernateJpaAutoConfiguration.class,
       JpaRepositoriesAutoConfiguration.class
   })
   ```

4. Conditional exclusion:
   ```java
   @ConditionalOnProperty(name = "some.property", havingValue = "false")
   @Configuration
   public class MyAutoConfiguration {
       // Configuration to be conditionally excluded
   }
   ```

Best practices:
- Always verify the impact of disabling auto-configuration
- Consider using configuration properties before disabling auto-configuration
- Document why auto-configuration was disabled
- Use condition annotations for more fine-grained control

### 9. What is Spring Boot DevTools?
Spring Boot DevTools (Developer Tools) is a set of tools that makes application development more convenient. It provides several features that enhance the development experience:

1. Automatic Restart:
   The application automatically restarts when files on the classpath change:
   ```xml
   <dependency>
       <groupId>org.springframework.boot</groupId>
       <artifactId>spring-boot-devtools</artifactId>
       <optional>true</optional>
   </dependency>
   ```

2. Live Reload:
   Automatically refreshes the browser when resources change:
   ```properties
   spring.devtools.livereload.enabled=true
   ```

3. Property Defaults:
   DevTools sets certain properties suitable for development:
   - Disables template caching
   - Enables debug logging for web group
   - Enables H2 console

4. Remote Development Support:
   ```properties
   spring.devtools.remote.secret=mysecret
   ```

Example configuration class:
```java
@Configuration
public class DevToolsConfig {
    @Bean
    public DevToolsPropertyDefaultsPostProcessor devToolsPropertyDefaultsPostProcessor() {
        return new DevToolsPropertyDefaultsPostProcessor();
    }
}
```

Best practices:
- Disable DevTools in production
- Configure trigger file for more control over restarts
- Use excludes to prevent unnecessary restarts
- Configure specific paths for monitoring

[Continuing with detailed explanations for remaining questions...]