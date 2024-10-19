## **Backend Development with Spring Boot – Part 1: Foundations and Getting Started**

---

### **Introduction to Backend Development**
Backend development focuses on **how a server handles data** and **serves client requests**. It involves:
- **Processing logic** for business rules.
- **Database operations** (like saving or retrieving data).
- **API design** to enable interaction with other systems.
- Using backend frameworks (like **Spring Boot**) to simplify development.

This guide explains **backend fundamentals** using **Spring Boot**, a powerful Java framework.

---

## **1. What is Spring Boot? Why Should We Use It?**

### **What is Spring Boot?**
Spring Boot is a **framework** built on top of Spring Framework. It allows developers to create **standalone applications** with minimal configuration. 

- **Standalone Application**: An application that can run on its own, without needing an external server.
- **Embedded Server**: Spring Boot provides **Tomcat** server out of the box to run your application.

### **Why Use Spring Boot?**
- **Reduces boilerplate code**: Automates configuration.
- **Embedded server**: No need to manually deploy on external servers.
- **Easy dependency management** using Maven or Gradle.
- **Supports RESTful APIs** out of the box.

---

## **2. Setting Up Your First Spring Boot Application**

Follow these steps to create your first **Spring Boot project**.

### **Step 1: Install Prerequisites**
- **Java Development Kit (JDK)**: Version 8 or later.
- **Maven** or **Gradle**: For dependency management.
- **IDE**: Use IntelliJ IDEA or Eclipse for development.

### **Step 2: Create a New Project Using Spring Initializr**
Spring Initializr is a tool that helps create a Spring Boot project quickly.

1. Visit **https://start.spring.io**.
2. Choose the following options:
   - **Project**: Maven or Gradle.
   - **Language**: Java.
   - **Spring Boot version**: 3.x or later.
   - **Dependencies**: Add `Spring Web` (for building web applications).
3. Click **Generate** to download the project.

---

## **3. Project Structure in Spring Boot**

After generating the project, you will see the following structure:

```
my-first-project/
│
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com.example.demo/
│   │   │       ├── DemoApplication.java   # Main class
│   │   │       └── HelloController.java   # REST Controller
│   │   └── resources/
│           └── application.properties     # Configuration file
├── pom.xml                                # Maven dependencies
```

1. **`DemoApplication.java`**: Entry point for the application.
2. **`HelloController.java`**: Handles HTTP requests.
3. **`application.properties`**: Stores configuration (like port settings).

---

## **4. Writing Your First REST API in Spring Boot**

REST APIs allow the backend to interact with the frontend or other systems via HTTP.

### **Step 1: Create a Controller**

Create a new class `HelloController.java` under `com.example.demo` directory:

```java
package com.example.demo;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class HelloController {

    @GetMapping("/hello")
    public String sayHello() {
        return "Hello, World!";
    }
}
```

### **Explanation**:
- **`@RestController`**: Marks the class as a REST controller.
- **`@GetMapping("/hello")`**: Maps HTTP GET requests to `/hello`.
- **Method `sayHello()`**: When `/hello` is called, it returns `"Hello, World!"`.

---

## **5. Running the Application**

### **Step 1: Run the Application**
- Open `DemoApplication.java` and run it using your IDE.

```java
package com.example.demo;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class DemoApplication {

    public static void main(String[] args) {
        SpringApplication.run(DemoApplication.class, args);
    }
}
```

- This **starts the embedded Tomcat server** at **`http://localhost:8080`**.

### **Step 2: Access the API**
- Open a browser and go to **`http://localhost:8080/hello`**.
- You should see **"Hello, World!"** as the response.

---

## **6. REST API Concepts**

- **GET**: Retrieve information from the server.
- **POST**: Send new data to the server.
- **PUT/PATCH**: Update existing data.
- **DELETE**: Remove data from the server.

### **Example: Creating a User API**

```java
package com.example.demo;

import org.springframework.web.bind.annotation.*;

@RestController
@RequestMapping("/user")
public class UserController {

    @GetMapping("/{id}")
    public String getUser(@PathVariable int id) {
        return "User with ID: " + id;
    }

    @PostMapping("/")
    public String createUser(@RequestBody String name) {
        return "User " + name + " created!";
    }
}
```

1. **`@RequestMapping("/user")`**: Prefix for all user-related endpoints.
2. **`@GetMapping("/{id}")`**: Fetches a user by their ID.
3. **`@PostMapping("/")`**: Creates a new user.

---

## **7. Configuring Application Properties**

Change application settings in `application.properties`.

```properties
# Change server port to 8081
server.port=8081
```

- Restart the application. Now it will run on **`http://localhost:8081`**.

---

## **8. Working with Databases Using Spring Boot**

Spring Boot makes it easy to connect with relational databases.

### **Step 1: Add Database Dependency**
Add the following dependency in `pom.xml` for MySQL:

```xml
<dependency>
    <groupId>mysql</groupId>
    <artifactId>mysql-connector-java</artifactId>
    <scope>runtime</scope>
</dependency>
```

### **Step 2: Configure Database Settings**

In `application.properties`:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/mydb
spring.datasource.username=root
spring.datasource.password=password
spring.jpa.hibernate.ddl-auto=update
```

- **`ddl-auto=update`**: Automatically updates the database schema.

---

## **9. Error Handling in Spring Boot**

### **Common Errors and Solutions**

1. **Port Already in Use**:
   - Change the port in `application.properties`:
     ```properties
     server.port=8081
     ```

2. **404 Not Found**:
   - Ensure that your **URL mapping** is correct.

3. **Dependency Issues**:
   - Verify dependencies in `pom.xml` and ensure no version conflicts.

---

## **10. Recap and Next Steps**

- You have learned the basics of backend development with **Spring Boot**:
  1. Setting up a Spring Boot project.
  2. Writing a **Hello World** REST API.
  3. Working with HTTP methods like **GET** and **POST**.
  4. Configuring the application through **application.properties**.
  5. Connecting to a **database** using MySQL.

### **Next Steps**:
- Explore **advanced topics** like:
  - Database operations using **Spring Data JPA**.
  - Implementing **Security** in Spring Boot.
  - Adding **Exception Handling** for APIs.

---

This concludes **Part 1** of the backend development series with Spring Boot. Let me know if you need further explanation on any topic or if you are ready to move to **Part 2**!
