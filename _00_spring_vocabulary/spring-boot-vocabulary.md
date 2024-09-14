# Spring Boot Vocabulary

Welcome to the Spring Boot vocabulary guide! This dictionary will help you understand key terms in Spring Boot with simple explanations and easy examples.

---

### **Spring Boot**

**Description:**
A framework that simplifies the development of Java applications by providing default configurations and an embedded server. It lets you focus on writing code without worrying about boilerplate setup.

**Example:**

```java
@SpringBootApplication
public class MyApplication {
    public static void main(String[] args) {
        SpringApplication.run(MyApplication.class, args);
    }
}
```

---

### **@SpringBootApplication**

**Description:**
An annotation that marks the main class of a Spring Boot application. It combines three annotations: `@EnableAutoConfiguration`, `@ComponentScan`, and `@Configuration`.

**Example:**

```java
@SpringBootApplication
public class MyApplication {
    // Application code here
}
```

---

### **Dependency Injection**

**Description:**
A design pattern where an object receives its dependencies from an external source rather than creating them itself. This promotes loose coupling between components.

**Example:**

```java
@Component
public class MyService {
    private final MyRepository repository;

    @Autowired
    public MyService(MyRepository repository) {
        this.repository = repository;
    }
}
```

---

### **@Component**

**Description:**
An annotation used to mark a Java class as a component so that Spring can detect and include it in the application context.

**Example:**

```java
@Component
public class MyComponent {
    // Component code here
}
```

---

### **@Service**

**Description:**
A specialization of `@Component`. It indicates that the class holds business logic and is part of the service layer.

**Example:**

```java
@Service
public class UserService {
    // Business logic here
}
```

---

### **@Repository**

**Description:**
Another specialization of `@Component`. It indicates that the class interacts with the database and is part of the data access layer.

**Example:**

```java
@Repository
public interface UserRepository extends JpaRepository<User, Long> {
    // Database access methods
}
```

---

### **@Controller**

**Description:**
An annotation used to define a controller in Spring MVC. It handles HTTP requests and returns views (like HTML pages).

**Example:**

```java
@Controller
public class HomeController {
    @GetMapping("/")
    public String home() {
        return "home"; // Returns the "home.html" template
    }
}
```

---

### **@RestController**

**Description:**
A combination of `@Controller` and `@ResponseBody`. It is used to create RESTful web services by returning data directly instead of views.

**Example:**

```java
@RestController
public class UserController {
    @GetMapping("/users")
    public List<User> getUsers() {
        return userService.findAll();
    }
}
```

---

### **@Autowired**

**Description:**
An annotation that allows Spring to automatically inject dependencies into a class.

**Example:**

```java
@Service
public class UserService {
    @Autowired
    private UserRepository userRepository;
    // Service methods
}
```

---

### **Bean**

**Description:**
An object managed by the Spring framework. Beans are created, wired together, and managed by the Spring container.

**Example:**

```java
@Configuration
public class AppConfig {
    @Bean
    public MyService myService() {
        return new MyService();
    }
}
```

---

### **@Configuration**

**Description:**
An annotation that indicates a class contains bean definitions. It tells Spring to use this class to generate beans.

**Example:**

```java
@Configuration
public class AppConfig {
    // Bean definitions
}
```

---

### **Application Properties**

**Description:**
Configuration settings for your application, stored in `application.properties` or `application.yml` files.

**Example (`application.properties`):**

```
server.port=8081
spring.datasource.url=jdbc:mysql://localhost:3306/mydb
```

---

### **@GetMapping**

**Description:**
An annotation for mapping HTTP GET requests to specific handler methods.

**Example:**

```java
@RestController
public class UserController {
    @GetMapping("/users")
    public List<User> getAllUsers() {
        return userService.findAll();
    }
}
```

---

### **@PostMapping**

**Description:**
An annotation for mapping HTTP POST requests to specific handler methods.

**Example:**

```java
@RestController
public class UserController {
    @PostMapping("/users")
    public User createUser(@RequestBody User user) {
        return userService.save(user);
    }
}
```

---

### **@RequestBody**

**Description:**
An annotation that binds the body of an HTTP request to a method parameter.

**Example:**

```java
@PostMapping("/users")
public User createUser(@RequestBody User user) {
    // Process user data
}
```

---

### **@PathVariable**

**Description:**
An annotation that binds a URI template variable to a method parameter.

**Example:**

```java
@GetMapping("/users/{id}")
public User getUserById(@PathVariable Long id) {
    return userService.findById(id);
}
```

---

### **@RequestParam**

**Description:**
An annotation that binds a web request parameter to a method parameter.

**Example:**

```java
@GetMapping("/search")
public List<User> searchUsers(@RequestParam String name) {
    return userService.findByName(name);
}
```

---

### **Thymeleaf**

**Description:**
A server-side Java template engine for processing and creating HTML, XML, JavaScript, CSS, and text.

**Example:**

**Controller:**

```java
@Controller
public class HomeController {
    @GetMapping("/")
    public String home(Model model) {
        model.addAttribute("message", "Hello, Thymeleaf!");
        return "home";
    }
}
```

**Template (`home.html`):**

```html
<!DOCTYPE html>
<html>
<head>
    <title>Home</title>
</head>
<body>
    <p th:text="${message}"></p>
</body>
</html>
```

---

### **Spring Data JPA**

**Description:**
A part of Spring Data that simplifies working with relational databases using Java Persistence API (JPA).

**Example:**

```java
public interface UserRepository extends JpaRepository<User, Long> {
    // Custom query methods can be added here
}
```

---

### **@Entity**

**Description:**
An annotation that marks a class as a JPA entity, which maps to a database table.

**Example:**

```java
@Entity
public class User {
    @Id
    @GeneratedValue
    private Long id;
    private String name;
    // Getters and setters
}
```

---

### **Inversion of Control (IoC)**

**Description:**
A principle where the control of object creation and management is transferred to a container or framework (like Spring), rather than being handled by the application code.

**Example:**

By using `@Autowired`, you let Spring create and manage the dependencies for you.

---

### **Spring Initializr**

**Description:**
A web-based tool for quickly generating a new Spring Boot project with the desired dependencies.

**Example:**

Visit [start.spring.io](https://start.spring.io/) to create a new project.

---

### **Actuator**

**Description:**
A feature in Spring Boot that provides endpoints to monitor and manage your application, such as health checks and metrics.

**Example:**

By adding `spring-boot-starter-actuator` to your dependencies, you can access endpoints like `/actuator/health`.

---

### **Auto-Configuration**

**Description:**
A mechanism in Spring Boot that automatically configures your application based on the dependencies present on the classpath.

**Example:**

If you include `spring-boot-starter-web`, Spring Boot auto-configures a web server for you.

---

### **Embedded Server**

**Description:**
Spring Boot applications come with an embedded web server (like Tomcat or Jetty), so you don't need to deploy WAR files to an external server.

**Example:**

You can run your application directly using `java -jar myapp.jar`.

---

### **Profiles**

**Description:**
A way to separate parts of your application configuration and make them only available in certain environments (like development, testing, production).

**Example:**

Define profile-specific properties files like `application-dev.properties` and `application-prod.properties`.

---

### **@Profile**

**Description:**
An annotation that specifies that a component or configuration is only active in certain profiles.

**Example:**

```java
@Profile("dev")
@Service
public class DevService {
    // Development-specific logic
}
```

---

### **DevTools**

**Description:**
A Spring Boot module that provides additional development-time features like automatic restart and live reloading.

**Example:**

Include `spring-boot-devtools` in your project to enable these features.

---

### **CommandLineRunner**

**Description:**
An interface used to execute code after the Spring Boot application has started.

**Example:**

```java
@Component
public class StartupRunner implements CommandLineRunner {
    @Override
    public void run(String... args) {
        System.out.println("Application has started!");
    }
}
```

---

### **Logging**

**Description:**
Spring Boot uses a default logging framework but allows you to configure logging levels and outputs.

**Example (`application.properties`):**

```
logging.level.root=WARN
logging.level.com.example=DEBUG
```

---

### **@Value**

**Description:**
An annotation used to inject values from properties files into fields.

**Example:**

```java
@Component
public class MyBean {
    @Value("${my.property}")
    private String myProperty;
}
```

---

### **@ConfigurationProperties**

**Description:**
An annotation that binds external configurations (like those in properties files) to a Java class.

**Example:**

```java
@ConfigurationProperties(prefix = "app")
public class AppProperties {
    private String name;
    private int timeout;
    // Getters and setters
}
```

**In `application.properties`:**

```
app.name=MyApp
app.timeout=30
```

---

### **Testing**

**Description:**
Spring Boot provides testing support with annotations and utilities to help test your application.

**Example:**

```java
@SpringBootTest
public class ApplicationTests {
    @Test
    public void contextLoads() {
        // Test code here
    }
}
```

---

### **@SpringBootTest**

**Description:**
An annotation that tells Spring Boot to load the full application context for testing.

**Example:**

```java
@SpringBootTest
public class MyApplicationTests {
    // Test methods
}
```

---

### **MockMvc**

**Description:**
A class that provides support for testing Spring MVC controllers without starting the server.

**Example:**

```java
@WebMvcTest(HomeController.class)
public class HomeControllerTest {
    @Autowired
    private MockMvc mockMvc;

    @Test
    public void testHomePage() throws Exception {
        mockMvc.perform(get("/"))
               .andExpect(status().isOk())
               .andExpect(view().name("home"));
    }
}
```

---

### **AOP (Aspect-Oriented Programming)**

**Description:**
A programming paradigm that allows you to add cross-cutting concerns like logging or security across your application without modifying the actual code.

**Example:**

```java
@Aspect
@Component
public class LoggingAspect {
    @Before("execution(* com.example.service.*.*(..))")
    public void logBeforeMethod(JoinPoint joinPoint) {
        // Logging logic here
    }
}
```

---

### **Properties**

**Description:**
Configuration settings for your application, usually stored in `application.properties` or `application.yml`.

**Example (`application.properties`):**

```
spring.jpa.show-sql=true
server.port=8080
```

---

### **YAML**

**Description:**
An alternative to properties files for configuration, using indentation to represent structure.

**Example (`application.yml`):**

```yaml
server:
  port: 8080

spring:
  datasource:
    url: jdbc:mysql://localhost:3306/mydb
    username: user
    password: pass
```

---

### **Starter POMs**

**Description:**
Pre-defined dependencies provided by Spring Boot to simplify adding commonly used libraries.

**Example:**

Including `spring-boot-starter-web` adds all necessary dependencies for building web applications.

---

### **@ResponseBody**

**Description:**
An annotation that tells Spring to write the returned object directly to the HTTP response body.

**Example:**

```java
@GetMapping("/hello")
@ResponseBody
public String sayHello() {
    return "Hello, World!";
}
```

---

### **Exception Handling**

**Description:**
Mechanisms provided by Spring to handle exceptions and return appropriate HTTP responses.

**Example:**

```java
@ControllerAdvice
public class GlobalExceptionHandler {
    @ExceptionHandler(Exception.class)
    public ResponseEntity<String> handleAllExceptions(Exception ex) {
        return ResponseEntity.status(HttpStatus.INTERNAL_SERVER_ERROR)
                             .body("An error occurred");
    }
}
```

---

### **Security**

**Description:**
Spring Boot integrates with Spring Security to provide authentication and authorization features.

**Example:**

By adding `spring-boot-starter-security`, you secure your application with default settings.

---

### **@EnableAutoConfiguration**

**Description:**
An annotation that enables Spring Boot's auto-configuration mechanism.

**Example:**

It's included in `@SpringBootApplication`, so you usually don't need to use it directly.

---

### **@ComponentScan**

**Description:**
An annotation that tells Spring where to look for components to include in the application context.

**Example:**

Also included in `@SpringBootApplication`.

---

### **@Bean**

**Description:**
An annotation that indicates a method produces a bean to be managed by the Spring container.

**Example:**

```java
@Configuration
public class AppConfig {
    @Bean
    public MyService myService() {
        return new MyService();
    }
}
```

---

### **@Scope**

**Description:**
An annotation that specifies the scope of a bean (like singleton or prototype).

**Example:**

```java
@Component
@Scope("prototype")
public class PrototypeBean {
    // A new instance is created each time it's needed
}
```

---

### **@Qualifier**

**Description:**
An annotation used along with `@Autowired` to specify which bean should be injected when multiple candidates are available.

**Example:**

```java
@Service
public class MyService {
    @Autowired
    @Qualifier("specificBean")
    private MyBean myBean;
}
```

---

### **SpringApplication**

**Description:**
A class that provides a convenient way to bootstrap a Spring application from the main method.

**Example:**

```java
public static void main(String[] args) {
    SpringApplication.run(MyApplication.class, args);
}
```

---

### **Environment**

**Description:**
An interface representing the environment in which the application is running, allowing access to properties and profiles.

**Example:**

```java
@Autowired
private Environment env;

public void printProperty() {
    System.out.println(env.getProperty("my.property"));
}
```

---

### **Externalized Configuration**

**Description:**
Spring Boot allows you to externalize your configuration, making it easy to work with different settings for different environments.

**Example:**

Using environment variables, command-line arguments, or properties files to configure your application.

---

### **Spring Expression Language (SpEL)**

**Description:**
A powerful expression language that supports querying and manipulating an object graph at runtime.

**Example:**

```java
@Value("#{systemProperties['user.name']}")
private String userName;
```

---

### **Caching**

**Description:**
Spring provides a caching abstraction to improve application performance by storing expensive method results.

**Example:**

```java
@EnableCaching
@SpringBootApplication
public class MyApplication {
    // ...
}

@Service
public class ProductService {
    @Cacheable("products")
    public Product getProductById(Long id) {
        // Fetch product from database
    }
}
```

---

### **Scheduling**

**Description:**
Running tasks at specific times or intervals using Spring's scheduling support.

**Example:**

```java
@EnableScheduling
@SpringBootApplication
public class MyApplication {
    // ...
}

@Component
public class ScheduledTasks {
    @Scheduled(fixedRate = 5000)
    public void reportCurrentTime() {
        System.out.println("Current time is " + new Date());
    }
}
```

---

### **Validation**

**Description:**
Validating user input in your application using annotations.

**Example:**

```java
@PostMapping("/users")
public User createUser(@Valid @RequestBody User user) {
    // Save user
}

public class User {
    @NotNull
    private String name;
    // Other fields and methods
}
```

---

### **@Valid**

**Description:**
An annotation used to mark a method parameter for validation.

**Example:**

As shown above.

---

### **Banner**

**Description:**
A graphic or text displayed when the application starts. You can customize it or turn it off.

**Example:**

Create a `banner.txt` file in your resources directory to customize.

---

### **Flyway**

**Description:**
A database migration tool that allows you to manage and version your database schema.

**Example:**

By adding `flyway-core` to your dependencies, you can manage database changes with SQL scripts.

---

### **Asynchronous Methods**

**Description:**
Methods that run in the background, allowing the main thread to continue processing.

**Example:**

```java
@EnableAsync
@SpringBootApplication
public class MyApplication {
    // ...
}

@Service
public class NotificationService {
    @Async
    public void sendEmail(String email) {
        // Code to send email
    }
}
```

---

### **@EnableAsync**

**Description:**
An annotation that enables Spring's asynchronous method execution capability.

**Example:**

As shown above.

---

### **@EnableScheduling**

**Description:**
An annotation that enables Spring's scheduled task execution capability.

**Example:**

As shown in the scheduling example.

---

### **Exception Handling with @ControllerAdvice**

**Description:**
A global exception handling mechanism that allows you to handle exceptions across the whole application.

**Example:**

```java
@ControllerAdvice
public class GlobalExceptionHandler {
    @ExceptionHandler(ResourceNotFoundException.class)
    public ResponseEntity<String> handleNotFound(ResourceNotFoundException ex) {
        return ResponseEntity.status(HttpStatus.NOT_FOUND)
                             .body(ex.getMessage());
    }
}
```

---

### **RESTful Web Services**

**Description:**
Services that use HTTP methods (GET, POST, PUT, DELETE) to perform CRUD operations.

**Example:**

Using `@RestController` and mapping methods with `@GetMapping`, `@PostMapping`, etc.

---

### **CORS (Cross-Origin Resource Sharing)**

**Description:**
A mechanism that allows restricted resources on a web page to be requested from another domain.

**Example:**

```java
@RestController
@CrossOrigin(origins = "http://example.com")
public class MyController {
    // Controller methods
}
```

---

### **Multipart File Upload**

**Description:**
Handling file uploads in your application.

**Example:**

```java
@PostMapping("/upload")
public String handleFileUpload(@RequestParam("file") MultipartFile file) {
    // Process the uploaded file
}
```

---

### **WebClient**

**Description:**
A non-blocking, reactive client for making HTTP requests.

**Example:**

```java
WebClient client = WebClient.create("http://localhost:8080");
client.get()
      .uri("/users")
      .retrieve()
      .bodyToFlux(User.class)
      .subscribe(user -> System.out.println(user.getName()));
```

---

### **Reactive Programming**

**Description:**
A programming paradigm focused on asynchronous data streams and the propagation of change.

**Example:**

Using `Mono` and `Flux` types from Project Reactor in Spring WebFlux.

---

### **Validation Constraints**

**Description:**
Annotations used to enforce validation rules on fields.

**Example:**

```java
public class User {
    @NotNull
    @Size(min = 2, max = 30)
    private String name;
    // Other fields
}
```

---

### **Spring Shell**

**Description:**
A framework for creating command-line applications.

**Example:**

By adding `spring-shell-starter`, you can create interactive CLI applications.

---

### **Actuator Endpoints**

**Description:**
Endpoints provided by Actuator for monitoring and managing your application.

**Example:**

- `/actuator/health` shows application health status.
- `/actuator/info` displays application information.

---

WIP++ ;
