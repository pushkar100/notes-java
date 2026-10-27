# Spring Boot 3 Master Tutorial & Engineering Guide

Navigate directly to any module, architectural concept, code reference, or practice exercise across the master curriculum:

## Master Table of Contents

- [**Part 0: Spring Core Foundations & Architectural Primer**](#part-0-spring-core-foundations-architectural-primer)
  - [0.0 Fundamental Concepts: Annotations, Records, Entities, and DTOs](#00-fundamental-concepts-annotations-records-entities-and-dtos)
  - [0.1 The Architectural Crisis of Plain Java & Enterprise J2EE](#01-the-architectural-crisis-of-plain-java-enterprise-j2ee)
  - [0.2 Inversion of Control (IoC) & Dependency Injection (DI)](#02-inversion-of-control-ioc-dependency-injection-di)
  - [0.3 The Spring IoC Container & Bean Lifecycle](#03-the-spring-ioc-container-bean-lifecycle)
  - [0.4 Stereotype Annotations & Layered Architecture](#04-stereotype-annotations-layered-architecture)
    - [0.4.1 Spring AOP & Proxies: The "Secret Service" Mental Model](#041-spring-aop--proxies-the-secret-service-mental-model)
  - [0.5 From Spring Framework to Spring Boot: The Magic Unveiled](#05-from-spring-framework-to-spring-boot-the-magic-unveiled)
    - [0.5.1 How Auto-Configuration Actually Works Under the Hood](#051-how-auto-configuration-actually-works-under-the-hood)
- [**Part 1: Web Applications and Microservices**](#part-1-web-applications-and-microservices)
  - [Chapter 1: Building RESTful APIs](#chapter-1-building-restful-apis)
    - [1.0 Foundations of Web Communication & The Simplest Spring Web App](#10-foundations-of-web-communication-the-simplest-spring-web-app)
      - [1.0.1 The Web Request Lifecycle: DispatcherServlet Under the Hood](#101-the-web-request-lifecycle-dispatcherservlet-under-the-hood)
    - [1.1 Accepting Inputs: Path Variables, Query Parameters, and Headers](#11-accepting-inputs-path-variables-query-parameters-and-headers)
    - [1.2 Data Serialization, Deserialization, DTOs & Jackson Deep Dive](#12-data-serialization-deserialization-dtos-jackson-deep-dive)
    - [1.3 Complete CRUD Operations in Practice](#13-complete-crud-operations-in-practice)
    - [1.4 Input Validation & Global Exception Handling with RFC 7807](#14-input-validation-global-exception-handling-with-rfc-7807)
    - [1.5 Package Architecture Best Practices: Layer vs Feature](#15-package-architecture-best-practices-layer-vs-feature)
    - [1.6 Custom DB Queries vs ORM Mapping (In Brief at Web Boundary)](#16-custom-db-queries-vs-orm-mapping-in-brief-at-web-boundary)
    - [1.7 Living API Documentation with OpenAPI & Swagger UI](#17-living-api-documentation-with-openapi-swagger-ui)
    - [1.8 Testing the Web Layer with `@WebMvcTest` and `MockMvc`](#18-testing-the-web-layer-with-webmvctest-and-mockmvc)
    - [1.9 Consuming Downstream APIs with `RestClient` and WireMock](#19-consuming-downstream-apis-with-restclient-and-wiremock)
      - [1.9.1 Modern Declarative HTTP Interfaces with `@HttpExchange`](#191-modern-declarative-http-interfaces-with-httpexchange)
    - [1.10 Real-Time Server Push: Server-Sent Events (SSE) with SseEmitter](#110-real-time-server-push-server-sent-events-sse-with-sseemitter)
    - [Chapter 1 Exercises & Solutions](#chapter-1-exercises-solutions)
  - [Chapter 2: Securing Spring Boot Applications with OAuth2](#chapter-2-securing-spring-boot-applications-with-oauth2)
    - [2.0 The Spring Security Mental Model](#20-the-spring-security-mental-model)
    - [2.1 Configuring the Modern `SecurityFilterChain`](#21-configuring-the-modern-securityfilterchain)
      - [2.1.1 CORS & CSRF Demystified for Modern REST APIs](#211-cors--csrf-demystified-for-modern-rest-apis)
      - [2.1.2 Handling Security Failures with RFC 7807 ProblemDetail Responses](#212-handling-security-failures-with-rfc-7807-problemdetail-responses)
    - [2.2 Password Encoding & User Authentication](#22-password-encoding-user-authentication)
    - [2.3 Role-Based Access Control (RBAC) & Method Security](#23-role-based-access-control-rbac-method-security)
    - [2.4 OAuth2 & OpenID Connect (OIDC) Protocol Architecture](#24-oauth2-openid-connect-oidc-protocol-architecture)
    - [2.5 Configuring an OAuth2 Resource Server with JWTs](#25-configuring-an-oauth2-resource-server-with-jwts)
    - [2.6 Single Sign-On (SSO) with OAuth2 Client Login](#26-single-sign-on-sso-with-oauth2-client-login)
    - [2.7 Working with JWTs: Generation, Custom Filter, and Refresh Tokens](#27-working-with-jwts-generation-custom-filter-and-refresh-tokens)
    - [Chapter 2 Exercises & Solutions](#chapter-2-exercises-solutions)
  - [Chapter 3: Observability, Monitoring, and Application Management](#chapter-3-observability-monitoring-and-application-management)
    - [3.0 The Four Pillars of Observability](#30-the-four-pillars-of-observability)
    - [3.1 Production Health & Metrics with Spring Boot Actuator](#31-production-health-metrics-with-spring-boot-actuator)
      - [3.1.1 Kubernetes Liveness, Readiness & Graceful Shutdown](#311-kubernetes-liveness-readiness--graceful-shutdown)
    - [3.2 Authoring Custom Health Indicators](#32-authoring-custom-health-indicators)
    - [3.3 Publishing Metrics to Prometheus with Micrometer](#33-publishing-metrics-to-prometheus-with-micrometer)
      - [3.3.1 Unified Telemetry with the Micrometer Observation API (`@Observed`)](#331-unified-telemetry-with-the-micrometer-observation-api-observed)
      - [3.3.2 Authoring Custom Actuator Endpoints (`@Endpoint`)](#332-authoring-custom-actuator-endpoints-endpoint)
    - [3.4 Distributed Tracing with Micrometer Tracing & Zipkin](#34-distributed-tracing-with-micrometer-tracing-zipkin)
    - [3.5 Enterprise Logging: SLF4J, Logback, and Log4j2](#35-enterprise-logging-slf4j-logback-and-log4j2)
    - [Chapter 3 Exercises & Solutions](#chapter-3-exercises-solutions)
  - [Chapter 4: Spring Cloud and Microservices Architecture](#chapter-4-spring-cloud-and-microservices-architecture)
    - [4.0 Microservices Design Principles & Challenges](#40-microservices-design-principles-challenges)
    - [4.1 Service Registration & Discovery with Netflix Eureka](#41-service-registration-discovery-with-netflix-eureka)
      - [4.1.1 Client-Side Load Balancing with Spring Cloud LoadBalancer](#411-client-side-load-balancing-with-spring-cloud-loadbalancer)
    - [4.2 API Routing & Filtering with Spring Cloud Gateway](#42-api-routing-filtering-with-spring-cloud-gateway)
      - [4.2.1 Edge Security: Validating JWTs in Gateway Filters](#421-edge-security-validating-jwts-in-gateway-filters)
      - [4.2.2 Distributed Edge Rate Limiting with Redis](#422-distributed-edge-rate-limiting-with-redis)
    - [4.3 Fault Tolerance & Circuit Breaking with Resilience4j](#43-fault-tolerance-circuit-breaking-with-resilience4j)
    - [4.4 Centralized Configuration Management with Spring Cloud Config](#44-centralized-configuration-management-with-spring-cloud-config)
    - [4.5 Distributed Tracing & W3C Trace Context Propagation Across Services](#45-distributed-tracing--w3c-trace-context-propagation-across-services)
    - [Chapter 4 Exercises & Solutions](#chapter-4-exercises-solutions)
- [**Part 2: Database Technologies**](#part-2-database-technologies)
  - [Chapter 5: Data Persistence and Relational Database Integration with Spring Data](#chapter-5-data-persistence-and-relational-database-integration-with-spring-data)
    - [5.0 The Database Abstraction Ladder & Core Architecture](#50-the-database-abstraction-ladder-core-architecture)
    - [5.1 Docker Setup & Database Connectivity](#51-docker-setup-database-connectivity)
      - [5.1.1 Zero-Config Local Containers with `spring-boot-docker-compose`](#511-zero-config-local-containers-with-spring-boot-docker-compose)
    - [5.2 Lightweight High-Speed SQL with `JdbcClient`](#52-lightweight-high-speed-sql-with-jdbcclient)
    - [5.3 Entity Modeling & Jakarta Persistence (JPA)](#53-entity-modeling-jakarta-persistence-jpa)
    - [5.4 Mastering Entity Relationships](#54-mastering-entity-relationships)
    - [5.5 Querying with Spring Data Repositories](#55-querying-with-spring-data-repositories)
    - [5.6 The N+1 Query Problem: Complete Deep Dive](#56-the-n1-query-problem-complete-deep-dive)
    - [5.7 Database Schema Version Control with Flyway](#57-database-schema-version-control-with-flyway)
    - [5.8 Transaction Management with `@Transactional`](#58-transaction-management-with-transactional)
    - [5.8.1 Concurrency Control: Optimistic vs. Pessimistic Locking](#581-concurrency-control-optimistic-vs-pessimistic-locking)
    - [5.9 Automated Integration Testing with Testcontainers](#59-automated-integration-testing-with-testcontainers)
      - [5.9.1 Modern Integration Testing with Spring Boot 3.1 `@ServiceConnection`](#591-modern-integration-testing-with-spring-boot-31-serviceconnection)
    - [Chapter 5 Exercises & Comprehensive Scenarios with Solutions](#chapter-5-exercises-comprehensive-scenarios-with-solutions)
  - [Chapter 6: Data Persistence and NoSQL Database Integration with Spring Data](#chapter-6-data-persistence-and-nosql-database-integration-with-spring-data)
    - [6.0 The NoSQL Mental Model & Architecture](#60-the-nosql-mental-model-architecture)
    - [6.1 Integrating MongoDB with Spring Data Mongo](#61-integrating-mongodb-with-spring-data-mongo)
    - [6.2 Distributed Caching with Redis](#62-distributed-caching-with-redis)
    - [6.3 Advanced Caching Scenarios & Production Pitfalls](#63-advanced-caching-scenarios-production-pitfalls)
    - [Chapter 6 Exercises & Comprehensive Scenarios with Solutions](#chapter-6-exercises-comprehensive-scenarios-with-solutions)
- [**Part 3: Application Optimization**](#part-3-application-optimization)
  - [Chapter 7: Finding Bottlenecks and Optimizing Your Application](#chapter-7-finding-bottlenecks-and-optimizing-your-application)
    - [7.0 The Performance Engineering Mindset](#70-the-performance-engineering-mindset)
    - [7.1 Database Performance Tuning & The N+1 Solution](#71-database-performance-tuning-the-n1-solution)
    - [7.2 HikariCP Connection Pool Optimization](#72-hikaricp-connection-pool-optimization)
    - [7.3 Concurrency Evolution: Java 21 Virtual Threads (Project Loom)](#73-concurrency-evolution-java-21-virtual-threads-project-loom)
    - [7.4 JVM Profiling, Memory Leaks, and Garbage Collection Tuning](#74-jvm-profiling-memory-leaks-and-garbage-collection-tuning)
    - [7.5 Production Observability: Prometheus & Grafana Performance Dashboards](#75-production-observability-prometheus-grafana-performance-dashboards)
    - [7.6 Task Scheduling and Distributed Locking with ShedLock and Redis](#76-task-scheduling-and-distributed-locking-with-shedlock-and-redis)
    - [Chapter 7 Exercises & Solutions](#chapter-7-exercises-solutions)
  - [Chapter 8: Spring Reactive and Spring Cloud Stream](#chapter-8-spring-reactive-and-spring-cloud-stream)
    - [8.0 Reactive Streams Mental Model: Mono and Flux](#80-reactive-streams-mental-model-mono-and-flux)
    - [8.1 Building Reactive REST APIs with Spring WebFlux](#81-building-reactive-rest-apis-with-spring-webflux)
    - [8.2 Non-Blocking Relational Persistence with Spring Data R2DBC](#82-non-blocking-relational-persistence-with-spring-data-r2dbc)
    - [8.3 Event-Driven Messaging with Spring Cloud Stream and RabbitMQ](#83-event-driven-messaging-with-spring-cloud-stream-and-rabbitmq)
    - [8.4 Pub/Sub and Event Streaming with Apache Kafka & Reactive Spring](#84-pubsub-and-event-streaming-with-apache-kafka--reactive-spring)
    - [Chapter 8 Exercises & Solutions](#chapter-8-exercises-solutions)
- [**Part 4: Upgrading to Spring Boot 3 from Previous Versions**](#part-4-upgrading-to-spring-boot-3-from-previous-versions)
  - [Chapter 9: Upgrading from Spring Boot 2.x to Spring Boot 3.0](#chapter-9-upgrading-from-spring-boot-2x-to-spring-boot-30)
    - [9.0 The Major Milestones of Spring Boot 3](#90-the-major-milestones-of-spring-boot-3)
    - [9.1 The Java 17 Baseline & Java EE to Jakarta EE Namespace Migration](#91-the-java-17-baseline-java-ee-to-jakarta-ee-namespace-migration)
    - [9.2 Modern Security Configuration Updates (Spring Security 6)](#92-modern-security-configuration-updates-spring-security-6)
    - [9.3 Hibernate 6 & Spring Data 3 Breaking Changes](#93-hibernate-6--spring-data-3-breaking-changes)
    - [9.4 Migrating Distributed Tracing: The Sleuth to Micrometer Transition](#94-migrating-distributed-tracing-the-sleuth-to-micrometer-transition)
    - [9.5 The Spring Boot 3.x Feature Roadmap (3.1, 3.2, 3.3, 3.4)](#95-the-spring-boot-3x-feature-roadmap-31-32-33-34)
    - [9.6 Automated Migration with OpenRewrite](#96-automated-migration-with-openrewrite)
    - [9.7 The 10-Step Production Upgrade Playbook (Checklist)](#97-the-10-step-production-upgrade-playbook-checklist)
    - [Chapter 9 Exercises & Solutions](#chapter-9-exercises-solutions)
- [**Chapter 10: Massive Exercises Section (Concept Checks, Debugging & Capstones)**](#chapter-10-massive-exercises-section-concept-checks-debugging-capstones)
  - [10.1 Conceptual & Architectural Review Questions](#101-conceptual-architectural-review-questions)
  - [10.2 Code Pitfall & Debugging Challenges](#102-code-pitfall-debugging-challenges)
  - [10.3 Comprehensive Cumulative Capstone Projects](#103-comprehensive-cumulative-capstone-projects)
---

# Part 0: Spring Core Foundations & Architectural Primer

Every software framework exists to solve specific, painful problems that plagued earlier generations of developers. To understand Spring and Spring Boot deeply, you must understand the architectural crisis that occurred when enterprise Java applications were built using plain Java and classic J2EE specifications.

---

### 0.0 Fundamental Concepts: Annotations, Records, Entities, and DTOs

Before examining enterprise design patterns, dependency injection containers, and web frameworks, every developer must master four core building blocks that form the vocabulary of modern Spring Boot applications: **Annotations**, **Java Records**, **Entities**, and **Data Transfer Objects (DTOs)**.

#### 1. Java Annotations Demystified

In Java, an **annotation** (designated by the `@` prefix) is structured metadata attached to source code elements—such as classes, interfaces, methods, parameters, and fields.

##### What Does an Annotation Actually Do?

A critical concept for beginners to understand is that **annotations do not execute code by themselves**. An annotation is merely a passive declaration or marker. It does not alter compiled method bytecode on its own.

Instead, annotations rely on an external processor—such as the Java compiler, the JVM runtime, or a framework like Spring—to inspect the annotation and execute corresponding logic. When you write `@RestController` or `@Transactional`, you are leaving a structured instruction that Spring interprets at application startup or during request execution.

##### How Annotations are Defined in Java

Java defines annotations using the `@interface` keyword, accompanied by meta-annotations that specify where the annotation can be placed and how long it survives:

The following code illustrates how a custom runtime annotation is declared:

```java
package com.example.demo.annotation;

import java.lang.annotation.*;

// @Target defines WHERE the annotation can be placed in Java source code
@Target({ElementType.TYPE, ElementType.METHOD}) 
// @Retention defines HOW LONG the annotation survives in the compiled application
@Retention(RetentionPolicy.RUNTIME) 
@Documented
public @interface AuditLog {
    String action() default "DEFAULT_ACTION";
}
```

The two most essential meta-annotations are:
- **`@Target`**: Restricts the syntactic locations where the annotation is allowed:
  - `ElementType.TYPE`: Classes, interfaces, enums, or records.
  - `ElementType.METHOD`: Class or interface methods.
  - `ElementType.FIELD`: Instance or static variables.
  - `ElementType.PARAMETER`: Method or constructor arguments.
- **`@Retention`**: Controls the lifecycle of the annotation:
  - `RetentionPolicy.SOURCE`: Discarded by the compiler after syntax checking (e.g., `@Override`, `@SuppressWarnings`). Never present in `.class` files.
  - `RetentionPolicy.CLASS`: Recorded in `.class` files by the compiler, but ignored by the JVM at runtime.
  - `RetentionPolicy.RUNTIME`: Loaded into JVM memory and accessible at runtime via **Java Reflection**. **Spring relies almost exclusively on `RUNTIME` retention to discover and wire components dynamically.**

##### How Spring Discovers and Executes Annotations

When your Spring Boot application starts, the Spring IoC container performs classpath scanning using Java Reflection. The following flowchart illustrates how Spring reads metadata to construct application beans:

```mermaid
flowchart TD
    Scan["1. Classpath Scanner inspects loaded classes"] --> Inspect{"Class.isAnnotationPresent(@Service)?"}
    Inspect -->|"Yes"| CreateInstance["2. Instantiates Object via Reflection (new UserService())"]
    CreateInstance --> Register["3. Registers Object in ApplicationContext as Singleton Bean"]
    Register --> Proxies{"Method has @Transactional?"}
    Proxies -->|"Yes"| WrapProxy["4. Generates CGLIB / Dynamic Proxy around Bean to handle SQL commit/rollback"]
    Proxies -->|"No"| Ready["5. Bean ready for Dependency Injection"]
```

##### Master Annotation Reference Taxonomy

Spring Boot applications employ specialized annotations organized into five functional families:

| Annotation Family | Key Annotations | Where Placed | What Spring Does When It Sees Them |
| :--- | :--- | :--- | :--- |
| **Component & Bean Management** | `@Component`, `@Service`, `@Repository`, `@Controller`, `@RestController`, `@Configuration`, `@Bean` | Classes & Configuration Methods | Instantiates the class, manages its lifecycle, and registers it as an injectable Spring Bean in the IoC container. |
| **Dependency Injection** | `@Autowired`, `@Qualifier`, `@Primary`, `@Value` | Constructors, Fields, Methods | Locates matching beans in the container and automatically passes them into the dependent class. |
| **Web & REST Routing** | `@RequestMapping`, `@GetMapping`, `@PostMapping`, `@PutMapping`, `@DeleteMapping`, `@RequestBody`, `@PathVariable`, `@RequestParam` | Controller Classes & Methods | Registers HTTP URL routes, matches HTTP request verbs, and deserializes incoming headers, query parameters, or JSON payloads into Java arguments. |
| **Data Persistence (JPA)** | `@Entity`, `@Table`, `@Id`, `@GeneratedValue`, `@Column`, `@OneToMany`, `@ManyToOne`, `@JoinColumn` | Domain Classes & Fields | Instructs Hibernate ORM to map the Java class to a relational database table and synchronize state with SQL queries. |
| **Input Validation** | `@Valid`, `@NotNull`, `@NotBlank`, `@Size`, `@Min`, `@Max`, `@Email` | Record / DTO Fields & Controller Parameters | Enforces data integrity rules, rejecting invalid client payloads with HTTP 400 Bad Request before business logic executes. |

---

#### 2. Java 17 Records Explained

Modern Java applications handle immense volumes of structured data. Historically, Java developers wrote verbose "JavaBean" classes filled with repetitive boilerplate code. Java 14 introduced—and Java 16/17 finalized—**Records (JEP 395)** to eliminate this boilerplate entirely.

##### What is a Java Record?

A **Record** is a specialized form of class designed to act as a pure, immutable transparent carrier for data. When you declare a record, the Java compiler automatically generates all standard object methods behind the scenes.

##### Code Comparison: Traditional JavaBean vs Modern Java Record

Consider a simple data structure carrying a user's identification, display name, and email address.

The following class illustrates the traditional, verbose JavaBean approach requiring over 50 lines of boilerplate code:

```java
// Traditional Java Approach: Exhausting Boilerplate POJO
public class UserDto {
    private final Long id;
    private final String name;
    private final String email;

    public UserDto(Long id, String name, String email) {
        this.id = id;
        this.name = name;
        this.email = email;
    }

    public Long getId() { return id; }
    public String getName() { return name; }
    public String getEmail() { return email; }

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (!(o instanceof UserDto userDto)) return false;
        return Objects.equals(id, userDto.id) &&
               Objects.equals(name, userDto.name) &&
               Objects.equals(email, userDto.email);
    }

    @Override
    public int hashCode() {
        return Objects.hash(id, name, email);
    }

    @Override
    public String toString() {
        return "UserDto{" + "id=" + id + ", name='" + name + '\'' + ", email='" + email + '\'' + '}';
    }
}
```

The following single-line record declaration produces the exact same functionality with zero boilerplate:

```java
// Modern Java 17+ Approach: Exactly One Line!
public record UserDto(Long id, String name, String email) {}
```

##### Key Properties of Java Records

When you declare a record, the Java compiler enforces specific architectural rules:
1. **Implicitly Final**: A record cannot be extended (`final class`), and cannot extend any other class (it automatically extends `java.lang.Record`). However, it can implement interfaces.
2. **Immutable State**: Every field (component) declared in the record header is implicitly `private final`. Once instantiated, its values cannot be modified.
3. **Accessor Methods Without `get` Prefix**: Getters are generated matching the component name directly. For example, call `userDto.name()` rather than `userDto.getName()`.
4. **Automatic Canonical Constructor**: The compiler generates a constructor accepting all parameters in declaration order.
5. **State-Based `equals()`, `hashCode()`, and `toString()`**: Two record instances with identical component values are considered equal automatically.

##### Compact Constructors for Instant Validation

Records support a special constructor syntax called the **Compact Constructor**, designed specifically for input validation and normalization without repeating field assignments:

The following record validates and normalizes its fields upon creation:

```java
public record CreateUserRequest(String name, String email) {
    // Compact constructor: parameter list is omitted!
    public CreateUserRequest {
        if (name == null || name.isBlank()) {
            throw new IllegalArgumentException("User name cannot be empty");
        }
        if (email == null || !email.contains("@")) {
            throw new IllegalArgumentException("Invalid email format");
        }
        // Normalizes email to lowercase automatically
        email = email.trim().toLowerCase();
    }
}
```

---

#### 3. Entities Explained (The Relational Database Model)

An **Entity** is a Java class that represents a persistent data record stored in a database table. In Spring applications utilizing Spring Data JPA and Hibernate, entities are decorated with the `@Entity` annotation.

##### Core Characteristics of an Entity

Unlike transient in-memory objects, an entity possesses distinct architectural qualities:

1. **Persistent Identity (`@Id`)**: Every entity must declare a primary key field annotated with `@Id`. Two entity objects with identical primary key values represent the exact same database row, even if their other in-memory fields differ.
2. **Mutable State**: Entities are typically mutable classes with getters and setters, allowing business logic to modify table state during transactions.
3. **Hibernate Persistence Context Tracking**: When an entity is retrieved from a database within a `@Transactional` boundary, it becomes **managed** by the Hibernate persistence context. Hibernate tracks every modification to the entity's fields. When the transaction commits, Hibernate executes "dirty checking" and emits an SQL `UPDATE` statement automatically—without requiring you to call `repository.save()`!
4. **Entity Lifecycle States**:
   - **Transient (New)**: The object was instantiated with `new User()`; it has no database ID and is not tracked by Hibernate.
   - **Persistent (Managed)**: The object is associated with a database row and actively tracked by the current Hibernate session.
   - **Detached**: The database transaction finished and the Hibernate session closed. The entity still holds its data and ID, but changes made to it are no longer tracked.
   - **Removed**: The entity is scheduled for deletion via an SQL `DELETE` statement upon transaction commit.

The following class demonstrates a typical JPA entity mapping to a PostgreSQL `customers` table:

```java
package com.example.demo.domain;

import jakarta.persistence.*;
import java.time.Instant;

@Entity
@Table(name = "customers")
public class CustomerEntity {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @Column(nullable = false, length = 100)
    private String fullName;

    @Column(nullable = false, unique = true, length = 150)
    private String email;

    @Column(nullable = false, updatable = false)
    private Instant createdAt = Instant.now();

    // Default no-arg constructor required by JPA specification via reflection
    protected CustomerEntity() {}

    public CustomerEntity(String fullName, String email) {
        this.fullName = fullName;
        this.email = email;
    }

    public Long getId() { return id; }
    public String getFullName() { return fullName; }
    public void setFullName(String fullName) { this.fullName = fullName; }
    public String getEmail() { return email; }
    public void setEmail(String email) { this.email = email; }
}
```

---

#### 4. Data Transfer Objects (DTOs) Explained (The Network Contract)

A **Data Transfer Object (DTO)** is an object whose sole architectural responsibility is transporting data across network boundaries—such as between a frontend client (browser/mobile app) and a REST controller, or between two microservices.

##### Why Do We Need DTOs?

A common beginner misconception is: *"Why create both a CustomerEntity and a CustomerDto? Isn't that duplicate work?"*

In enterprise software engineering, the internal database structure and the external API contract serve completely different purposes and evolve at different speeds:
- The **Entity** is optimized for relational database normalization, foreign key constraints, indexing, and transactional integrity.
- The **DTO** is optimized for network efficiency, API usability, data security, and client requirements.

The following table summarizes the fundamental differences between Entities and DTOs:

| Architectural Dimension | JPA Entity (`@Entity`) | Data Transfer Object (DTO Record) |
| :--- | :--- | :--- |
| **Primary Purpose** | Represents persistent database table rows | Defines public API request/response contracts |
| **State Lifecycle** | Managed by Hibernate persistence context | Pure transient in-memory data carrier |
| **Mutability** | Mutable (requires setters for ORM hydration & updates) | Immutable (implemented using Java 17 Records) |
| **Database Identity** | Requires `@Id` primary key mapping | Has no primary key concept (pure data snapshot) |
| **Business Logic** | May contain domain rules and relationship invariants | Zero business logic; contains only data fields |
| **Serialization Safety**| Dangerous for JSON (risks infinite recursion & security leaks) | 100% safe for Jackson JSON serialization |

---

#### 5. The Golden Architecture: Why Entities Must NEVER Cross the Web Boundary

In professional Spring development, **JPA Entities must NEVER be used as `@RequestBody` or return types in `@RestController` endpoints**. All web communication must pass strictly through DTOs.

##### The 3 Catastrophic Pitfalls of Exposing Entities

Exposing entities directly to your REST API introduces three severe failure modes:

1. **Mass Assignment / Over-Posting Vulnerability**:
   Suppose your `UserEntity` has an `isAdmin` or `accountBalance` column. If your controller method signature is `public void createUser(@RequestBody UserEntity user)`, an attacker can send:
   ```json
   { "name": "Eve", "email": "eve@attacker.com", "isAdmin": true, "accountBalance": 99999.00 }
   ```
   Spring's deserializer will automatically bind those JSON fields to the entity. When the entity is saved, the attacker successfully grants themselves administrative privileges! Using a dedicated `CreateUserRequest` record containing *only* `name` and `email` makes mass assignment attacks impossible.
2. **The Infinite Recursion Trap (`StackOverflowError`)**:
   Relational databases feature bidirectional relationships (e.g., an `Author` has a `@OneToMany List<Book>`, and each `Book` has a `@ManyToOne Author`). When Jackson attempts to serialize the `Author` entity into JSON, it serializes its books. While serializing each `Book`, Jackson encounters the parent `Author` and serializes it again, recursing infinitely until the JVM crashes with `java.lang.StackOverflowError`. DTOs flatten or selectively structure data, eliminating cyclical references.
3. **Database Schema Coupling & Fragility**:
   If you rename a column in your database or normalize a table into two tables, exposing entities forces immediate breaking changes onto your mobile app and web frontend clients. DTOs decouple internal database refactoring from the external public API contract.

##### The Complete End-to-End Architectural Data Flow

The following sequence diagram illustrates how DTOs and Entities collaborate safely across layers during an HTTP request:

```mermaid
sequenceDiagram
    autonumber
    actor Client as HTTP Client (Mobile / Web)
    participant Ctrl as Presentation Layer (@RestController)
    participant Svc as Business Logic Layer (@Service)
    participant Repo as Data Access Layer (@Repository)
    participant DB as PostgreSQL Database

    Client->>Ctrl: POST /api/v1/customers (JSON Body)
    Note over Ctrl: Jackson deserializes JSON into CreateCustomerRequest DTO Record
    
    Ctrl->>Svc: registerCustomer(CreateCustomerRequest dto)
    Note over Svc: 1. Validates business invariants<br/>2. Maps DTO -> CustomerEntity
    
    Svc->>Repo: save(CustomerEntity entity)
    Repo->>DB: INSERT INTO customers (full_name, email) VALUES (?, ?)
    DB-->>Repo: Saved row with generated ID = 42
    Repo-->>Svc: Returns managed CustomerEntity(id=42)
    
    Note over Svc: Maps CustomerEntity -> CustomerResponse DTO Record
    Svc-->>Ctrl: Returns CustomerResponse(id=42, fullName, email)
    
    Ctrl-->>Client: 201 Created with CustomerResponse JSON
    Note over Client,Ctrl: Entity never leaves the Service layer boundary!
```

##### End-to-End Implementation in Code

The following complete, minimal code example demonstrates this golden architecture in practice:

First, define the request and response DTO records:

```java
package com.example.demo.dto;

import jakarta.validation.constraints.Email;
import jakarta.validation.constraints.NotBlank;
import java.time.Instant;

// Request DTO: Contains ONLY input data accepted from the client
public record CreateCustomerRequest(
    @NotBlank(message = "Name is required") String fullName,
    @Email(message = "Must be a valid email") @NotBlank String email
) {}

// Response DTO: Contains ONLY the safe output data returned to the client
public record CustomerResponse(
    Long id,
    String fullName,
    String email,
    Instant memberSince
) {}
```

Second, define the service layer that maps between DTOs and the persistent entity:

```java
package com.example.demo.service;

import com.example.demo.domain.CustomerEntity;
import com.example.demo.dto.CreateCustomerRequest;
import com.example.demo.dto.CustomerResponse;
import com.example.demo.repository.CustomerRepository;
import org.springframework.stereotype.Service;
import org.springframework.transaction.annotation.Transactional;

@Service
public class CustomerService {

    private final CustomerRepository repository;

    public CustomerService(CustomerRepository repository) {
        this.repository = repository;
    }

    @Transactional
    public CustomerResponse createCustomer(CreateCustomerRequest request) {
        // Step 1: Map Request DTO -> JPA Entity
        CustomerEntity entity = new CustomerEntity(request.fullName(), request.email());

        // Step 2: Persist entity to database via repository
        CustomerEntity saved = repository.save(entity);

        // Step 3: Map saved JPA Entity -> Response DTO
        return new CustomerResponse(
            saved.getId(),
            saved.getFullName(),
            saved.getEmail(),
            saved.getCreatedAt()
        );
    }
}
```

Third, define the REST controller that speaks exclusively in DTOs:

```java
package com.example.demo.controller;

import com.example.demo.dto.CreateCustomerRequest;
import com.example.demo.dto.CustomerResponse;
import com.example.demo.service.CustomerService;
import jakarta.validation.Valid;
import org.springframework.http.HttpStatus;
import org.springframework.web.bind.annotation.*;

@RestController
@RequestMapping("/api/v1/customers")
public class CustomerController {

    private final CustomerService service;

    public CustomerController(CustomerService service) {
        this.service = service;
    }

    @PostMapping
    @ResponseStatus(HttpStatus.CREATED)
    public CustomerResponse create(@Valid @RequestBody CreateCustomerRequest request) {
        // Accepts Request DTO, returns Response DTO. Entity is safely encapsulated!
        return service.createCustomer(request);
    }
}
```

---

### 0.1 The Architectural Crisis of Plain Java & Enterprise J2EE

Before the year 2003, developers built enterprise web applications using either pure Core Java primitives or the heavy Java 2 Platform, Enterprise Edition (J2EE) specification. In both approaches, applications suffered from three crippling structural defects.

#### Problem 1: Hardcoded Dependencies and Tight Coupling

In object-oriented programming, classes collaborate to accomplish business tasks. For example, an `OrderService` must process credit card transactions using a `PaymentGateway`. In plain Java, the natural instinct of a beginner is to instantiate the dependency directly inside the class:

The following class demonstrates tight coupling by creating its own dependency using the `new` keyword:

```java
public class OrderService {
    // Problem: The OrderService class decides exactly WHICH implementation to use!
    // It is tightly bound to StripePaymentGateway.
    private StripePaymentGateway paymentGateway = new StripePaymentGateway();

    public void checkout(String orderId, double amount) {
        System.out.println("Beginning checkout for order: " + orderId);
        // Direct call to the hardcoded Stripe implementation
        paymentGateway.processPayment(amount);
    }
}
```

This design introduces severe architectural problems:
1. **Zero Flexibility**: What happens if your company decides to switch from Stripe to PayPal or Adyen? You must open `OrderService.java`, modify its source code, recompile, and redeploy.
2. **Impossible to Unit Test**: When writing a unit test for `OrderService`, you want to test order calculation logic without actually charging real credit cards or making network calls. Because `StripePaymentGateway` is hardcoded inside `OrderService`, you cannot substitute a mock gateway. The test will either crash due to missing API keys or trigger real financial charges!

The following test illustrates why tight coupling breaks automated testing:

```java
public class OrderServiceTest {
    @Test
    public void testCheckout() {
        OrderService service = new OrderService();
        // FAILS! This attempts to contact the real Stripe network because
        // we have no way to pass in a fake/mock payment gateway!
        service.checkout("ORD-101", 49.99);
    }
}
```

#### Problem 2: Resource Leaks and Boilerplate in Raw JDBC

When interacting with relational databases, plain Java developers used the Java Database Connectivity (JDBC) API. Raw JDBC required manual management of network sockets, prepared statements, and result sets inside deeply nested `try-catch-finally` blocks.

The following code illustrates the massive boilerplate and connection leak danger in raw JDBC:

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;

public class RawJdbcUserRepository {

    public String findEmailById(long userId) {
        Connection connection = null;
        PreparedStatement statement = null;
        ResultSet resultSet = null;
        try {
            // Step 1: Manually open a physical TCP connection (costly!)
            connection = DriverManager.getConnection("jdbc:postgresql://localhost:5432/appdb", "user", "pass");

            // Step 2: Manually compile the SQL statement
            statement = connection.prepareStatement("SELECT email FROM users WHERE id = ?");
            statement.setLong(1, userId);

            // Step 3: Execute query and extract cursor results
            resultSet = statement.executeQuery();
            if (resultSet.next()) {
                return resultSet.getString("email");
            }
            return null;
        } catch (SQLException e) {
            // Must handle low-level driver exceptions manually
            throw new RuntimeException("Database failure", e);
        } finally {
            // Step 4: Manually close every resource in reverse order
            // If any close() call throws an exception, the connection leaks!
            if (resultSet != null) { try { resultSet.close(); } catch (SQLException ignored) {} }
            if (statement != null) { try { statement.close(); } catch (SQLException ignored) {} }
            if (connection != null) { try { connection.close(); } catch (SQLException ignored) {} }
        }
    }
}
```

Notice that out of 34 lines of code, only **one single line** (`SELECT email FROM users WHERE id = ?`) contains actual business logic. The remaining 33 lines are ceremonial plumbing. If a developer forgot to close the connection in the `finally` block, the database connection pool would starve within hours, crashing the server.

#### Problem 3: The Heavyweight Complexity of Classic J2EE

The Java 2 Enterprise Edition (J2EE) specification attempted to solve enterprise concerns (transactions, security, remoting) using Enterprise JavaBeans (EJBs). However, EJBs introduced extreme accidental complexity:
- Every business bean required three separate files: a Home interface, a Remote/Local interface, and the Implementation class.
- Configuration required writing thousands of lines of fragile XML deployment descriptors.
- Code could not be executed or tested in a normal JVM; it required starting heavy, commercial application servers like IBM WebSphere or BEA WebLogic, taking 5 to 10 minutes just to boot up!

In 2002, Australian developer **Rod Johnson** published the seminal book *"Expert One-on-One J2EE Design and Development"*. He demonstrated that 95% of enterprise applications could be built using simple, lightweight **Plain Old Java Objects (POJOs)** combined with a lightweight container that wired dependencies together. This open-source code accompanied the book and became the foundation of the **Spring Framework**.

---

### 0.2 Inversion of Control (IoC) & Dependency Injection (DI)

To eliminate hardcoded dependencies, Spring applies an architectural principle called **Inversion of Control (IoC)**, implemented via the **Dependency Injection (DI)** design pattern.

#### The Core Mental Model: Inverting Control

In traditional procedural programming, your custom class is in the driver's seat: it controls the instantiation of all collaborating objects.

```text
Traditional Control Flow:
[ Your OrderService ] ===== uses 'new' =====> Creates [ StripePaymentGateway ]
(OrderService is in total control of what object is constructed)
```

**Inversion of Control (IoC)** turns this dynamic on its head: an external entity (the framework container) takes control of instantiating objects, configuring them, and supplying them to your classes.

```text
Inverted Control Flow:
                      [ Spring IoC Container ]
                            │          │
         Creates & Manages  │          │  Creates & Manages
                            ▼          ▼
                   [ PaymentGateway ]  [ OrderService ]
                            │
               Injected into│
                            ▼
                   [ OrderService ] receives PaymentGateway from Container!
```

#### The Real-World Restaurant Analogy

Understanding the difference between traditional control and Inversion of Control is simple when compared to dining out:

- **Traditional Control (Cooking at Home)**: You must physically buy a stove, purchase groceries, chop vegetables, cook the food, and wash the dishes. You are forced to manage every single dependency yourself.
- **Inversion of Control (Visiting a Restaurant)**: You sit at a table and order dinner. The restaurant owns the kitchen, employs the chefs, sources the ingredients, and delivers the prepared meal directly to your table. You do not build the kitchen; the restaurant provides the finished service to you.

#### What is Dependency Injection (DI)?

**Dependency Injection** is the specific pattern used to implement IoC. Instead of a class pulling dependencies in using `new`, the dependencies are *pushed* (injected) into the class from the outside.

Let us refactor our earlier `OrderService` step-by-step to use Dependency Injection.

##### Step 1: Define a Clean Abstraction (Interface)

The following interface decouples the high-level business concept of processing payments from any concrete third-party provider:

```java
public interface PaymentGateway {
    // Contract: Any payment provider must implement this method
    void processPayment(double amount);
}
```

##### Step 2: Implement Concrete Collaborators

The following two classes implement the interface, representing real production Stripe processing versus an in-memory test simulator:

```java
// Production implementation: connects to external Stripe servers
public class StripePaymentGateway implements PaymentGateway {
    @Override
    public void processPayment(double amount) {
        System.out.println("Processing $" + amount + " through Stripe network API.");
    }
}

// Test implementation: fake simulator that never touches real money
public class MockPaymentGateway implements PaymentGateway {
    private boolean paymentProcessed = false;

    @Override
    public void processPayment(double amount) {
        System.out.println("Simulating test payment of $" + amount + " locally.");
        this.paymentProcessed = true;
    }

    public boolean isPaymentProcessed() {
        return paymentProcessed;
    }
}
```

##### Step 3: Inject the Dependency via Constructor

The following class demonstrates **Constructor Injection**. The `OrderService` no longer knows or cares which concrete class executes the payment; it only knows that whatever is passed into its constructor satisfies the `PaymentGateway` contract:

```java
public class OrderService {
    // 1. Declare the dependency as final (immutable and thread-safe)
    private final PaymentGateway paymentGateway;

    // 2. Supply the dependency through the constructor from the outside
    public OrderService(PaymentGateway paymentGateway) {
        if (paymentGateway == null) {
            throw new IllegalArgumentException("PaymentGateway cannot be null!");
        }
        this.paymentGateway = paymentGateway;
    }

    public void checkout(String orderId, double amount) {
        System.out.println("Checking out order: " + orderId);
        // Calls the interface method polymorphically
        paymentGateway.processPayment(amount);
    }
}
```

##### Step 4: The Massive Testing Benefit

Because `OrderService` accepts its dependency through its constructor, testing it in isolation is now effortless. We can pass our `MockPaymentGateway` directly without booting up Spring, without network connections, and without API keys!

The following JUnit test verifies `OrderService` in microseconds using plain Java:

```java
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;

public class OrderServiceUnitTest {

    @Test
    public void testCheckoutWithMockGateway() {
        // Arrange: Create a fake mock gateway
        MockPaymentGateway mockGateway = new MockPaymentGateway();

        // Act: Inject the mock directly into the service constructor
        OrderService service = new OrderService(mockGateway);
        service.checkout("ORD-555", 99.00);

        // Assert: Verify business behavior without hitting real payment servers
        assertTrue(mockGateway.isPaymentProcessed());
    }
}
```

#### Comparing the Three Types of Dependency Injection

Spring supports three primary mechanisms for injecting dependencies into a class. Understanding why one is universally preferred is crucial for every Java engineer.

| Injection Style | Mechanism | Immutability (`final`) | Ease of Unit Testing | Recommended By Spring Team? |
| :--- | :--- | :--- | :--- | :--- |
| **Constructor Injection** | Injected via constructor arguments | **Yes** (fields can be `final`) | **Trivial** (pass mocks via `new`) | **YES (Universal Best Practice)** |
| **Setter Injection** | Injected via `setXxx(...)` methods | No (fields must be mutable) | Moderate (must call setters) | Only for optional dependencies |
| **Field Injection** | Injected via `@Autowired` on private field | No (fields cannot be `final`) | Difficult (requires reflection hacks) | **NO (Avoid in Production)** |

##### Why Constructor Injection is the Industry Gold Standard

1. **Guarantees Complete Initialization**: An object cannot be instantiated in a half-baked, broken state. If `OrderService` requires a `PaymentGateway`, the Java compiler refuses to let you instantiate it without providing one.
2. **True Immutability**: Declaring fields as `final` ensures that once the object is constructed, its dependencies can never be accidentally reassigned or corrupted by other threads.
3. **Fail-Fast Circular Dependency Detection**: If Class A requires Class B in its constructor, and Class B requires Class A, Spring immediately fails during startup with a descriptive error, preventing hidden runtime deadlocks.
4. **Spring Boot 3 Convenience**: In modern Spring, if a class has **only one constructor**, you do **NOT** even need to write the `@Autowired` annotation! Spring detects the constructor and injects dependencies automatically.

The following class demonstrates modern, clean constructor injection without any framework annotations on the constructor:

```java
import org.springframework.stereotype.Service;

@Service
public class CustomerNotificationService {

    private final EmailClient emailClient;
    private final SmsClient smsClient;

    // No @Autowired required! Spring Boot automatically wires parameters
    public CustomerNotificationService(EmailClient emailClient, SmsClient smsClient) {
        this.emailClient = emailClient;
        this.smsClient = smsClient;
    }
}
```

##### Why Field Injection is an Anti-Pattern

Many beginners write `@Autowired private PaymentGateway paymentGateway;` directly on private variables because it requires less typing. Here is why senior engineers reject this pattern in code reviews:

The following code illustrates the dangerous hidden dependency flaw of field injection:

```java
@Service
public class FlawedService {

    // ANTI-PATTERN: Field injection hides dependencies and prevents immutability!
    @Autowired
    private PaymentGateway paymentGateway;

    public void process(double amount) {
        paymentGateway.processPayment(amount);
    }
}
```

If you try to test this class in a plain unit test (`FlawedService service = new FlawedService(); service.process(100);`), it immediately crashes with a `NullPointerException`! Because `paymentGateway` is private and lacks a constructor or setter, you cannot supply a mock dependency without starting a slow Spring test context or using reflection hacks.

---

### 0.3 The Spring IoC Container & Bean Lifecycle

If classes no longer use `new` to instantiate their dependencies, who creates the objects? The **Spring IoC Container**.

#### What is a Spring Bean?

A **Spring Bean** is simply a normal Java object that is instantiated, assembled, and managed by the Spring IoC container rather than by manual `new` expressions in your application code.

#### What is the `ApplicationContext`?

The `ApplicationContext` is the official Java interface representing the Spring IoC container. Think of it as the central registry and brain of your application. It:
1. Scans your project for bean declarations.
2. Reads configuration properties.
3. Instantiates beans in topological dependency order.
4. Injects dependencies into constructors.
5. Manages bean lifecycles from creation to shutdown.

The following sequence illustrates how the Spring IoC container wires an application on startup:

```mermaid
sequenceDiagram
    autonumber
    actor JVM as Application Startup
    participant Container as Spring ApplicationContext
    participant Stripe as StripePaymentGateway
    participant Order as OrderService

    JVM->>Container: Boot Spring Container
    Container->>Container: Scan classpath for @Component & @Service
    Container->>Stripe: Instantiate StripePaymentGateway (Bean)
    Stripe-->>Container: Instance ready in registry
    Container->>Order: Instantiate OrderService(StripePaymentGateway)
    Note over Container,Order: Container injects Stripe bean into OrderService constructor!
    Order-->>Container: Instance ready in registry
    Container-->>JVM: ApplicationContext fully initialized!
```

#### How Beans are Declared: Configuration vs Component Scanning

Spring provides two primary methods for registering beans with the container:

##### Method 1: Component Scanning (`@Component`, `@Service`, `@Repository`)

For classes that you author within your project, annotate the class directly with a stereotype annotation. Spring automatically discovers them during startup classpath scanning:

The following class registers itself automatically as a Spring Bean using the `@Service` annotation:

```java
package com.example.demo.service;

import org.springframework.stereotype.Service;

// Spring sees @Service and creates a singleton instance automatically!
@Service
public class InventoryService {
    public boolean isInStock(String sku) {
        return true;
    }
}
```

##### Method 2: Explicit Java Configuration (`@Configuration` & `@Bean`)

When you integrate third-party libraries (such as Jackson's `ObjectMapper`, an AWS SDK client, or a Redis connection pool), you cannot add `@Service` to their source code because their classes are compiled inside third-party JARs. In this scenario, you write a `@Configuration` class containing `@Bean` factory methods:

The following class demonstrates how to expose a third-party library object as a managed Spring Bean:

```java
package com.example.demo.config;

import com.fasterxml.jackson.databind.ObjectMapper;
import com.fasterxml.jackson.databind.SerializationFeature;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

// 1. @Configuration tells Spring this class contains bean definition recipes
@Configuration
public class ThirdPartyLibraryConfig {

    // 2. @Bean registers the return value of this method as a Spring Bean!
    // The bean name defaults to the method name: "objectMapper"
    @Bean
    public ObjectMapper customObjectMapper() {
        ObjectMapper mapper = new ObjectMapper();
        // Customize the third-party instance
        mapper.enable(SerializationFeature.INDENT_OUTPUT);
        return mapper;
    }
}
```

#### The Complete Spring Bean Lifecycle

Every Spring bean progresses through a deterministic lifecycle managed by the container. Understanding this sequence allows you to initialize database connections, warm up caches, and release system resources gracefully.

```mermaid
flowchart TD
    Step1["1. Instantiation (Constructor invoked via reflection)"] --> Step2["2. Populate Properties (Dependencies injected)"]
    Step2 --> Step3["3. Aware Interfaces (BeanNameAware, ApplicationContextAware)"]
    Step3 --> Step4["4. BeanPostProcessor: postProcessBeforeInitialization()"]
    Step4 --> Step5["5. Initialization (@PostConstruct method executed)"]
    Step5 --> Step6["6. BeanPostProcessor: postProcessAfterInitialization() (AOP Proxies created)"]
    Step6 --> Step7["7. Bean Ready for Use (Servicing application requests)"]
    Step7 --> Step8["8. Container Shutdown Triggered"]
    Step8 --> Step9["9. Destruction (@PreDestroy method executed)"]
```

##### Demonstrating Lifecycle Hooks in Practice

The `@PostConstruct` annotation marks a method to run *after* the constructor has completed and all dependencies are injected. The `@PreDestroy` annotation marks a method to run right before the bean is removed from memory on application shutdown:

The following component demonstrates real-world resource initialization and cleanup:

```java
package com.example.demo.lifecycle;

import jakarta.annotation.PostConstruct;
import jakarta.annotation.PreDestroy;
import org.springframework.stereotype.Component;

@Component
public class CacheWarmupManager {

    public CacheWarmupManager() {
        // Step 1: Constructor runs first
        System.out.println("[Phase 1: Constructor] Bean instance created in memory.");
    }

    @PostConstruct
    public void onStartup() {
        // Step 5: Runs AFTER constructor and dependencies are fully injected
        System.out.println("[Phase 5: @PostConstruct] Container is ready! Warming up cache from database...");
    }

    @PreDestroy
    public void onShutdown() {
        // Step 9: Runs right before the application stops
        System.out.println("[Phase 9: @PreDestroy] Application stopping! Flushing cache and closing sockets...");
    }
}
```

#### Bean Scopes: Singleton vs Prototype

Spring allows you to control how many instances of a bean the container creates.

##### 1. Singleton Scope (Default)

In Spring, beans are **Singletons** by default. This means the container creates exactly **one single instance** of the class per `ApplicationContext`. Every class that injects this bean shares the exact same reference.

```text
Singleton Scope in Memory:
[ CustomerController ] ──┐
                         ├───> [ Single Shared UserService Instance (Heap) ]
[ AdminController ]    ──┘
```

> [!WARNING]
> Because singleton beans are shared across all concurrent web request threads, **singleton beans must be strictly stateless**. Never store user-specific or request-specific state in class fields of a singleton bean!

##### 2. Prototype Scope

When a bean is marked as `@Scope("prototype")`, the container creates a **brand-new instance** every single time the bean is requested from the container.

The following class configures an ephemeral task worker as a prototype bean:

```java
package com.example.demo.scope;

import org.springframework.context.annotation.Scope;
import org.springframework.stereotype.Component;

// A fresh instance is created every time this bean is requested!
@Component
@Scope("prototype")
public class ReportGenerationTask {
    private String taskId;

    public void execute() {
        System.out.println("Processing report task: " + this.hashCode());
    }
}
```

##### The Prototype Injection Trap

What happens when a `singleton` bean injects a `prototype` bean via standard constructor injection?

```java
@Service
public class OrderService {
    private final ReportGenerationTask reportTask;

    // TRAP! The constructor is only called ONCE when OrderService is created.
    // Therefore, OrderService holds onto the same prototype instance forever!
    public OrderService(ReportGenerationTask reportTask) {
        this.reportTask = reportTask;
    }
}
```

Because the singleton `OrderService` is instantiated only once at startup, its constructor executes only once. Consequently, it receives a single prototype instance and holds onto it forever, destroying the prototype behavior!

To obtain a truly fresh prototype instance on every method call, inject an `ObjectProvider<T>`:

The following service uses `ObjectProvider` to retrieve a fresh prototype instance on demand:

```java
package com.example.demo.scope;

import org.springframework.beans.factory.ObjectProvider;
import org.springframework.stereotype.Service;

@Service
public class CorrectedOrderService {

    // ObjectProvider acts as an on-demand factory for Spring beans
    private final ObjectProvider<ReportGenerationTask> taskProvider;

    public CorrectedOrderService(ObjectProvider<ReportGenerationTask> taskProvider) {
        this.taskProvider = taskProvider;
    }

    public void generateOrderReport() {
        // getObject() asks the Spring container for a brand-new prototype instance!
        ReportGenerationTask freshTask = taskProvider.getObject();
        freshTask.execute();
    }
}
```

---

### 0.4 Stereotype Annotations & Layered Architecture

Enterprise applications separate code into distinct logical layers to enforce the **Single Responsibility Principle**. Spring provides specialized stereotype annotations for each layer.

#### The 3-Tier Enterprise Architecture Flowchart

Every incoming web request travels through three distinct layers before reaching persistent storage:

```mermaid
flowchart TD
    Client["HTTP Client (Web Browser / Mobile App)"] --> Controller["1. Presentation Layer (@RestController)"]
    Controller --> Service["2. Business Logic Layer (@Service)"]
    Service --> Repository["3. Data Access Layer (@Repository)"]
    Repository --> Database[("Database Engine (PostgreSQL / MySQL)")]
```

#### Why Do We Have Multiple Annotations for `@Component`?

If `@Component` marks a class as a Spring Bean, why do we need `@Service`, `@Repository`, and `@RestController`?
All three are meta-annotated with `@Component`:

```java
// Under the hood, @Service is just a specialized @Component!
@Target(ElementType.TYPE)
@Retention(RetentionPolicy.RUNTIME)
@Documented
@Component
public @interface Service {}
```

Spring provides distinct annotations for three critical architectural reasons:
1. **Semantic Clarity**: Reading the code immediately communicates the architectural intent of the class to other developers.
2. **Layer-Specific Exception Translation**: Classes annotated with `@Repository` automatically gain Spring's persistence exception translation. Low-level driver errors (like `SQLException` or `HibernateException`) are caught by Spring AOP proxies and rethrown as Spring's standardized, technology-agnostic `DataAccessException` hierarchy!
3. **Targeted Pointcuts**: Security, transaction, and logging aspects can target specific layers (e.g., applying transactions only to `@Service` classes).

#### The Stereotype Annotations in Action

The following three classes demonstrate a complete, correctly architected 3-tier user registration feature:

##### 1. The Data Access Layer (`@Repository`)

The repository handles SQL or ORM operations, isolating database interactions from business rules:

```java
package com.example.demo.repository;

import org.springframework.stereotype.Repository;

@Repository
public class UserRepository {
    public boolean existsByEmail(String email) {
        // Simulate database lookup query
        return "admin@example.com".equalsIgnoreCase(email);
    }

    public void saveUser(String name, String email) {
        // Simulate SQL INSERT statement
        System.out.println("Saving user to database: " + name + " (" + email + ")");
    }
}
```

##### 2. The Business Logic Layer (`@Service`)

The service enforces business validation, coordinates multiple repositories, and manages transactional boundaries:

```java
package com.example.demo.service;

import com.example.demo.repository.UserRepository;
import org.springframework.stereotype.Service;

@Service
public class UserService {

    private final UserRepository userRepository;

    public UserService(UserRepository userRepository) {
        this.userRepository = userRepository;
    }

    public void registerUser(String name, String email) {
        // Business Rule: Emails must be unique
        if (userRepository.existsByEmail(email)) {
            throw new IllegalArgumentException("User with email " + email + " already exists!");
        }

        // Delegate persistence to repository
        userRepository.saveUser(name, email);
    }
}
```

##### 3. The Presentation Layer (`@RestController`)

The controller accepts incoming HTTP traffic, parses JSON parameters, and delegates processing to the service:

```java
package com.example.demo.controller;

import com.example.demo.service.UserService;
import org.springframework.http.HttpStatus;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.*;

@RestController
@RequestMapping("/api/v1/users")
public class UserController {

    private final UserService userService;

    public UserController(UserService userService) {
        this.userService = userService;
    }

    @PostMapping
    public ResponseEntity<String> register(@RequestParam String name, @RequestParam String email) {
        userService.registerUser(name, email);
        return ResponseEntity.status(HttpStatus.CREATED).body("User successfully registered!");
    }
}
```

---

### 0.4.1 Spring AOP & Proxies: The "Secret Service" Mental Model

One of the greatest sources of confusion for developers new to Spring is how annotations like `@Transactional`, `@Async`, `@Cacheable`, `@CircuitBreaker`, and `@PreAuthorize` actually execute. 

Do these annotations magically alter your compiled Java bytecode? **No.**
Spring achieves this declarative magic through **Aspect-Oriented Programming (AOP)** using **Dynamic Proxies**.

#### The Real-World Secret Service Analogy

Think of your Spring Bean as a high-profile Head of State (the Target Object). 
When foreign dignitaries (the Client) want to speak with the Head of State, they never speak to the person directly. Instead, they interact with the **Secret Service Bodyguard (the Spring Proxy)** standing in front of them:

1. **Before the meeting**: The Secret Service verifies the visitor's credentials (Security check / `@PreAuthorize`), opens the security gate, and starts an audio recording (Beginning transaction / `@Transactional`).
2. **During the meeting**: The Secret Service steps aside and delegates the actual conversation to the Head of State (invoking your actual Java method).
3. **After the meeting**: The Secret Service seals the room, archives the recording (Committing transaction), and logs the exit timestamp (Metrics / Logging).
4. **If an incident occurs**: If an intruder attacks during the meeting (Unchecked exception thrown), the Secret Service locks down the building and rolls back all open vaults (Rollback transaction).

```mermaid
sequenceDiagram
    autonumber
    actor Client as Caller (e.g., Controller)
    participant Proxy as Spring AOP Proxy (Bodyguard)
    participant Target as Real Service Bean (Target Object)
    participant DB as Transaction / Cache / Security Aspect

    Client->>Proxy: Calls orderService.placeOrder(dto)
    Note over Proxy,DB: [Before Advice]: Start DB Transaction, Check Security
    Proxy->>DB: Begin Transaction (conn.setAutoCommit(false))
    Proxy->>Target: Delegates: real target.placeOrder(dto)
    
    alt Method executes successfully
        Target-->>Proxy: Returns OrderConfirmationDto
        Note over Proxy,DB: [After Returning Advice]: Commit Transaction
        Proxy->>DB: Commit Transaction (conn.commit())
        Proxy-->>Client: Returns OrderConfirmationDto to Caller
    else Method throws RuntimeException
        Target-->>Proxy: Throws RuntimeException("Payment failed")
        Note over Proxy,DB: [After Throwing Advice]: Rollback Transaction
        Proxy->>DB: Rollback Transaction (conn.rollback())
        Proxy-->>Client: Propagates Exception
    end
```

#### How Spring Creates Proxies: JDK Dynamic Proxies vs. CGLIB

Spring uses two distinct mechanisms to generate dynamic proxy objects at runtime:

| Proxy Technology | How It Works | Requirement | Spring Boot 3 Default |
| :--- | :--- | :--- | :--- |
| **JDK Dynamic Proxies** | Generates an in-memory proxy class implementing the exact same Java `interface` as your bean. | Bean **must** implement one or more Java interfaces. | Used only if explicitly configured (`spring.aop.proxy-target-class=false`). |
| **CGLIB (Code Generation Library)** | Generates a dynamic subclass of your actual bean class at runtime, overriding public methods to inject interceptor logic. | Bean class and methods **must NOT be `final`**. | **Default in Spring Boot 2 & 3** (`proxyTargetClass=true`). |

```mermaid
flowchart TD
    subgraph JDKProxy ["1. JDK Dynamic Proxy (Interface-Based)"]
        Interface["UserService (Interface)"]
        Interface --> RealService["UserServiceImpl (Real Bean)"]
        Interface --> JdkP["$Proxy123 (Generated Proxy)"]
        JdkP -->|"Delegates to"| RealService
    end

    subgraph CglibProxy ["2. CGLIB Dynamic Proxy (Class-Based Subclass)"]
        RealClass["UserService (Concrete Class)"]
        CglibP["UserService$$SpringCGLIB$$0 (Generated Subclass)"]
        CglibP -->|"Extends & Overrides methods"| RealClass
    end
```

#### The #1 Spring Beginner Trap: The Self-Invocation Pitfall

Consider this seemingly innocent code:

```java
@Service
public class OrderService {

    // Non-transactional public method called by the Controller
    public void processOrder(Long orderId) {
        System.out.println("Validating order parameters...");
        // Calling another method in the SAME class!
        this.saveOrderToDatabase(orderId);
    }

    @Transactional // Expecting a database transaction here!
    public void saveOrderToDatabase(Long orderId) {
        // SQL statements executed here
    }
}
```

> [!CAUTION]
> **The Catastrophic Bug**:
> When a client calls `orderService.processOrder(1L)`, the transaction on `saveOrderToDatabase()` **WILL NEVER START**! The `@Transactional` annotation is completely ignored!
> 
> **Why?**
> The client invokes `processOrder()` through the Spring Proxy. The Proxy has no advice for `processOrder()`, so it delegates directly to the real target `OrderService`.
> Once execution is inside `OrderService`, `this.saveOrderToDatabase()` is an internal Java `this` reference. **It bypasses the proxy bodyguard entirely!** Because the proxy is never touched, the transaction advice never intercepts the call!

```text
External Client ───> [ Spring Proxy ] ───> OrderService.processOrder()
                                                    │
                                            (calls this.saveOrderToDatabase())
                                                    │
                                                    ▼
                                           OrderService.saveOrderToDatabase()
                                           [ BYPASSES PROXY! NO TRANSACTION! ]
```

##### How to Fix the Self-Invocation Bug:

1. **Extract to a Separate Collaborator Bean (Recommended)**: Move the transactional method to a dedicated `OrderPersistenceService` and inject it. This ensures every call flows through the Spring Proxy.
2. **Self-Injection with `ObjectProvider` or Lazy Dependency**:
   ```java
   @Service
   public class OrderService {
       private final ObjectProvider<OrderService> selfProvider;

       public OrderService(ObjectProvider<OrderService> selfProvider) {
           this.selfProvider = selfProvider;
       }

       public void processOrder(Long orderId) {
           // Invokes through the proxy bean obtained from the Spring container!
           selfProvider.getObject().saveOrderToDatabase(orderId);
       }

       @Transactional
       public void saveOrderToDatabase(Long orderId) { ... }
   }
   ```

---

### 0.5 From Spring Framework to Spring Boot: The Magic Unveiled

While the classic Spring Framework solved object coupling and resource management, setting up a new project remained notoriously painful.

#### What Was the Problem with Classic Spring Framework?

Before Spring Boot was created in 2014, creating a simple "Hello World" web service required days of manual setup:
1. Writing massive `web.xml` deployment descriptors.
2. Configuring `DispatcherServlet` XML files.
3. Manually downloading Apache Tomcat, configuring server ports, and building `.war` files.
4. Dealing with "JAR Hell": manually resolving conflicting versions of 30+ transitive dependencies in Maven.

#### The Three Architectural Pillars of Spring Boot

Spring Boot was created to eliminate this configuration overhead through three transformative innovations:

```mermaid
flowchart TD
    Boot["Spring Boot Magic"] --> P1["1. Embedded Servlet Containers (Tomcat/Jetty)"]
    Boot --> P2["2. Starter Dependencies (spring-boot-starter-*)"]
    Boot --> P3["3. Automatic Configuration (@EnableAutoConfiguration)"]

    P1 --> Run["Runnable JARs (java -jar app.jar)"]
    P2 --> BOM["Zero Version Conflicts via BOM"]
    P3 --> Guess["Intelligent Classpath-Based Bean Generation"]
```

##### 1. Embedded Servlet Containers (Tomcat)

In traditional Java web development, you had to install Apache Tomcat on a physical Linux server, package your application as a `.war` file, and deploy it into Tomcat's `webapps/` directory.

**Spring Boot inverts this architecture**: Apache Tomcat is embedded directly inside your application JAR file as a standard Java library!

```text
The Old Deployment Model (WAR):
[ Linux Host ] ───> [ Standalone Tomcat Server ] ───> [ Deploys app.war inside Tomcat ]

The Modern Spring Boot Model (Fat/Runnable JAR):
[ java -jar my-application.jar ] ───> [ Boots up Embedded Tomcat internally on port 8080! ]
```

##### 2. Spring Boot Starters (Curated Dependency Bundles)

Instead of manually hunting for compatible versions of Hibernate, Jackson, and Spring MVC in Maven, Spring Boot provides **Starters**—pre-tested, pre-configured bundles:
- `spring-boot-starter-web`: Pulls Spring MVC, Jackson JSON, and Embedded Tomcat.
- `spring-boot-starter-data-jpa`: Pulls Hibernate ORM, Spring Data, and the HikariCP connection pool.
- `spring-boot-starter-security`: Pulls Spring Security core, OAuth2 libraries, and the servlet filter infrastructure.

##### 3. Automatic Configuration (`@SpringBootApplication`)

When your Spring Boot application boots up, it inspects your classpath. If it finds `postgresql.jar` and `spring-boot-starter-data-jpa`, it automatically constructs a PostgreSQL `DataSource` bean and sets up Hibernate!

The main application class combines three critical annotations into one:

The following class is the standard entry point for every Spring Boot application:

```java
package com.example.demo;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

// @SpringBootApplication combines:
// 1. @Configuration: Allows registering extra beans
// 2. @EnableAutoConfiguration: Starts Spring Boot's automatic configuration engine
// 3. @ComponentScan: Scans this package and all child subpackages for @Component, @Service, etc.
@SpringBootApplication
public class DemoApplication {

    public static void main(String[] args) {
        // Launches embedded Tomcat, creates ApplicationContext, and boots the application!
        SpringApplication.run(DemoApplication.class, args);
    }
}
```

##### Standard Spring Boot Directory Layout

A production-grade Spring Boot project follows Maven's standardized directory layout:

```text
my-ecommerce-project/
├── pom.xml                               <-- Maven dependencies and build plugins
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/example/ecommerce/
│   │   │       ├── EcommerceApplication.java  <-- Main @SpringBootApplication entry point
│   │   │       ├── controller/                <-- Presentation Layer (@RestController)
│   │   │       ├── service/                   <-- Business Logic Layer (@Service)
│   │   │       ├── repository/                <-- Persistence Layer (@Repository)
│   │   │       ├── model/                     <-- Domain Entities and Java Records
│   │   │       └── config/                    <-- @Configuration classes
│   │   └── resources/
│   │       ├── application.yml           <-- Application configuration properties
│   │       ├── static/                   <-- Static web assets (HTML, CSS, JS)
│   │       └── templates/                <-- Server-rendered templates (Thymeleaf)
│   └── test/
│       └── java/
│           └── com/example/ecommerce/
│               └── EcommerceApplicationTests.java <-- Automated integration test suite
```

---

### 0.5.1 How Auto-Configuration Actually Works Under the Hood

The greatest breakthrough of Spring Boot is **Opinionated Auto-Configuration**. But to junior developers, it often feels like an unpredictable "black box". Let us open the engine and examine every gear.

#### The Core Mechanism: The Imports Registry

When `@SpringBootApplication` executes, it triggers `@EnableAutoConfiguration`. 

In Spring Boot 1.x and 2.x, auto-configuration classes were registered in `META-INF/spring.factories`. 
In **Spring Boot 3.0+**, this mechanism was modernized to use a dedicated imports file:
```text
META-INF/spring/org.springframework.boot.autoconfigure.AutoConfiguration.imports
```

Inside `spring-boot-autoconfigure.jar`, this file contains a plain-text list of over 140 pre-packaged `@Configuration` classes, such as:
- `org.springframework.boot.autoconfigure.web.servlet.DispatcherServletAutoConfiguration`
- `org.springframework.boot.autoconfigure.jdbc.DataSourceAutoConfiguration`
- `org.springframework.boot.autoconfigure.orm.jpa.HibernateJpaAutoConfiguration`
- `org.springframework.boot.autoconfigure.security.servlet.SecurityAutoConfiguration`

#### The Gatekeepers: Conditional Annotations

Spring Boot does not blindly instantiate all 140 configurations! That would bloat startup time and consume gigabytes of RAM.
Instead, every auto-configuration class is guarded by a battery of **Conditional Annotations**:

```mermaid
flowchart TD
    Boot["Spring Boot Starts Up"] --> Read["Reads AutoConfiguration.imports"]
    Read --> Loop["Inspects each Candidate AutoConfiguration Class"]
    
    Loop --> Cond1{"@ConditionalOnClass?\nIs the library JAR on classpath?"}
    Cond1 -- NO --> Skip["SKIP: Do not create beans"]
    Cond1 -- YES --> Cond2{"@ConditionalOnMissingBean?\nHas user already declared custom bean?"}
    
    Cond2 -- NO (User provided bean) --> Backoff["BACK OFF: Respect user's custom bean!"]
    Cond2 -- YES (No user bean exists) --> Cond3{"@ConditionalOnProperty?\nIs feature enabled in application.yml?"}
    
    Cond3 -- NO --> Skip
    Cond3 -- YES --> Create["INSTANTIATE: Register default Spring Boot Bean!"]
```

#### The Master Conditionals Cheatsheet

| Annotation | What It Checks | Real-World Example |
| :--- | :--- | :--- |
| **`@ConditionalOnClass`** | Passes only if specified `.class` files exist on the JVM classpath. | If `DataSource.class` and `HikariDataSource.class` exist in JARs, prepare database pool! |
| **`@ConditionalOnMissingClass`** | Passes only if a class is **not** on the classpath. | Useful for fallback implementations when an optional library is omitted. |
| **`@ConditionalOnBean`** | Passes only if a specific Spring Bean is already in the `ApplicationContext`. | Create `FlywayMigrationInitializer` only if a `Flyway` bean exists. |
| **`@ConditionalOnMissingBean`** | Passes only if the user has **not** defined their own bean. **This is why Spring Boot never gets in your way!** | Spring provides a default `ObjectMapper` or `SecurityFilterChain` *only* if you didn't write your own `@Bean`. |
| **`@ConditionalOnProperty`** | Passes only if a configuration property matches in `application.yml`. | Enable caching only if `spring.cache.type != none`. |
| **`@ConditionalOnWebApplication`** | Passes only if running inside a Servlet or Reactive web environment. | Only spin up Tomcat if this is a web application. |

#### Real Code Anatomy: How `DataSourceAutoConfiguration` Works

Here is a simplified look at how Spring Boot automatically configures your database:

```java
@AutoConfiguration
@ConditionalOnClass({ DataSource.class, EmbeddedDatabaseType.class }) // 1. Only if JDBC classes are on classpath
@EnableConfigurationProperties(DataSourceProperties.class)           // 2. Bind spring.datasource.* properties
public class DataSourceAutoConfiguration {

    @Configuration(proxyBeanMethods = false)
    @ConditionalOnMissingBean(DataSource.class)                      // 3. User has NOT defined their own DataSource
    static class PooledDataSourceConfiguration {

        @Bean
        @ConditionalOnClass(HikariDataSource.class)                  // 4. HikariCP is on classpath!
        @ConditionalOnProperty(name = "spring.datasource.type", 
                               havingValue = "com.zaxxer.hikari.HikariDataSource", 
                               matchIfMissing = true)                // 5. Default choice if unspecified
        public HikariDataSource dataSource(DataSourceProperties properties) {
            return properties.initializeDataSourceBuilder().type(HikariDataSource.class).build();
        }
    }
}
```

> [!TIP]
> **How to Peek Behind the Curtain in Any Project**:
> Add `--debug` when running your application:
> ```bash
> ./mvnw spring-boot:run -Dspring-boot.run.arguments="--debug"
> ```
> Spring Boot will print the **CONDITIONS EVALUATION REPORT**, displaying every single bean that was created, every condition that passed, and every condition that backed off!

---

# Part 1: Web Applications and Microservices

Distributed web systems exchange state across networks using standardized protocols. Understanding how to build resilient, secure, observable services requires mastering the client-server request pipeline, authentication filters, metrics instrumentation, and distributed cloud routing patterns.

---

## Chapter 1: Building RESTful APIs

A RESTful web service exposes domain resources through uniform HTTP endpoints. Before writing complex enterprise controllers, a developer must understand how computers exchange data across networks, how data serializes into text formats like JSON, and how Spring Boot automates the servlet pipeline starting from the simplest single-line endpoint.

### 1.0 Foundations of Web Communication & The Simplest Spring Web App

Every web application relies on networking fundamentals. Before writing controller code, let us define the core networking primitives that make web communication possible.

#### Understanding Ports, TCP Sockets, and HTTP

When two computers communicate over the internet or a local network, they operate across layers of networking protocols:

- **IP Address**: The unique numeric address identifying a physical or virtual machine on a network (e.g., `192.168.1.1` or `127.0.0.1` for local machine).
- **Network Port**: A 16-bit number (from 0 to 65535) that directs incoming network packets to a specific software program running on that machine. For example, web servers commonly listen on port `80` (HTTP), `443` (HTTPS), or `8080` (standard Spring Boot local development).
- **TCP Socket**: A two-way software communication endpoint. When a client establishes a connection to a server port over the Transmission Control Protocol (TCP), an open socket is created that allows streams of bytes to travel reliably in both directions.
- **HTTP (HyperText Transfer Protocol)**: A human-readable, text-based request-and-response protocol that operates on top of a TCP socket. Clients send an HTTP request message, and servers reply with an HTTP response message.

#### Building the Simplest Spring Web Application ("Hello, World!")

To build a web application in Spring Boot, you add the `spring-boot-starter-web` dependency to your Maven `pom.xml`. This single dependency pulls in Spring MVC, Jackson JSON, and an embedded Apache Tomcat web server.

The following controller is the absolute simplest web endpoint you can write in Spring Boot:

```java
package com.example.demo.api;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

// @RestController tells Spring:
// 1. This class is a web component managed by the Spring IoC container.
// 2. The return value of every method should be written directly to the HTTP response body!
@RestController
public class HelloWorldController {

    // @GetMapping("/hello") maps HTTP GET requests for the path "/hello" to this method
    @GetMapping("/hello")
    public String sayHello() {
        return "Hello, World!";
    }
}
```

#### What Happens When You Run This Code?

When you start your Spring Boot application and navigate to `http://localhost:8080/hello` in your web browser, the following sequence occurs automatically:

1. **Embedded Tomcat Starts**: Spring Boot automatically starts an internal Apache Tomcat server listening on port `8080`.
2. **Browser Sends Request**: Your browser establishes a TCP socket connection to `localhost:8080` and sends a plain text HTTP request:
   ```text
   GET /hello HTTP/1.1
   Host: localhost:8080
   User-Agent: Mozilla/5.0...
   Accept: text/html,application/xhtml+xml...
   ```
3. **`DispatcherServlet` Intercepts**: Tomcat accepts the TCP socket, wraps the raw text into an `HttpServletRequest` object, and hands it to Spring MVC's central front controller, the `DispatcherServlet`.
4. **`HandlerMapping` Finds Match**: `DispatcherServlet` inspects the URL path (`/hello`) and HTTP verb (`GET`). It checks registered controllers and finds `HelloWorldController.sayHello()`.
5. **Method Executes**: Spring invokes `sayHello()`, which returns the Java string `"Hello, World!"`.
6. **Response Written**: Because the class is annotated with `@RestController`, Spring writes an HTTP response:
   ```text
   HTTP/1.1 200 OK
   Content-Type: text/plain;charset=UTF-8
   Content-Length: 13

   Hello, World!
   ```
7. **Browser Renders**: Your browser receives the bytes and displays "Hello, World!" on your screen.

#### URLs, URIs, and HTTP Verbs: Safe vs Idempotent Operations

In web communication, addresses and methods have precise semantic definitions.

##### What is the Difference Between a URI and a URL?

Every resource exposed on the web is addressed using standard identifiers with specific scoping rules:

- **URI (Uniform Resource Identifier)**: The generic name for all identifiers that name or locate a resource. For example, `/api/v1/products/42` is a URI identifying product number 42.
- **URL (Uniform Resource Locator)**: A specific type of URI that also specifies the network location and protocol to fetch the resource (e.g., `https://api.example.com/api/v1/products/42`).

##### HTTP Method Semantics: Safety and Idempotency

HTTP defines specific semantic rules for each request method:

| HTTP Verb | Action | Safe? | Idempotent? | Typical Success Status Code |
| :--- | :--- | :--- | :--- | :--- |
| `GET` | Read resource representation | **Yes** | **Yes** | `200 OK` |
| `POST` | Create resource or process operation | **No** | **No** | `201 Created` / `200 OK` |
| `PUT` | Replace entire resource representation | **No** | **Yes** | `200 OK` / `204 No Content` |
| `PATCH` | Partially update resource fields | **No** | **No** (usually) | `200 OK` / `204 No Content` |
| `DELETE` | Remove target resource | **No** | **Yes** | `204 No Content` / `200 OK` |

- **Safe Methods (`GET`, `HEAD`)**: Calling a safe method does not modify the state of the resource on the server. Because `GET` requests never mutate state, web browsers and Content Delivery Networks (CDNs) can safely cache them indefinitely to save bandwidth.
- **Idempotent Methods (`GET`, `PUT`, `DELETE`)**: Making $N$ identical requests produces the exact same server-side outcome as making a single request. If a network timeout occurs after sending a `PUT` or `DELETE` request, the client can safely retry the request without creating duplicate records or corrupting database state.
- **Non-Idempotent Methods (`POST`)**: If a client sends `POST /api/v1/orders` twice due to a network blip, the server will create two separate orders and charge the customer twice unless an idempotency key is implemented.

---

### 1.0.1 The Web Request Lifecycle: DispatcherServlet Under the Hood

To truly master Spring Boot web development, you must understand the **Front Controller Design Pattern** implemented by Spring MVC's **`DispatcherServlet`**.

Every single HTTP request sent to a Spring Boot web application passes through a carefully orchestrated pipeline:

```mermaid
sequenceDiagram
    autonumber
    actor Client as HTTP Client (Browser / App)
    participant Tomcat as Embedded Tomcat & Servlet Filters
    participant DS as DispatcherServlet (Front Controller)
    participant HM as HandlerMapping
    participant HA as HandlerAdapter
    participant AR as HandlerMethodArgumentResolver
    participant Controller as Your @RestController
    participant MC as HttpMessageConverter (Jackson)

    Client->>Tomcat: TCP HTTP Request (e.g., POST /api/v1/orders)
    Tomcat->>Tomcat: Passes through FilterChain (Security, CORS, Logging)
    Tomcat->>DS: Delegates to DispatcherServlet.doDispatch()
    
    DS->>HM: getHandler(request): Who can handle "/api/v1/orders"?
    HM-->>DS: Returns HandlerExecutionChain (Controller method + Interceptors)
    
    DS->>HA: getHandlerAdapter(handler)
    Note over DS,HA: Pre-Handle Interceptors Execute
    
    HA->>AR: Resolve method parameters (@PathVariable, @RequestBody, @Valid)
    AR->>MC: Read HTTP body JSON -> Deserialize to Java Record / DTO
    MC-->>AR: Java Object Instantiated
    
    HA->>Controller: Invokes yourControllerMethod(orderDto)
    Controller-->>HA: Returns ResponseEntity<OrderResponseDto>
    
    HA->>MC: Write Object -> Serialize Java Record to JSON bytes
    MC-->>DS: Response Body Formatted (Content-Type: application/json)
    
    Note over DS: Post-Handle & After-Completion Interceptors Execute
    DS-->>Tomcat: HttpServletResponse populated
    Tomcat-->>Client: Returns HTTP 201 Created + JSON payload
```

#### The 5 Pillars of the Spring MVC Request Pipeline:

1. **`DispatcherServlet` (The Air Traffic Controller)**:
   The central front controller. It doesn't perform business logic itself; instead, it coordinates the entire request processing lifecycle, querying specialized components to map, adapt, execute, and render responses.
2. **`HandlerMapping` (The Directory Lookup)**:
   Maintains a lookup table of URL patterns, HTTP verbs, and headers mapped to controller methods. Spring's default `RequestMappingHandlerMapping` scans all `@RestController` and `@RequestMapping` classes at application boot time to build this routing table.
3. **`HandlerAdapter` & `HandlerMethodArgumentResolver` (The Translator)**:
   Java methods have custom signatures: parameters annotated with `@PathVariable`, `@RequestParam`, `@RequestBody`, or `@RequestHeader`. The `HandlerAdapter` iterates over registered `HandlerMethodArgumentResolver` implementations to extract and convert raw HTTP data into strongly typed Java arguments.
4. **`HttpMessageConverter` (The Serializer / Deserializer)**:
   The workhorse responsible for converting between HTTP body byte streams and Java objects. For JSON APIs, `MappingJackson2HttpMessageConverter` reads incoming JSON text and parses it into Java records or entities, and formats outgoing Java return values back into JSON strings.
5. **`HandlerInterceptor` (The Cross-Cutting Guardrail)**:
   Provides hooks to intercept requests **before** (`preHandle`), **after** (`postHandle`), and **upon completion** (`afterCompletion`). Unlike Servlet Filters (which operate at the low-level Tomcat container level), Interceptors have full access to Spring's `ApplicationContext` and the specific controller `HandlerMethod`.

---

### 1.1 Accepting Inputs: Path Variables, Query Parameters, and Headers

A static "Hello World" endpoint is not useful for real business applications. Controllers must accept dynamic input data from incoming HTTP requests.

#### Method 1: Dynamic Path Variables (`@PathVariable`)

A **Path Variable** captures dynamic values embedded directly inside the URL path template (e.g., `/users/{userId}`).

The following controller demonstrates extracting dynamic path variables with automatic type conversion:

```java
package com.example.demo.api;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class UserGreetingController {

    // The template segment '{username}' is dynamic.
    // When a user requests GET /greet/alice, Spring extracts "alice" and passes it to the method!
    @GetMapping("/greet/{username}")
    public String greetUser(@PathVariable String username) {
        return "Welcome back, " + username + "!";
    }

    // Spring automatically converts String path segments to numeric primitives (Long, Integer)!
    // Handles GET /users/42/badges/7
    @GetMapping("/users/{userId}/badges/{badgeId}")
    public String getUserBadge(@PathVariable Long userId, @PathVariable Integer badgeId) {
        return "User ID: " + userId + " owns Badge ID: " + badgeId;
    }
}
```

#### Method 2: Query Parameters (`@RequestParam`)

A **Query Parameter** captures key-value pairs following the `?` question mark in a URL (e.g., `/search?query=java&page=1&size=20`). Query parameters are ideal for optional filtering, pagination, and sorting.

The following controller demonstrates optional query parameters, default values, and required checks:

```java
package com.example.demo.api;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class SearchController {

    // Handles GET /search?keyword=keyboard&page=0&limit=10
    @GetMapping("/search")
    public String searchProducts(
            // required = false makes this parameter optional; if omitted, 'keyword' is null
            @RequestParam(required = false) String keyword,

            // defaultValue ensures that if the client omits 'page', it defaults to "0"
            @RequestParam(defaultValue = "0") int page,

            // defaultValue ensures that if the client omits 'limit', it defaults to "20"
            @RequestParam(defaultValue = "20") int limit) {

        return "Searching for: " + keyword + " | Page: " + page + " | Limit: " + limit;
    }
}
```

#### Method 3: HTTP Request Headers (`@RequestHeader`)

HTTP headers transmit metadata about the request, such as authorization tokens, accepted languages, or custom tenant identifiers.

The following method demonstrates reading HTTP headers with fallbacks:

```java
package com.example.demo.api;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestHeader;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class HeaderInspectionController {

    // Handles GET /api/tenant-info with custom header X-Tenant-Id
    @GetMapping("/api/tenant-info")
    public String getTenantInfo(
            // Required header: if client omits X-Tenant-Id, Spring returns 400 Bad Request
            @RequestHeader("X-Tenant-Id") String tenantId,

            // Optional header with a default fallback
            @RequestHeader(value = "Accept-Language", defaultValue = "en-US") String language) {

        return "Active Tenant: " + tenantId + " | Language: " + language;
    }
}
```

---

### 1.2 Data Serialization, Deserialization, DTOs & Jackson Deep Dive

A web application spends a huge amount of time translating between **JSON text on the network** and **Java objects in JVM memory**.

#### What is Serialization and Deserialization?

At its core, web communication requires converting in-memory Java runtime data structures into wire-transferable text formats and vice-versa:

- **Serialization (Marshalling)**: Converting a live Java in-memory object into a byte sequence or string format (JSON) that can be transmitted across the network:
  `Java Object (Heap)` $\rightarrow$ `JSON Text: {"title":"Desk","price":99.0}`
- **Deserialization (Unmarshalling)**: Converting incoming JSON text from an HTTP request body into a strongly-typed Java object in memory:
  `JSON Text: {"title":"Desk","price":99.0}` $\rightarrow$ `Java CreateProductRequest Record`

Spring Boot delegates this entire translation process to **Jackson**, the industry-standard JSON library for Java.

#### The DTO Pattern: Why You Must NEVER Expose JPA Entities to REST APIs

A common beginner mistake is using `@Entity` classes directly inside `@RestController` methods:

```java
// DANGEROUS ANTI-PATTERN: Exposing JPA entities directly in controllers!
@PostMapping
public User saveUser(@RequestBody User userEntity) { 
    return userRepository.save(userEntity); 
}
```

Here are the three critical reasons why professional engineers **never** expose JPA entities directly to the web layer:

1. **Mass Assignment / Over-Posting Security Vulnerability**: If your `User` entity has an `isAdmin` or `balance` field, a malicious client can simply include `{"isAdmin": true}` in their JSON body. If you bind directly to the entity, Spring sets `isAdmin = true` on the database record!
2. **Infinite Recursion Crash (`StackOverflowError`)**: If you have a bidirectional JPA relationship (`Category` has many `Product`s, and `Product` has one `Category`), Jackson tries to serialize the category, which serializes its products, which serializes the category... in an infinite loop until the JVM crashes with `StackOverflowError`!
3. **API Contract Stability**: Your database tables change constantly (adding audit columns, changing data types, normalizing tables). If your database changes force breaking changes on mobile apps and frontends, your API contract is fragile. DTOs decouple internal database schemas from public API contracts.

#### Java 17 Records: The Ultimate DTOs

In modern Java, **Records** are the perfect choice for DTOs:
- **Immutable**: All fields are `private final` by default, preventing accidental mutation.
- **Zero Boilerplate**: The compiler automatically generates the canonical constructor, getters (`title()`, `price()`), `equals()`, `hashCode()`, and `toString()`. No Lombok required!

The following code defines clean read and write DTOs using Java Records:

```java
package com.example.demo.api.dto;

import jakarta.validation.constraints.NotBlank;
import jakarta.validation.constraints.Positive;

// 1. Read DTO: What we send back to the client
public record ProductResponse(
    Long id,
    String title,
    double price
) {}

// 2. Write DTO: What we accept from the client
public record CreateProductRequest(
    @NotBlank(message = "Title cannot be blank")
    String title,

    @Positive(message = "Price must be strictly positive")
    double price
) {}
```

#### The Essential Jackson Annotations Cheat Sheet

Jackson provides powerful annotations to customize how Java fields map to JSON keys:

| Annotation | Purpose | Example |
| :--- | :--- | :--- |
| `@JsonProperty("custom_key")` | Maps a Java field to a different JSON key name. | `@JsonProperty("unit_price") double price` |
| `@JsonIgnore` | Completely hides a field from JSON serialization (e.g., passwords). | `@JsonIgnore String passwordHash` |
| `@JsonInclude(Include.NON_NULL)` | Omits the field from JSON output if its value is `null`. | `@JsonInclude(JsonInclude.Include.NON_NULL)` |
| `@JsonFormat(pattern = "...")` | Formats dates and timestamps into readable strings. | `@JsonFormat(pattern = "yyyy-MM-dd HH:mm:ss")` |
| `@JsonNaming(...)` | Automatically converts camelCase fields to snake_case. | `@JsonNaming(PropertyNamingStrategies.SnakeCaseStrategy.class)` |

The following DTO demonstrates how Jackson annotations customize JSON output:

```java
package com.example.demo.api.dto;

import com.fasterxml.jackson.annotation.JsonFormat;
import com.fasterxml.jackson.annotation.JsonIgnore;
import com.fasterxml.jackson.annotation.JsonInclude;
import com.fasterxml.jackson.annotation.JsonProperty;

import java.time.Instant;

@JsonInclude(JsonInclude.Include.NON_NULL) // Skips null fields in JSON response
public record DetailedProductResponse(
    Long id,

    @JsonProperty("product_name") // Appears as "product_name" in JSON
    String title,

    double price,

    @JsonIgnore // NEVER serialized to JSON: keeps internal data private
    String internalSupplierCost,

    @JsonFormat(pattern = "yyyy-MM-dd'T'HH:mm:ss'Z'", timezone = "UTC")
    Instant createdAt
) {}
```

#### Working with Jackson `ObjectMapper` Programmatically

While Spring Boot automatically handles JSON conversion behind the scenes in `@RestController`, you will frequently need to serialize or deserialize JSON manually (e.g., when calling external APIs, processing Kafka messages, or writing tests).

Spring Boot auto-configures a singleton `ObjectMapper` bean:

The following service demonstrates the four most important `ObjectMapper` methods:

```java
package com.example.demo.service;

import com.example.demo.api.dto.ProductResponse;
import com.fasterxml.jackson.core.JsonProcessingException;
import com.fasterxml.jackson.databind.JsonNode;
import com.fasterxml.jackson.databind.ObjectMapper;
import org.springframework.stereotype.Service;

@Service
public class JacksonUtilityService {

    private final ObjectMapper objectMapper;

    public JacksonUtilityService(ObjectMapper objectMapper) {
        this.objectMapper = objectMapper;
    }

    // 1. writeValueAsString(): Convert Java Object -> JSON String
    public String toJsonString(ProductResponse product) throws JsonProcessingException {
        return objectMapper.writeValueAsString(product);
        // Result: "{\"id\":1,\"title\":\"Keyboard\",\"price\":129.99}"
    }

    // 2. readValue(): Convert JSON String -> Java Object
    public ProductResponse fromJsonString(String jsonText) throws JsonProcessingException {
        return objectMapper.readValue(jsonText, ProductResponse.class);
    }

    // 3. readTree(): Inspect dynamic JSON without a dedicated Java class
    public String extractTitleFromArbitraryJson(String jsonText) throws JsonProcessingException {
        JsonNode rootNode = objectMapper.readTree(jsonText);
        // Navigate through JSON hierarchy safely
        return rootNode.path("title").asText("Default Title");
    }

    // 4. convertValue(): Transform one Java object type to another (e.g., Map to Record)
    public ProductResponse convertMapToRecord(java.util.Map<String, Object> map) {
        return objectMapper.convertValue(map, ProductResponse.class);
    }
}
```

---

### 1.3 Complete CRUD Operations in Practice

Let us build a complete, real-world CRUD controller demonstrating proper HTTP status codes, validation, dynamic location headers, and partial updates.

#### Full Implementation: Product CRUD Controller

The following controller demonstrates all standard REST operations:

```java
package com.example.demo.api;

import com.example.demo.api.dto.CreateProductRequest;
import com.example.demo.api.dto.ProductResponse;
import jakarta.validation.Valid;
import jakarta.validation.constraints.Positive;
import org.springframework.http.HttpStatus;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.*;
import org.springframework.web.servlet.support.ServletUriComponentsBuilder;

import java.net.URI;
import java.util.*;
import java.util.concurrent.ConcurrentHashMap;
import java.util.concurrent.atomic.AtomicLong;

@RestController
@RequestMapping("/api/v1/products") // Base URI for all operations in this controller
public class ProductCrudController {

    // In-memory data store for demonstration
    private final Map<Long, ProductResponse> productStore = new ConcurrentHashMap<>();
    private final AtomicLong idSequence = new AtomicLong(100);

    public ProductCrudController() {
        productStore.put(1L, new ProductResponse(1L, "Mechanical Keyboard", 129.99));
        productStore.put(2L, new ProductResponse(2L, "Wireless Mouse", 59.95));
    }

    // 1. READ ALL (Paginated and Filtered): GET /api/v1/products?keyword=key&limit=10
    @GetMapping
    public ResponseEntity<List<ProductResponse>> listProducts(
            @RequestParam(required = false) String keyword,
            @RequestParam(defaultValue = "0") int page,
            @RequestParam(defaultValue = "20") int limit) {

        List<ProductResponse> results = productStore.values().stream()
                .filter(p -> keyword == null || p.title().toLowerCase().contains(keyword.toLowerCase()))
                .skip((long) page * limit)
                .limit(limit)
                .toList();

        return ResponseEntity.ok(results); // HTTP 200 OK
    }

    // 2. READ BY ID: GET /api/v1/products/{id}
    @GetMapping("/{id}")
    public ResponseEntity<ProductResponse> getProductById(@PathVariable Long id) {
        ProductResponse product = productStore.get(id);
        if (product == null) {
            return ResponseEntity.notFound().build(); // HTTP 404 Not Found
        }
        return ResponseEntity.ok(product); // HTTP 200 OK
    }

    // 3. CREATE: POST /api/v1/products
    @PostMapping
    public ResponseEntity<ProductResponse> createProduct(@Valid @RequestBody CreateProductRequest request) {
        Long newId = idSequence.incrementAndGet();
        ProductResponse created = new ProductResponse(newId, request.title(), request.price());
        productStore.put(newId, created);

        // Standard REST requirement: Return HTTP 201 Created with Location header pointing to new resource
        URI location = ServletUriComponentsBuilder.fromCurrentRequest()
                .path("/{id}")
                .buildAndExpand(newId)
                .toUri();

        return ResponseEntity.created(location).body(created); // HTTP 201 Created + Location header
    }

    // 4. FULL UPDATE (Replace): PUT /api/v1/products/{id}
    @PutMapping("/{id}")
    public ResponseEntity<ProductResponse> replaceProduct(
            @PathVariable Long id,
            @Valid @RequestBody CreateProductRequest request) {

        if (!productStore.containsKey(id)) {
            return ResponseEntity.notFound().build(); // HTTP 404 Not Found
        }

        ProductResponse replaced = new ProductResponse(id, request.title(), request.price());
        productStore.put(id, replaced);
        return ResponseEntity.ok(replaced); // HTTP 200 OK
    }

    // 5. PARTIAL UPDATE: PATCH /api/v1/products/{id}/price
    @PatchMapping("/{id}/price")
    public ResponseEntity<ProductResponse> updatePrice(
            @PathVariable Long id,
            @RequestParam @Positive(message = "Price must be strictly positive") double newPrice) {

        ProductResponse existing = productStore.get(id);
        if (existing == null) {
            return ResponseEntity.notFound().build();
        }

        ProductResponse updated = new ProductResponse(existing.id(), existing.title(), newPrice);
        productStore.put(id, updated);
        return ResponseEntity.ok(updated); // HTTP 200 OK
    }

    // 6. DELETE: DELETE /api/v1/products/{id}
    @DeleteMapping("/{id}")
    @ResponseStatus(HttpStatus.NO_CONTENT) // HTTP 204 No Content
    public void deleteProduct(@PathVariable Long id) {
        // Idempotent: deleting an already-deleted ID produces no error
        productStore.remove(id);
    }
}
```

---

### 1.4 Input Validation & Global Exception Handling with RFC 7807

Production services must strictly validate input payloads and return informative, standardized error responses.

#### Step 1: Adding the Validation Starter

To enable Bean Validation annotations, add the starter to your Maven `pom.xml`:

```xml
<!-- Jakarta Bean Validation implementation (Hibernate Validator) -->
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-validation</artifactId>
</dependency>
```

#### Step 2: What is RFC 7807 Problem Details?

Prior to Spring Boot 3, every development team formatted error responses differently:
- Team A returned: `{"error": "Invalid price"}`
- Team B returned: `{"statusCode": 400, "message": "Failed validation"}`

In 2016, the Internet Engineering Task Force (IETF) created **RFC 7807: Problem Details for HTTP APIs** to establish a universal JSON schema for reporting machine-readable errors. Spring Boot 3 provides native support via the `ProblemDetail` class:

```json
{
  "type": "https://api.example.com/errors/validation",
  "title": "Invalid Request Content",
  "status": 400,
  "detail": "Input validation failed on 1 field(s)",
  "instance": "/api/v1/products",
  "timestamp": "2026-10-27T12:00:00Z",
  "invalidParams": {
    "price": "Price must be strictly greater than zero"
  }
}
```

#### Step 3: Implementing `@RestControllerAdvice`

The `@RestControllerAdvice` annotation designates a class as a global interceptor for uncaught exceptions thrown by any controller:

The following class intercepts validation failures and missing resources, formatting them into RFC 7807 payloads:

```java
package com.example.demo.api.exception;

import org.springframework.http.HttpStatus;
import org.springframework.http.ProblemDetail;
import org.springframework.validation.FieldError;
import org.springframework.web.bind.MethodArgumentNotValidException;
import org.springframework.web.bind.annotation.ExceptionHandler;
import org.springframework.web.bind.annotation.RestControllerAdvice;

import java.net.URI;
import java.time.Instant;
import java.util.HashMap;
import java.util.Map;
import java.util.NoSuchElementException;

@RestControllerAdvice // Applies globally to all @RestController classes
public class GlobalApiExceptionHandler {

    // 1. Intercepts Spring Bean Validation errors triggered by @Valid
    @ExceptionHandler(MethodArgumentNotValidException.class)
    public ProblemDetail handleValidationException(MethodArgumentNotValidException ex) {
        // Create standard RFC 7807 ProblemDetail object with HTTP 400 Bad Request
        ProblemDetail problem = ProblemDetail.forStatusAndDetail(
                HttpStatus.BAD_REQUEST,
                "Request payload failed validation checks"
        );
        problem.setTitle("Validation Failure");
        problem.setType(URI.create("https://api.example.com/errors/validation"));
        problem.setProperty("timestamp", Instant.now());

        // Extract each invalid field and its validation error message
        Map<String, String> invalidFields = new HashMap<>();
        for (FieldError fieldError : ex.getBindingResult().getFieldErrors()) {
            invalidFields.put(fieldError.getField(), fieldError.getDefaultMessage());
        }
        // Attach custom properties to the RFC 7807 JSON output
        problem.setProperty("invalidParams", invalidFields);

        return problem;
    }

    // 2. Intercepts custom domain exception when a resource is missing
    @ExceptionHandler(NoSuchElementException.class)
    public ProblemDetail handleNotFoundException(NoSuchElementException ex) {
        ProblemDetail problem = ProblemDetail.forStatusAndDetail(
                HttpStatus.NOT_FOUND,
                ex.getMessage()
        );
        problem.setTitle("Resource Not Found");
        problem.setProperty("timestamp", Instant.now());
        return problem;
    }
}
```

---

### 1.5 Package Architecture Best Practices: Layer vs Feature

How you organize your project packages determines how easy your codebase is to navigate, maintain, and scale over time.

#### 1. Package-by-Layer (Classic Approach - Best for Small Apps)

In this layout, files are grouped by their technical role in the architectural stack (controllers with controllers, services with services, repositories with repositories):

```text
com.example.ecommerce/
├── EcommerceApplication.java
├── controller/
│   ├── ProductController.java
│   ├── OrderController.java
│   └── UserController.java
├── service/
│   ├── ProductService.java
│   ├── OrderService.java
│   └── UserService.java
├── repository/
│   ├── ProductRepository.java
│   ├── OrderRepository.java
│   └── UserRepository.java
└── model/
    ├── Product.java
    ├── Order.java
    └── User.java
```

*Trade-off*: Easy to understand for beginners, but as the app grows to 50+ classes, every business feature requires jumping across 4 different folders to find related files.

#### 2. Package-by-Feature (Modern Production Standard - Best for Scalability)

In this layout, all files related to a single business capability (e.g., `product`, `order`, `customer`) live together in the same package:

```text
com.example.ecommerce/
├── EcommerceApplication.java
├── common/                              <-- Shared cross-cutting concerns
│   ├── exception/
│   │   └── GlobalExceptionHandler.java  <-- RFC 7807 Error Handler
│   └── config/
│       ├── OpenApiConfig.java
│       └── SecurityConfig.java
├── product/                             <-- Everything related to Products!
│   ├── ProductController.java           <-- Web endpoint handler
│   ├── ProductService.java              <-- Business logic interface
│   ├── ProductServiceImpl.java          <-- Implementation
│   ├── ProductRepository.java           <-- Data persistence
│   ├── Product.java                     <-- JPA Entity
│   └── dto/
│       ├── ProductResponse.java         <-- Read Record DTO
│       ├── CreateProductRequest.java    <-- Write Record DTO
│       └── UpdateProductRequest.java
└── order/                               <-- Everything related to Orders!
    ├── OrderController.java
    ├── OrderService.java
    ├── OrderRepository.java
    └── dto/
```

*Advantage*: High cohesion. Everything related to `product` is in one place. Deleting or extracting the feature into a microservice later requires touching only one directory!

---

### 1.6 Custom DB Queries vs ORM Mapping (In Brief at Web Boundary)

At the boundary between your REST controllers, service layer, and database, beginners often wonder: *"Should I use Spring Data JPA or write custom SQL?"*

Here is the practical rule of thumb:

```mermaid
flowchart TD
    Request["Incoming Web Request"] --> Decision{"What does the endpoint do?"}
    Decision -->|"Standard CRUD / Single Item by ID"| JPA["Spring Data JPA (findById, save)"]
    Decision -->|"Domain Logic with Parent-Child Entities"| JPA
    Decision -->|"Multi-Table Analytics Dashboard / Complex Reporting"| SQL["Direct SQL via JdbcClient"]
    Decision -->|"High-Volume Bulk Updates (50,000 rows)"| SQL
```

- **Use Spring Data JPA (ORM)** when:
  - You are loading a single entity by ID, validating its fields, and modifying it.
  - You are persisting an aggregate parent with children (`Order` with `OrderItem`s).
  - You want automatic optimistic locking (`@Version`) and audit timestamps.
- **Use Direct SQL via `JdbcClient`** when:
  - You need to join 6 tables for an analytics dashboard and map the results to a flat DTO.
  - You need to update 10,000 records at once (`UPDATE items SET status = 'EXPIRED'`).
  - You need database-specific features (e.g. PostgreSQL `JSONB` or `DISTINCT ON`).

---

### 1.7 Living API Documentation with OpenAPI & Swagger UI

API documentation manually written in wikis quickly becomes outdated. SpringDoc OpenAPI generates living documentation by inspecting controller code at runtime.

#### Step 1: Adding the SpringDoc Dependency

Include the SpringDoc OpenAPI starter in `pom.xml`:

```xml
<!-- SpringDoc OpenAPI Starter with embedded Swagger UI -->
<dependency>
    <groupId>org.springdoc</groupId>
    <artifactId>springdoc-openapi-starter-webmvc-ui</artifactId>
    <version>2.5.0</version>
</dependency>
```

#### Step 2: Annotating Endpoints for Documentation

The following controller illustrates Swagger metadata annotations:

```java
package com.example.demo.api;

import com.example.demo.api.dto.ProductResponse;
import io.swagger.v3.oas.annotations.Operation;
import io.swagger.v3.oas.annotations.responses.ApiResponse;
import io.swagger.v3.oas.annotations.tags.Tag;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.*;

@Tag(name = "Products", description = "Operations for searching and managing product catalog items")
@RestController
@RequestMapping("/api/v1/documented-products")
public class DocumentedProductController {

    @Operation(summary = "Fetch product by ID", description = "Retrieves full product details. Returns 404 if ID does not exist.")
    @ApiResponse(responseCode = "200", description = "Product found and returned")
    @ApiResponse(responseCode = "404", description = "Product not found")
    @GetMapping("/{id}")
    public ResponseEntity<ProductResponse> getById(@PathVariable Long id) {
        return ResponseEntity.ok(new ProductResponse(id, "Sample", 49.99));
    }
}
```

Once started, open `http://localhost:8080/swagger-ui.html` in your web browser to interactively execute API requests.

---

### 1.8 Testing the Web Layer with `@WebMvcTest` and `MockMvc`

Testing controllers does not require starting a real HTTP server on a physical port. Spring Boot provides **test slicing** to test web handlers in isolation.

#### Testing Spectrum: `@SpringBootTest` vs `@WebMvcTest`

Spring Boot offers two primary levels of integration testing depending on whether you require full application context or isolated web layer execution:

- **`@SpringBootTest`**: Starts the entire application context (all services, repositories, database connection pools, security filters). Thorough but slow (takes several seconds to boot).
- **`@WebMvcTest`**: A specialized **test slice** that loads only web infrastructure (`DispatcherServlet`, `@RestController`, `@ControllerAdvice`, filters). It mocks all service beans, executing in milliseconds.

#### Complete Implementation: MockMvc Controller Test

The following JUnit 5 test verifies HTTP routing, validation rules, and JSON payloads in isolation:

```java
package com.example.demo.api;

import com.fasterxml.jackson.databind.ObjectMapper;
import org.junit.jupiter.api.DisplayName;
import org.junit.jupiter.api.Test;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.autoconfigure.web.servlet.WebMvcTest;
import org.springframework.http.MediaType;
import org.springframework.test.web.servlet.MockMvc;

// Static imports for fluent test assertions
import static org.springframework.test.web.servlet.request.MockMvcRequestBuilders.*;
import static org.springframework.test.web.servlet.result.MockMvcResultMatchers.*;

@WebMvcTest(ProductCrudController.class) // Slices context: loads ONLY ProductCrudController
class ProductControllerTest {

    @Autowired
    private MockMvc mockMvc; // Simulates HTTP requests without network sockets

    @Autowired
    private ObjectMapper objectMapper; // Serializes test objects to JSON strings

    @Test
    @DisplayName("GET /api/v1/products/1 returns HTTP 200 and expected JSON attributes")
    void shouldReturnProductById() throws Exception {
        mockMvc.perform(get("/api/v1/products/1")
                .accept(MediaType.APPLICATION_JSON))
                // Verify HTTP Status
                .andExpect(status().isOk())
                // Verify Content-Type Header
                .andExpect(content().contentType(MediaType.APPLICATION_JSON))
                // Verify JSON fields using JsonPath expressions
                .andExpect(jsonPath("$.id").value(1))
                .andExpect(jsonPath("$.title").value("Mechanical Keyboard"))
                .andExpect(jsonPath("$.price").value(129.99));
    }

    @Test
    @DisplayName("POST /api/v1/products with negative price returns HTTP 400 Bad Request")
    void shouldRejectInvalidProductPayload() throws Exception {
        String invalidJsonPayload = """
                {
                  "title": "USB Cable",
                  "price": -15.50
                }
                """;

        mockMvc.perform(post("/api/v1/products")
                .contentType(MediaType.APPLICATION_JSON)
                .content(invalidJsonPayload))
                // Expect 400 Bad Request due to @Valid trigger
                .andExpect(status().isBadRequest())
                .andExpect(jsonPath("$.title").value("Validation Failure"))
                .andExpect(jsonPath("$.invalidParams.price").exists());
    }
}
```

---

### 1.9 Consuming Downstream APIs with `RestClient` and WireMock

Spring Boot 3.2 introduced `RestClient`, a synchronous HTTP client with a fluent, declarative API that replaces the older `RestTemplate`.

#### Why `RestClient` Over Legacy `RestTemplate`?

`RestTemplate` relied on overloaded methods with dozens of parameters, making header customization and status inspection cumbersome. `RestClient` provides a modern builder pattern:

The following service demonstrates consuming a downstream exchange rate service using `RestClient`:

```java
package com.example.demo.client;

import org.springframework.http.HttpStatusCode;
import org.springframework.stereotype.Service;
import org.springframework.web.client.RestClient;

// Response representation from downstream API
public record ExchangeRateDto(String currency, double rate) {}

@Service
public class CurrencyClientService {

    private final RestClient restClient;

    // RestClient.Builder is auto-configured by Spring Boot
    public CurrencyClientService(RestClient.Builder builder) {
        this.restClient = builder
                .baseUrl("https://api.exchangerate.host")
                .defaultHeader("Accept", "application/json")
                .build();
    }

    public ExchangeRateDto fetchRate(String symbol) {
        return restClient.get()
                .uri("/latest?base=USD&symbols={symbol}", symbol)
                .retrieve()
                // Handle 4xx client errors
                .onStatus(HttpStatusCode::is4xxClientError, (request, response) -> {
                    throw new RuntimeException("External client error: " + response.getStatusCode());
                })
                // Automatically deserializes JSON body into Java Record
                .body(ExchangeRateDto.class);
    }
}
```

#### Mocking Downstream APIs with WireMock

Automated integration tests should never make real HTTP calls to external third-party services like Stripe or Twilio. Network latency, rate limits, and outages cause builds to fail intermittently. WireMock runs an embedded HTTP server that stubs these endpoints:

The following integration test uses WireMock to test `CurrencyClientService` without touching external servers:

```java
package com.example.demo.client;

import com.github.tomakehurst.wiremock.junit5.WireMockTest;
import org.junit.jupiter.api.DisplayName;
import org.junit.jupiter.api.Test;
import org.springframework.web.client.RestClient;

// WireMock static matchers
import static com.github.tomakehurst.wiremock.client.WireMock.*;
import static org.junit.jupiter.api.Assertions.*;

@WireMockTest(httpPort = 8089) // Starts local WireMock server on port 8089
class CurrencyClientServiceTest {

    @Test
    @DisplayName("Successfully parses downstream currency JSON response from WireMock")
    void shouldFetchExchangeRate() {
        // 1. Arrange: Configure WireMock stub
        stubFor(get(urlEqualTo("/latest?base=USD&symbols=EUR"))
                .willReturn(aResponse()
                        .withHeader("Content-Type", "application/json")
                        .withStatus(200)
                        .withBody("""
                                {
                                  "currency": "EUR",
                                  "rate": 0.92
                                }
                                """)));

        // 2. Act: Point client to local WireMock port
        RestClient.Builder builder = RestClient.builder().baseUrl("http://localhost:8089");
        CurrencyClientService clientService = new CurrencyClientService(builder);
        ExchangeRateDto result = clientService.fetchRate("EUR");

        // 3. Assert: Verify parsed data
        assertNotNull(result);
        assertEquals("EUR", result.currency());
        assertEquals(0.92, result.rate());
    }
}
```

---

### 1.9.1 Modern Declarative HTTP Interfaces with `@HttpExchange`

While `RestClient` is great for programmatic HTTP calls, writing repetitive boilerplate methods for every downstream endpoint creates unnecessary code bloat. 

In older Spring Boot versions, teams had to pull in Netflix Feign or OpenFeign via Spring Cloud to get declarative HTTP clients.
In **Spring Framework 6 and Spring Boot 3.0+**, the Spring team introduced **native Declarative HTTP Interfaces** directly into the core framework!

#### The Mental Model: Spring Data for Remote HTTP APIs

Just as Spring Data JPA generates repository implementations automatically from a simple interface (`interface UserRepository extends JpaRepository`), Spring's HTTP Interface generates an entire REST client implementation at runtime from an annotated Java interface!

```mermaid
flowchart TD
    subgraph DeclarativeClient ["Modern Declarative HTTP Client Pipeline"]
        Interface["Java Interface\n(@HttpExchange, @GetExchange, @PostExchange)"]
        Factory["HttpServiceProxyFactory\n(backed by RestClient or WebClient)"]
        Proxy["Dynamic Spring Proxy Bean\n(Auto-generates HTTP calls, serializes JSON)"]
        Remote["Downstream Remote Microservice / Third-Party API"]
        
        Interface --> Factory
        Factory --> Proxy
        Proxy --> Remote
    end
```

#### The Client Evolution in Spring:

| Client Type | Introduced In | Programming Style | Status in Spring Boot 3.x |
| :--- | :--- | :--- | :--- |
| **`RestTemplate`** | Spring 3.0 (2009) | Template method pattern, heavy parameter overloading | **Maintenance Mode** (Deprecated for new code) |
| **`WebClient`** | Spring 5.0 (2017) | Reactive, non-blocking builder (requires WebFlux) | Active (Best for reactive / high concurrency) |
| **`RestClient`** | Spring Boot 3.2 | Fluent, synchronous, builder-based | **Recommended Standard** for imperative code |
| **`@HttpExchange`** | Spring Boot 3.0+ | **Declarative interface proxy** (zero implementation code) | **State-of-the-art** for clean microservice contracts |

#### Step 1: Define the Declarative Client Interface

Declare the HTTP contract as a clean Java interface using Spring's exchange annotations:

```java
package com.example.demo.client;

import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.RequestBody;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.service.annotation.*;

import java.util.List;

public record UserDto(Long id, String name, String email) {}
public record CreateUserRequest(String name, String email) {}

@HttpExchange("/api/v1/users") // Base path for all endpoints in this contract
public interface UserApiClient {

    @GetExchange
    List<UserDto> getAllUsers(@RequestParam(defaultValue = "1") int page);

    @GetExchange("/{id}")
    UserDto getUserById(@PathVariable("id") Long id);

    @PostExchange
    UserDto createUser(@RequestBody CreateUserRequest request);

    @DeleteExchange("/{id}")
    void deleteUser(@PathVariable("id") Long id);
}
```

#### Step 2: Register the Client Bean with `HttpServiceProxyFactory`

Configure a factory bean that wires `RestClient` into the dynamic proxy adapter:

```java
package com.example.demo.config;

import com.example.demo.client.UserApiClient;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.web.client.RestClient;
import org.springframework.web.client.support.RestClientAdapter;
import org.springframework.web.service.invoker.HttpServiceProxyFactory;

@Configuration
public class ClientInterfaceConfig {

    @Bean
    public UserApiClient userApiClient(
            RestClient.Builder restClientBuilder,
            @Value("${downstream.user-service.url:https://api.internal-users.com}") String baseUrl) {
        
        // 1. Build the underlying RestClient with base URL and default timeout headers
        RestClient restClient = restClientBuilder
                .baseUrl(baseUrl)
                .defaultHeader("Accept", "application/json")
                .defaultHeader("User-Agent", "SpringBoot3-Core-Client")
                .build();

        // 2. Wrap the RestClient in an HTTP Adapter
        RestClientAdapter adapter = RestClientAdapter.create(restClient);

        // 3. Build the HttpServiceProxyFactory using the adapter
        HttpServiceProxyFactory factory = HttpServiceProxyFactory.builderFor(adapter).build();

        // 4. Generate the dynamic proxy implementing our UserApiClient interface!
        return factory.createClient(UserApiClient.class);
    }
}
```

#### Step 3: Inject and Use Like Any Standard Spring Bean

In your service layer, inject `UserApiClient` just like any regular Spring `@Service` or `@Repository`:

```java
package com.example.demo.service;

import com.example.demo.client.UserApiClient;
import com.example.demo.client.UserDto;
import org.springframework.stereotype.Service;

@Service
public class OrderProcessingService {

    private final UserApiClient userApiClient;

    public OrderProcessingService(UserApiClient userApiClient) {
        this.userApiClient = userApiClient;
    }

    public void verifyCustomerEligibility(Long customerId) {
        // Zero HTTP boilerplate! Invokes GET /api/v1/users/{id} and maps JSON to UserDto!
        UserDto user = userApiClient.getUserById(customerId);
        System.out.println("Verified customer: " + user.name() + " (" + user.email() + ")");
    }
}
```

> [!TIP]
> **Why `@HttpExchange` Wins in Microservices**:
> You can package the `UserApiClient` interface and its DTO records into a lightweight shared Maven JAR (e.g., `user-api-contract.jar`). Other microservices simply include the contract JAR and configure the proxy bean in 5 lines of code, ensuring type-safe, contract-driven inter-service communication!

---

### 1.10 Real-Time Server Push: Server-Sent Events (SSE) with SseEmitter

Modern web applications require instantaneous updates: order status notifications, live stock quotes, sports tickers, or streaming token-by-token responses from generative AI models. 

#### What is Server-Sent Events (SSE)?

**Server-Sent Events (SSE)** is an open W3C standard that allows a server to push real-time event notifications to a web client over a standard persistent HTTP connection (`text/event-stream`).

Unlike standard REST requests where the server returns a response and terminates the socket, an SSE endpoint leaves the HTTP response socket open indefinitely, streaming discrete text payloads whenever an event occurs on the server.

```mermaid
sequenceDiagram
    autonumber
    participant Browser as Client Browser (JavaScript EventSource)
    participant Spring as Spring MVC (SseEmitter)
    participant Worker as Background Event / Service Layer

    Browser->>Spring: GET /api/v1/notifications/subscribe (Accept: text/event-stream)
    Note over Spring: Spring keeps HTTP socket open (HTTP 200 OK)
    Spring-->>Browser: Connection Established (Content-Type: text/event-stream)

    loop Event Broadcasts
        Worker->>Spring: send(NotificationEvent)
        Spring-->>Browser: data: {"id": 101, "message": "Order #482 Shipped!"}\n\n
    end

    loop Keep-Alive Heartbeat (Every 15s)
        Spring-->>Browser: :ping (comment line prevents proxy timeout)\n\n
    end

    alt Client Network Disconnects
        Browser->>Spring: Reconnects automatically with Header: Last-Event-ID: 101
    end
```

#### SSE vs WebSockets vs Polling: Architectural Comparison

Choosing the correct real-time protocol is critical to system scalability:

| Feature | Short Polling | Long Polling | Server-Sent Events (SSE) | WebSockets |
| :--- | :--- | :--- | :--- | :--- |
| **Communication Direction** | Client $\rightarrow$ Server | Client $\rightarrow$ Server | **Server $\rightarrow$ Client (Unidirectional)** | **Full Duplex (Bidirectional)** |
| **Underlying Protocol** | Standard HTTP/1.1 | Standard HTTP/1.1 | **Standard HTTP/1.1 or HTTP/2** | TCP Upgrade (`ws://` or `wss://`) |
| **Automatic Reconnection** | Manual (`setInterval`) | Manual loop | **Built into browser standard (`EventSource`)** | Manual JavaScript implementation |
| **Firewall / Proxy Friendly** | Yes | Yes | **Yes (Pure standard HTTP)** | Often blocked or requires special proxy config |
| **Server Overhead** | Very High (repeated handshakes) | Moderate | **Low (Single persistent HTTP socket)** | Low (Binary frame streaming) |
| **Best Use Cases** | Low-frequency checks | Legacy fallbacks | **Live notifications, stock updates, AI token streaming** | **Multiplayer gaming, collaborative editing, chat apps** |

> [!TIP]
> **Rule of Thumb**: If your clients only need to **receive** real-time updates from the server (e.g., "Your payment was processed", "Flight status updated"), **use SSE**. It runs over standard HTTP, avoids custom WebSocket handshake complexity, and comes with built-in browser reconnection logic!

---

#### How SseEmitter Works in Spring MVC

In standard Spring MVC, request threads are drawn from Tomcat's thread pool. If an endpoint left a thread blocked waiting for events, Tomcat's default 200 threads would be exhausted in seconds!

To solve this, Spring MVC uses **`SseEmitter`** (an implementation of asynchronous request processing). When a controller returns an `SseEmitter`:
1. Spring detaches the Tomcat worker thread and returns it to the pool immediately.
2. The underlying HTTP connection remains open in Tomcat's NIO non-blocking connector.
3. When your application calls `emitter.send()`, a lightweight thread writes the data frame to the client.
4. When the emitter completes or times out, the socket is cleanly closed.

---

#### Complete Production Implementation: Live Notification System

Here is a production-grade, thread-safe notification system supporting individual user subscriptions, topic broadcasting, and heartbeat keep-alives.

##### Step 1: The Notification Event DTO

```java
package com.example.demo.notification.dto;

import java.time.Instant;

public record NotificationDto(
        String id,
        String userId,
        String title,
        String message,
        Instant timestamp
) {}
```

##### Step 2: Thread-Safe `SseNotificationService`

This service manages active subscriber connections in a `ConcurrentHashMap`, handles lifecycle callbacks (`onCompletion`, `onTimeout`, `onError`), and sends periodic heartbeats to prevent intermediate proxies (Nginx, AWS ALB) from closing idle connections.

```java
package com.example.demo.notification.service;

import com.example.demo.notification.dto.NotificationDto;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.scheduling.annotation.Scheduled;
import org.springframework.stereotype.Service;
import org.springframework.web.servlet.mvc.method.annotation.SseEmitter;

import java.io.IOException;
import java.util.Map;
import java.util.concurrent.ConcurrentHashMap;
import java.util.concurrent.CopyOnWriteArrayList;

@Service
public class SseNotificationService {

    private static final Logger log = LoggerFactory.getLogger(SseNotificationService.class);

    // Timeout: 30 minutes in milliseconds (0L = indefinite, but not recommended in production)
    private static final Long EMITTER_TIMEOUT = 30 * 60 * 1000L;

    // Thread-safe map tracking multiple client tabs/connections per userId
    private final Map<String, CopyOnWriteArrayList<SseEmitter>> userEmitters = new ConcurrentHashMap<>();

    /**
     * Creates a new persistent SSE connection for a specific user.
     */
    public SseEmitter subscribe(String userId) {
        SseEmitter emitter = new SseEmitter(EMITTER_TIMEOUT);

        userEmitters.computeIfAbsent(userId, k -> new CopyOnWriteArrayList<>()).add(emitter);

        // Lifecycle cleanup callbacks
        emitter.onCompletion(() -> {
            log.info("SSE connection completed for user: {}", userId);
            removeEmitter(userId, emitter);
        });

        emitter.onTimeout(() -> {
            log.warn("SSE connection timed out for user: {}", userId);
            emitter.complete();
            removeEmitter(userId, emitter);
        });

        emitter.onError((ex) -> {
            log.error("SSE connection error for user: {}: {}", userId, ex.getMessage());
            removeEmitter(userId, emitter);
        });

        // Send an initial handshake event so client knows connection succeeded
        try {
            emitter.send(SseEmitter.event()
                    .name("INIT")
                    .id("init-" + System.currentTimeMillis())
                    .data("Connected to live notification stream"));
        } catch (IOException e) {
            log.error("Failed to send INIT handshake to user {}", userId, e);
            removeEmitter(userId, emitter);
        }

        return emitter;
    }

    /**
     * Pushes a real-time notification to all active devices of a specific user.
     */
    public void sendToUser(String userId, NotificationDto notification) {
        CopyOnWriteArrayList<SseEmitter> emitters = userEmitters.get(userId);
        if (emitters == null || emitters.isEmpty()) {
            log.debug("No active SSE connections for user: {}", userId);
            return;
        }

        for (SseEmitter emitter : emitters) {
            try {
                emitter.send(SseEmitter.event()
                        .name("NOTIFICATION")
                        .id(notification.id())
                        .data(notification));
            } catch (IOException e) {
                log.warn("Dead emitter detected while sending to user {}. Cleaning up.", userId);
                removeEmitter(userId, emitter);
            }
        }
    }

    /**
     * Broadcasts a notification to every connected client across the system.
     */
    public void broadcast(NotificationDto notification) {
        userEmitters.forEach((userId, emitters) -> {
            sendToUser(userId, notification);
        });
    }

    /**
     * Keep-alive ping sent every 20 seconds.
     * Intermediate firewalls and cloud proxies terminate idle TCP sockets if no bytes are sent!
     */
    @Scheduled(fixedRate = 20000)
    public void sendHeartbeat() {
        userEmitters.forEach((userId, emitters) -> {
            for (SseEmitter emitter : emitters) {
                try {
                    // SSE comments start with a colon ':' and are ignored by client event handlers
                    emitter.send(SseEmitter.event().comment("ping"));
                } catch (IOException e) {
                    removeEmitter(userId, emitter);
                }
            }
        });
    }

    private void removeEmitter(String userId, SseEmitter emitter) {
        CopyOnWriteArrayList<SseEmitter> emitters = userEmitters.get(userId);
        if (emitters != null) {
            emitters.remove(emitter);
            if (emitters.isEmpty()) {
                userEmitters.remove(userId);
            }
        }
    }
}
```

##### Step 3: The Notification REST Controller

```java
package com.example.demo.notification.controller;

import com.example.demo.notification.dto.NotificationDto;
import com.example.demo.notification.service.SseNotificationService;
import org.springframework.http.HttpStatus;
import org.springframework.http.MediaType;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.*;
import org.springframework.web.servlet.mvc.method.annotation.SseEmitter;

import java.time.Instant;
import java.util.UUID;

@RestController
@RequestMapping("/api/v1/notifications")
public class NotificationController {

    private final SseNotificationService notificationService;

    public NotificationController(SseNotificationService notificationService) {
        this.notificationService = notificationService;
    }

    /**
     * Client subscribes to live updates.
     * NOTE: produces = MediaType.TEXT_EVENT_STREAM_VALUE is MANDATORY for SSE!
     */
    @GetMapping(value = "/subscribe/{userId}", produces = MediaType.TEXT_EVENT_STREAM_VALUE)
    public SseEmitter subscribe(@PathVariable String userId) {
        return notificationService.subscribe(userId);
    }

    /**
     * Endpoint to simulate an event trigger (e.g. called by payment service or admin).
     */
    @PostMapping("/send/{userId}")
    public ResponseEntity<Void> sendNotification(
            @PathVariable String userId,
            @RequestParam String title,
            @RequestParam String message) {

        NotificationDto dto = new NotificationDto(
                UUID.randomUUID().toString(),
                userId,
                title,
                message,
                Instant.now()
        );

        notificationService.sendToUser(userId, dto);
        return ResponseEntity.status(HttpStatus.ACCEPTED).build();
    }
}
```

##### Step 4: Client-Side Consumption (HTML5 / JavaScript)

Connecting to an SSE stream in the browser requires just a few lines of native JavaScript:

```javascript
// Native browser API — no external npm packages or libraries required!
const userId = "user-123";
const eventSource = new EventSource(`/api/v1/notifications/subscribe/${userId}`);

// 1. Listen for connection opening
eventSource.onopen = () => {
    console.log("Connected to live notification stream!");
};

// 2. Listen for custom named event: "NOTIFICATION"
eventSource.addEventListener("NOTIFICATION", (event) => {
    const notification = JSON.parse(event.data);
    console.log("Received notification:", notification);
    alert(`[${notification.title}] ${notification.message}`);
});

// 3. Listen for errors & auto-reconnect
eventSource.onerror = (error) => {
    console.error("SSE stream error. Browser will automatically retry connection...", error);
};
```

---

#### 4 Critical Production Gotchas for SSE

1. **Proxy Buffering (Nginx / Cloudflare)**:
   - By default, reverse proxies like Nginx buffer HTTP responses until a full block is received. This ruins real-time streaming!
   - **Fix**: In Nginx, add the header: `proxy_set_header X-Accel-Buffering no;`.
2. **HTTP/1.1 Connection Limits**:
   - Browsers allow a maximum of **6 concurrent open HTTP/1.1 connections** per domain. If a user opens 6 tabs with SSE, a 7th tab will freeze!
   - **Fix**: Use **HTTP/2**. Under HTTP/2, all streams are multiplexed over a single TCP connection, allowing hundreds of active streams per domain.
3. **Always Clean Up on Disconnect**:
   - Forgetting to register `emitter.onCompletion()` or `emitter.onTimeout()` leads to memory leaks as dead sockets accumulate in your map.
4. **Periodic Heartbeats Are Mandatory**:
   - AWS Application Load Balancers (ALB) terminate idle connections after 60 seconds. A scheduled `:ping` event every 15–20 seconds keeps the socket active.

---

### Chapter 1 Exercises & Solutions

Test your comprehension of Spring Web MVC, parameter binding, validation, and testing.

#### Exercise 1.1: Authoring a PATCH Endpoint for Partial Updates

**Task**: Add a `PATCH /api/v1/products/{id}/price` endpoint to `ProductCrudController` that allows modifying only the product price. Ensure the new price is strictly positive.

The following code implements the partial price update endpoint:

```java
// 1. Request DTO with validation
public record UpdatePriceRequest(
    @Positive(message = "New price must be strictly positive")
    double price
) {}

// 2. Controller Handler
@PatchMapping("/{id}/price")
public ResponseEntity<ProductResponse> updateProductPrice(
        @PathVariable Long id,
        @Valid @RequestBody UpdatePriceRequest request) {
    ProductResponse existing = productStore.get(id);
    if (existing == null) {
        return ResponseEntity.notFound().build();
    }
    // Construct updated record with new price
    ProductResponse updated = new ProductResponse(existing.id(), existing.title(), request.price());
    productStore.put(id, updated);
    return ResponseEntity.ok(updated);
}
```

#### Exercise 1.2: MockMvc Validation Verification

**Task**: Write a `MockMvc` test verifying that submitting a blank title `""` to `POST /api/v1/products` returns HTTP `400 Bad Request` with an `invalidParams.title` property.

The following test verifies that blank product titles are rejected:

```java
@Test
@DisplayName("POST /api/v1/products with blank title returns 400 Bad Request")
void shouldRejectBlankTitle() throws Exception {
    String payload = """
            {
              "title": "",
              "price": 29.99
            }
            """;

    mockMvc.perform(post("/api/v1/products")
            .contentType(MediaType.APPLICATION_JSON)
            .content(payload))
            .andExpect(status().isBadRequest())
            .andExpect(jsonPath("$.title").value("Validation Failure"))
            .andExpect(jsonPath("$.invalidParams.title").exists());
}
```

#### Exercise 1.3: Custom Jackson Snake Case Serializer Test

**Task**: How do you configure Jackson to serialize a field named `orderNumber` as `"order_number"` in JSON?

**Explanation**:
Annotate the field with `@JsonProperty("order_number")` on the Record or class property:
```java
public record OrderDto(
    @JsonProperty("order_number") String orderNumber
) {}
```
Alternatively, apply `@JsonNaming(PropertyNamingStrategies.SnakeCaseStrategy.class)` at the class level to automatically convert all camelCase fields to snake_case.

#### Exercise 1.4: Dynamic Location Header Construction

**Task**: In a `@PostMapping` handler, write the single line of code that creates a `URI` pointing to `/api/v1/users/{newUserId}` using `ServletUriComponentsBuilder`.

The following snippet constructs the dynamic location URI:

```java
URI location = ServletUriComponentsBuilder.fromCurrentRequest()
        .path("/{id}")
        .buildAndExpand(newUserId)
        .toUri();
```

---

## Chapter 2: Securing Spring Boot Applications with OAuth2

Applications operating in distributed environments must protect sensitive endpoints, authenticate user identities, enforce granular permissions, and delegate identity management using modern OAuth2 and OpenID Connect (OIDC) protocols.

### 2.0 The Spring Security Mental Model

Spring Security is an interceptor-based framework built entirely on the standard Java Servlet Filter mechanism. Understanding how security requests are filtered before they ever reach your controllers is essential to mastering security configuration.

#### The Filter Chain Architecture Flowchart

Every incoming HTTP request must pass through a sequence of security filters managed by `FilterChainProxy`:

```mermaid
flowchart LR
    Request["Incoming HTTP Request"] --> FCP["FilterChainProxy"]
    subgraph SecurityFilterChain["Ordered Security Filter Chain"]
        F1["CorsFilter"] --> F2["CsrfFilter"]
        F2 --> F3["BearerTokenAuthenticationFilter"]
        F3 --> F4["UsernamePasswordAuthenticationFilter"]
        F4 --> F5["AuthorizationFilter"]
    end
    FCP --> F1
    F5 --> Controller["ProductController (@RestController)"]
    F5 -.->|"401 Unauthorized / 403 Forbidden"| ErrorHandler["AuthenticationEntryPoint / AccessDeniedHandler"]
```

#### Key Security Concepts Defined

Before configuring access rules, master these core terminology definitions used throughout Spring Security:

- **Authentication**: Answering the question: *"Who are you?"* (Verifying username/password, API keys, or JWT bearer tokens).
- **Authorization**: Answering the question: *"Are you permitted to perform this specific action?"* (Checking user roles, scopes, and permissions).
- **`SecurityContextHolder`**: The central repository storing the currently authenticated principal using `ThreadLocal` storage.
- **`SecurityFilterChain`**: The modern interface where URL matching rules, authentication providers, and session policies are declared.

---

### 2.1 Configuring the Modern `SecurityFilterChain`

In Spring Security 6 (shipped with Spring Boot 3), the legacy `WebSecurityConfigurerAdapter` base class was completely removed. All security configuration is now expressed via standalone `@Bean` definitions using a modern Lambda DSL.

#### Step 1: Adding the Security Starter

Add Spring Security to your `pom.xml`:

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-security</artifactId>
</dependency>
```

#### Step 2: Component-Based Security Configuration

The following configuration class configures a stateless REST API with role-based URL protection:

```java
package com.example.demo.config;

import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.http.HttpMethod;
import org.springframework.security.config.Customizer;
import org.springframework.security.config.annotation.method.configuration.EnableMethodSecurity;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.config.annotation.web.configuration.EnableWebSecurity;
import org.springframework.security.config.annotation.web.configurers.AbstractHttpConfigurer;
import org.springframework.security.config.http.SessionCreationPolicy;
import org.springframework.security.web.SecurityFilterChain;

@Configuration
@EnableWebSecurity
@EnableMethodSecurity(prePostEnabled = true) // Enables @PreAuthorize method-level security
public class ModernSecurityConfig {

    @Bean
    public SecurityFilterChain securityFilterChain(HttpSecurity http) throws Exception {
        return http
                // 1. Disable CSRF for stateless REST APIs (stateless Bearer tokens are immune to CSRF)
                .csrf(AbstractHttpConfigurer::disable)

                // 2. Enforce stateless session policy: never create HTTP session cookies
                .sessionManagement(session -> 
                        session.sessionCreationPolicy(SessionCreationPolicy.STATELESS))

                // 3. Define URL path authorization rules
                .authorizeHttpRequests(auth -> auth
                        // Public endpoints accessible without authentication
                        .requestMatchers("/swagger-ui/**", "/v3/api-docs/**", "/actuator/health").permitAll()
                        .requestMatchers(HttpMethod.GET, "/api/v1/products/**").permitAll()

                        // Role-restricted mutations: only users with ROLE_ADMIN can create or delete
                        .requestMatchers(HttpMethod.POST, "/api/v1/products/**").hasRole("ADMIN")
                        .requestMatchers(HttpMethod.DELETE, "/api/v1/products/**").hasRole("ADMIN")

                        // Any other request requires valid authentication
                        .anyRequest().authenticated()
                )

                // 4. Enable HTTP Basic authentication for testing purposes
                .httpBasic(Customizer.withDefaults())

                .build();
    }
}
```

---

### 2.1.1 CORS & CSRF Demystified for Modern REST APIs

Two of the most frequent points of failure when deploying modern single-page apps (React, Angular, Vue) against a Spring Boot backend are **CORS (Cross-Origin Resource Sharing)** errors and **CSRF (Cross-Site Request Forgery)** rejections.

#### 1. Why Do We Disable CSRF in Stateless REST APIs?

##### What is CSRF?
In traditional server-rendered web applications (e.g., Thymeleaf, JSP), user authentication relies on a session cookie stored in the user's browser (`JSESSIONID`).
When a user visits a malicious website while logged into their bank, the malicious site can submit a hidden form:
```html
<form action="https://mybank.com/transfer" method="POST">
  <input type="hidden" name="recipient" value="attacker" />
  <input type="hidden" name="amount" value="5000" />
</form>
<script>document.forms[0].submit();</script>
```
The browser **automatically attaches the bank's session cookie** with the request! The bank server sees a valid session and transfers the money.

##### Why Stateless REST APIs Are Immune to CSRF:
In modern REST APIs using JWTs, tokens are stored in memory or local storage and sent in the HTTP `Authorization` header:
```text
Authorization: Bearer eyJhbGciOi...
```
**Browsers NEVER automatically attach Authorization headers to cross-origin requests!**
Only JavaScript code running in the original application origin can attach custom headers. Because an attacker's website cannot read or inject the client's `Authorization: Bearer` token, **CSRF attacks are technically impossible against token-based stateless REST APIs**.

Therefore, calling `.csrf(AbstractHttpConfigurer::disable)` in Spring Security is safe and standard practice for stateless APIs.

---

#### 2. The CORS Disaster: Why `@CrossOrigin` Fails on Secured Endpoints

**CORS** is a browser security mechanism that blocks web applications running at one origin (e.g., `http://localhost:3000`) from reading responses from a server at a different origin (e.g., `https://api.mycompany.com`).

##### The Preflight `OPTIONS` Request:
Before a browser makes a cross-origin mutation (like `POST` or `PUT`) or sends custom headers (like `Authorization`), it sends an HTTP **`OPTIONS` preflight request** to ask the backend server:
*"Do you allow POST requests with Authorization headers from origin `http://localhost:3000`?"*

##### The Deadly `@CrossOrigin` Trap:
Beginners often put `@CrossOrigin(origins = "http://localhost:3000")` on their `@RestController`.
Then they test with React, and the browser throws a CORS error:
```text
Access to XMLHttpRequest at 'http://localhost:8080/api/v1/orders' from origin 'http://localhost:3000' 
has been blocked by CORS policy: Response to preflight request doesn't pass access control check!
```
**Why did it fail?**
The browser's preflight `OPTIONS` request does not include credentials. When it hits Spring Security's `FilterChainProxy`, Spring Security intercepts it **BEFORE** it reaches the controller! Spring Security says: *"This request has no credentials, 401 Unauthorized!"* and terminates the request. The `@CrossOrigin` annotation on the controller was never even reached!

##### The Production Fix: The `CorsConfigurationSource` Bean:
Configure CORS directly inside Spring Security's filter chain so preflight requests are processed and approved before authentication checks:

```java
package com.example.demo.config;

import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.security.config.Customizer;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.web.SecurityFilterChain;
import org.springframework.web.cors.CorsConfiguration;
import org.springframework.web.cors.CorsConfigurationSource;
import org.springframework.web.cors.UrlBasedCorsConfigurationSource;

import java.util.List;

@Configuration
public class ProductionSecurityConfig {

    @Bean
    public SecurityFilterChain filterChain(HttpSecurity http) throws Exception {
        return http
                // 1. Tell Spring Security to use the corsConfigurationSource Bean defined below!
                .cors(Customizer.withDefaults())
                .csrf(csrf -> csrf.disable())
                .authorizeHttpRequests(auth -> auth
                        .requestMatchers("/api/v1/public/**").permitAll()
                        .anyRequest().authenticated()
                )
                .build();
    }

    @Bean
    public CorsConfigurationSource corsConfigurationSource() {
        CorsConfiguration config = new CorsConfiguration();
        
        // Explicitly allow your frontend origins (Never use '*' in production with credentials!)
        config.setAllowedOrigins(List.of("http://localhost:3000", "https://app.mycompany.com"));
        
        // Allow all standard REST HTTP methods
        config.setAllowedMethods(List.of("GET", "POST", "PUT", "DELETE", "PATCH", "OPTIONS"));
        
        // Allow Authorization, Content-Type, and custom tracing headers
        config.setAllowedHeaders(List.of("Authorization", "Content-Type", "X-Requested-With", "traceparent"));
        
        // Allow browser to read custom response headers (e.g. pagination or rate limit headers)
        config.setExposedHeaders(List.of("X-Total-Count", "X-RateLimit-Remaining"));
        
        // Allow credentials (cookies / authorization headers)
        config.setAllowCredentials(true);
        
        // Cache preflight OPTIONS response for 1 hour (3600 seconds) so browser doesn't send OPTIONS on every click!
        config.setMaxAge(3600L);

        UrlBasedCorsConfigurationSource source = new UrlBasedCorsConfigurationSource();
        source.registerCorsConfiguration("/**", config); // Apply to all API routes
        return source;
    }
}
```

---

### 2.1.2 Handling Security Failures with RFC 7807 ProblemDetail Responses

By default, when an unauthenticated user or unauthorized role hits a protected endpoint, Spring Security either redirects to a HTML login page or returns an empty HTTP 401/403 status without a JSON body.

In modern REST APIs, security errors must return standardized **RFC 7807 `ProblemDetail`** payloads.

Spring Security delegates errors to two distinct components:
1. **`AuthenticationEntryPoint`**: Invoked when an unauthenticated user tries to access a protected resource (**HTTP 401 Unauthorized** - "Who are you?").
2. **`AccessDeniedHandler`**: Invoked when an authenticated user attempts to access a resource for which they lack the required permissions (**HTTP 403 Forbidden** - "You don't have permission").

```mermaid
flowchart TD
    Req["Incoming HTTP Request"] --> SecFilter["AuthorizationFilter"]
    
    SecFilter --> CheckAuth{"Is user authenticated?"}
    CheckAuth -- NO --> EntryPoint["AuthenticationEntryPoint\n(Returns HTTP 401 ProblemDetail JSON)"]
    
    CheckAuth -- YES --> CheckRole{"Does user have required role?"}
    CheckRole -- NO --> DeniedHandler["AccessDeniedHandler\n(Returns HTTP 403 ProblemDetail JSON)"]
    CheckRole -- YES --> Controller["Proceed to @RestController"]
```

#### Custom JSON Security Handlers Implementation:

```java
package com.example.demo.security;

import com.fasterxml.jackson.databind.ObjectMapper;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;
import org.springframework.http.HttpStatus;
import org.springframework.http.MediaType;
import org.springframework.http.ProblemDetail;
import org.springframework.security.access.AccessDeniedException;
import org.springframework.security.core.AuthenticationException;
import org.springframework.security.web.AuthenticationEntryPoint;
import org.springframework.security.web.access.AccessDeniedHandler;
import org.springframework.stereotype.Component;

import java.io.IOException;
import java.net.URI;
import java.time.Instant;

@Component
public class CustomSecurityProblemHandler implements AuthenticationEntryPoint, AccessDeniedHandler {

    private final ObjectMapper objectMapper;

    public CustomSecurityProblemHandler(ObjectMapper objectMapper) {
        this.objectMapper = objectMapper;
    }

    // Handles 401 Unauthorized (Missing or invalid token)
    @Override
    public void commence(HttpServletRequest request, HttpServletResponse response,
                         AuthenticationException authException) throws IOException {
        
        ProblemDetail problem = ProblemDetail.forStatusAndDetail(
                HttpStatus.UNAUTHORIZED, 
                "Authentication is required to access this resource: " + authException.getMessage()
        );
        problem.setTitle("Unauthorized Access");
        problem.setType(URI.create("https://api.mycompany.com/errors/unauthorized"));
        problem.setProperty("timestamp", Instant.now());
        problem.setProperty("path", request.getRequestURI());

        response.setStatus(HttpServletResponse.SC_UNAUTHORIZED);
        response.setContentType(MediaType.APPLICATION_PROBLEM_JSON_VALUE);
        objectMapper.writeValue(response.getOutputStream(), problem);
    }

    // Handles 403 Forbidden (User logged in, but lacks required role)
    @Override
    public void handle(HttpServletRequest request, HttpServletResponse response,
                       AccessDeniedException accessDeniedException) throws IOException {

        ProblemDetail problem = ProblemDetail.forStatusAndDetail(
                HttpStatus.FORBIDDEN, 
                "You do not possess the required permissions or roles to perform this operation."
        );
        problem.setTitle("Forbidden Resource");
        problem.setType(URI.create("https://api.mycompany.com/errors/forbidden"));
        problem.setProperty("timestamp", Instant.now());
        problem.setProperty("path", request.getRequestURI());

        response.setStatus(HttpServletResponse.SC_FORBIDDEN);
        response.setContentType(MediaType.APPLICATION_PROBLEM_JSON_VALUE);
        objectMapper.writeValue(response.getOutputStream(), problem);
    }
}
```

#### Registering Handlers in `SecurityFilterChain`:

```java
@Bean
public SecurityFilterChain securityFilterChain(HttpSecurity http, CustomSecurityProblemHandler problemHandler) throws Exception {
    return http
            // Register custom RFC 7807 error handlers
            .exceptionHandling(ex -> ex
                    .authenticationEntryPoint(problemHandler) // 401 handler
                    .accessDeniedHandler(problemHandler)       // 403 handler
            )
            // other configurations...
            .build();
}
```

---

### 2.2 Password Encoding & User Authentication

Storing plaintext passwords in databases is a catastrophic security failure. If an attacker breaches the database, every user's credentials are leaked instantly.

#### How BCrypt Password Hashing Works

Spring Security provides `BCryptPasswordEncoder`. BCrypt is a cryptographic hashing function designed specifically for passwords:
1. **Random Salting**: BCrypt generates a 16-byte random salt for every password before hashing. Even if two users share the password `"secret123"`, their resulting hashes are completely different, defeating pre-computed rainbow table attacks.
2. **Configurable Work Factor**: BCrypt uses an adaptive cost factor ($2^{\text{cost}}$ iterations). As hardware becomes faster, the cost factor can be increased to ensure password verification remains computationally expensive for brute-force attackers.

The following configuration demonstrates configuring `BCryptPasswordEncoder` and an in-memory user registry:

```java
package com.example.demo.config;

import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.security.core.userdetails.User;
import org.springframework.security.core.userdetails.UserDetails;
import org.springframework.security.core.userdetails.UserDetailsService;
import org.springframework.security.crypto.bcrypt.BCryptPasswordEncoder;
import org.springframework.security.crypto.password.PasswordEncoder;
import org.springframework.security.provisioning.InMemoryUserDetailsManager;

@Configuration
public class UserAuthConfig {

    @Bean
    public PasswordEncoder passwordEncoder() {
        // Default strength is 10 (2^10 = 1,024 hashing rounds)
        return new BCryptPasswordEncoder();
    }

    @Bean
    public UserDetailsService userDetailsService(PasswordEncoder encoder) {
        // Define an administrator user
        UserDetails adminUser = User.builder()
                .username("admin")
                .password(encoder.encode("admin-secret-password"))
                .roles("ADMIN", "USER") // Automatically assigns ROLE_ADMIN and ROLE_USER
                .build();

        // Define a regular read-only user
        UserDetails regularUser = User.builder()
                .username("john_doe")
                .password(encoder.encode("user-password-123"))
                .roles("USER")
                .build();

        return new InMemoryUserDetailsManager(adminUser, regularUser);
    }
}
```

---

### 2.3 Role-Based Access Control (RBAC) & Method Security

While URL-level security protects entire path prefixes, granular business operations require method-level security.

#### The Crucial Distinction: `hasRole` vs `hasAuthority`

Understanding the naming convention difference between roles and authorities prevents frustrating 403 Forbidden bugs:
- **`hasRole('ADMIN')`**: Spring Security automatically prepends `ROLE_` behind the scenes! It checks if the user possesses the authority named `ROLE_ADMIN`.
- **`hasAuthority('ADMIN')`**: Checks for the exact, literal string `'ADMIN'` without prepending any prefix.

#### Using `@PreAuthorize` with Spring Expression Language (SpEL)

The following service demonstrates fine-grained method security using `@PreAuthorize`:

```java
package com.example.demo.service;

import org.springframework.security.access.prepost.PreAuthorize;
import org.springframework.stereotype.Service;

@Service
public class OrderManagementService {

    // Only callers with ROLE_ADMIN can execute this method
    @PreAuthorize("hasRole('ADMIN')")
    public void purgeCancelledOrders() {
        System.out.println("Purging cancelled orders from database...");
    }

    // A user can only access their own order, unless they are an administrator
    // #username binds to the method parameter; authentication.name is the logged-in user
    @PreAuthorize("hasRole('ADMIN') or #username == authentication.name")
    public String fetchUserOrderDetails(String username, Long orderId) {
        return "Order details for: " + username + " (ID: " + orderId + ")";
    }
}
```

---

### 2.4 OAuth2 & OpenID Connect (OIDC) Protocol Architecture

In enterprise architectures, microservices delegate identity management to a centralized Authorization Server (such as Keycloak, Okta, or Auth0) rather than storing passwords locally.

#### The Four Core OAuth2 Roles

1. **Resource Owner**: The human end-user who owns the account data and grants access.
2. **Client**: The application requesting access (e.g., a React SPA, mobile app, or backend microservice).
3. **Authorization Server**: The centralized identity provider that authenticates users, verifies credentials, and issues cryptographically signed tokens.
4. **Resource Server**: Your Spring Boot API that guards protected resources and validates incoming access tokens.

#### Anatomy of a JSON Web Token (JWT)

A JWT is a compact, URL-safe bearer token structured into three base64url-encoded parts separated by periods (`.`):

```text
eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTYiLCJuYW1lIjoiQWxpY2UiLCJyb2xlcyI6WyJBRE1JTiJdfQ.dBjftJeZ4CVP-mB...
└────────────────┬─────────────────┘ └───────────────────────┬──────────────────────┘ └──────────────────┬─────────────────┘
           1. HEADER                                   2. PAYLOAD                                  3. SIGNATURE
     Algorithm & Token Type                       Claims, Identity, Roles                     Cryptographic Verification
```

- **Header**: Specifies the signature algorithm (e.g., `RS256` asymmetric RSA with SHA-256).
- **Payload (Claims)**: Contains statements about the user (`sub` = user ID, `exp` = expiration timestamp, `roles` = granted roles).
- **Signature**: Generated by encrypting the header and payload with the Authorization Server's **private key**. Anyone possessing the corresponding **public key** can verify that the token was not tampered with.

---

### 2.5 Configuring an OAuth2 Resource Server with JWTs

When configured as an OAuth2 Resource Server, Spring Boot automatically downloads the public keys from your identity provider's JWKS (JSON Web Key Set) endpoint. It validates incoming JWT signatures locally without making slow network round-trips for each request!

#### Step 1: Adding the Resource Server Starter

Include the OAuth2 Resource Server starter in `pom.xml`:

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-oauth2-resource-server</artifactId>
</dependency>
```

#### Step 2: Configuring JWKS in `application.yml`

Point Spring Boot to your Authorization Server's JWKS endpoint:

```yaml
spring:
  security:
    oauth2:
      resourceserver:
        jwt:
          issuer-uri: https://auth.example.com/realms/ecommerce
          jwk-set-uri: https://auth.example.com/realms/ecommerce/protocol/openid-connect/certs
```

#### Step 3: Mapping Custom JWT Claims to Roles

Identity providers often store user roles in custom JSON claims (such as `"roles": ["ADMIN", "USER"]`). Spring Boot by default looks for `"scope"` or `"scp"`. We can configure a custom `JwtAuthenticationConverter` to map custom role claims:

The following configuration extracts roles from a custom `roles` claim and prepends the `ROLE_` prefix:

```java
package com.example.demo.config;

import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.core.convert.converter.Converter;
import org.springframework.security.authentication.AbstractAuthenticationToken;
import org.springframework.security.core.GrantedAuthority;
import org.springframework.security.core.authority.SimpleGrantedAuthority;
import org.springframework.security.oauth2.jwt.Jwt;
import org.springframework.security.oauth2.server.resource.authentication.JwtAuthenticationToken;

import java.util.Collection;
import java.util.List;
import java.util.stream.Collectors;

@Configuration
public class CustomJwtConverterConfig {

    @Bean
    public Converter<Jwt, AbstractAuthenticationToken> jwtAuthenticationConverter() {
        return jwt -> {
            // Extract the "roles" JSON array claim from the JWT payload
            List<String> roles = jwt.getClaimAsStringList("roles");
            Collection<GrantedAuthority> authorities = (roles == null) ? List.of() :
                    roles.stream()
                            .map(role -> new SimpleGrantedAuthority("ROLE_" + role.toUpperCase()))
                            .collect(Collectors.toList());

            // Construct authenticated principal token with username and authorities
            return new JwtAuthenticationToken(jwt, authorities, jwt.getClaimAsString("preferred_username"));
        };
    }
}
```

---

### 2.6 Single Sign-On (SSO) with OAuth2 Client Login

When building web applications that allow users to click "Log in with GitHub" or "Log in with Google", configure Spring Boot as an OAuth2 Client.

#### Step 1: Adding the OAuth2 Client Starter

Add the OAuth2 Client starter to `pom.xml`:

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-oauth2-client</artifactId>
</dependency>
```

#### Step 2: Configuring GitHub OAuth2 Credentials

Configure your OAuth2 application credentials in `application.yml`:

```yaml
spring:
  security:
    oauth2:
      client:
        registration:
          github:
            client-id: YOUR_GITHUB_CLIENT_ID
            client-secret: YOUR_GITHUB_CLIENT_SECRET
            scope: read:user,user:email
```

When users navigate to a protected page, Spring Boot automatically redirects them to GitHub's authorization page and exchanges the authorization code for an access token upon return.

---

### 2.7 Working with JWTs: Generation, Custom Filter, and Refresh Tokens

While Section 2.5 demonstrated using Spring Boot as an OAuth2 Resource Server relying on an external identity provider (like Keycloak), many production systems require Spring Boot to **issue, sign, and validate its own JSON Web Tokens (JWTs)** internally.

#### What is a JSON Web Token (JWT)?

A **JWT** is a compact, URL-safe standard (RFC 7519) for transmitting claims securely between two parties. It is cryptographically signed, meaning the recipient can verify that the token was created by a trusted authority and has not been altered in transit.

```
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiJhbGljZSIsInJvbGVzIjpbIlJPTEVfVVNFUiJdLCJleHAiOjE3NjE1Nzc2MDB9.7s9Dk3...
[------------------ HEADER ------------------] . [------------------ PAYLOAD ------------------] . [---- SIGNATURE ----]
```

```mermaid
flowchart TD
    subgraph JWT ["Anatomy of a Signed JWT"]
        direction TB
        H["1. Header (Base64Url)\nAlgorithm: HMAC-SHA256\nType: JWT"]
        P["2. Payload / Claims (Base64Url)\nsub: user-102\nroles: ['ROLE_USER', 'ROLE_ADMIN']\niat: 1761570000 (Issued At)\nexp: 1761570900 (Expires)"]
        S["3. Cryptographic Signature\nHMACSHA256(Base64(Header) + '.' + Base64(Payload), SecretKey)"]
        H --- P
        P --- S
    end

    style H fill:#e1f5fe,stroke:#0288d1,color:#000
    style P fill:#fff9c4,stroke:#fbc02d,color:#000
    style S fill:#ffcdd2,stroke:#d32f2f,color:#000
```

> [!IMPORTANT]
> **JWT Myth: "JWTs Are Encrypted"**:
> Standard JWTs are **signed, NOT encrypted**. Anyone who intercepts a JWT can decode the Header and Payload using standard Base64 decoding (`atob()` in browser). **Never store sensitive data like passwords or credit card numbers inside JWT claims!**

---

#### Stateful Sessions vs Stateless JWT Architecture

```mermaid
flowchart LR
    subgraph Stateful ["Stateful Session Architecture"]
        Client1["Client"] -->|"1. Session Cookie"| Server1["App Instance 1"]
        Server1 -->|"2. Look up session in RAM/DB"| SessionDB[("Central Session Store (Redis)")]
    end

    subgraph Stateless ["Stateless JWT Architecture"]
        Client2["Client"] -->|"1. Authorization: Bearer <token>"| Server2["Any App Instance"]
        Server2 -->|"2. Validates signature locally using Secret Key\n(Zero DB/Network calls!)"| Done["Request Authorized"]
    end

    style Stateful fill:#fff3e0,stroke:#ef6c00
    style Stateless fill:#e8f5e9,stroke:#388e3c
```

- **Stateful (Cookies + Sessions)**: The server stores session state in memory or Redis. Every HTTP request requires a database or cache lookup to identify the user. Hard to scale across distributed multi-region data centers.
- **Stateless (JWTs)**: The token itself contains the user identity and permissions. Any backend microservice possessing the signing key can validate the token locally in $< 1\text{ ms}$ with zero network or database queries!

---

#### The Full Authentication & Token Refresh Flow

In production, never issue an access token that lives for hours. If an access token is stolen, an attacker has access until it expires! Instead, pair a **short-lived Access Token (15 mins)** with a **long-lived Refresh Token (7 days)**:

```mermaid
sequenceDiagram
    autonumber
    participant Client as Frontend Client (React/Vue/Mobile)
    participant Auth as Auth Controller
    participant Filter as JwtAuthenticationFilter
    participant API as Protected /api/v1/orders
    participant DB as User Database

    Note over Client,Auth: 1. Initial Login
    Client->>Auth: POST /api/auth/login { "email": "alice@ex.com", "password": "secretPassword" }
    Auth->>DB: Verify credentials with BCrypt
    DB-->>Auth: User Valid (Roles: USER)
    Auth-->>Client: Returns: { "accessToken": "xyz... (15m)", "refreshToken": "abc... (7d)" }

    Note over Client,API: 2. Accessing Protected Resource
    Client->>Filter: GET /api/v1/orders (Header: Authorization: Bearer xyz...)
    Filter->>Filter: Verify signature & expiration
    Filter->>API: Valid! Set SecurityContextHolder -> Dispatch to Controller
    API-->>Client: HTTP 200 OK [Orders JSON]

    Note over Client,Auth: 3. Token Expiration & Refresh (15 minutes later)
    Client->>Filter: GET /api/v1/orders (Header: Authorization: Bearer xyz...)
    Filter-->>Client: HTTP 401 Unauthorized (Token Expired)
    Client->>Auth: POST /api/auth/refresh { "refreshToken": "abc..." }
    Auth->>Auth: Verify refresh token
    Auth-->>Client: Returns NEW Access Token: { "accessToken": "new_xyz... (15m)" }
    Client->>Filter: Re-tries GET /api/v1/orders with NEW token -> Success!
```

---

#### Complete Implementation: Custom JWT in Spring Boot 3

##### Step 1: Add Modern JJWT 0.12.x Dependencies to `pom.xml`

```xml
<!-- Modern Java JWT (JJWT) by Auth0 / io.jsonwebtoken -->
<dependency>
    <groupId>io.jsonwebtoken</groupId>
    <artifactId>jjwt-api</artifactId>
    <version>0.12.5</version>
</dependency>
<dependency>
    <groupId>io.jsonwebtoken</groupId>
    <artifactId>jjwt-impl</artifactId>
    <version>0.12.5</version>
    <scope>runtime</scope>
</dependency>
<dependency>
    <groupId>io.jsonwebtoken</groupId>
    <artifactId>jjwt-jackson</artifactId>
    <version>0.12.5</version>
    <scope>runtime</scope>
</dependency>
```

##### Step 2: Configure Secret Key in `application.yml`

The signing key for `HS256` must be at least **256 bits (32 bytes)** long:

```yaml
application:
  security:
    jwt:
      # Must be a 256-bit base64-encoded secret key
      secret-key: 404E635266556A586E3272357538782F413F4428472B4B6250645367566B5970
      access-token-expiration-ms: 900000    # 15 minutes
      refresh-token-expiration-ms: 604800000 # 7 days
```

##### Step 3: The `JwtService` (Signing & Extraction)

```java
package com.example.demo.security.jwt;

import io.jsonwebtoken.Claims;
import io.jsonwebtoken.Jwts;
import io.jsonwebtoken.io.Decoders;
import io.jsonwebtoken.security.Keys;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.security.core.userdetails.UserDetails;
import org.springframework.stereotype.Service;

import javax.crypto.SecretKey;
import java.util.Date;
import java.util.HashMap;
import java.util.Map;
import java.util.function.Function;

@Service
public class JwtService {

    @Value("${application.security.jwt.secret-key}")
    private String secretKey;

    @Value("${application.security.jwt.access-token-expiration-ms}")
    private long accessTokenExpirationMs;

    @Value("${application.security.jwt.refresh-token-expiration-ms}")
    private long refreshTokenExpirationMs;

    /**
     * Extracts username (the 'sub' claim) from token.
     */
    public String extractUsername(String token) {
        return extractClaim(token, Claims::getSubject);
    }

    public <T> T extractClaim(String token, Function<Claims, T> claimsResolver) {
        final Claims claims = extractAllClaims(token);
        return claimsResolver.apply(claims);
    }

    /**
     * Generates an access token with custom user roles and claims.
     */
    public String generateAccessToken(UserDetails userDetails, Map<String, Object> extraClaims) {
        return buildToken(extraClaims, userDetails.getUsername(), accessTokenExpirationMs);
    }

    /**
     * Generates a long-lived refresh token.
     */
    public String generateRefreshToken(UserDetails userDetails) {
        return buildToken(new HashMap<>(), userDetails.getUsername(), refreshTokenExpirationMs);
    }

    private String buildToken(Map<String, Object> extraClaims, String subject, long expirationMs) {
        return Jwts.builder()
                .claims(extraClaims)
                .subject(subject)
                .issuedAt(new Date(System.currentTimeMillis()))
                .expiration(new Date(System.currentTimeMillis() + expirationMs))
                .signWith(getSignInKey(), Jwts.SIG.HS256)
                .compact();
    }

    /**
     * Validates that the token belongs to the user and is not expired.
     */
    public boolean isTokenValid(String token, UserDetails userDetails) {
        final String username = extractUsername(token);
        return (username.equals(userDetails.getUsername())) && !isTokenExpired(token);
    }

    private boolean isTokenExpired(String token) {
        return extractExpiration(token).before(new Date());
    }

    private Date extractExpiration(String token) {
        return extractClaim(token, Claims::getExpiration);
    }

    private Claims extractAllClaims(String token) {
        return Jwts.parser()
                .verifyWith(getSignInKey())
                .build()
                .parseSignedClaims(token)
                .getPayload();
    }

    private SecretKey getSignInKey() {
        byte[] keyBytes = Decoders.BASE64.decode(secretKey);
        return Keys.hmacShaKeyFor(keyBytes);
    }
}
```

##### Step 4: The `JwtAuthenticationFilter` (`OncePerRequestFilter`)

This filter intercepts every incoming HTTP request, reads the `Authorization: Bearer <token>` header, verifies the signature, and populates Spring's `SecurityContextHolder`:

```java
package com.example.demo.security.jwt;

import jakarta.servlet.FilterChain;
import jakarta.servlet.ServletException;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;
import org.springframework.lang.NonNull;
import org.springframework.security.authentication.UsernamePasswordAuthenticationToken;
import org.springframework.security.core.context.SecurityContextHolder;
import org.springframework.security.core.userdetails.UserDetails;
import org.springframework.security.core.userdetails.UserDetailsService;
import org.springframework.security.web.authentication.WebAuthenticationDetailsSource;
import org.springframework.stereotype.Component;
import org.springframework.web.filter.OncePerRequestFilter;

import java.io.IOException;

@Component
public class JwtAuthenticationFilter extends OncePerRequestFilter {

    private final JwtService jwtService;
    private final UserDetailsService userDetailsService;

    public JwtAuthenticationFilter(JwtService jwtService, UserDetailsService userDetailsService) {
        this.jwtService = jwtService;
        this.userDetailsService = userDetailsService;
    }

    @Override
    protected void doFilterInternal(
            @NonNull HttpServletRequest request,
            @NonNull HttpServletResponse response,
            @NonNull FilterChain filterChain
    ) throws ServletException, IOException {

        final String authHeader = request.getHeader("Authorization");

        // 1. Check if Authorization header is present and starts with 'Bearer '
        if (authHeader == null || !authHeader.startsWith("Bearer ")) {
            filterChain.doFilter(request, response);
            return;
        }

        final String jwt = authHeader.substring(7); // Remove 'Bearer ' prefix
        final String userEmail;

        try {
            userEmail = jwtService.extractUsername(jwt);
        } catch (Exception ex) {
            // Malformed or invalid token signature -> proceed without authenticating
            filterChain.doFilter(request, response);
            return;
        }

        // 2. If user is present and not yet authenticated in the current security context
        if (userEmail != null && SecurityContextHolder.getContext().getAuthentication() == null) {
            UserDetails userDetails = this.userDetailsService.loadUserByUsername(userEmail);

            // 3. Validate token signature and expiration against user
            if (jwtService.isTokenValid(jwt, userDetails)) {
                UsernamePasswordAuthenticationToken authToken = new UsernamePasswordAuthenticationToken(
                        userDetails,
                        null,
                        userDetails.getAuthorities()
                );
                authToken.setDetails(new WebAuthenticationDetailsSource().buildDetails(request));

                // 4. Set authentication in Spring Security Context!
                SecurityContextHolder.getContext().setAuthentication(authToken);
            }
        }

        // 5. Pass request down the remaining filter chain
        filterChain.doFilter(request, response);
    }
}
```

##### Step 5: Integrating Filter into `SecurityFilterChain`

```java
package com.example.demo.security.config;

import com.example.demo.security.jwt.JwtAuthenticationFilter;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.security.authentication.AuthenticationProvider;
import org.springframework.security.config.annotation.method.configuration.EnableMethodSecurity;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.config.annotation.web.configuration.EnableWebSecurity;
import org.springframework.security.config.annotation.web.configurers.AbstractHttpConfigurer;
import org.springframework.security.config.http.SessionCreationPolicy;
import org.springframework.security.web.SecurityFilterChain;
import org.springframework.security.web.authentication.UsernamePasswordAuthenticationFilter;

@Configuration
@EnableWebSecurity
@EnableMethodSecurity
public class SecurityConfiguration {

    private final JwtAuthenticationFilter jwtAuthFilter;
    private final AuthenticationProvider authenticationProvider;

    public SecurityConfiguration(JwtAuthenticationFilter jwtAuthFilter, AuthenticationProvider authenticationProvider) {
        this.jwtAuthFilter = jwtAuthFilter;
        this.authenticationProvider = authenticationProvider;
    }

    @Bean
    public SecurityFilterChain securityFilterChain(HttpSecurity http) throws Exception {
        http
            // 1. Disable CSRF (Cross-Site Request Forgery) because JWTs are stateless
            .csrf(AbstractHttpConfigurer::disable)
            // 2. Configure endpoint authorization rules
            .authorizeHttpRequests(auth -> auth
                .requestMatchers("/api/v1/auth/**", "/swagger-ui/**", "/v3/api-docs/**").permitAll()
                .anyRequest().authenticated()
            )
            // 3. Enforce STATELESS session creation (Never store session on server!)
            .sessionManagement(session -> session
                .sessionCreationPolicy(SessionCreationPolicy.STATELESS)
            )
            .authenticationProvider(authenticationProvider)
            // 4. Insert our JwtAuthenticationFilter BEFORE standard username/password filter
            .addFilterBefore(jwtAuthFilter, UsernamePasswordAuthenticationFilter.class);

        return http.build();
    }
}
```

---

#### 3 Essential JWT Security Best Practices

1. **Short Token Lifetimes**: Keep Access Tokens strictly between 5 and 15 minutes.
2. **Where to Store Tokens on the Frontend?**:
   - **Bad**: Storing access/refresh tokens in `localStorage` or `sessionStorage`. Any cross-site scripting (XSS) vulnerability allows malicious JavaScript to steal the token via `localStorage.getItem("token")`!
   - **Good**: Store the long-lived Refresh Token in an **`HttpOnly, Secure, SameSite=Strict` cookie**. JavaScript cannot read `HttpOnly` cookies, preventing XSS token theft! Store the short-lived access token in client application memory (e.g. React state/Redux).
3. **Token Invalidation / Revocation**:
   - Since JWTs are stateless, you cannot "delete" a JWT before its expiration date.
   - **Solution (Blacklist in Redis)**: When a user clicks "Logout" or changes their password, store the token's ID (`jti`) or token string in Redis with a TTL equal to the token's remaining lifetime. In `JwtAuthenticationFilter`, reject requests if the token exists in the Redis blacklist.

---

### Chapter 2 Exercises & Solutions

Test your knowledge of Spring Security 6, password encoding, and role authorization.

#### Exercise 2.1: Securing Method Execution with Multiple Roles

**Task**: Write a service method `archiveProduct(Long id)` that requires the caller to possess either the `ROLE_SUPERVISOR` or `ROLE_ADMIN` role.

The following method enforces dual-role authorization:

```java
@PreAuthorize("hasAnyRole('SUPERVISOR', 'ADMIN')")
public void archiveProduct(Long id) {
    System.out.println("Product " + id + " has been archived.");
}
```

#### Exercise 2.2: MockMvc Security Testing

**Task**: Write a `MockMvc` test verifying that an unauthenticated caller attempting `DELETE /api/v1/products/1` receives `401 Unauthorized`.

The following test verifies that unauthenticated deletes are blocked:

```java
@Test
@DisplayName("DELETE /api/v1/products/1 without credentials returns 401 Unauthorized")
void shouldRejectUnauthenticatedDelete() throws Exception {
    mockMvc.perform(delete("/api/v1/products/1"))
            .andExpect(status().isUnauthorized());
}
```

---

## Chapter 3: Observability, Monitoring, and Application Management

Operating microservices in production requires real-time insight into application health, performance metrics, and distributed execution paths across networked systems.

### 3.0 The Four Pillars of Observability

Observability is the ability to understand the internal state of a software system based solely on its external telemetry. Enterprise observability rests on four pillars:

```mermaid
flowchart TD
    Obs["Observability Framework"] --> Health["1. Health Probes (Actuator)"]
    Obs --> Metrics["2. Numeric Metrics (Micrometer / Prometheus)"]
    Obs --> Traces["3. Distributed Tracing (Zipkin / OpenTelemetry)"]
    Obs --> Logs["4. Structured Logs (Logback / JSON)"]

    Health --> K8s["Kubernetes Liveness & Readiness"]
    Metrics --> Grafana["Grafana Dashboards & Alert Rules"]
    Traces --> Waterfall["Latency Waterfall Visualizations"]
    Logs --> ELK["Elasticsearch Log Analytics"]
```

- **Health Checks**: Binary indicators answering whether the service and its critical dependencies (database, message queues) are operational.
- **Metrics**: Numeric time-series data (CPU load, JVM memory, request rates, error rates).
- **Traces**: Distributed request paths recording the lifecycle of a single user action as it travels across multiple services.
- **Logs**: Discrete timestamped records documenting events and exceptions.

---

### 3.1 Production Health & Metrics with Spring Boot Actuator

Spring Boot Actuator exposes production-ready management endpoints out of the box with zero boilerplate.

#### Step 1: Adding the Actuator Starter

Include the Actuator starter in `pom.xml`:

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-actuator</artifactId>
</dependency>
```

#### Step 2: Configuring Endpoint Exposure in `application.yml`

By default, Spring Boot exposes only `/actuator/health` over HTTP for security reasons. Configure exposure for production monitoring:

```yaml
management:
  endpoints:
    web:
      exposure:
        include: health, info, metrics, prometheus # Expose specific endpoints
  endpoint:
    health:
      show-details: always # Shows database, disk, and custom component statuses
      probes:
        enabled: true     # Enables Kubernetes liveness and readiness probes
```

Navigate to `http://localhost:8080/actuator/health` to inspect the composite system health status.

---

### 3.1.1 Kubernetes Liveness, Readiness & Graceful Shutdown

In modern containerized deployments (Kubernetes, Amazon ECS, Google Cloud Run), the container orchestrator relies on Actuator probes to determine whether your container is healthy or should be restarted.

#### Liveness vs. Readiness Probes Explained Simply:

```mermaid
flowchart TD
    subgraph K8sProbes ["Kubernetes Health Probe Mental Model"]
        Liveness["1. Liveness Probe (/actuator/health/liveness)\nQuestion: Is the application stuck in a deadlock or OOM?\nAction if FAILS: RESTART THE CONTAINER (Kill & Reboot Pod)"]
        Readiness["2. Readiness Probe (/actuator/health/readiness)\nQuestion: Is the application ready to handle incoming web traffic?\nAction if FAILS: STOP SENDING TRAFFIC (Remove from Load Balancer, do NOT kill)"]
    end
```

- **Liveness Failure**: The JVM has entered an unrecoverable state (e.g., permanent deadlock or fatal memory leak). Kubernetes detects this, executes `SIGKILL`, and restarts the pod fresh.
- **Readiness Failure**: The application is busy warming up caches, executing Flyway database migrations, or the database connection pool is temporarily saturated. Kubernetes **does not kill** the application; it simply detaches the pod from the Kubernetes Service load balancer so users don't receive HTTP 500 errors. Once the application catches up and readiness turns `UP`, traffic resumes automatically!

#### Production Configuration for Kubernetes:

Configure probes and **Graceful Shutdown** in `application.yml`:

```yaml
server:
  # Enable Graceful Shutdown: Stop accepting new requests and finish in-flight requests cleanly!
  shutdown: graceful

spring:
  lifecycle:
    # Max time (30 seconds) allowed for in-flight requests to complete before hard termination
    timeout-per-shutdown-phase: 30s

management:
  endpoint:
    health:
      probes:
        # Enables /actuator/health/liveness and /actuator/health/readiness
        enabled: true
  health:
    livenessstate:
      enabled: true
    readinessstate:
      enabled: true
```

#### Programmatically Mutating Readiness State:

If your service experiences an event where it needs to temporarily stop receiving traffic (e.g., preparing for heavy local cache re-indexing), publish an `AvailabilityChangeEvent`:

```java
package com.example.demo.service;

import org.springframework.boot.availability.AvailabilityChangeEvent;
import org.springframework.boot.availability.ReadinessState;
import org.springframework.context.ApplicationEventPublisher;
import org.springframework.stereotype.Service;

@Service
public class MaintenanceService {

    private final ApplicationEventPublisher eventPublisher;

    public MaintenanceService(ApplicationEventPublisher eventPublisher) {
        this.eventPublisher = eventPublisher;
    }

    public void pauseTrafficForHeavyBatchJob() {
        // Marks /actuator/health/readiness as OUT_OF_SERVICE
        // Kubernetes immediately removes this pod from load balancer!
        AvailabilityChangeEvent.publish(eventPublisher, this, ReadinessState.REFUSING_TRAFFIC);
    }

    public void resumeTraffic() {
        // Marks /actuator/health/readiness as UP
        // Kubernetes puts this pod back into rotation!
        AvailabilityChangeEvent.publish(eventPublisher, this, ReadinessState.ACCEPTING_TRAFFIC);
    }
}
```

---

### 3.2 Authoring Custom Health Indicators

When your service depends on an external dependency (such as an external payment provider or custom socket service), write a custom `HealthIndicator` so Actuator reports its status accurately:

The following class implements a custom health probe:

```java
package com.example.demo.actuator;

import org.springframework.boot.actuate.health.Health;
import org.springframework.boot.actuate.health.HealthIndicator;
import org.springframework.stereotype.Component;

import java.net.InetSocketAddress;
import java.net.Socket;

@Component
public class ExternalPaymentGatewayHealthIndicator implements HealthIndicator {

    private static final String HOST = "api.stripe.com";
    private static final int PORT = 443;
    private static final int TIMEOUT_MS = 1500;

    @Override
    public Health health() {
        // Attempt a lightweight socket handshake to test connectivity
        try (Socket socket = new Socket()) {
            socket.connect(new InetSocketAddress(HOST, PORT), TIMEOUT_MS);
            // Report UP with diagnostic details
            return Health.up()
                    .withDetail("paymentGateway", HOST)
                    .withDetail("latency", "Normal")
                    .build();
        } catch (Exception ex) {
            // Report DOWN with exception details
            return Health.down()
                    .withDetail("paymentGateway", HOST)
                    .withDetail("failureReason", ex.getMessage())
                    .build();
        }
    }
}
```

---

### 3.3 Publishing Metrics to Prometheus with Micrometer

**Micrometer** is a vendor-neutral metrics facade—often called the "SLF4J for metrics". It allows you to collect metrics once and export them to Prometheus, Datadog, or InfluxDB.

#### Step 1: Adding the Prometheus Registry Dependency

Include the Micrometer Prometheus registry in `pom.xml`:

```xml
<dependency>
    <groupId>io.micrometer</groupId>
    <artifactId>micrometer-registry-prometheus</artifactId>
</dependency>
```

#### Step 2: Instrumenting Business Logic with Counters and Timers

Micrometer categorizes metric measurements into distinct meter types based on mathematical behavior:

- **Counter**: A monotonically increasing value tracking discrete occurrences (e.g., total orders placed).
- **Timer**: Measures both the duration of short-lived events and their rate of occurrence (e.g., checkout latency).

The following service instruments order processing metrics:

```java
package com.example.demo.service;

import io.micrometer.core.instrument.Counter;
import io.micrometer.core.instrument.MeterRegistry;
import io.micrometer.core.instrument.Timer;
import org.springframework.stereotype.Service;

import java.util.concurrent.TimeUnit;

@Service
public class OrderMetricsService {

    private final Counter successfulOrdersCounter;
    private final Timer checkoutDurationTimer;

    public OrderMetricsService(MeterRegistry registry) {
        // 1. Register a Counter tagged with department
        this.successfulOrdersCounter = Counter.builder("ecommerce.orders.success")
                .description("Total successfully processed orders")
                .tag("department", "checkout")
                .register(registry);

        // 2. Register a Timer that computes p50, p95, and p99 percentiles
        this.checkoutDurationTimer = Timer.builder("ecommerce.checkout.duration")
                .description("Time taken to complete checkout flow")
                .publishPercentiles(0.5, 0.95, 0.99)
                .register(registry);
    }

    public void processOrderWithMetrics(Runnable checkoutLogic) {
        long startTime = System.nanoTime();
        try {
            checkoutLogic.run();
            // Increment the counter
            successfulOrdersCounter.increment();
        } finally {
            // Record execution time in the timer
            checkoutDurationTimer.record(System.nanoTime() - startTime, TimeUnit.NANOSECONDS);
        }
    }
}
```

Metrics are exposed at `http://localhost:8080/actuator/prometheus` in Prometheus scrape format.

---

### 3.3.1 Unified Telemetry with the Micrometer Observation API (`@Observed`)

Before Spring Boot 3, developers had to manage two completely separate instrumentation pipelines:
1. Writing `Timer` and `Counter` code for **Micrometer metrics**.
2. Writing manual spans and Baggage code for **Spring Cloud Sleuth / OpenTelemetry tracing**.

**Spring Boot 3 introduced the Micrometer Observation API**, unifying metrics, distributed tracing, and structured logging into a single programmatic and declarative abstraction!

```mermaid
flowchart TD
    Obs["Single Call: Observation.createNotStarted(...) or @Observed"]
    Obs --> Metric["1. Micrometer Timer / Counter (Sent to Prometheus)"]
    Obs --> Trace["2. Distributed Tracing Span (Sent to Zipkin / Jaeger)"]
    Obs --> Log["3. MDC Diagnostic Context (Injected into Logback JSON)"]
```

#### Step 1: Enable AOP for `@Observed`

Add the AOP starter and declare an `ObservedAspect` bean:

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-aop</artifactId>
</dependency>
```

```java
package com.example.demo.config;

import io.micrometer.observation.ObservationRegistry;
import io.micrometer.observation.aop.ObservedAspect;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

@Configuration
public class ObservationConfig {

    @Bean
    public ObservedAspect observedAspect(ObservationRegistry observationRegistry) {
        return new ObservedAspect(observationRegistry);
    }
}
```

#### Step 2: Instrument Methods Declaratively with `@Observed`

Annotate any service method with `@Observed`:

```java
package com.example.demo.service;

import io.micrometer.observation.annotation.Observed;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.stereotype.Service;

@Service
public class PaymentProcessingService {

    private static final Logger log = LoggerFactory.getLogger(PaymentProcessingService.class);

    @Observed(
            name = "payment.processing",          // Metric name in Prometheus
            contextualName = "process-payment-tx" // Span name in Zipkin / distributed trace
    )
    public String executeTransaction(String customerId, double amount) {
        log.info("Processing credit card payment for customer: {}", customerId);
        
        // Simulating processing logic
        try {
            Thread.sleep(120);
        } catch (InterruptedException ignored) {}

        return "TX-SUCCESS-" + System.currentTimeMillis();
    }
}
```

##### What Happens Automatically Behind the Scenes:
1. **Prometheus Metric Generated**: Creates a timer `payment_processing_seconds_count` and `payment_processing_seconds_sum` recording exact execution duration and success/failure counts.
2. **Distributed Tracing Span Created**: Automatically starts a child span named `process-payment-tx` attached to the current active Trace ID!
3. **MDC Injected**: Injects tracing IDs into the SLF4J MDC context so every log statement inside the method includes the current trace and span ID.

---

### 3.3.2 Authoring Custom Actuator Endpoints (`@Endpoint`)

Beyond the standard `/actuator/health` and `/actuator/metrics`, enterprise architectures often require exposing proprietary internal runtime state (e.g., active WebSocket sessions, cache hit ratios, feature toggle states).

Spring Boot allows authoring custom Actuator endpoints using the `@Endpoint` annotation:

```java
package com.example.demo.actuator;

import org.springframework.boot.actuate.endpoint.annotation.*;
import org.springframework.stereotype.Component;

import java.time.Instant;
import java.util.Map;
import java.util.concurrent.ConcurrentHashMap;

@Component
@Endpoint(id = "features") // Exposes endpoint at /actuator/features
public class CustomFeatureFlagEndpoint {

    private final Map<String, Boolean> featureFlags = new ConcurrentHashMap<>();

    public CustomFeatureFlagEndpoint() {
        featureFlags.put("dark_mode_v2", true);
        featureFlags.put("instant_checkout", false);
        featureFlags.put("ai_recommendations", true);
    }

    // 1. @ReadOperation handles HTTP GET /actuator/features
    @ReadOperation
    public Map<String, Object> getAllFeatures() {
        return Map.of(
                "timestamp", Instant.now(),
                "activeFlagsCount", featureFlags.size(),
                "flags", featureFlags
        );
    }

    // 2. @ReadOperation with path parameter: GET /actuator/features/{name}
    @ReadOperation
    public Boolean getFeatureStatus(@Selector String name) {
        return featureFlags.getOrDefault(name, false);
    }

    // 3. @WriteOperation handles HTTP POST /actuator/features to toggle runtime flags
    @WriteOperation
    public Map<String, Object> updateFeatureFlag(String name, boolean enabled) {
        featureFlags.put(name, enabled);
        return Map.of("updated", name, "enabled", enabled);
    }

    // 4. @DeleteOperation handles HTTP DELETE /actuator/features/{name}
    @DeleteOperation
    public void deleteFeatureFlag(@Selector String name) {
        featureFlags.remove(name);
    }
}
```

#### Exposing and Securing the Custom Endpoint in `application.yml`:

```yaml
management:
  endpoints:
    web:
      exposure:
        include: health, info, metrics, prometheus, features # Add custom endpoint id
```

---

### 3.4 Distributed Tracing with Micrometer Tracing & Zipkin

In a microservices architecture, a single user transaction can trigger a cascade of calls across dozens of services. Distributed tracing correlates every step using unique identifiers.

#### Trace ID vs Span ID

Distributed tracing organizes request paths using two hierarchical identifier types:

- **Trace ID**: A globally unique identifier assigned to the initial request that travels across all participating microservices.
- **Span ID**: A unique identifier for a discrete unit of work within a single service. Spans form a parent-child tree hierarchy:

```text
Trace ID: 9f8a7b6c (Propagated across the entire distributed request)
├── Span 1: API Gateway (Total: 140ms)
│   ├── Span 2: Order Service (95ms)
│   │   ├── Span 3: PostgreSQL Query (18ms)
│   │   └── Span 4: Payment Service HTTP Call (65ms)
│   └── Span 5: Kafka Event Publish (12ms)
```

#### Step 1: Adding Tracing Dependencies

In Spring Boot 3, add Micrometer Tracing with the Brave bridge and Zipkin reporter:

```xml
<dependency>
    <groupId>io.micrometer</groupId>
    <artifactId>micrometer-tracing-bridge-brave</artifactId>
</dependency>
<dependency>
    <groupId>io.zipkin.reporter2</groupId>
    <artifactId>zipkin-reporter-brave</artifactId>
</dependency>
```

#### Step 2: Configuring Zipkin Endpoint in `application.yml`

Configure the sampling probability and Zipkin server URL in your application configuration:

```yaml
management:
  tracing:
    sampling:
      probability: 1.0 # Sample 100% of requests for development (use 0.1 for 10% in production)
  zipkin:
    tracing:
      endpoint: http://localhost:9411/api/v2/spans
```

Launch Zipkin using Docker: `docker run -d -p 9411:9411 openzipkin/zipkin`. Open `http://localhost:9411` in your browser to inspect end-to-end request latency waterfalls.

---

### 3.5 Enterprise Logging: SLF4J, Logback, and Log4j2

Logging is the primary telemetry source used by engineers during production incidents. A well-designed logging architecture enables instant troubleshooting, audit compliance, and automated alerting.

#### The Architecture of Java Logging: Facade vs. Implementation

In modern Java, logging is split into two distinct tiers: **the logging facade (API)** and **the logging engine (implementation)**.

```mermaid
flowchart TD
    App["Your Spring Boot Application Code\n(@Slf4j or LoggerFactory.getLogger)"] --> Facade["SLF4J Facade API\n(org.slf4j.Logger & org.slf4j.MDC)"]
    
    subgraph Engines ["Pluggable Logging Implementations"]
        Facade -->|Default in Spring Boot| Logback["Logback Classic Engine\n(logback-spring.xml)"]
        Facade -.->|Optional High-Performance| Log4j2["Apache Log4j2 Engine\n(log4j2-spring.xml)"]
    end

    Logback --> Console["Console Output (Stdout)"]
    Logback --> RollingFile["Rolling Log Files (/var/log/app.log)"]
    Logback --> JSON["JSON Stream (ELK / Splunk / Datadog)"]

    style Facade fill:#bbdefb,stroke:#1976d2,stroke-width:2px,color:#000
    style Logback fill:#c8e6c9,stroke:#388e3c,color:#000
    style Log4j2 fill:#ffe0b2,stroke:#f57c00,color:#000
```

- **SLF4J (Simple Logging Facade for Java)**: A standardized Java interface. Your business code imports `org.slf4j.Logger` and never couples directly to concrete logging libraries.
- **Logback**: The default logging implementation packaged with Spring Boot. Created by the author of Log4j 1.x as an enhanced, modern engine.
- **Log4j2**: An enterprise-grade logging engine created by Apache, famous for its asynchronous loggers built on the LMAX Disruptor ring buffer.

---

#### Why `System.out.println()` Must Never Be Used in Production

| Problem | `System.out.println()` | SLF4J / Logback |
| :--- | :--- | :--- |
| **I/O Performance** | **Synchronous & Blocking**: Acquires a monitor lock on `System.out`, stalling request threads. | **Asynchronous / Buffered**: Writes to memory buffers without blocking the main worker threads. |
| **Log Levels** | None. Everything prints at 100% volume in production. | Granular control: configure `DEBUG` in dev, `INFO` in staging, `WARN` in prod. |
| **Log File Rotation** | None. Writes blindly to standard output. | Rotates logs daily or at size thresholds (e.g. 50MB), automatically compressing into `.gz` archives. |
| **Metadata** | Prints plain strings with no context. | Automatically records: timestamp, thread name, class, line number, traceId, and severity. |

---

#### The Log Level Hierarchy Explained Simply

Log levels form an ordered threshold:

$$\text{TRACE} < \text{DEBUG} < \text{INFO} < \text{WARN} < \text{ERROR} < \text{OFF}$$

```
TRACE  [ Lowest Level / Verbose ]  -> Step-by-step loop executions, byte dumps
DEBUG  [ Development Diagnostic ]   -> SQL query parameters, incoming DTO values
INFO   [ Normal Operations ]        -> App startup, order created, payment confirmed
WARN   [ Potential Problems ]       -> Retried database query, slow response (> 2s), high heap
ERROR  [ Severe Failures ]          -> Uncaught exceptions, DB connection down, payment failed
```

> [!TIP]
> **Production Recommendation**:
> Set your root logger to `INFO`. Set third-party framework loggers (Hibernate, Spring, Apache HttpClient) to `WARN`. Temporarily lower specific package loggers to `DEBUG` via Actuator at runtime without restarting the application:
> `POST /actuator/loggers/com.example.demo.order { "configuredLevel": "DEBUG" }`.

---

#### Parametric Logging: The High-Performance Pattern

In Java, passing string concatenation to a method evaluates the concatenation **before** the method executes, regardless of whether the log level is enabled!

```java
// ❌ TERRIBLE: String concatenation executes on every request even if DEBUG is disabled!
// Allocates memory on the heap and consumes CPU cycles pointlessly!
log.debug("Processing payment for user: " + user.getId() + " with " + order.getItems().size() + " items");

// ✅ EXCELLENT: SLF4J Parameterized Logging
// If DEBUG is disabled, SLF4J returns immediately without building any string!
log.debug("Processing payment for user: {} with {} items", user.getId(), order.getItems().size());
```

---

#### MDC (Mapped Diagnostic Context): Tracing Requests Across Threads

When 50 concurrent users generate thousands of log lines, standard logs become a jumbled mess. How do you find which logs belong to a specific user?

**MDC (Mapped Diagnostic Context)** stores key-value pairs in a `ThreadLocal` map that SLF4J automatically includes in every log line printed by that thread!

```mermaid
sequenceDiagram
    autonumber
    participant Client
    participant Filter as LoggingMdcFilter
    participant Controller as OrderController
    participant Service as OrderService

    Client->>Filter: HTTP GET /api/v1/orders (Header: X-Correlation-ID: req-abc-123)
    Note over Filter: MDC.put("correlationId", "req-abc-123")<br/>MDC.put("userId", "usr-88")
    
    Filter->>Controller: Dispatch request
    Note over Controller: log.info("Fetching orders")<br/>-> Output: [req-abc-123] [usr-88] Fetching orders
    
    Controller->>Service: calculateDiscount()
    Note over Service: log.info("Applied 10% coupon")<br/>-> Output: [req-abc-123] [usr-88] Applied 10% coupon
    
    Service-->>Controller: Return result
    Controller-->>Filter: HTTP 200 OK
    Note over Filter: MANDATORY: MDC.clear() to prevent memory leak!
```

##### Implementing `LoggingMdcFilter`:

```java
package com.example.demo.logging;

import jakarta.servlet.FilterChain;
import jakarta.servlet.ServletException;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;
import org.slf4j.MDC;
import org.springframework.core.Ordered;
import org.springframework.core.annotation.Order;
import org.springframework.stereotype.Component;
import org.springframework.web.filter.OncePerRequestFilter;

import java.io.IOException;
import java.util.UUID;

@Component
@Order(Ordered.HIGHEST_PRECEDENCE) // Execute before security and web controllers
public class LoggingMdcFilter extends OncePerRequestFilter {

    private static final String CORRELATION_ID_HEADER = "X-Correlation-ID";
    private static final String CORRELATION_ID_KEY = "correlationId";

    @Override
    protected void doFilterInternal(
            HttpServletRequest request,
            HttpServletResponse response,
            FilterChain filterChain
    ) throws ServletException, IOException {

        // 1. Extract correlation ID from incoming header or generate a new UUID
        String correlationId = request.getHeader(CORRELATION_ID_HEADER);
        if (correlationId == null || correlationId.isBlank()) {
            correlationId = UUID.randomUUID().toString();
        }

        // 2. Put into MDC (ThreadLocal storage)
        MDC.put(CORRELATION_ID_KEY, correlationId);
        
        // 3. Return correlation ID in response header for client debugging
        response.setHeader(CORRELATION_ID_HEADER, correlationId);

        try {
            filterChain.doFilter(request, response);
        } finally {
            // 4. CRITICAL: Clear MDC! Tomcat reuses worker threads from a pool.
            // Failing to clear MDC leaks user data across requests!
            MDC.clear();
        }
    }
}
```

---

#### Production Configuration: `logback-spring.xml`

Create `src/main/resources/logback-spring.xml` to configure production rolling file logs and colorful console formats:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration scan="true" scanPeriod="30 seconds">

    <!-- Define log output directory and file names -->
    <property name="LOG_DIR" value="./logs" />
    <property name="APP_NAME" value="ecommerce-service" />

    <!-- 1. Colorized Console Appender for Local Development -->
    <appender name="CONSOLE" class="ch.qos.logback.core.ConsoleAppender">
        <encoder>
            <pattern>%d{yyyy-MM-dd HH:mm:ss.SSS} %highlight(%-5level) [%blue(%thread)] %cyan([%X{correlationId}]) %logger{36} - %msg%n</pattern>
        </encoder>
    </appender>

    <!-- 2. Rolling File Appender with Automatic Compression (.gz) -->
    <appender name="ROLLING_FILE" class="ch.qos.logback.core.rolling.RollingFileAppender">
        <file>${LOG_DIR}/${APP_NAME}.log</file>
        <rollingPolicy class="ch.qos.logback.core.rolling.SizeAndTimeBasedRollingPolicy">
            <!-- Daily rollover pattern: ecommerce-service.2026-10-27.0.log.gz -->
            <fileNamePattern>${LOG_DIR}/archived/${APP_NAME}.%d{yyyy-MM-dd}.%i.log.gz</fileNamePattern>
            <!-- Max file size before creating a new split: 50MB -->
            <maxFileSize>50MB</maxFileSize>
            <!-- Retain logs for 30 days -->
            <maxHistory>30</maxHistory>
            <!-- Total cap of all log files: 5GB -->
            <totalSizeCap>5GB</totalSizeCap>
        </rollingPolicy>
        <encoder>
            <pattern>%d{yyyy-MM-dd HH:mm:ss.SSS} %-5level [%thread] [%X{correlationId}] %logger{36} - %msg%n</pattern>
        </encoder>
    </appender>

    <!-- 3. Profile-Specific Root Logging Rules -->
    <springProfile name="dev">
        <root level="INFO">
            <appender-ref ref="CONSOLE" />
        </root>
        <logger name="com.example.demo" level="DEBUG" />
    </springProfile>

    <springProfile name="prod">
        <root level="INFO">
            <appender-ref ref="CONSOLE" />
            <appender-ref ref="ROLLING_FILE" />
        </root>
        <logger name="org.springframework.web" level="WARN" />
        <logger name="org.hibernate.SQL" level="WARN" />
    </springProfile>

</configuration>
```

---

#### How to Switch from Logback to Apache Log4j2

If your application requires extreme throughput (millions of log entries per second), switch to **Log4j2 Async Loggers**:

##### Step 1: Exclude Logback and Include Log4j2 in `pom.xml`:

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter</artifactId>
    <exclusions>
        <!-- 1. Exclude Spring Boot's default Logback starter -->
        <exclusion>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-logging</artifactId>
        </exclusion>
    </exclusions>
</dependency>

<!-- 2. Include Spring Boot's Log4j2 starter -->
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-log4j2</artifactId>
</dependency>

<!-- 3. High-Performance LMAX Disruptor for Async Logging -->
<dependency>
    <groupId>com.lmax</groupId>
    <artifactId>disruptor</artifactId>
    <version>3.4.4</version>
</dependency>
```

##### Step 2: Enable Async Loggers via JVM System Property:
```properties
# Add to application.properties or JVM startup flag:
log4j2.contextSelector=org.apache.logging.log4j.core.async.AsyncLoggerContextSelector
```

---

### Chapter 3 Exercises & Solutions

Test your knowledge of health probes and metrics instrumentation.

#### Exercise 3.1: Securing Actuator Endpoints

**Task**: Configure Spring Security so that `/actuator/health/**` is public, but all other Actuator endpoints require the `ACTUATOR_ADMIN` authority.

The following security filter chain secures management endpoints:

```java
@Bean
public SecurityFilterChain actuatorSecurity(HttpSecurity http) throws Exception {
    return http
            .authorizeHttpRequests(auth -> auth
                    .requestMatchers("/actuator/health/**").permitAll()
                    .requestMatchers("/actuator/**").hasAuthority("ACTUATOR_ADMIN")
                    .anyRequest().authenticated()
            )
            .httpBasic(Customizer.withDefaults())
            .build();
}
```

#### Exercise 3.2: Instrumenting a Custom Failure Counter

**Task**: Write a method that increments a counter named `ecommerce.payments.failed` tagged with `failure_reason`.

The following method instruments a tagged failure counter:

```java
public void recordPaymentFailure(MeterRegistry registry, String reason) {
    registry.counter("ecommerce.payments.failed", "failure_reason", reason).increment();
}
```

---

## Chapter 4: Spring Cloud and Microservices Architecture

Scaling distributed applications requires dynamic service discovery, centralized edge routing, resilience against cascading failures, and unified configuration management across environments.

### 4.0 Microservices Design Principles & Challenges

Decomposing monolithic architectures into autonomous microservices introduces distributed systems challenges:
1. **Dynamic IP Addresses**: Containers spin up and down dynamically with changing IP addresses; hardcoding IPs in client configurations is impossible.
2. **Cascading Failures**: If Service A calls Service B, and Service B hangs due to a database deadlock, Service A exhausts its connection threads waiting for B. Soon, the entire system crashes.
3. **Edge Routing**: Exposing dozens of internal microservices directly to public clients introduces severe CORS, security, and versioning complexities.

---

### 4.1 Service Registration & Discovery with Netflix Eureka

**Eureka** acts as a dynamic phonebook. When an instance boots up, it registers its IP address and port with the Eureka server. Client services query Eureka to discover live instances dynamically.

#### Step 1: Setting Up the Eureka Server

Add the Eureka Server starter to `pom.xml`:

```xml
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-netflix-eureka-server</artifactId>
</dependency>
```

Enable the Eureka server in your main application class:

```java
package com.example.eurekaserver;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.cloud.netflix.eureka.server.EnableEurekaServer;

@SpringBootApplication
@EnableEurekaServer // Activates Eureka Server registry engine
public class EurekaServerApplication {
    public static void main(String[] args) {
        SpringApplication.run(EurekaServerApplication.class, args);
    }
}
```

Configure `application.yml` for the standalone server:

```yaml
server:
  port: 8761
eureka:
  client:
    register-with-eureka: false # Standalone server does not register with itself
    fetch-registry: false
```

#### Step 2: Registering a Microservice (Eureka Client)

Add the Eureka Client starter to your microservice `pom.xml`:

```xml
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-netflix-eureka-client</artifactId>
</dependency>
```

Configure registration in `application.yml`:

```yaml
spring:
  application:
    name: order-service # Service ID registered with Eureka
eureka:
  client:
    service-url:
      defaultZone: http://localhost:8761/eureka/
```

#### Eureka High Availability & Self-Preservation Mode

In production, two Eureka mechanics are critical to understand:

1. **Client-Side Registry Caching**:
   When `order-service` calls `product-service`, it does **not** query Eureka on every single HTTP request! That would turn Eureka into a massive performance bottleneck.
   Instead, Eureka clients cache the entire service registry locally in memory, refreshing it in the background every 30 seconds (`eureka.client.registry-fetch-interval-seconds`). If Eureka crashes completely, microservices can still communicate with each other using their local cache!

2. **Self-Preservation Mode**:
   Every microservice instance sends a heartbeat to Eureka every 30 seconds. If Eureka stops receiving heartbeats from an instance, it normally evicts it after 90 seconds.
   However, if a network glitch occurs between Eureka and an entire AWS availability zone, Eureka might suddenly lose heartbeats from 40% of all microservices. 
   Instead of foolishly deleting all 40% from the registry, Eureka enters **Self-Preservation Mode**: it pauses all evictions, assuming the services are still running and the network between them is just temporarily impaired!

---

### 4.1.1 Client-Side Load Balancing with Spring Cloud LoadBalancer

In early Spring Cloud versions, Netflix **Ribbon** was used for client-side load balancing. Ribbon was deprecated and completely removed.
The modern standard is **Spring Cloud LoadBalancer**, a lightweight, non-blocking load balancer fully integrated with Spring MVC and WebFlux.

#### How Client-Side Load Balancing Works Under the Hood:

```mermaid
sequenceDiagram
    autonumber
    participant Order as Order Service (Client)
    participant LB as Spring Cloud LoadBalancer
    participant Cache as Local Eureka Registry Cache
    participant Prod1 as Product Service Instance 1 (10.0.1.5:8081)
    participant Prod2 as Product Service Instance 2 (10.0.1.8:8081)

    Order->>LB: Calls http://PRODUCT-SERVICE/api/v1/products/42
    LB->>Cache: Look up live instances of "PRODUCT-SERVICE"
    Cache-->>LB: Returns [10.0.1.5:8081, 10.0.1.8:8081]
    Note over LB: Round-Robin Algorithm picks 10.0.1.8:8081
    LB->>Order: Rewrites URL to http://10.0.1.8:8081/api/v1/products/42
    Order->>Prod2: Direct TCP HTTP Request executed!
```

#### Configuring `@LoadBalanced` with Modern `RestClient` in Spring Boot 3:

Add the load balancer starter to `pom.xml`:

```xml
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-loadbalancer</artifactId>
</dependency>
```

Annotate the `RestClient.Builder` bean with `@LoadBalanced`:

```java
package com.example.demo.config;

import org.springframework.cloud.client.loadbalancer.LoadBalanced;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.web.client.RestClient;

@Configuration
public class LoadBalancedClientConfig {

    // @LoadBalanced intercepts RestClient calls and replaces virtual service IDs with physical IPs!
    @Bean
    @LoadBalanced
    public RestClient.Builder loadBalancedRestClientBuilder() {
        return RestClient.builder();
    }

    @Bean
    public RestClient productRestClient(RestClient.Builder loadBalancedBuilder) {
        return loadBalancedBuilder
                .baseUrl("http://PRODUCT-SERVICE") // Virtual Eureka service ID!
                .build();
    }
}
```

Now, calling `productRestClient.get().uri("/api/v1/products/{id}", id).retrieve()` automatically distributes requests across all healthy instances using Round-Robin!

---

### 4.2 API Routing & Filtering with Spring Cloud Gateway

**Spring Cloud Gateway** acts as the single reverse-proxy entry point for all incoming traffic. Built on non-blocking Spring WebFlux and Netty, it handles routing, rate limiting, and header modification.

#### Declarative Routing Configuration

Configure routes in `application.yml` using predicates and filters:

```yaml
spring:
  cloud:
    gateway:
      routes:
        # Route 1: Product Service
        - id: product-service-route
          uri: lb://PRODUCT-SERVICE # Discovered dynamically via Eureka load balancing
          predicates:
            - Path=/api/v1/products/**
          filters:
            - AddRequestHeader=X-Gateway-Origin, EdgeGateway
            - StripPrefix=0

        # Route 2: Order Service
        - id: order-service-route
          uri: lb://ORDER-SERVICE
          predicates:
            - Path=/api/v1/orders/**
          filters:
            - AddRequestHeader=X-Gateway-Origin, EdgeGateway
```

#### 4.2.1 Edge Security: Validating JWTs in Gateway Filters

In production microservices, internal services (like `order-service` or `inventory-service`) should never be exposed directly to the public internet. 
The **API Gateway acts as the security perimeter**: it inspects and cryptographically verifies the incoming `Authorization: Bearer <JWT>` token. If valid, the gateway extracts user metadata and forwards clean HTTP headers (`X-User-Id`, `X-User-Roles`) to downstream services!

```mermaid
sequenceDiagram
    autonumber
    actor User as Public Client / Mobile App
    participant GW as Spring Cloud Gateway (Edge Perimeter)
    participant Auth as Identity Provider (Keycloak / Auth0)
    participant Order as Order Microservice (Internal Network)

    User->>GW: POST /api/v1/orders (Authorization: Bearer JWT)
    GW->>GW: JwtValidationFilter executes!
    GW->>GW: Cryptographically verifies JWT signature against public key
    
    alt Token is Missing or Expired
        GW-->>User: Returns HTTP 401 Unauthorized (Rejected at Edge!)
    else Token is Valid
        GW->>GW: Extracts userId="usr_987", role="ROLE_CUSTOMER"
        GW->>GW: Mutates request: Injects X-User-Id and X-User-Roles headers
        GW->>Order: Forwards request with clean headers!
        Order-->>GW: Order created (201 Created)
        GW-->>User: 201 Created
    end
```

##### Implementing a Custom Reactive Gateway Filter:

Because Spring Cloud Gateway is built on non-blocking Spring WebFlux, gateway filters implement `GatewayFilter` and manipulate `ServerWebExchange`:

```java
package com.example.gateway.filter;

import io.jsonwebtoken.Claims;
import io.jsonwebtoken.Jwts;
import io.jsonwebtoken.security.Keys;
import org.springframework.cloud.gateway.filter.GatewayFilter;
import org.springframework.cloud.gateway.filter.factory.AbstractGatewayFilterFactory;
import org.springframework.http.HttpHeaders;
import org.springframework.http.HttpStatus;
import org.springframework.http.server.reactive.ServerHttpRequest;
import org.springframework.stereotype.Component;

import javax.crypto.SecretKey;
import java.nio.charset.StandardCharsets;

@Component
public class AuthenticationGatewayFilterFactory extends AbstractGatewayFilterFactory<AuthenticationGatewayFilterFactory.Config> {

    private final SecretKey signingKey;

    public AuthenticationGatewayFilterFactory() {
        super(Config.class);
        // In production, inject via @Value("${jwt.secret}")
        this.signingKey = Keys.hmacShaKeyFor("YourSuperSecret256BitKeyForJwtSigningHere!".getBytes(StandardCharsets.UTF_8));
    }

    public static class Config {}

    @Override
    public GatewayFilter apply(Config config) {
        return (exchange, chain) -> {
            ServerHttpRequest request = exchange.getRequest();

            // 1. Verify Authorization Header exists
            if (!request.getHeaders().containsKey(HttpHeaders.AUTHORIZATION)) {
                exchange.getResponse().setStatusCode(HttpStatus.UNAUTHORIZED);
                return exchange.getResponse().setComplete(); // Short-circuit and return 401
            }

            String authHeader = request.getHeaders().getFirst(HttpHeaders.AUTHORIZATION);
            if (authHeader == null || !authHeader.startsWith("Bearer ")) {
                exchange.getResponse().setStatusCode(HttpStatus.UNAUTHORIZED);
                return exchange.getResponse().setComplete();
            }

            String token = authHeader.substring(7);

            try {
                // 2. Validate cryptographic signature and parse claims
                Claims claims = Jwts.parser()
                        .verifyWith(signingKey)
                        .build()
                        .parseSignedClaims(token)
                        .getPayload();

                // 3. Mutate the request: Inject user identity headers for downstream microservices
                ServerHttpRequest mutatedRequest = exchange.getRequest().mutate()
                        .header("X-User-Id", claims.getSubject())
                        .header("X-User-Email", claims.get("email", String.class))
                        .header("X-User-Roles", claims.get("roles", String.class))
                        .build();

                // 4. Forward mutated request downstream
                return chain.filter(exchange.mutate().request(mutatedRequest).build());

            } catch (Exception ex) {
                // Invalid or expired token
                exchange.getResponse().setStatusCode(HttpStatus.UNAUTHORIZED);
                return exchange.getResponse().setComplete();
            }
        };
    }
}
```

#### 4.2.2 Distributed Edge Rate Limiting with Redis

To protect your system against Distributed Denial of Service (DDoS) attacks and brute-force abuse, Spring Cloud Gateway includes a built-in **Token Bucket Rate Limiter** powered by Redis (`RequestRateLimiter`).

Configure rate limiting per IP or per API key in `application.yml`:

```yaml
spring:
  data:
    redis:
      host: localhost
      port: 6379
  cloud:
    gateway:
      routes:
        - id: rate-limited-order-route
          uri: lb://ORDER-SERVICE
          predicates:
            - Path=/api/v1/orders/**
          filters:
            - name: RequestRateLimiter
              args:
                # Number of tokens added to bucket per second (sustained rate)
                redis-rate-limiter.replenishRate: 10
                # Maximum capacity of bucket (allows short bursts up to 20 requests)
                redis-rate-limiter.burstCapacity: 20
                # Cost per request in tokens
                redis-rate-limiter.requestedTokens: 1
                # Bean name of KeyResolver to determine identity of caller
                key-resolver: "#{@ipKeyResolver}"
```

Declare the `KeyResolver` bean in Java to rate-limit by client IP address:

```java
package com.example.gateway.config;

import org.springframework.cloud.gateway.filter.ratelimit.KeyResolver;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import reactor.core.publisher.Mono;

@Configuration
public class RateLimiterConfig {

    @Bean
    public KeyResolver ipKeyResolver() {
        // Resolve client remote IP address as rate limit key
        return exchange -> Mono.just(
                exchange.getRequest().getRemoteAddress() != null
                        ? exchange.getRequest().getRemoteAddress().getAddress().getHostAddress()
                        : "anonymous"
        );
    }
}
```

---

### 4.3 Fault Tolerance & Circuit Breaking with Resilience4j

In a microservices architecture, remote network calls will inevitably fail. A network partition occurs, a downstream service crashes, or a database query hangs. Without fault tolerance patterns, a single failing service can trigger a **cascading collapse** across your entire infrastructure.

#### The Cascading Failure Crisis

Imagine an `Order Service` that calls a `Payment Gateway`. Under normal load, the payment gateway replies in $50\text{ ms}$.

```mermaid
flowchart TD
    subgraph Collapse ["How a Single Slow Dependency Kills Your System"]
        direction TB
        C1["500 User Requests arrive at Order Service"] --> T1["Tomcat assigns 200 worker threads"]
        T1 --> D1["Payment Gateway hangs (taking 30s per request)"]
        D1 --> T2["All 200 Tomcat worker threads blocked waiting for Payment Gateway!"]
        T2 --> C2["Order Service can no longer accept ANY incoming HTTP requests!"]
        C2 --> C3["CRASH: Entire Order Service goes down (HTTP 504 Timeouts for all users)"]
    end

    style Collapse fill:#ffebee,stroke:#c62828,stroke-width:2px,color:#000
```

> [!IMPORTANT]
> **Why Simple Timeouts Are Not Enough**:
> If your HTTP timeout is set to 5 seconds, and 200 requests arrive per second, your server will hold **1,000 concurrent hanging threads** before any timeout fires! This exhausts JVM memory and server CPU. A **Circuit Breaker** solves this by cutting off calls immediately after detecting failure.

---

#### Real-World Analogy: The Electrical Circuit Breaker

In your home, when an electrical appliance short-circuits, the circuit breaker **trips open**, cutting off current to prevent your electrical wires from catching fire. 

In software:
- **CLOSED**: Everything works normally. Electricity (requests) flows freely.
- **OPEN**: Downstream service is failing. The breaker trips! Requests are **rejected instantly** (failing fast) and routed to a fallback method without touching the network.
- **HALF-OPEN**: After a cooling-off period (e.g. 10s), the breaker lets a few test requests pass through to check if the downstream service has recovered.

```mermaid
stateDiagram-v2
    [*] --> CLOSED
    CLOSED --> OPEN : Error rate exceeds threshold (e.g., > 50% failures in last 100 calls)
    OPEN --> HALF_OPEN : Wait duration expires (e.g., 10s cooling-off period)
    HALF_OPEN --> CLOSED : Trial calls succeed -> Service is healthy again!
    HALF_OPEN --> OPEN : Trial calls fail -> Service still dead, re-trip breaker!
```

---

#### Sliding Window Mechanics: Count-Based vs. Time-Based

Resilience4j calculates the error rate using a **Sliding Window**:

```
Count-Based Window (Size = 10):
[ ✅ | ✅ | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ ]  -> 7 Failures out of 10 calls = 70% Error Rate!
  Older calls drop off <------------------------ Newest call arrives
```

1. **Count-Based Sliding Window**: Records the outcome of the last $N$ calls (e.g., last 100 calls).
2. **Time-Based Sliding Window**: Records the outcome of calls made during the last $N$ seconds (e.g., last 60 seconds).
3. **Minimum Number of Calls**: Prevents tripping the breaker on the very first failure. If configured with `minimum-number-of-calls: 10`, Resilience4j will not evaluate the error rate until at least 10 calls have been recorded.

---

#### Complete Production Configuration: `application.yml`

Configure Resilience4j with fine-grained production thresholds:

```yaml
resilience4j:
  circuitbreaker:
    instances:
      paymentService:
        # 1. Use COUNT_BASED (last N calls) or TIME_BASED (last N seconds)
        sliding-window-type: COUNT_BASED
        # 2. Number of calls to evaluate
        sliding-window-size: 20
        # 3. Minimum calls before error rate evaluation begins
        minimum-number-of-calls: 10
        # 4. Trip breaker if 50% or more calls fail
        failure-rate-threshold: 50
        # 5. Trip breaker if 50% or more calls are slow (> 2 seconds)
        slow-call-rate-threshold: 50
        slow-call-duration-threshold: 2000ms
        # 6. How long the breaker stays OPEN before testing in HALF-OPEN (10 seconds)
        wait-duration-in-open-state: 10000ms
        # 7. Number of trial calls permitted in HALF-OPEN state
        permitted-number-of-calls-in-half-open-state: 5
        # 8. Automatically move from OPEN to HALF-OPEN without waiting for incoming calls
        automatic-transition-from-open-to-half-open-enabled: true
        # 9. Register health indicator with Spring Boot Actuator
        register-health-indicator: true

  # Bonus: Automatic Retries with Exponential Backoff
  retry:
    instances:
      paymentService:
        max-attempts: 3
        wait-duration: 500ms
        enable-exponential-backoff: true
        exponential-backoff-multiplier: 2
        retry-exceptions:
          - java.io.IOException
          - org.springframework.web.client.ResourceAccessException
        ignore-exceptions:
          - com.example.demo.exception.InvalidPaymentException # Don't retry user input errors!
```

---

#### Production Code: Circuit Breaker + Fallback + Retry

Add the Resilience4j starters to `pom.xml`:

```xml
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-circuitbreaker-resilience4j</artifactId>
</dependency>
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-aop</artifactId>
</dependency>
```

##### The Service Implementation:

```java
package com.example.demo.payment.client;

import io.github.resilience4j.circuitbreaker.annotation.CircuitBreaker;
import io.github.resilience4j.retry.annotation.Retry;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.stereotype.Service;
import org.springframework.web.client.RestClient;

import java.math.BigDecimal;

public record PaymentRequest(String orderId, BigDecimal amount) {}
public record PaymentResponse(String transactionId, String status) {}

@Service
public class PaymentGatewayClient {

    private static final Logger log = LoggerFactory.getLogger(PaymentGatewayClient.class);
    private final RestClient restClient;

    public PaymentGatewayClient(RestClient.Builder builder) {
        this.restClient = builder.baseUrl("https://api.external-payment.com").build();
    }

    /**
     * Protected by both @CircuitBreaker and @Retry.
     * Order of execution: Retry runs first; if all retries fail, CircuitBreaker records failure.
     */
    @CircuitBreaker(name = "paymentService", fallbackMethod = "paymentFallback")
    @Retry(name = "paymentService")
    public PaymentResponse processPayment(PaymentRequest request) {
        log.info("Sending payment request to external gateway for order: {}", request.orderId());

        return restClient.post()
                .uri("/v1/charge")
                .body(request)
                .retrieve()
                .body(PaymentResponse.class);
    }

    /**
     * Fallback Method Rules (MANDATORY):
     * 1. Must have the EXACT same parameter arguments as the original method.
     * 2. Must accept a trailing Throwable parameter.
     * 3. Must return the EXACT same return type as the original method.
     */
    public PaymentResponse paymentFallback(PaymentRequest request, Throwable ex) {
        log.error("Circuit breaker tripped or payment gateway unreachable for order: {}. Reason: {}", 
                request.orderId(), ex.getMessage());

        // Graceful degradation: Return PENDING status and queue order for background processing
        return new PaymentResponse(
                "OFFLINE-PAYMENT-" + request.orderId(),
                "QUEUED_FOR_OFFLINE_PROCESSING"
        );
    }
}
```

---

#### The Full Resilience4j Annotation Toolbelt

Resilience4j provides 5 composable resilience patterns:

| Annotation | What It Does | When to Use It |
| :--- | :--- | :--- |
| **`@CircuitBreaker`** | Stops calling failing remote services when error rate exceeds threshold. | Any network call to downstream microservices, payment gateways, or third-party APIs. |
| **`@Retry`** | Automatically retries transient network glitches with exponential backoff. | Temporary network blips, 503 Service Unavailable, connection resets. |
| **`@RateLimiter`** | Restricts execution rate (e.g. max 50 requests per second). | Protecting your API against abusive consumers or honoring third-party API rate quotas. |
| **`@Bulkhead`** | Limits concurrent calls to a resource (thread pool or semaphore isolation). | Isolating slow reports or export jobs so they don't consume all web server threads. |
| **`@TimeLimiter`** | Sets strict asynchronous execution timeout. | Killing slow queries or long-running computations. |

> [!WARNING]
> **Spring AOP Self-Invocation Pitfall**:
> Just like `@Transactional`, Resilience4j annotations work through **Spring Dynamic Proxies**. If method `A()` inside `PaymentService` calls `@CircuitBreaker` method `B()` in the **same class** via `this.processPayment()`, **the Circuit Breaker will NOT execute**! You must invoke annotated methods across different Spring beans.

---

#### Monitoring Circuit Breakers via Spring Boot Actuator

With `management.endpoints.web.exposure.include: health,metrics`, you can monitor circuit breakers live:

1. **Health Endpoint** (`GET /actuator/health`):
   ```json
   {
     "status": "UP",
     "components": {
       "circuitBreakers": {
         "status": "UP",
         "details": {
           "paymentService": {
             "status": "UP",
             "state": "CLOSED",
             "failureRate": "0.0%",
             "slowCallRate": "0.0%"
           }
         }
       }
     }
   }
   ```
2. **Prometheus Metrics**:
   - `resilience4j_circuitbreaker_state{name="paymentService", state="open"}`
   - `resilience4j_circuitbreaker_calls_seconds_count{kind="successful"}`
   - `resilience4j_circuitbreaker_calls_seconds_count{kind="failed"}`

---

### 4.4 Centralized Configuration Management with Spring Cloud Config

Instead of bundling properties files inside each individual JAR, **Spring Cloud Config** centralizes configurations in an external Git repository.

The following architectural diagram illustrates centralized configuration distribution:

```text
[ Git Repository: config-repo ]
       │
       ▼
[ Spring Cloud Config Server (Port 8888) ]
       │
       ├───> [ Product Service ] (Pulls product-service.yml on startup)
       └───> [ Order Service ]   (Pulls order-service.yml on startup)
```

Microservices fetch their properties on startup and can refresh dynamic properties at runtime using `@RefreshScope` and the `/actuator/refresh` endpoint without restarting the container.

---

### 4.5 Distributed Tracing & W3C Trace Context Propagation Across Services

In a monolith, tracking a request is straightforward because execution occurs within a single JVM process and log file. In a microservices architecture, a single user click ("Place Order") triggers a complex sequence of remote network calls across multiple independently deployed services.

Without **Distributed Context Propagation**, debugging an intermittent timeout across 6 microservices is nearly impossible.

#### The W3C TraceContext Standard

Modern Spring Boot 3 applications adhere to the **W3C TraceContext specification**. When an incoming request reaches your API Gateway, Spring generates a standard HTTP header named **`traceparent`**:

```text
traceparent: 00-4bf92f3577b34da6a3ce929d0e0e4736-00f067aa0ba902b7-01
              │  └───────────────┬───────────────┘ └───────┬──────┘ └─┬┘
           Version          Trace ID                    Parent/Span  Flags (01 = Sampled)
           (Always 00)  (Globally Unique 128-bit)      ID (64-bit)
```

- **Trace ID (`4bf92f3577b34da6a3ce929d0e0e4736`)**: Stays identical across every single service in the distributed transaction.
- **Span ID (`00f067aa0ba902b7`)**: Identifies the specific operation being executed within the current service.

#### The Distributed Propagation Flow:

```mermaid
sequenceDiagram
    autonumber
    actor User as Client
    participant GW as API Gateway
    participant Order as Order Service
    participant Pay as Payment Service
    participant Kafka as Apache Kafka
    participant Notif as Notification Service

    User->>GW: POST /api/v1/orders
    Note over GW: Generates TraceId: T1, SpanId: S1
    GW->>Order: POST /orders (Header: traceparent: 00-T1-S1-01)
    
    Note over Order: Inherits TraceId: T1<br/>Creates Child SpanId: S2
    Order->>Pay: POST /charge (Header: traceparent: 00-T1-S2-01)
    
    Note over Pay: Inherits TraceId: T1<br/>Creates Child SpanId: S3
    Pay-->>Order: 200 OK (Payment Verified)
    
    Order->>Kafka: Publish "OrderPlacedEvent" (Kafka Header: traceparent: 00-T1-S2-01)
    Order-->>GW: 201 Created
    GW-->>User: Order Completed!
    
    Kafka->>Notif: Consumes Event (Extracts traceparent from Kafka Record Headers!)
    Note over Notif: Inherits TraceId: T1<br/>Creates Child SpanId: S4 (Sends Email)
```

#### Automatic Propagation with `RestClient`:

When you use Spring Boot 3's auto-configured `RestClient.Builder` or `@LoadBalanced RestClient.Builder`, Micrometer Tracing registers an HTTP client interceptor (`ObservationClientHttpRequestInterceptor`).
This interceptor **automatically injects the current active `traceparent` header into every outgoing HTTP call** without writing a single line of custom header code!

```java
// Micrometer Tracing automatically attaches 'traceparent' under the hood!
PaymentResponse response = restClient.post()
        .uri("http://PAYMENT-SERVICE/v1/charge")
        .body(paymentRequest)
        .retrieve()
        .body(PaymentResponse.class);
```

When all services report their spans to Zipkin or Jaeger, you obtain a complete, unified **Waterfall Latency Graph** displaying the exact millisecond cost of every network hop and database query across your entire fleet of microservices.

---

### Chapter 4 Exercises & Solutions

Test your knowledge of service discovery, routing gateways, and circuit breaking.

#### Exercise 4.1: Gateway Header Filtering

**Task**: Write a Gateway route configuration that routes requests matching `/api/v1/billing/**` to `lb://BILLING-SERVICE` and adds an `X-Billing-Origin: EdgeGateway` header to the forwarded request.

The following configuration sets up the requested gateway route:

```yaml
spring:
  cloud:
    gateway:
      routes:
        - id: billing-route
          uri: lb://BILLING-SERVICE
          predicates:
            - Path=/api/v1/billing/**
          filters:
            - AddRequestHeader=X-Billing-Origin, EdgeGateway
```

#### Exercise 4.2: Circuit Breaker Fallback Signature

**Task**: Why does Resilience4j require the fallback method to accept a `Throwable` as its final parameter?

**Explanation**:
The trailing `Throwable` parameter provides the fallback method with programmatic access to the root cause of the failure (such as a `SocketTimeoutException` or `HttpServerErrorException`), allowing the fallback logic to log the exact error and make intelligent degradation decisions based on the exception type.

---

# Part 2: Database Technologies

Applications rely on persistence engines to store and retrieve business state reliably. Modern architectures balance relational databases that enforce strict transactional integrity with NoSQL document stores that offer schema flexibility and in-memory caches that deliver sub-millisecond read throughput.

---

## Chapter 5: Data Persistence and Relational Database Integration with Spring Data

Relational databases remain the backbone of enterprise software, guaranteeing strong consistency, referential integrity, and ACID transactional guarantees. Spring Boot provides layered abstractions that simplify data persistence while giving developers granular control over SQL execution and performance.

### 5.0 The Database Abstraction Ladder & Core Architecture

Connecting to a relational database in Java has evolved through multiple generations of software design. Understanding this evolution explains why modern Spring Boot applications combine Spring Data JPA and `JdbcClient`.

#### The Four Rungs of the Persistence Ladder

The following diagram illustrates the persistence technologies available in Spring Boot and their trade-offs:

```mermaid
flowchart TD
    App["Spring Boot Application Layer"] --> Choices{"Choose Persistence Strategy"}
    Choices -->|"Full ORM & Complex Domain Graphs"| JPA["1. Spring Data JPA (Hibernate)"]
    Choices -->|"Direct SQL & High Throughput"| JDBC["2. JdbcClient (Spring Boot 3.2+)"]
    Choices -->|"Reactive Non-Blocking Streams"| R2DBC["3. Spring Data R2DBC"]

    JPA --> Hikari["HikariCP Connection Pool"]
    JDBC --> Hikari
    Hikari --> DB[("PostgreSQL Database Engine")]
```

1. **Raw JDBC (1997)**: The foundational Java database API. Fast, but requires manual resource management and dozens of lines of repetitive plumbing code per query.
2. **`JdbcTemplate` (2003)**: Spring's classic JDBC wrapper. It eliminated connection leaks and `SQLException` handling, but still required writing manual row mappers and positional parameters.
3. **`JdbcClient` (Spring Boot 3.2+)**: A modern, fluent synchronous SQL client. It combines named parameter binding with automatic mapping into Java Records, providing raw SQL speed with zero ORM overhead.
4. **Spring Data JPA / Hibernate (2006+)**: A complete Object-Relational Mapping (ORM) framework. It maps relational database tables and foreign keys directly into Java classes and object references, automatically tracking modifications via "dirty checking".

#### What is a Database Connection and Why Does Opening One Hurt Performance?

When a Java program talks to a database, it must establish a physical network connection over a TCP socket.

The process of opening a single raw database connection involves heavy operating system and network overhead:
1. A TCP three-way handshake (`SYN`, `SYN-ACK`, `ACK`) occurs across the network.
2. The database server authenticates the credentials (username and password).
3. The database allocates dedicated server memory (process memory, statement caches, session buffers) for that specific client connection.
4. The entire handshake takes anywhere from **30 milliseconds to 100 milliseconds**!

If an e-commerce website receives 1,000 requests per second and each request opens a brand-new physical connection, the database server will collapse within seconds simply trying to authenticate TCP handshakes!

#### HikariCP Connection Pooling Explained in Plain English

A **Connection Pool** solves this performance crisis by acting like a fleet of rental cars ready for immediate use.

Instead of opening a new connection for every query, the connection pool initializes a fixed number of authenticated connections during application startup and keeps them open in memory:
- When a service method needs to run a database query, it **borrows** an already-authenticated, idle connection from the pool. This checkout takes **less than 0.1 milliseconds**!
- The service executes the query.
- When the method completes, the service does not close the physical socket; it simply **returns** the connection back to the pool for the next thread to use.

Spring Boot uses **HikariCP** as its default connection pool because benchmarks consistently show it is the fastest, lightest, and most reliable connection pool in the Java ecosystem.

#### Sizing the Connection Pool (The Pool Size Math)

A common beginner mistake is setting the connection pool to a huge number (such as 200 or 500 connections), assuming more connections automatically mean faster throughput.

In reality, a database server has a limited number of physical CPU cores and disk spindles:
- If 200 threads try to query the disk simultaneously, the operating system spends more CPU cycles pausing and switching between threads (context switching) and thrashing disk read heads than actually executing SQL.
- A smaller pool ensures queries execute in a streamlined queue without overwhelming the database CPU.

The formula established by PostgreSQL and HikariCP engineers is:

$$\text{Pool Size} = (\text{CPU Cores} \times 2) + \text{Effective Spindle Count}$$

For example, on a 4-core database server with an SSD (effective spindle count = 1), the optimal pool size is $(4 \times 2) + 1 = 9$ connections! A pool of **10 to 20 connections** can easily service thousands of concurrent web requests when queries execute quickly.

---

### 5.1 Docker Setup & Database Connectivity

Enterprise applications should always be developed and tested against genuine database engines rather than in-memory toys like H2.

#### Spinning Up PostgreSQL with Docker

The following shell command starts an official PostgreSQL 16 container locally in a single command:

```bash
docker run -d \
  --name postgres-ecommerce \
  -e POSTGRES_DB=ecommercedb \
  -e POSTGRES_USER=postgres \
  -e POSTGRES_PASSWORD=postgres \
  -p 5432:5432 \
  postgres:16-alpine
```

#### Configuring `pom.xml` Dependencies

Add the Spring Data JPA starter and PostgreSQL JDBC driver to your project build file:

```xml
<!-- Spring Data JPA: includes Hibernate, Spring Data, and HikariCP -->
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-jpa</artifactId>
</dependency>

<!-- PostgreSQL JDBC Driver: required for Java to communicate over TCP with Postgres -->
<dependency>
    <groupId>org.postgresql</groupId>
    <artifactId>postgresql</artifactId>
    <scope>runtime</scope>
</dependency>
```

#### Configuring `application.yml` (HikariCP, DataSource, JPA)

Spring Boot automatically reads these properties to instantiate the `HikariDataSource` and configure Hibernate's `EntityManagerFactory`:

```yaml
spring:
  datasource:
    # JDBC connection URL specifying host, port, and database name
    url: jdbc:postgresql://localhost:5432/ecommercedb
    username: postgres
    password: postgres
    driver-class-name: org.postgresql.Driver
    hikari:
      maximum-pool-size: 10      # Max connections active in pool
      minimum-idle: 5            # Min idle connections kept ready
      idle-timeout: 300000       # 5 minutes before idle connection is retired
      connection-timeout: 20000  # Max wait time (20s) before throwing an exception if pool is exhausted
      pool-name: EcommerceHikariPool

  jpa:
    hibernate:
      # Schema generation strategy: validate, update, create, create-drop, none
      ddl-auto: validate
    show-sql: false              # Set to true to print raw SQL to console during development
    properties:
      hibernate:
        format_sql: true         # Pretty-prints console SQL
        default_batch_fetch_size: 25 # Mitigates N+1 query problem by batching queries
```

#### The Danger of `ddl-auto`: Why `update` Destroys Production & Why `validate` is King

The `hibernate.ddl-auto` setting tells Hibernate how to synchronize Java `@Entity` classes with the physical database tables on application startup:

- **`create`**: Drops existing tables and creates brand-new ones. **Destroys all data on every restart!**
- **`create-drop`**: Creates tables on startup and drops them on shutdown. Useful only for automated unit tests.
- **`update`**: Compares your Java classes to the database tables and automatically adds missing columns or tables. While convenient for local development, **`update` is dangerous in production** because it never drops unused columns, cannot handle column renames safely, and can lock high-traffic tables unexpectedly.
- **`validate`**: Compares your Java entities to the existing database tables. If any column, table, or data type does not match, **it refuses to start the application and throws an error**. This is the **recommended production setting**.
- **`none`**: Disables all schema inspection and generation completely.

---

### 5.1.1 Zero-Config Local Containers with `spring-boot-docker-compose`

In older Spring Boot versions, developers had to manually run `docker run` or `docker compose up -d` before starting their application, and had to copy database ports and passwords into `application.yml`. If they forgot to boot Docker, the app crashed immediately.

**Spring Boot 3.1 introduced automatic Docker Compose support!**

#### How It Works:
When you add `spring-boot-docker-compose` to your build, Spring Boot automatically discovers your `compose.yaml` file on startup:
1. It executes `docker compose up` in the background.
2. It waits for PostgreSQL to pass its healthcheck.
3. It **automatically extracts the dynamically assigned database port, username, and password** and binds them to Spring's `DataSource`!
4. You do not need **ANY database URL, username, or password in `application.yml`**!
5. When you stop the Spring Boot application (e.g. clicking Stop in IntelliJ), Spring Boot automatically stops the container.

#### Step 1: Add Dependency to `pom.xml`

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-docker-compose</artifactId>
    <scope>runtime</scope>
    <optional>true</optional>
</dependency>
```

#### Step 2: Create `compose.yaml` in the Project Root Directory

```yaml
services:
  postgres:
    image: 'postgres:16-alpine'
    environment:
      - 'POSTGRES_DB=ecommercedb'
      - 'POSTGRES_USER=postgres'
      - 'POSTGRES_PASSWORD=secret'
    ports:
      - '5432' # Leaving host port blank allows Docker to assign an available ephemeral port!
```

#### Step 3: Run the Application!

Execute `./mvnw spring-boot:run`. Spring Boot's console logs:
```text
Using Docker Compose file: /Users/pushkar/Desktop/my-project/compose.yaml
Created container: my-project-postgres-1
Started container: my-project-postgres-1
Connected to PostgreSQL at 127.0.0.1:5432
```
Zero configuration, zero port collisions across developer laptops!

---

### 5.2 Lightweight High-Speed SQL with `JdbcClient`

While Spring Data JPA is ideal for rich object domain models, many real-world scenarios (such as analytics, high-throughput bulk operations, and reporting dashboards) are best handled using direct SQL.

#### Why `JdbcClient` in Spring Boot 3.2+ is a Game Changer

Prior to Spring Boot 3.2, developers had to choose between the heavy ORM overhead of Hibernate or the verbose boilerplate of legacy `JdbcTemplate` (which required manual `RowMapper` implementations).

`JdbcClient` provides a modern, fluent synchronous API that:
- Uses named parameters (`:id`, `:email`) to prevent SQL injection.
- Automatically maps SQL query columns directly into Java 17 Records without writing a single line of mapping code.
- Executes direct SQL without Hibernate dirty checking, entity tracking, or proxy overhead.

#### Scenario 1: Fetching Single Records into Java Records with Named Parameters

Suppose we have a table called `products` and want to fetch a lightweight read representation:

The following code defines an immutable Java Record and queries a single row using `JdbcClient`:

```java
package com.example.demo.repository;

import org.springframework.jdbc.core.simple.JdbcClient;
import org.springframework.stereotype.Repository;

import java.util.Optional;

// 1. Immutable Data Transfer Record matching the SQL column names
public record ProductSummary(Long id, String title, double price) {}

@Repository
public class ProductSummaryRepository {

    private final JdbcClient jdbcClient;

    // Spring Boot automatically injects the auto-configured JdbcClient
    public ProductSummaryRepository(JdbcClient jdbcClient) {
        this.jdbcClient = jdbcClient;
    }

    public Optional<ProductSummary> getSummaryById(Long id) {
        return jdbcClient.sql("SELECT id, title, price FROM products WHERE id = :id")
                .param("id", id) // Binds named parameter safely against SQL injection
                .query(ProductSummary.class) // Automatically maps columns to ProductSummary constructor!
                .optional(); // Returns Optional.empty() if no row found, or Optional.of(summary)
    }
}
```

#### Scenario 2: Querying Lists and Handling Missing Rows Gracefully

When querying multiple rows with dynamic filtering parameters, `JdbcClient` provides a clean `.list()` method:

The following method demonstrates querying a list of records with multiple filter parameters:

```java
public List<ProductSummary> getProductsByPriceRange(double minPrice, double maxPrice, int limit) {
    return jdbcClient.sql("""
            SELECT id, title, price 
            FROM products 
            WHERE price >= :minPrice AND price <= :maxPrice 
            ORDER BY price ASC 
            LIMIT :limit
            """)
            .param("minPrice", minPrice)
            .param("maxPrice", maxPrice)
            .param("limit", limit)
            .query(ProductSummary.class)
            .list(); // Returns an empty List if no matching rows exist (never null)
}
```

#### Scenario 3: High-Throughput Bulk Inserts & Updates

When updating 50,000 rows in a database, loading 50,000 Hibernate entities into memory to modify them is catastrophically slow. Direct SQL execution with `JdbcClient` executes in milliseconds:

The following method executes a high-speed bulk update directly on the database server:

```java
public int applyCategoryDiscount(Long categoryId, double discountPercentage) {
    // Calculates updated price directly inside the SQL engine
    return jdbcClient.sql("""
            UPDATE products 
            SET price = price * (1.0 - :discount / 100.0) 
            WHERE category_id = :catId
            """)
            .param("discount", discountPercentage)
            .param("catId", categoryId)
            .update(); // Returns the integer count of affected database rows
}
```

#### Scenario 4: Mapping Complex Column Aliases

What if database column names do not match your Java Record field names? For example, if the database column is `prod_name` but your Record has `title`:

The following code demonstrates using SQL column aliases (`AS`) to map mismatched names to Record components:

```java
public Optional<ProductSummary> getProductWithAliasedColumns(Long id) {
    // Alias the SQL columns to match the Record component names: 'id', 'title', 'price'
    return jdbcClient.sql("""
            SELECT 
                product_id AS id, 
                prod_name AS title, 
                retail_price AS price 
            FROM products 
            WHERE product_id = :id
            """)
            .param("id", id)
            .query(ProductSummary.class)
            .optional();
}
```

---

### 5.3 Entity Modeling & Jakarta Persistence (JPA)

When building complex domain logic where objects have relationships, lifecycle events, and business rules, Spring Data JPA and Hibernate provide automated Object-Relational Mapping (ORM).

#### What is an Entity? (POJO vs Record, Why Records Cannot Be Entities)

A **JPA Entity** is a lightweight, persistent domain object that represents a table row in a relational database.

> [!WARNING]
> **Why Java Records CANNOT Be JPA Entities**:
> - JPA specifications require entities to have a **no-argument constructor** so Hibernate can instantiate them using reflection.
> - JPA requires entities to be **mutable** because Hibernate's "dirty checking" engine tracks field modifications and issues SQL updates automatically.
> - Hibernate creates dynamic runtime subclasses (proxies) for lazy loading; Java Records are `final` and cannot be subclassed.
> - **Rule**: Use mutable POJO classes for `@Entity` models; use immutable Java Records for DTOs and API payloads!

#### Primary Key Generation Strategies: `IDENTITY` vs `SEQUENCE` vs `UUID`

Every entity must have a primary key annotated with `@Id`. JPA supports three primary generation strategies:

1. **`GenerationType.IDENTITY`**: Relies on the database engine's auto-incrementing column (e.g., PostgreSQL `BIGSERIAL` or MySQL `AUTO_INCREMENT`). Simple, but disables Hibernate's JDBC batch insert optimization because Hibernate must immediately execute `INSERT` to retrieve the generated ID.
2. **`GenerationType.SEQUENCE`**: Relies on a database sequence object. Hibernate can pre-allocate blocks of 50 IDs in advance, allowing high-speed batch inserts. **Recommended for high-throughput write workloads.**
3. **`UUID`**: Uses a 128-bit globally unique identifier. Ideal for distributed microservices where client applications generate IDs before contacting the database.

The following entity demonstrates configuring a sequence-based primary key:

```java
package com.example.demo.domain;

import jakarta.persistence.*;

@Entity
@Table(name = "customers")
public class Customer {

    @Id
    @GeneratedValue(strategy = GenerationType.SEQUENCE, generator = "customer_seq")
    @SequenceGenerator(name = "customer_seq", sequenceName = "customer_id_seq", allocationSize = 50)
    private Long id;

    @Column(nullable = false, length = 100)
    private String fullName;

    protected Customer() {} // JPA requires a no-arg constructor

    public Customer(String fullName) {
        this.fullName = fullName;
    }

    public Long getId() { return id; }
    public String getFullName() { return fullName; }
}
```

#### Auditing Entities Automatically: `@CreatedDate`, `@LastModifiedDate`, `@EntityListeners`

In enterprise applications, every database table should track when it was created and when it was last modified. Spring Data JPA provides automated auditing annotations so you never have to set timestamps manually:

The following base class provides automated creation and modification timestamp tracking for all child entities:

```java
package com.example.demo.domain;

import jakarta.persistence.Column;
import jakarta.persistence.EntityListeners;
import jakarta.persistence.MappedSuperclass;
import org.springframework.data.annotation.CreatedDate;
import org.springframework.data.annotation.LastModifiedDate;
import org.springframework.data.jpa.domain.support.AuditingEntityListener;

import java.time.Instant;

@MappedSuperclass // Tells JPA this is not a table, but child entities inherit these columns
@EntityListeners(AuditingEntityListener.class) // Activates Spring Data's auditing listener
public abstract class AuditableEntity {

    @CreatedDate
    @Column(nullable = false, updatable = false)
    private Instant createdAt; // Automatically set when entity is first saved

    @LastModifiedDate
    @Column(nullable = false)
    private Instant updatedAt; // Automatically updated every time entity is modified

    public Instant getCreatedAt() { return createdAt; }
    public Instant getUpdatedAt() { return updatedAt; }
}
```

To enable auditing, add `@EnableJpaAuditing` to your main `@SpringBootApplication` or `@Configuration` class:

```java
@Configuration
@EnableJpaAuditing // Activates automated timestamp auditing
public class JpaConfig {}
```

#### Enumerations and Value Objects: `@Enumerated(EnumType.STRING)` and `@Embeddable`

Beyond basic primitives, JPA allows mapping rich domain types such as type-safe enums and multi-column value objects:

##### Mapping Java Enums Safely

By default, JPA stores enums as integer ordinals (`0, 1, 2`). If another developer reorders or inserts an enum value later, all existing database records will point to the wrong enum! **Always use `EnumType.STRING`**:

The following entity demonstrates safe string-based enum mapping:

```java
public enum OrderStatus { PENDING, PAID, SHIPPED, CANCELLED }

@Entity
@Table(name = "orders")
public class OrderEntity {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    // Stores "PENDING", "PAID", etc. as varchar text in the database column
    @Enumerated(EnumType.STRING)
    @Column(nullable = false, length = 20)
    private OrderStatus status = OrderStatus.PENDING;
}
```

##### Value Objects with `@Embeddable` and `@Embedded`

When grouping related fields (such as street, city, and zip code) that belong to the same database table, use `@Embeddable`:

The following classes demonstrate embedding address fields into a customer table:

```java
package com.example.demo.domain;

import jakarta.persistence.Embeddable;

// Embeddable value object: does NOT have its own table; its fields live in the parent table
@Embeddable
public record Address(String street, String city, String zipCode) {
    public Address() { this(null, null, null); } // JPA compatibility constructor
}
```

```java
@Entity
@Table(name = "users")
public class UserEntity {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;

    // Embedded in users table: creates columns 'street', 'city', and 'zip_code' in users table
    @Embedded
    private Address shippingAddress;
}
```

---

### 5.4 Mastering Entity Relationships

Relational databases connect data through foreign keys. JPA represents foreign keys using relationship annotations.

#### Relationship 1: `@ManyToOne` (The Most Common & Important Association)

In relational databases, foreign keys reside on the "child" table pointing to the "parent" table. In JPA, this is represented by `@ManyToOne`.

> [!CRITICAL]
> **The Golden Rule of Associations**:
> `@ManyToOne` defaults to `FetchType.EAGER`. Eager fetching causes Hibernate to automatically execute joins or extra select queries every time the child is loaded, destroying performance. **ALWAYS explicitly set `fetch = FetchType.LAZY`!**

The following entity demonstrates a child record holding a foreign key to a parent category:

```java
package com.example.demo.domain;

import jakarta.persistence.*;

@Entity
@Table(name = "products")
public class Product {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @Column(nullable = false)
    private String title;

    // Many Products belong to One Category
    // 1. fetch = FetchType.LAZY prevents loading Category until getCategory() is called
    // 2. @JoinColumn specifies the foreign key column name in the 'products' table
    @ManyToOne(fetch = FetchType.LAZY)
    @JoinColumn(name = "category_id", nullable = false)
    private Category category;

    protected Product() {}

    public Product(String title, Category category) {
        this.title = title;
        this.category = category;
    }

    public Long getId() { return id; }
    public String getTitle() { return title; }
    public Category getCategory() { return category; }
    public void setCategory(Category category) { this.category = category; }
}
```

#### Relationship 2: `@OneToMany` with `mappedBy` (Bidirectional Sync & Helper Methods)

When the parent entity also wants a collection reference to its children, add `@OneToMany`:
- `mappedBy = "category"`: Tells Hibernate that the foreign key is already owned by the `category` field in the `Product` entity. Without `mappedBy`, Hibernate creates an unnecessary third join table!
- `fetch = FetchType.LAZY`: The default for `@OneToMany`, ensuring items are only loaded when accessed.

The following parent entity demonstrates bidirectional synchronization:

```java
package com.example.demo.domain;

import jakarta.persistence.*;
import java.util.ArrayList;
import java.util.List;

@Entity
@Table(name = "categories")
public class Category {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @Column(nullable = false, unique = true)
    private String name;

    // One Category has Many Products
    @OneToMany(mappedBy = "category", cascade = CascadeType.ALL, orphanRemoval = true, fetch = FetchType.LAZY)
    private List<Product> products = new ArrayList<>();

    protected Category() {}

    public Category(String name) {
        this.name = name;
    }

    // Bidirectional Helper Method: keeps both sides of the Java object graph in sync!
    public void addProduct(String productTitle) {
        Product product = new Product(productTitle, this);
        this.products.add(product);
    }

    public void removeProduct(Product product) {
        this.products.remove(product);
        product.setCategory(null);
    }

    public Long getId() { return id; }
    public String getName() { return name; }
    public List<Product> getProducts() { return products; }
}
```

#### Cascade Types Explained: `PERSIST`, `MERGE`, `REMOVE`, `ALL`, and `orphanRemoval`

The `cascade` attribute tells Hibernate whether operations performed on the parent should automatically propagate to the children:

- **`CascadeType.PERSIST`**: Saving a new parent automatically saves all its new children in the database.
- **`CascadeType.MERGE`**: Updating an existing detached parent automatically updates its children.
- **`CascadeType.REMOVE`**: Deleting a parent automatically executes SQL `DELETE` for all its children.
- **`CascadeType.ALL`**: Combines `PERSIST`, `MERGE`, `REMOVE`, `REFRESH`, and `DETACH`.
- **`orphanRemoval = true`**: If you remove a child from the parent's collection (`category.getProducts().remove(product)`), Hibernate automatically emits a SQL `DELETE` to purge that orphaned child from the database table.

#### Relationship 3: `@ManyToMany` Done Right (Why the Naive Way Fails & How to Use an Intermediate Join Entity)

In many domains, entities have many-to-many relationships (e.g., `Student` and `Course`, or `User` and `Role`). While JPA provides `@ManyToMany`, senior engineers avoid direct `@ManyToMany` in production for two critical reasons:
1. You cannot add additional metadata to the relationship (such as `enrolledDate`, `grade`, or `assignedBy`).
2. Hibernate handles removals in direct `@ManyToMany` inefficiently by deleting all rows in the join table and re-inserting the remaining ones!

**The Professional Solution**: Decompose `@ManyToMany` into two `@ManyToOne` relationships using an explicit intermediate join entity:

The following code models an enrollment join entity with custom relationship attributes:

```mermaid
erDiagram
    STUDENT ||--o{ ENROLLMENT : has
    COURSE ||--o{ ENROLLMENT : contains
```

```java
package com.example.demo.domain;

import jakarta.persistence.*;
import java.time.Instant;

@Entity
@Table(name = "enrollments")
public class Enrollment {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @ManyToOne(fetch = FetchType.LAZY)
    @JoinColumn(name = "student_id", nullable = false)
    private Student student;

    @ManyToOne(fetch = FetchType.LAZY)
    @JoinColumn(name = "course_id", nullable = false)
    private Course course;

    // Extra relationship metadata impossible with plain @ManyToMany!
    @Column(nullable = false)
    private Instant enrolledAt = Instant.now();

    private Integer gradeScore;

    protected Enrollment() {}

    public Enrollment(Student student, Course course) {
        this.student = student;
        this.course = course;
    }

    public Long getId() { return id; }
    public Student getStudent() { return student; }
    public Course getCourse() { return course; }
    public Instant getEnrolledAt() { return enrolledAt; }
}
```

---

### 5.5 Querying with Spring Data Repositories

Spring Data JPA allows developers to interact with the database simply by declaring Java interfaces. At runtime, Spring dynamically generates proxy classes implementing these interfaces.

#### Derived Query Methods: Syntax Cheat Sheet & Common Patterns

Spring Data parses method names into SQL queries based on keywords:

| Method Name in Interface | Generated SQL Clause |
| :--- | :--- |
| `findByTitle(String title)` | `WHERE title = ?` |
| `findByTitleIgnoreCase(String title)` | `WHERE UPPER(title) = UPPER(?)` |
| `findByPriceLessThan(double price)` | `WHERE price < ?` |
| `findByPriceBetween(double min, double max)` | `WHERE price BETWEEN ? AND ?` |
| `findByTitleContaining(String keyword)` | `WHERE title LIKE '%keyword%'` |
| `findByCategoryNameOrderByPriceDesc(String cat)` | `WHERE c.name = ? ORDER BY price DESC` |
| `existsByEmail(String email)` | `SELECT CASE WHEN COUNT(...) > 0 THEN true...` |
| `countByStatus(OrderStatus status)` | `SELECT COUNT(*) WHERE status = ?` |

#### Custom JPQL Queries with `@Query`

When queries become complex, derived method names become unwieldy (e.g., `findByTitleAndCategoryNameAndPriceLessThan...`). Use Jakarta Persistence Query Language (JPQL), which queries your **Java Entities and Fields** rather than database tables and columns:

The following repository demonstrates custom JPQL queries with named parameters:

```java
package com.example.demo.repository;

import com.example.demo.domain.Product;
import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.data.jpa.repository.Query;
import org.springframework.data.repository.query.Param;
import org.springframework.stereotype.Repository;

import java.util.List;

@Repository
public interface ProductRepository extends JpaRepository<Product, Long> {

    // JPQL queries against the Java Class 'Product' and its field 'category.name'
    @Query("SELECT p FROM Product p WHERE p.category.name = :catName AND p.title LIKE %:keyword%")
    List<Product> searchByCategoryAndKeyword(
            @Param("catName") String categoryName, 
            @Param("keyword") String keyword
    );
}
```

#### Native SQL Queries with PostgreSQL-Specific Operators

If you need database-specific features (such as PostgreSQL's JSONB operators `->>`, full-text search `to_tsvector`, or spatial functions), pass `nativeQuery = true`:

The following repository method executes a PostgreSQL-specific native query:

```java
// nativeQuery = true executes raw SQL directly against the physical PostgreSQL tables
@Query(value = """
        SELECT * FROM products p 
        WHERE p.metadata ->> 'brand' = :brandName 
        ORDER BY p.price ASC
        """, nativeQuery = true)
List<Product> findByBrandInJsonbMetadata(@Param("brandName") String brandName);
```

#### Projections: Fetching Partial Data (Record Projections vs Interface Projections)

If an entity contains 30 columns, but your API endpoint only needs the product `id` and `title`, loading the entire entity is wasteful. **Projections** allow querying only the required columns directly into a Java Record:

The following code demonstrates a type-safe Record projection:

```java
// 1. Define Record containing only the needed fields
public record ProductListingView(Long id, String title) {}

// 2. Declare projection method in repository
@Repository
public interface ProductProjectionRepository extends JpaRepository<Product, Long> {
    
    // Spring Data constructs ProductListingView directly from the SQL SELECT statement!
    @Query("SELECT p.id AS id, p.title AS title FROM Product p WHERE p.category.name = :cat")
    List<ProductListingView> findListingViewsByCategory(@Param("cat") String category);
}
```

#### Pagination and Sorting: `Pageable`, `Sort`, and `Page<T>` vs `Slice<T>`

Loading 100,000 rows into memory will crash your server with an `OutOfMemoryError`. Real applications always paginate data using Spring Data's `Pageable`.

##### Understanding `Page<T>` vs `Slice<T>`

Spring Data provides two pagination abstractions optimized for different user interface experiences:

- **`Page<T>`**: Executes **two queries**: the main query to fetch the page data, plus an expensive `SELECT COUNT(*)` query to calculate total pages. Use when you need numbered pagination buttons (`1, 2, 3... 10`).
- **`Slice<T>`**: Fetches $N + 1$ rows to check if a next page exists, but **skips the expensive `COUNT(*)` query**. **Best practice for mobile infinite scrolling feeds!**

The following repository demonstrates paginated queries:

```java
package com.example.demo.repository;

import com.example.demo.domain.Product;
import org.springframework.data.domain.Page;
import org.springframework.data.domain.Pageable;
import org.springframework.data.domain.Slice;
import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.stereotype.Repository;

@Repository
public interface PaginatedProductRepository extends JpaRepository<Product, Long> {

    // 1. Returns Page: includes total elements and total pages count
    Page<Product> findByCategoryName(String categoryName, Pageable pageable);

    // 2. Returns Slice: skips COUNT(*) query for high performance infinite scrolling
    Slice<Product> findByTitleContaining(String keyword, Pageable pageable);
}
```

The following service demonstrates calling paginated repository methods:

```java
@Service
public class CatalogService {

    private final PaginatedProductRepository repository;

    public CatalogService(PaginatedProductRepository repository) {
        this.repository = repository;
    }

    public Page<Product> getProducts(int pageIndex, int pageSize) {
        // Page index is zero-based: 0 = page 1, 1 = page 2
        // Sort by title ascending, then price descending
        Pageable pageable = PageRequest.of(pageIndex, pageSize, 
                Sort.by("title").ascending().and(Sort.by("price").descending()));

        return repository.findByCategoryName("Electronics", pageable);
    }
}
```

---

### 5.6 The N+1 Query Problem: Complete Deep Dive

The N+1 query problem is the single most destructive performance flaw in enterprise Spring applications.

#### What is the N+1 Problem and Why Does It Happen? (SQL Trace Proof)

Suppose we have 5 categories, and each category has products. We write this innocent loop:

```java
List<Category> categories = categoryRepository.findAll();
for (Category cat : categories) {
    System.out.println("Category " + cat.getName() + " has " + cat.getProducts().size() + " products.");
}
```

Let us look at the raw SQL trace generated by Hibernate:

```sql
-- Query 1: The initial query fetching all 5 categories
SELECT id, name FROM categories;

-- Query 2: Triggered inside the loop for Category 1
SELECT id, title, category_id FROM products WHERE category_id = 1;

-- Query 3: Triggered inside the loop for Category 2
SELECT id, title, category_id FROM products WHERE category_id = 2;

-- Query 4: Triggered inside the loop for Category 3
SELECT id, title, category_id FROM products WHERE category_id = 3;

-- Query 5: Triggered inside the loop for Category 4
SELECT id, title, category_id FROM products WHERE category_id = 4;

-- Query 6: Triggered inside the loop for Category 5
SELECT id, title, category_id FROM products WHERE category_id = 5;
```

Notice: We executed **1 initial query** + **5 additional queries** = **6 queries total**!
If our database had 500 categories, Hibernate would execute **501 separate database round-trips** across the network, freezing the web request for seconds.

#### Solution 1: JPQL `JOIN FETCH`

`JOIN FETCH` instructs Hibernate to issue an SQL `LEFT JOIN` and load both the parent category and its child products in **one single SQL query**:

The following repository method eliminates the N+1 query problem using `JOIN FETCH`:

```java
@Repository
public interface CategoryRepository extends JpaRepository<Category, Long> {

    // Solves N+1: Executes 1 single SQL query joining categories and products!
    @Query("SELECT DISTINCT c FROM Category c LEFT JOIN FETCH c.products")
    List<Category> findAllWithProductsFetch();
}
```

Now, Hibernate emits only **1 SQL query**:

```sql
SELECT DISTINCT c.id, c.name, p.id, p.title, p.category_id 
FROM categories c 
LEFT OUTER JOIN products p ON c.id = p.category_id;
```

#### Solution 2: `@EntityGraph` (Dynamic Lazy Override)

If you prefer using Spring Data's derived query methods without writing explicit JPQL, use `@EntityGraph`:

The following repository method uses `@EntityGraph` to eagerly load products:

```java
@Repository
public interface CategoryGraphRepository extends JpaRepository<Category, Long> {

    // Overrides FetchType.LAZY dynamically for this specific query method
    @EntityGraph(attributePaths = {"products"})
    List<Category> findByNameStartingWith(String prefix);
}
```

#### Solution 3: Hibernate Batch Fetching (`default_batch_fetch_size`)

What if a service method calls existing code where you cannot rewrite the query with `JOIN FETCH`?
Configure Hibernate's batch fetch size in `application.yml`:

```yaml
spring:
  jpa:
    properties:
      hibernate:
        default_batch_fetch_size: 25 # Batches lazy collection loading
```

Instead of running 500 individual queries (`WHERE id = 1`, `WHERE id = 2`...), Hibernate groups the IDs into batches of 25 using the SQL `IN` operator:

```sql
-- Batch query loads 25 categories' items simultaneously!
SELECT * FROM products WHERE category_id IN (1, 2, 3, 4, ... 25);
```

This immediately slashes query counts from 501 down to 21 queries!

---

### 5.7 Database Schema Version Control with Flyway

In professional engineering teams, developers never modify database tables manually or use `ddl-auto=update`. All database changes are tracked in versioned SQL migration scripts using **Flyway**.

#### Why Automated Schema Migrations are Essential

Automated schema management eliminates manual database tampering and drift across deployment environments:

- **Reproducibility**: Every developer, test environment, and production server runs the exact same schema.
- **Auditability**: Database migrations are committed to Git, showing who changed which column and why.
- **Zero Drift**: Prevents accidental discrepancies between staging and production databases.

#### Setting Up Flyway in Spring Boot

Include the Flyway starter in `pom.xml`:

```xml
<dependency>
    <groupId>org.flywaydb</groupId>
    <artifactId>flyway-core</artifactId>
</dependency>
<dependency>
    <groupId>org.flywaydb</groupId>
    <artifactId>flyway-database-postgresql</artifactId>
</dependency>
```

#### Writing Versioned Migration Scripts (`V1__init.sql`, `V2__add_index.sql`)

Flyway looks for SQL scripts inside `src/main/resources/db/migration/`.
The naming convention is strict: `V<Version>__<Description>.sql` (note the **two underscores**):

The following script (`V1__init_schema.sql`) creates the initial tables:

```sql
-- src/main/resources/db/migration/V1__init_schema.sql

CREATE TABLE categories (
    id BIGSERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL UNIQUE
);

CREATE TABLE products (
    id BIGSERIAL PRIMARY KEY,
    title VARCHAR(200) NOT NULL,
    price NUMERIC(10, 2) NOT NULL,
    category_id BIGINT NOT NULL,
    CONSTRAINT fk_products_categories FOREIGN KEY (category_id) REFERENCES categories(id)
);
```

When new features require an index, create a second migration script:

```sql
-- src/main/resources/db/migration/V2__add_product_title_index.sql

CREATE INDEX idx_products_title ON products(title);
```

When Spring Boot starts up, Flyway inspects its internal `flyway_schema_history` table and automatically applies any newly added SQL scripts in sequential order.

---

### 5.8 Transaction Management with `@Transactional`

A database transaction is an atomic unit of work enforcing ACID guarantees: either all operations succeed and are permanently committed, or any failure triggers an immediate rollback to the previous state.

#### How Transactions Work (Spring AOP Proxy Mechanism)

Spring manages transactions declaratively using Aspect-Oriented Programming (AOP). When you annotate a class or method with `@Transactional`, Spring creates a dynamic proxy around your bean:

```mermaid
sequenceDiagram
    autonumber
    actor Caller as Web Controller
    participant Proxy as Spring AOP Transaction Proxy
    participant Service as OrderService (Target Bean)
    participant Pool as HikariCP / Database

    Caller->>Proxy: processOrder()
    Proxy->>Pool: Borrow Connection & execute "BEGIN TRANSACTION"
    Proxy->>Service: Execute processOrder() method body
    Service->>Pool: Execute SQL operations
    alt Method completes normally
        Service-->>Proxy: Return result
        Proxy->>Pool: Execute "COMMIT" & return connection to pool
        Proxy-->>Caller: Success
    else Uncaught Exception occurs
        Service-->>Proxy: Throws Exception
        Proxy->>Pool: Execute "ROLLBACK" & return connection to pool
        Proxy-->>Caller: Exception rethrown / database unaffected!
    end
```

#### Transaction Propagation Levels Explained with Real-World Scenarios

Spring supports 7 propagation behaviors. Understanding the top two is essential for every developer:

1. **`Propagation.REQUIRED` (Default)**: If a transaction already exists, join it. If no transaction exists, start a brand-new one. **Used for 99% of business operations.**
2. **`Propagation.REQUIRES_NEW`**: Always suspends the current transaction and starts a completely independent new transaction! If the outer transaction later fails and rolls back, the `REQUIRES_NEW` transaction **remains committed**. Ideal for audit logs or security event recording where the log entry must be saved even if the order fails!

The following service demonstrates `REQUIRES_NEW` for audit logging:

```java
package com.example.demo.service;

import org.springframework.stereotype.Service;
import org.springframework.transaction.annotation.Propagation;
import org.springframework.transaction.annotation.Transactional;

@Service
public class AuditLogService {

    // Runs in its own independent transaction!
    // If the caller transaction fails, this audit log still commits permanently to the database.
    @Transactional(propagation = Propagation.REQUIRES_NEW)
    public void recordSecurityEvent(String username, String action) {
        System.out.println("Audit recorded: " + username + " -> " + action);
    }
}
```

#### Transaction Isolation Levels: Dirty Reads, Non-Repeatable Reads, Phantom Reads

Isolation controls how concurrent transactions see changes made by other transactions:

- **`ISOLATION_READ_COMMITTED` (PostgreSQL Default)**: Prevents *Dirty Reads* (reading uncommitted data from another transaction). A transaction only sees data that has already been committed.
- **`ISOLATION_REPEATABLE_READ`**: Prevents *Non-Repeatable Reads* (re-reading the same row within a transaction will always return the exact same data, even if another transaction committed an update).
- **`ISOLATION_SERIALIZABLE`**: Highest isolation. Completely locks affected rows, executing concurrent transactions sequentially. Prevents *Phantom Reads*, but severely reduces concurrency throughput.

#### Rollback Rules: The Checked vs Unchecked Exception Trap

By default, Spring's `@Transactional` only rolls back on **unchecked exceptions** (subclasses of `RuntimeException` and `Error`). If a method throws a standard **checked exception** (subclass of `java.lang.Exception`), Spring **commits the transaction anyway**!

To ensure transactions roll back on all exceptions, always specify `rollbackFor`:

```java
// CRITICAL: rollbackFor = Exception.class guarantees rollback on BOTH checked and unchecked exceptions!
@Transactional(rollbackFor = Exception.class)
public void executeFinancialTransfer(String fromAcc, String toAcc, double amount) throws InsufficientFundsException {
    debit(fromAcc, amount);
    if (!verifySolvency(fromAcc)) {
        throw new InsufficientFundsException("Insufficient funds!"); // Checked exception
    }
    credit(toAcc, amount);
}
```

#### Pitfall: Self-Invocation Proxy Bypass and How to Avoid It

Because Spring transactions rely on AOP proxies, calling a `@Transactional` method from another method **within the same class** completely bypasses the proxy!

The following code illustrates this trap and its solution:

```java
@Service
public class OrderService {

    public void processCheckout() {
        // BUG! 'this.saveOrder()' calls the internal Java method directly, bypassing the Spring Proxy!
        // The @Transactional annotation on saveOrder() is completely IGNORED!
        this.saveOrder();
    }

    @Transactional(rollbackFor = Exception.class)
    public void saveOrder() {
        // Transaction will NOT be created if called via processCheckout()!
    }
}
```

**The Fix**: Place `@Transactional` on the public method called from outside the class, or move `saveOrder()` into a separate collaborator service bean.

#### Performance Optimization: `readOnly = true`

On queries and read operations, always configure `@Transactional(readOnly = true)`:

```java
@Transactional(readOnly = true)
public Product getProduct(Long id) {
    return productRepository.findById(id).orElseThrow();
}
```

When `readOnly = true` is set:
1. Hibernate disables **dirty checking** (it skips taking snapshot copies of entities in memory), reducing CPU usage and memory footprint.
2. Spring sets the JDBC connection to read-only mode, allowing database engines (like PostgreSQL) to route queries to read-replicas.

---

### 5.8.1 Concurrency Control: Optimistic vs. Pessimistic Locking

When multiple users or background threads read and update the same database row simultaneously, applications face severe data corruption bugs called **Lost Updates** and **Race Conditions**.

#### The Lost Update Disaster Explained

Imagine an e-commerce flash sale where an item has **1 unit left in stock** (`stock = 1`). Two customers, Alice and Bob, click "Buy Now" at the exact same millisecond:

```mermaid
sequenceDiagram
    autonumber
    participant Alice as Alice's Request (Thread 1)
    participant Bob as Bob's Request (Thread 2)
    participant DB as PostgreSQL Database

    Alice->>DB: SELECT stock FROM products WHERE id = 42; (Returns stock = 1)
    Bob->>DB: SELECT stock FROM products WHERE id = 42; (Returns stock = 1)

    Note over Alice: Alice verifies stock > 0.<br/>Computes new stock = 0.
    Note over Bob: Bob verifies stock > 0.<br/>Computes new stock = 0.

    Alice->>DB: UPDATE products SET stock = 0 WHERE id = 42;
    Bob->>DB: UPDATE products SET stock = 0 WHERE id = 42;

    Note over DB: DISASTER! Both orders were confirmed,<br/>but only 1 item existed in physical inventory!
```

To prevent this data corruption, enterprise architectures use **Concurrency Control Locks**.

---

#### Which Layer Does What? (Architectural Taxonomy)

A common point of beginner confusion is not knowing which layer manages locking:

```mermaid
flowchart TD
    Web["1. Controller / Web Layer\nCatches Lock Exceptions & Translates to HTTP 409 Conflict"] --> Service["2. Service Layer (@Transactional)\nDefines transaction boundaries & retry policies (@Retryable)"]
    Service --> Repo["3. Repository Layer (@Lock)\nSpecifies lock type (PESSIMISTIC_WRITE, PESSIMISTIC_READ)"]
    Repo --> Entity["4. Entity Domain Layer (@Version)\nDeclares version field for Optimistic verification"]
    Entity --> DB[("5. Database Engine Layer\nExecutes row-level locks (SELECT ... FOR UPDATE)")]

    style Web fill:#e1f5fe,stroke:#0288d1
    style Service fill:#c8e6c9,stroke:#388e3c,stroke-width:2px
    style Repo fill:#fff9c4,stroke:#fbc02d
    style Entity fill:#ffe0b2,stroke:#f57c00
    style DB fill:#ede7f6,stroke:#7e57c2
```

| Layer | Annotation Used | Purpose |
| :--- | :--- | :--- |
| **Domain Entity** | `@Version` | Tells Hibernate to track an entity modification counter for **Optimistic Locking**. |
| **Data Repository** | `@Lock(LockModeType.PESSIMISTIC_WRITE)` | Instructs JPA to append `FOR UPDATE` to the SQL query for **Pessimistic Locking**. |
| **Service Layer** | `@Transactional` & `@Retryable` | Controls transaction boundaries and automatically retries transactions that fail due to optimistic collisions. |
| **Database Engine** | Engine Lock Tables | Physically blocks competing transactions at the disk/row level. |

---

#### 1. Optimistic Locking: "Hope for the Best, Verify on Write"

##### What is it?
Optimistic locking **does not lock the database row** while reading or modifying data. Instead, it assumes conflicts are rare. When saving changes, it checks whether another transaction modified the row since it was originally read.

##### How it works:
1. Add a `@Version` field to the JPA entity (`Integer` or `Long`).
2. When Hibernate reads the entity, it records the current version (e.g., `version = 1`).
3. When saving, Hibernate automatically increments the version and appends a `WHERE version = ?` clause to the SQL `UPDATE`:
   ```sql
   UPDATE products 
   SET stock_quantity = 0, version = 2 
   WHERE id = 42 AND version = 1;
   ```
4. If another transaction already committed an update, the database version is now `2`. The `WHERE version = 1` condition matches **0 rows**!
5. Hibernate notices that 0 rows were updated and immediately throws `OptimisticLockException` (translated by Spring into `ObjectOptimisticLockingFailureException`).

```mermaid
sequenceDiagram
    autonumber
    participant T1 as Thread 1 (Alice)
    participant T2 as Thread 2 (Bob)
    participant DB as Database (Product #42, version = 1)

    T1->>DB: SELECT * FROM products WHERE id = 42; (version = 1)
    T2->>DB: SELECT * FROM products WHERE id = 42; (version = 1)

    Note over T1: Computes new stock...
    Note over T2: Computes new stock...

    T1->>DB: UPDATE products SET stock = 0, version = 2 WHERE id = 42 AND version = 1;
    DB-->>T1: 1 row updated (SUCCESS!)

    T2->>DB: UPDATE products SET stock = 0, version = 2 WHERE id = 42 AND version = 1;
    DB-->>T2: 0 rows updated! (Version is already 2)
    Note over T2: Hibernate throws OptimisticLockException! Transaction Rolled Back.
```

##### Complete Optimistic Locking Code:

```java
// 1. Entity Definition
package com.example.demo.product.domain;

import jakarta.persistence.*;

@Entity
@Table(name = "products")
public class Product {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;
    private int stockQuantity;

    // MANDATORY: The @Version annotation activates JPA Optimistic Locking
    @Version
    private Long version;

    // Standard getters, setters, constructors
    public void deductStock(int quantity) {
        if (this.stockQuantity < quantity) {
            throw new IllegalStateException("Insufficient inventory!");
        }
        this.stockQuantity -= quantity;
    }
}
```

```java
// 2. Service Layer with Automated Retries
package com.example.demo.product.service;

import com.example.demo.product.domain.Product;
import com.example.demo.product.repository.ProductRepository;
import org.springframework.orm.ObjectOptimisticLockingFailureException;
import org.springframework.retry.annotation.Backoff;
import org.springframework.retry.annotation.Retryable;
import org.springframework.stereotype.Service;
import org.springframework.transaction.annotation.Transactional;

@Service
public class ProductService {

    private final ProductRepository productRepository;

    public ProductService(ProductRepository productRepository) {
        this.productRepository = productRepository;
    }

    /**
     * @Retryable: If an optimistic lock collision occurs, Spring automatically 
     * retries this method up to 3 times with a 100ms backoff before giving up!
     */
    @Retryable(
            retryFor = ObjectOptimisticLockingFailureException.class,
            maxAttempts = 3,
            backoff = @Backoff(delay = 100)
    )
    @Transactional
    public void purchaseProductOptimistic(Long productId, int quantity) {
        Product product = productRepository.findById(productId)
                .orElseThrow(() -> new IllegalArgumentException("Product not found"));

        product.deductStock(quantity);
        // Hibernate automatically verifies version on commit!
    }
}
```

---

#### 2. Pessimistic Locking: "Prepare for the Worst, Lock the Door"

##### What is it?
Pessimistic locking **locks the database row immediately upon reading it**. Any other transaction that attempts to read or update that row is forced to **block and wait** until the locking transaction finishes and commits.

##### How it works:
1. Define a repository method annotated with `@Lock(LockModeType.PESSIMISTIC_WRITE)`.
2. JPA translates this into a native SQL `SELECT ... FOR UPDATE`:
   ```sql
   SELECT id, name, stock_quantity, version 
   FROM products 
   WHERE id = 42 
   FOR UPDATE;
   ```
3. The database engine places an exclusive row-level lock on row `42`.
4. Any competing transaction trying to query that row with `FOR UPDATE` is paused in the database wait queue until the lock is released.

```mermaid
sequenceDiagram
    autonumber
    participant T1 as Thread 1 (Alice)
    participant T2 as Thread 2 (Bob)
    participant DB as PostgreSQL Database

    T1->>DB: SELECT * FROM products WHERE id = 42 FOR UPDATE;
    Note over DB: Exclusive Row Lock acquired by Thread 1!
    DB-->>T1: Returns Product #42

    T2->>DB: SELECT * FROM products WHERE id = 42 FOR UPDATE;
    Note over DB: Thread 2 BLOCKED! Must wait for Thread 1...

    Note over T1: Thread 1 checks stock, deducts item
    T1->>DB: UPDATE products SET stock = 0 WHERE id = 42;
    T1->>DB: COMMIT TRANSACTION;
    Note over DB: Row Lock RELEASED!

    Note over DB: Thread 2 wakes up and receives updated row
    DB-->>T2: Returns Product #42 (stock = 0)
    Note over T2: Thread 2 sees stock == 0! Throws "Insufficient Inventory".
```

##### Complete Pessimistic Locking Code:

```java
// 1. Repository with @Lock
package com.example.demo.product.repository;

import com.example.demo.product.domain.Product;
import jakarta.persistence.LockModeType;
import jakarta.persistence.QueryHint;
import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.data.jpa.repository.Lock;
import org.springframework.data.jpa.repository.Query;
import org.springframework.data.jpa.repository.QueryHints;
import org.springframework.data.repository.query.Param;

import java.util.Optional;

public interface ProductRepository extends JpaRepository<Product, Long> {

    /**
     * PESSIMISTIC_WRITE: Generates SELECT ... FOR UPDATE.
     * QueryHint: Times out after 3000ms if row lock cannot be acquired,
     * preventing permanent server thread deadlocks!
     */
    @Lock(LockModeType.PESSIMISTIC_WRITE)
    @QueryHints({@QueryHint(name = "jakarta.persistence.lock.timeout", value = "3000")})
    @Query("SELECT p FROM Product p WHERE p.id = :id")
    Optional<Product> findByIdWithPessimisticLock(@Param("id") Long id);
}
```

```java
// 2. Service Layer
package com.example.demo.product.service;

import com.example.demo.product.domain.Product;
import com.example.demo.product.repository.ProductRepository;
import org.springframework.stereotype.Service;
import org.springframework.transaction.annotation.Transactional;

@Service
public class PessimisticOrderService {

    private final ProductRepository productRepository;

    public PessimisticOrderService(ProductRepository productRepository) {
        this.productRepository = productRepository;
    }

    @Transactional
    public void purchaseProductPessimistic(Long productId, int quantity) {
        // Blocks other threads right here until lock is acquired!
        Product product = productRepository.findByIdWithPessimisticLock(productId)
                .orElseThrow(() -> new IllegalArgumentException("Product not found"));

        product.deductStock(quantity);
        // Row lock automatically released on transaction commit!
    }
}
```

---

#### Optimistic vs. Pessimistic Locking: Decision Matrix

| Comparison Criteria | Optimistic Locking (`@Version`) | Pessimistic Locking (`@Lock`) |
| :--- | :--- | :--- |
| **Locking Mechanism** | Application/Hibernate level (version counter check). | Database engine level (`SELECT ... FOR UPDATE` row locks). |
| **Database Overhead** | **Zero DB locks**. High concurrency throughput. | **Heavy**. Holds physical connection and database locks. |
| **Risk of Deadlocks** | None. | **High**, especially if multiple rows are locked in different orders. |
| **Behavior on Collision** | Exception thrown (`OptimisticLockException`); requires retry. | Calling thread waits patiently until lock is released. |
| **Read-Heavy vs Write-Heavy** | **Best for Read-Heavy, Low-Contention**: 95% reads, 5% writes (User profiles, blogs, catalog items). | **Best for Write-Heavy, Extreme Contention**: Flash sales, airline seat reservations, financial account balance debits. |

---

### 5.9 Automated Integration Testing with Testcontainers

Never use H2 in-memory databases to test code written for PostgreSQL. H2 lacks support for PostgreSQL JSONB operators, case-sensitivity rules, and PostgreSQL-specific dialect features, leading to false-positive tests that crash in production.

#### Setting Up Testcontainers with PostgreSQL in JUnit 5

Include Testcontainers in `pom.xml`:

```xml
<dependency>
    <groupId>org.testcontainers</groupId>
    <artifactId>postgresql</artifactId>
    <version>1.19.7</version>
    <scope>test</scope>
</dependency>
<dependency>
    <groupId>org.testcontainers</groupId>
    <artifactId>junit-jupiter</artifactId>
    <version>1.19.7</version>
    <scope>test</scope>
</dependency>
```

#### Writing Real Database Integration Tests with `@DataJpaTest`

The `@DynamicPropertySource` dynamically binds the random ephemeral container port to Spring's `spring.datasource.url`:

The following test verifies repository operations against a real PostgreSQL container:

```java
package com.example.demo.repository;

import com.example.demo.domain.Category;
import org.junit.jupiter.api.DisplayName;
import org.junit.jupiter.api.Test;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.autoconfigure.jdbc.AutoConfigureTestDatabase;
import org.springframework.boot.test.autoconfigure.orm.jpa.DataJpaTest;
import org.springframework.test.context.DynamicPropertyRegistry;
import org.springframework.test.context.DynamicPropertySource;
import org.testcontainers.containers.PostgreSQLContainer;
import org.testcontainers.junit.jupiter.Container;
import org.testcontainers.junit.jupiter.Testcontainers;

import static org.junit.jupiter.api.Assertions.*;

@DataJpaTest
@Testcontainers
@AutoConfigureTestDatabase(replace = AutoConfigureTestDatabase.Replace.NONE) // Prevents replacing Postgres with H2
class CategoryRepositoryIntegrationTest {

    // Starts a genuine PostgreSQL container for the duration of this test class
    @Container
    static PostgreSQLContainer<?> postgres = new PostgreSQLContainer<>("postgres:16-alpine")
            .withDatabaseName("testdb")
            .withUsername("test")
            .withPassword("test");

    // Injects the container's dynamic JDBC URL into Spring's environment
    @DynamicPropertySource
    static void configureProperties(DynamicPropertyRegistry registry) {
        registry.add("spring.datasource.url", postgres::getJdbcUrl);
        registry.add("spring.datasource.username", postgres::getUsername);
        registry.add("spring.datasource.password", postgres::getPassword);
    }

    @Autowired
    private CategoryRepository categoryRepository;

    @Test
    @DisplayName("Persist and query category in real PostgreSQL container")
    void shouldSaveAndRetrieveCategory() {
        Category category = new Category("Books");
        Category saved = categoryRepository.save(category);

        assertNotNull(saved.getId());
        assertEquals("Books", saved.getName());
    }
}
```

#### 5.9.1 Modern Integration Testing with Spring Boot 3.1 `@ServiceConnection`

While `@DynamicPropertySource` works, it requires 8 lines of repetitive boilerplate code for every container (Postgres, Redis, Kafka, RabbitMQ) across every test class.

**Spring Boot 3.1 introduced `@ServiceConnection`**, which completely eliminates `@DynamicPropertySource`!

##### The Revolution in 3 Lines of Code:
When you annotate a container with `@ServiceConnection`, Spring Boot automatically queries the Testcontainer, determines its service type, and dynamically registers the corresponding `ConnectionDetails` bean:

```java
package com.example.demo.repository;

import com.example.demo.domain.Category;
import org.junit.jupiter.api.DisplayName;
import org.junit.jupiter.api.Test;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.autoconfigure.jdbc.AutoConfigureTestDatabase;
import org.springframework.boot.test.autoconfigure.orm.jpa.DataJpaTest;
import org.springframework.boot.testcontainers.service.connection.ServiceConnection;
import org.testcontainers.containers.PostgreSQLContainer;
import org.testcontainers.junit.jupiter.Container;
import org.testcontainers.junit.jupiter.Testcontainers;

import static org.junit.jupiter.api.Assertions.*;

@DataJpaTest
@Testcontainers
@AutoConfigureTestDatabase(replace = AutoConfigureTestDatabase.Replace.NONE)
class ModernCategoryRepositoryTest {

    // @ServiceConnection automatically extracts port, username, password and configures DataSource!
    // NO @DynamicPropertySource METHOD NEEDED!
    @Container
    @ServiceConnection
    static PostgreSQLContainer<?> postgres = new PostgreSQLContainer<>("postgres:16-alpine");

    @Autowired
    private CategoryRepository categoryRepository;

    @Test
    @DisplayName("Persist and retrieve entity using modern @ServiceConnection")
    void testCategoryPersistence() {
        Category saved = categoryRepository.save(new Category("Electronics"));
        assertNotNull(saved.getId());
        assertEquals("Electronics", saved.getName());
    }
}
```

> [!TIP]
> `@ServiceConnection` works out of the box with over 15 Testcontainers modules, including PostgreSQL, MySQL, MariaDB, Oracle, MongoDB, Redis, Kafka, RabbitMQ, and Neo4j!

---

### Chapter 5 Exercises & Comprehensive Scenarios with Solutions

Test your comprehension of relational data persistence, transactions, and modern query APIs across multiple practical scenarios.

#### Exercise 5.1: Writing a Paginated Query with Multiple Sort Fields

**Scenario**: You are building an e-commerce administration panel. Write a repository method and service method to fetch products belonging to a given category name, sorted primarily by product price ascending and secondarily by product title ascending, paginated.

The following code implements the multi-sort paginated query:

```java
// 1. Repository Interface
@Repository
public interface ProductAdminRepository extends JpaRepository<Product, Long> {
    Page<Product> findByCategoryName(String categoryName, Pageable pageable);
}

// 2. Service Implementation
@Service
public class ProductAdminService {
    private final ProductAdminRepository repository;

    public ProductAdminService(ProductAdminRepository repository) {
        this.repository = repository;
    }

    public Page<Product> getProductsSorted(String categoryName, int pageIndex, int pageSize) {
        // Multi-level sort: price ASC, then title ASC
        Sort multiSort = Sort.by("price").ascending().and(Sort.by("title").ascending());
        Pageable pageable = PageRequest.of(pageIndex, pageSize, multiSort);
        return repository.findByCategoryName(categoryName, pageable);
    }
}
```

#### Exercise 5.2: Investigating Transaction Rollback Rules

**Scenario**: What happens to the database when the following method executes, and how do you ensure the transaction rolls back?

```java
@Transactional
public void processPayment() throws IOException {
    orderRepository.markAsPaid(42L);
    if (networkFails()) {
        throw new IOException("Socket timed out"); // Checked exception!
    }
}
```

**Explanation & Fix**:
Because `IOException` is a **checked exception** (subclass of `java.lang.Exception`, not `RuntimeException`), Spring's default transaction interceptor **will NOT roll back**! The order will remain marked as `PAID` in the database despite the network failure.
**The Fix**: Add `rollbackFor = Exception.class`:
```java
@Transactional(rollbackFor = Exception.class)
public void processPayment() throws IOException { ... }
```

#### Exercise 5.3: High-Speed Direct SQL Update with `JdbcClient`

**Scenario**: Write a `JdbcClient` method that resets stock quantities to zero for all products whose category ID matches the parameter.

The following method executes the stock reset update:

```java
@Repository
public class StockJdbcRepository {
    private final JdbcClient jdbcClient;

    public StockJdbcRepository(JdbcClient jdbcClient) {
        this.jdbcClient = jdbcClient;
    }

    public int resetCategoryStock(Long categoryId) {
        return jdbcClient.sql("UPDATE products SET stock_quantity = 0 WHERE category_id = :catId")
                .param("catId", categoryId)
                .update();
    }
}
```

#### Exercise 5.4: Eliminating N+1 with `JOIN FETCH`

**Scenario**: Write a JPQL query that fetches all `Order` entities along with their `OrderItem` list in a single query, filtering only orders created after a specific timestamp.

The following repository method loads orders and items in a single query:

```java
@Repository
public interface OrderFetchRepository extends JpaRepository<Order, Long> {

    @Query("SELECT DISTINCT o FROM Order o LEFT JOIN FETCH o.items WHERE o.createdAt >= :cutoff")
    List<Order> findRecentOrdersWithItems(@Param("cutoff") Instant cutoff);
}
```

#### Exercise 5.5: Solving Self-Invocation Transaction Failure

**Scenario**: Refactor the following buggy code so that `updateAccountBalance` executes inside a real database transaction:

```java
@Service
public class AccountService {
    public void deposit(Long accountId, double amount) {
        logActivity(accountId);
        this.updateAccountBalance(accountId, amount); // Self-invocation bug!
    }

    @Transactional(rollbackFor = Exception.class)
    public void updateAccountBalance(Long accountId, double amount) {
        // Database update logic
    }
}
```

The following refactored service places `@Transactional` on the public method called by clients:

```java
@Service
public class AccountService {

    // Move @Transactional to the public entry point intercepted by Spring's dynamic proxy
    @Transactional(rollbackFor = Exception.class)
    public void deposit(Long accountId, double amount) {
        logActivity(accountId);
        updateAccountBalance(accountId, amount);
    }

    private void updateAccountBalance(Long accountId, double amount) {
        // Database update logic executes safely inside the caller's active transaction!
    }

    private void logActivity(Long accountId) {
        System.out.println("Processing deposit for: " + accountId);
    }
}
```

#### Exercise 5.6: Testcontainers Integration Test for Derived Queries

**Scenario**: Write a complete `@DataJpaTest` using Testcontainers that saves two products and verifies `findByTitleContaining` returns only the matching product.

The following test verifies derived query execution against a PostgreSQL container:

```java
@DataJpaTest
@Testcontainers
@AutoConfigureTestDatabase(replace = AutoConfigureTestDatabase.Replace.NONE)
class ProductSearchIntegrationTest {

    @Container
    static PostgreSQLContainer<?> postgres = new PostgreSQLContainer<>("postgres:16-alpine")
            .withDatabaseName("testdb")
            .withUsername("test")
            .withPassword("test");

    @DynamicPropertySource
    static void configureProperties(DynamicPropertyRegistry registry) {
        registry.add("spring.datasource.url", postgres::getJdbcUrl);
        registry.add("spring.datasource.username", postgres::getUsername);
        registry.add("spring.datasource.password", postgres::getPassword);
    }

    @Autowired
    private ProductRepository productRepository;

    @Autowired
    private CategoryRepository categoryRepository;

    @Test
    void shouldFindProductsByKeyword() {
        Category cat = categoryRepository.save(new Category("Hardware"));
        productRepository.save(new Product("Mechanical Keyboard", cat));
        productRepository.save(new Product("Wireless Mouse", cat));

        List<Product> results = productRepository.findByTitleContainingIgnoreCase("Keyboard");

        assertEquals(1, results.size());
        assertEquals("Mechanical Keyboard", results.get(0).getTitle());
    }
}
```

---

## Chapter 6: Data Persistence and NoSQL Database Integration with Spring Data

Modern systems rarely rely solely on relational databases. NoSQL document databases like MongoDB offer flexible schemas for polymorphic content, while in-memory data grids like Redis supercharge application throughput by caching frequently read data.

### 6.0 The NoSQL Mental Model & Architecture

Choosing between relational and NoSQL storage depends on access patterns, data velocity, and consistency guarantees:

```mermaid
flowchart TD
    Store{"Choose Data Store"}
    Store -->|"ACID, Foreign Keys, Complex Joins"| SQL[("PostgreSQL / Relational")]
    Store -->|"Hierarchical Documents, Schema Agility"| Mongo[("MongoDB Document Store")]
    Store -->|"Sub-millisecond Reads, TTL Caches, Counters"| Redis[("Redis In-Memory Key-Value")]
```

#### When to Choose NoSQL Over SQL (CAP Theorem, Document vs Relational)

Selecting a database technology requires evaluating consistency guarantees, query flexibility, and horizontal scalability:

- **Relational Databases (PostgreSQL)**: Prioritize **Consistency** and strict schema integrity. Ideal for core financial records, order management, and relational graphs requiring complex cross-table joins.
- **Document Databases (MongoDB)**: Prioritize **Schema Flexibility** and developer agility. Ideal for content management, product catalogs with varying technical specifications, and JSON document storage.
- **In-Memory Caches (Redis)**: Prioritize **Raw Read Speed** (< 1ms latency). Operates entirely in server RAM. Ideal for session management, API rate limiting, and caching hot read queries.

#### Documents vs Tables, Collections vs Rows

Understanding the terminology mapping between SQL and MongoDB:

| Relational Concept (PostgreSQL) | MongoDB Document Store Equivalent |
| :--- | :--- |
| Database | Database |
| Table | **Collection** |
| Row | **Document (BSON / JSON)** |
| Column | **Field** |
| Primary Key (`id`) | **`_id` (ObjectId)** |
| Foreign Key Join | **Embedded Document** or **`@DocumentReference`** |

---

### 6.1 Integrating MongoDB with Spring Data Mongo

MongoDB stores data as self-contained BSON (Binary JSON) documents, eliminating the need for expensive multi-table joins.

#### Running MongoDB with Docker

Start an official MongoDB 7 instance locally:

```bash
docker run -d \
  --name mongodb-ecommerce \
  -p 27017:27017 \
  mongo:7.0
```

#### Modeling MongoDB Documents: `@Document`, `@Id`, `@Field`, `@Indexed`

In Spring Data MongoDB, classes are annotated with `@Document`:
- `@Document(collection = "products")`: Maps the class to a MongoDB collection named `products`.
- `@Id`: Marks the unique primary key (typically a `String` or `ObjectId`).
- `@Field("prod_title")`: Maps a Java field to a specific BSON document field name.
- `@Indexed`: Instructs MongoDB to create a database index on that field for fast queries.

The following document class models a flexible catalog product:

```java
package com.example.demo.document;

import org.springframework.data.annotation.Id;
import org.springframework.data.mongodb.core.index.Indexed;
import org.springframework.data.mongodb.core.mapping.Document;
import org.springframework.data.mongodb.core.mapping.Field;

import java.util.List;
import java.util.Map;

// 1. Embedded Value Object (stored nested inside the parent document)
public record ProductSpecification(String specName, String specValue) {}

// 2. Main MongoDB Document
@Document(collection = "catalog_products")
public class CatalogProduct {

    @Id
    private String id; // Automatically assigned MongoDB ObjectId string

    @Indexed // Creates index in MongoDB for fast searches
    @Field("title")
    private String title;

    private double price;

    // Embedded List: stored directly as an array of JSON objects inside this document!
    private List<ProductSpecification> specifications;

    // Dynamic attributes map: handles unpredictable product properties without schema migrations!
    private Map<String, Object> customAttributes;

    public CatalogProduct(String title, double price, List<ProductSpecification> specifications, Map<String, Object> customAttributes) {
        this.title = title;
        this.price = price;
        this.specifications = specifications;
        this.customAttributes = customAttributes;
    }

    public String getId() { return id; }
    public String getTitle() { return title; }
    public double getPrice() { return price; }
    public List<ProductSpecification> getSpecifications() { return specifications; }
    public Map<String, Object> getCustomAttributes() { return customAttributes; }
}
```

#### Embedded Documents vs Document References (`@DocumentReference`)

MongoDB offers two ways to model relationships:

1. **Embedded Documents (Preferred for 90% of use cases)**: Child objects are stored directly inside the parent JSON document. For example, an `Order` document embeds its `List<OrderItem>`.
   - *Advantage*: The entire order and its items are read and written in a **single atomic disk operation** with zero joins.
2. **Document References (`@DocumentReference`)**: Stores only the ID of another document (similar to a foreign key).
   - *Use Case*: When child objects are huge (e.g., thousands of reviews) or shared across multiple documents (e.g., authors across thousands of books).

#### Spring Data Mongo Repositories & Custom JSON Queries

`MongoRepository` provides standard CRUD methods plus custom JSON query declarations:

The following repository demonstrates derived queries and custom JSON query syntax:

```java
package com.example.demo.repository;

import com.example.demo.document.CatalogProduct;
import org.springframework.data.mongodb.repository.MongoRepository;
import org.springframework.data.mongodb.repository.Query;
import org.springframework.stereotype.Repository;

import java.util.List;

@Repository
public interface CatalogProductRepository extends MongoRepository<CatalogProduct, String> {

    // 1. Derived query method
    List<CatalogProduct> findByPriceLessThan(double maxPrice);

    // 2. Custom MongoDB JSON query matching embedded fields
    // '?0' binds to the method parameter 'specName'; '?1' binds to 'specValue'
    @Query("{ 'specifications.specName': ?0, 'specifications.specValue': ?1 }")
    List<CatalogProduct> findBySpecification(String specName, String specValue);
}
```

#### Complex Queries with `MongoTemplate` and Criteria Builder

For dynamic queries with optional filter conditions, use `MongoTemplate`:

The following service demonstrates dynamic query building using `MongoTemplate`:

```java
package com.example.demo.service;

import com.example.demo.document.CatalogProduct;
import org.springframework.data.mongodb.core.MongoTemplate;
import org.springframework.data.mongodb.core.query.Criteria;
import org.springframework.data.mongodb.core.query.Query;
import org.springframework.stereotype.Service;

import java.util.List;

@Service
public class DynamicProductSearchService {

    private final MongoTemplate mongoTemplate;

    public DynamicProductSearchService(MongoTemplate mongoTemplate) {
        this.mongoTemplate = mongoTemplate;
    }

    public List<CatalogProduct> searchProducts(String keyword, Double maxPrice) {
        Query dynamicQuery = new Query();

        if (keyword != null && !keyword.isBlank()) {
            dynamicQuery.addCriteria(Criteria.where("title").regex(keyword, "i")); // Case-insensitive regex
        }
        if (maxPrice != null && maxPrice > 0) {
            dynamicQuery.addCriteria(Criteria.where("price").lte(maxPrice)); // price <= maxPrice
        }

        return mongoTemplate.find(dynamicQuery, CatalogProduct.class);
    }
}
```

---

### 6.2 Distributed Caching with Redis

A modern web application spends 70% of its execution time waiting for database queries to complete. Caching hot data in RAM accelerates read performance by 100x.

#### Why Cache? The Latency Gap (RAM vs SSD vs Network)

To understand why caching is mandatory in production, compare physical hardware access latencies:

- **CPU L1 Cache**: ~0.5 nanoseconds
- **Main Server RAM (Redis)**: **~100 nanoseconds (< 0.5 milliseconds over network)**
- **NVMe Solid State Drive (SSD)**: ~50 microseconds
- **Relational DB Query (Disk I/O + Joins)**: **~10 milliseconds to 50 milliseconds**

Reading an object from Redis is **50 to 100 times faster** than querying a relational database!

#### Running Redis with Docker

Start a lightweight Redis 7 container:

```bash
docker run -d \
  --name redis-ecommerce \
  -p 6379:6379 \
  redis:7.2-alpine
```

#### The Cache-Aside Pattern Step-by-Step

Spring Cache implements the **Cache-Aside** (Lazy Loading) design pattern:

```mermaid
sequenceDiagram
    autonumber
    actor Client as Web Request
    participant Svc as ProductService
    participant Cache as Redis Cache
    participant DB as PostgreSQL Database

    Client->>Svc: getProductById(42)
    Svc->>Cache: Check key "products::42"
    alt Cache HIT
        Cache-->>Svc: Return cached JSON payload (< 1ms)
        Svc-->>Client: Return Product
    else Cache MISS
        Cache-->>Svc: Key not found
        Svc->>DB: Execute SQL query "SELECT * FROM products WHERE id = 42"
        DB-->>Svc: Return row (15ms)
        Svc->>Cache: Save "products::42" to Redis with TTL
        Svc-->>Client: Return Product
    end
```

#### Configuring `RedisCacheManager` with Jackson JSON Serialization

By default, Spring Boot uses Java binary serialization for Redis values. This produces unreadable binary strings in Redis and crashes with `ClassCastException` whenever your Java classes are modified!

Configure a human-readable JSON serializer using Jackson:

The following configuration sets up readable JSON caching in Redis:

```java
package com.example.demo.config;

import org.springframework.cache.annotation.EnableCaching;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.data.redis.cache.RedisCacheConfiguration;
import org.springframework.data.redis.cache.RedisCacheManager;
import org.springframework.data.redis.connection.RedisConnectionFactory;
import org.springframework.data.redis.serializer.GenericJackson2JsonRedisSerializer;
import org.springframework.data.redis.serializer.RedisSerializationContext;

import java.time.Duration;

@Configuration
@EnableCaching // Activates Spring's declarative annotation-driven caching engine
public class RedisCacheConfig {

    @Bean
    public RedisCacheManager cacheManager(RedisConnectionFactory connectionFactory) {
        RedisCacheConfiguration defaultConfig = RedisCacheConfiguration.defaultCacheConfig()
                .entryTtl(Duration.ofMinutes(15)) // Default TTL 15 minutes
                .disableCachingNullValues()       // Prevent caching null values unless explicitly needed
                // Serialize Java objects into clean, human-readable JSON strings in Redis!
                .serializeValuesWith(RedisSerializationContext.SerializationPair.fromSerializer(
                        new GenericJackson2JsonRedisSerializer()));

        return RedisCacheManager.builder(connectionFactory)
                .cacheDefaults(defaultConfig)
                .build();
    }
}
```

#### Declarative Caching Annotations: `@Cacheable`, `@CachePut`, `@CacheEvict`, `@Caching`

Spring provides four primary annotations to manage caching declaratively:

1. **`@Cacheable`**: Checks the cache first. If found, returns the cached object without executing the method. If missing, runs the method and saves the return value to the cache.
2. **`@CachePut`**: Always executes the method and updates the cache with the method's result. Used on `update` methods.
3. **`@CacheEvict`**: Removes an entry from the cache. Used on `delete` methods.
4. **`@Caching`**: Groups multiple cache operations together.

The following service demonstrates all primary caching annotations:

```java
package com.example.demo.service;

import com.example.demo.domain.Product;
import com.example.demo.repository.ProductRepository;
import org.springframework.cache.annotation.CacheEvict;
import org.springframework.cache.annotation.CachePut;
import org.springframework.cache.annotation.Cacheable;
import org.springframework.cache.annotation.Caching;
import org.springframework.stereotype.Service;

@Service
public class CachedProductService {

    private final ProductRepository productRepository;

    public CachedProductService(ProductRepository productRepository) {
        this.productRepository = productRepository;
    }

    // 1. Look up from cache "products::#id". If missing, execute DB query and store in cache.
    @Cacheable(value = "products", key = "#id")
    public Product getProductById(Long id) {
        System.out.println("Cache MISS: Querying PostgreSQL database for product ID: " + id);
        return productRepository.findById(id)
                .orElseThrow(() -> new IllegalArgumentException("Product not found: " + id));
    }

    // 2. Always updates the database AND updates the cache entry with the fresh data
    @CachePut(value = "products", key = "#product.id")
    public Product updateProduct(Product product) {
        return productRepository.save(product);
    }

    // 3. Deletes from database AND evicts the specific key from Redis
    @CacheEvict(value = "products", key = "#id")
    public void deleteProduct(Long id) {
        productRepository.deleteById(id);
    }

    // 4. Grouped eviction: purges the specific product AND clears the category listing cache
    @Caching(evict = {
        @CacheEvict(value = "products", key = "#id"),
        @CacheEvict(value = "productListings", allEntries = true)
    })
    public void purgeProductAndListings(Long id) {
        productRepository.deleteById(id);
    }
}
```

#### Dynamic Cache Keys with SpEL (`#id`, `#user.email`)

Spring Expression Language (SpEL) allows constructing dynamic cache keys based on method arguments:

The following methods demonstrate dynamic SpEL key construction:

```java
// 1. Key based on method argument
@Cacheable(value = "users", key = "#email")
public User getUserByEmail(String email) { ... }

// 2. Key based on property of an object argument
@CachePut(value = "accounts", key = "#dto.accountNumber")
public Account updateAccount(AccountUpdateDto dto) { ... }

// 3. Conditional caching: only cache expensive orders where amount > 1000
@Cacheable(value = "highValueOrders", key = "#orderId", condition = "#amount > 1000.0")
public Order getHighValueOrder(Long orderId, double amount) { ... }
```

---

### 6.3 Advanced Caching Scenarios & Production Pitfalls

Operating caching systems in production requires defending against traffic stampedes, data inconsistency, and memory exhaustion.

#### Setting Per-Cache Time-To-Live (TTL)

Different data types require different expiration lifespans. For example, product details can be cached for 1 hour, whereas stock quantities should expire after 30 seconds:

The following configuration customizes TTLs per cache namespace:

```java
@Bean
public RedisCacheManager customTtlCacheManager(RedisConnectionFactory factory) {
    RedisCacheConfiguration defaultConfig = RedisCacheConfiguration.defaultCacheConfig()
            .entryTtl(Duration.ofMinutes(10));

    // Custom configuration map per cache name
    Map<String, RedisCacheConfiguration> cacheConfigs = new HashMap<>();
    cacheConfigs.put("products", defaultConfig.entryTtl(Duration.ofHours(1)));
    cacheConfigs.put("stockQuantities", defaultConfig.entryTtl(Duration.ofSeconds(30)));

    return RedisCacheManager.builder(factory)
            .cacheDefaults(defaultConfig)
            .withInitialCacheConfigurations(cacheConfigs)
            .build();
}
```

#### Mitigating the Cache Stampede (Thundering Herd) with Distributed Locks (`SETNX`)

When a high-traffic cache key (such as the front-page banner or flash-sale item) expires, hundreds of concurrent requests will simultaneously miss the cache and overwhelm the database.

**The Solution**: Use Redis `SETNX` (Set if Not Exists) to acquire a short-lived distributed mutex lock. Only a single thread queries the database, while other threads wait briefly:

The following service method implements single-flight cache loading with a distributed lock:

```java
package com.example.demo.service;

import org.springframework.data.redis.core.StringRedisTemplate;
import org.springframework.stereotype.Service;

import java.time.Duration;

@Service
public class StampedeProtectedCatalogService {

    private final StringRedisTemplate redisTemplate;

    public StampedeProtectedCatalogService(StringRedisTemplate redisTemplate) {
        this.redisTemplate = redisTemplate;
    }

    public String getHotProductData(String productId) {
        String cacheKey = "product_data:" + productId;
        String cached = redisTemplate.opsForValue().get(cacheKey);

        if (cached != null) {
            return cached; // Cache HIT
        }

        // Cache MISS: Acquire short-lived distributed lock (5 seconds)
        String lockKey = "lock:" + cacheKey;
        Boolean lockAcquired = redisTemplate.opsForValue().setIfAbsent(lockKey, "LOCKED", Duration.ofSeconds(5));

        if (Boolean.TRUE.equals(lockAcquired)) {
            try {
                // Exactly ONE thread queries the database and populates the cache!
                String freshData = queryDatabaseSlowly(productId);
                redisTemplate.opsForValue().set(cacheKey, freshData, Duration.ofMinutes(15));
                return freshData;
            } finally {
                redisTemplate.delete(lockKey); // Release lock
            }
        } else {
            // Other concurrent threads sleep briefly and read from the freshly populated cache
            try { Thread.sleep(60); } catch (InterruptedException ignored) {}
            return redisTemplate.opsForValue().get(cacheKey);
        }
    }

    private String queryDatabaseSlowly(String id) {
        return "Database Product Content for: " + id;
    }
}
```

#### Cache Penetration: Preventing DB DoS on Non-Existent Keys

**Cache Penetration** occurs when an attacker queries thousands of non-existent IDs (e.g., `getProductById(-99999)`). Because these keys never exist in the database, the cache is never populated, and every single request penetrates directly to the database.

**The Solutions**:
1. **Cache Null Values Briefly**: When an ID does not exist, write a placeholder `null` value with a short TTL (e.g., 2 minutes):
   ```java
   // In application.yml or RedisCacheConfiguration
   .entryTtl(Duration.ofMinutes(2)) // Allows caching nulls with short TTL
   ```
2. **Bloom Filters**: Use a Bloom filter (via Google Guava or RedisBloom) to verify whether an ID exists before ever touching Redis or the database.

#### Using `RedisTemplate` Directly for Counters, Sets, and Hashes

While `@Cacheable` handles simple object caching, `RedisTemplate` unlocks Redis's specialized data structures:

The following service demonstrates Redis atomic counters and hash maps:

```java
package com.example.demo.service;

import org.springframework.data.redis.core.StringRedisTemplate;
import org.springframework.stereotype.Service;

import java.util.Map;

@Service
public class RedisDataStructuresService {

    private final StringRedisTemplate redis;

    public RedisDataStructuresService(StringRedisTemplate redis) {
        this.redis = redis;
    }

    // 1. Atomic Counter: perfect for real-time page views and API rate limiters
    public Long incrementPageView(String pageId) {
        return redis.opsForValue().increment("pageviews:" + pageId);
    }

    // 2. Redis Hash: stores individual fields of an object without serializing entire JSON
    public void saveUserSession(String sessionId, String userId, String ipAddress) {
        String key = "session:" + sessionId;
        redis.opsForHash().put(key, "userId", userId);
        redis.opsForHash().put(key, "ipAddress", ipAddress);
    }

    public Map<Object, Object> getSessionData(String sessionId) {
        return redis.opsForHash().entries("session:" + sessionId);
    }
}
```

---

### Chapter 6 Exercises & Comprehensive Scenarios with Solutions

Test your comprehension of NoSQL document modeling and Redis caching mechanics.

#### Exercise 6.1: Writing a Cache-Aside Product Service

**Scenario**: Implement a service method `findCategoryById(Long id)` that uses `@Cacheable` with cache name `"categories"` and key `#id`. Ensure that updating a category evicts the cache entry.

The following service implements the requested caching behavior:

```java
@Service
public class CategoryCacheService {

    private final CategoryRepository repository;

    public CategoryCacheService(CategoryRepository repository) {
        this.repository = repository;
    }

    @Cacheable(value = "categories", key = "#id")
    public Category findCategoryById(Long id) {
        return repository.findById(id).orElseThrow();
    }

    @CacheEvict(value = "categories", key = "#category.id")
    public Category updateCategory(Category category) {
        return repository.save(category);
    }
}
```

#### Exercise 6.2: Custom RedisTemplate for Atomic Rate Limiting

**Scenario**: Write a method using `StringRedisTemplate` that increments an IP's request count. If the count exceeds 100 within a 60-second window, return `false` (rate limit exceeded).

The following method implements a fixed-window rate limiter:

```java
@Service
public class RateLimiterService {

    private final StringRedisTemplate redisTemplate;

    public RateLimiterService(StringRedisTemplate redisTemplate) {
        this.redisTemplate = redisTemplate;
    }

    public boolean isAllowed(String clientIp) {
        String key = "ratelimit:" + clientIp;
        Long currentCount = redisTemplate.opsForValue().increment(key);

        if (currentCount != null && currentCount == 1) {
            // First request: set window expiration to 60 seconds
            redisTemplate.expire(key, Duration.ofSeconds(60));
        }

        return currentCount != null && currentCount <= 100;
    }
}
```

#### Exercise 6.3: Custom JSON Query in Spring Data MongoDB

**Scenario**: Write a `MongoRepository` method using `@Query` to find all products where `price` is greater than or equal to a minimum value and the embedded attribute `metadata.category` matches a given string.

The following repository interface executes the embedded field search:

```java
@Repository
public interface ProductMongoQueryRepository extends MongoRepository<CatalogProduct, String> {

    @Query("{ 'price': { $gte: ?0 }, 'metadata.category': ?1 }")
    List<CatalogProduct> findByMinPriceAndCategory(double minPrice, String category);
}
```

#### Exercise 6.4: Purging All Cache Namespaces Dynamically

**Scenario**: Write an administrative service method that purges all entries from both the `"products"` and `"categories"` caches simultaneously.

The following method clears multiple cache namespaces:

```java
@Service
public class AdminCachePurgeService {

    @Caching(evict = {
        @CacheEvict(value = "products", allEntries = true),
        @CacheEvict(value = "categories", allEntries = true)
    })
    public void purgeAllCatalogCaches() {
        System.out.println("Purged products and categories caches.");
    }
}
```

---

# Part 3: Application Optimization

Scaling web services to handle heavy enterprise workloads requires identifying system bottlenecks, eliminating database query amplification, leveraging modern thread models, and adopting non-blocking reactive streams.

---

## Chapter 7: Finding Bottlenecks and Optimizing Your Application

Performance optimization requires empirical measurement rather than guessing. Discovering memory leaks, identifying the JPA N+1 query trap, tuning connection pools, and enabling Virtual Threads ensures your service handles traffic spikes predictably.

### 7.0 The Performance Engineering Mindset

Enterprise performance engineering is the disciplined practice of locating and removing throughput bottlenecks before they cause service degradation in production environments. System slowdowns generally stem from four root causes: database query amplification, connection pool starvation, operating system thread exhaustion, or memory allocation churn causing Garbage Collection pauses.

#### Core Performance Metrics and Laws

Before profiling an application, software engineers must understand the mathematical relationships governing latency, concurrency, and throughput:

- **Latency**: The time elapsed between a client sending an HTTP request and receiving the complete HTTP response. Latency is rarely uniform; production systems measure latency across statistical percentiles:
  - **p50 (Median)**: 50% of requests are faster than this threshold.
  - **p95**: 95% of requests are faster than this threshold; reflects typical user experience during peak periods.
  - **p99 and p99.9**: The worst-case latency tail, often caused by garbage collection pauses, database lock contention, or network packet retransmission.
- **Throughput**: The total volume of work processed per unit of time, typically expressed as Requests Per Second (RPS) or Transactions Per Second (TPS).
- **Little's Law ($L = \\lambda W$)**: A fundamental queuing theory theorem stating that the average number of concurrent requests in a system ($L$) equals the arrival rate (throughput $\\lambda$) multiplied by the average response time (latency $W$). If latency doubles while arrival rate stays constant, the number of active threads must double to prevent requests from queuing.
- **Amdahl's Law**: States that the theoretical speedup of a program is limited by the portion of the program that cannot be parallelized. Speeding up CPU-bound code yields minimal overall benefit if the system spends 90% of its time waiting on sequential relational database locks.

#### The Performance Diagnostic Decision Tree

When diagnosing application latency spikes or degraded throughput, engineers systematically isolate the bottleneck through structured observability:

```mermaid
flowchart TD
    Start["Performance Degradation Detected"] --> CheckMetrics{"Check CPU, Memory & I/O Metrics"}
    
    CheckMetrics -->|"High CPU (>85%)"| CPUAnalysis{"Analyze Thread Dumps & JFR"}
    CPUAnalysis -->|"Hot Loops / Regex / Crypto"| OptimizeAlgorithms["Optimize Algorithms & Cache Computation"]
    CPUAnalysis -->|"High GC Overhead"| CheckGC["Tune Heap Size & Switch to Generational ZGC"]
    
    CheckMetrics -->|"Low CPU (<30%) but High Latency"| IOAnalysis{"Inspect Waiting Threads"}
    IOAnalysis -->|"BLOCKED on DB Connections"| PoolTuning["Enlarge Connection Pool / Fix Leaks"]
    IOAnalysis -->|"WAITING on DB Queries"| QueryAnalysis{"Inspect SQL Logs"}
    QueryAnalysis -->|"Thousands of Similar Queries"| FixNPlusOne["Eliminate N+1 with JOIN FETCH or EntityGraph"]
    QueryAnalysis -->|"Slow Single Query"| AddIndex["Add Database Indexes & Analyze Execution Plan"]
    
    IOAnalysis -->|"WAITING on External HTTP Services"| ThreadExhaustion{"Check Active Tomcat Threads"}
    ThreadExhaustion -->|"Threads Maxed Out (200/200)"| EnableVirtualThreads["Enable Java 21 Virtual Threads"]
    ThreadExhaustion -->|"Slow Upstream Service"| AddCircuitBreaker["Add Resilience4j Circuit Breaker & Timeout"]
```

---

### 7.1 Database Performance Tuning & The N+1 Solution

Relational database interactions represent the single greatest source of performance degradation in Spring enterprise applications. Developers using Object-Relational Mapping (ORM) tools like Hibernate frequently write code that appears benign in Java but generates thousands of redundant SQL queries on the network wire.

#### Understanding the JPA N+1 Query Problem

The N+1 query problem occurs when an application executes 1 initial SQL query to retrieve a collection of parent entities, and subsequently executes $N$ additional independent SQL queries to fetch related child records for each parent:

```mermaid
sequenceDiagram
    autonumber
    actor Client
    participant App as Spring Boot Application
    participant DB as PostgreSQL Database

    Client->>App: GET /api/v1/authors
    Note over App,DB: Naive JPA Repository findAll()
    App->>DB: 1. SELECT * FROM authors LIMIT 50;
    DB-->>App: Returns 50 Author rows
    
    loop For each Author (N = 50 iterations)
        App->>DB: SELECT * FROM books WHERE author_id = ?;
        DB-->>App: Returns Book rows for this Author
    end
    Note over App,DB: Total Queries = 1 + 50 = 51 Network Round-trips!
    App-->>Client: 200 OK with JSON array
```

#### Reproducing the N+1 Problem in Code

Consider an e-commerce domain where an `Author` entity maintains a one-to-many relationship with a `Book` entity using default lazy loading:

The following entity classes define the parent-child relationship:

```java
package com.example.demo.domain;

import jakarta.persistence.*;
import java.util.ArrayList;
import java.util.List;

@Entity
@Table(name = "authors")
public class Author {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @Column(nullable = false)
    private String name;

    // LAZY loading is best practice, but accessing this collection
    // in an open session triggers an individual query if not fetched together!
    @OneToMany(mappedBy = "author", fetch = FetchType.LAZY, cascade = CascadeType.ALL)
    private List<Book> books = new ArrayList<>();

    public Author() {}

    public Long getId() { return id; }
    public String getName() { return name; }
    public List<Book> getBooks() { return books; }
}
```

The corresponding child entity links back to the author:

```java
package com.example.demo.domain;

import jakarta.persistence.*;

@Entity
@Table(name = "books")
public class Book {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @Column(nullable = false)
    private String title;

    @ManyToOne(fetch = FetchType.LAZY)
    @JoinColumn(name = "author_id", nullable = false)
    private Author author;

    public Book() {}

    public Long getId() { return id; }
    public String getTitle() { return title; }
}
```

When a naive controller or service iterates through authors to build a response, Hibernate generates a query storm:

```java
// Anti-Pattern: Triggers N+1 queries against the database!
List<Author> authors = authorRepository.findAll(); // Query 1: SELECT * FROM authors

List<AuthorDto> dtos = authors.stream().map(author -> {
    // Triggers an individual SQL query for EACH of the N authors!
    int bookCount = author.getBooks().size(); 
    return new AuthorDto(author.getId(), author.getName(), bookCount);
}).toList();
```

If the `authors` table has 100 rows, this code generates 101 separate database round-trips. Across 50 concurrent web requests, the application fires over 5,000 queries in milliseconds, exhausting database CPU and connection pools.

#### Solution 1: Explicit JPQL JOIN FETCH

The most robust way to eliminate the N+1 problem is using an explicit JPQL `JOIN FETCH` clause in your Spring Data repository:

The following repository interface executes a single SQL `INNER JOIN` or `LEFT JOIN` to hydrate both the parent and child entities in one query:

```java
package com.example.demo.repository;

import com.example.demo.domain.Author;
import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.data.jpa.repository.Query;
import org.springframework.stereotype.Repository;

import java.util.List;

@Repository
public interface AuthorRepository extends JpaRepository<Author, Long> {

    // Solution 1: Single SQL query fetches authors AND their books simultaneously
    // DISTINCT prevents duplicate Author root references caused by the SQL Cartesian product
    @Query("SELECT DISTINCT a FROM Author a LEFT JOIN FETCH a.books")
    List<Author> findAllWithBooks();
}
```

Under the hood, Hibernate executes the following single SQL statement:

```sql
SELECT DISTINCT a.id, a.name, b.id, b.title, b.author_id
FROM authors a
LEFT OUTER JOIN books b ON a.id = b.author_id;
```

#### Solution 2: Dynamic Fetching with `@EntityGraph`

When you want to keep repository query declarations clean or dynamically override fetch plans for specific finder methods, use Spring Data's `@EntityGraph` annotation:

The following method uses an entity graph to fetch books eagerly without writing explicit JPQL:

```java
    // Solution 2: Instructs Hibernate to override LAZY fetch dynamically for this query
    @EntityGraph(attributePaths = {"books"})
    List<Author> findByNameContainingIgnoreCase(String nameFragment);
```

#### Solution 3: Hibernate Batch Fetching (`@BatchSize`)

When fetching parent entities with pagination, `JOIN FETCH` can cause severe memory issues because Hibernate cannot apply SQL `LIMIT` and `OFFSET` cleanly on a joined Cartesian product. In such scenarios, batch fetching provides an optimal middle ground:

The following entity annotation configures Hibernate to fetch collections in batches using an SQL `IN` predicate:

```java
    @OneToMany(mappedBy = "author", fetch = FetchType.LAZY)
    @org.hibernate.annotations.BatchSize(size = 25)
    private List<Book> books = new ArrayList<>();
```

Alternatively, enable batch fetching globally across all lazy associations in `application.yml`:

```yaml
spring:
  jpa:
    properties:
      hibernate:
        default_batch_fetch_size: 25
```

With a batch size of 25, fetching 100 authors executes only $1 + (100 / 25) = 5$ queries instead of 101! Hibernate executes queries of the form:

```sql
SELECT * FROM books WHERE author_id IN (?, ?, ?, ?, ..., ?);
```

#### Comparison of N+1 Mitigation Strategies

Selecting the appropriate fetch strategy depends on data cardinality and pagination requirements:

| Strategy | Mechanism | Pros | Cons / Caveats |
| :--- | :--- | :--- | :--- |
| **`JOIN FETCH`** | Single SQL query with `JOIN` | Exactly 1 database query; highest performance for unpaginated queries | Cannot be used safely with SQL pagination (`PageRequest`); duplicates parent rows in SQL result set |
| **`@EntityGraph`** | Declarative fetch plan | Clean code; works on generated query methods | Suffers from identical Cartesian product pagination limitations as `JOIN FETCH` |
| **`@BatchSize` / Global Batching** | Executes `IN (?, ...)` queries | Works seamlessly with pagination (`Pageable`); avoids massive Cartesian products | Executes $1 + \lceil N / \text{batch} \rceil$ queries rather than a single query |
| **DTO Projections** | `SELECT new com.example.AuthorSummary(...)` | Fetches only required columns; zero entity management overhead | Read-only; cannot be updated or saved back via ORM |

---

### 7.2 HikariCP Connection Pool Optimization

A database connection is an expensive operating system resource. Establishing a new connection involves TCP 3-way handshakes, TLS negotiation, authentication verification, and server process memory allocation. High-performance applications maintain a pre-allocated pool of persistent connections using **HikariCP**, the default connection pool in Spring Boot.

#### How Connection Pooling Works Under the Hood

When an incoming web request arrives at a transactional service, it borrows an idle database connection from the pool, executes its queries, and returns the connection back to the pool upon transaction completion:

```mermaid
stateDiagram-v2
    [*] --> Idle: Application Starts & Initializes Pool
    
    Idle --> InUse: Thread borrows connection (pool.getConnection())
    InUse --> InUse: Executes SQL Queries within @Transactional boundary
    InUse --> Idle: Transaction completes / commits (connection.close())
    
    Idle --> Exhausted: All max connections currently borrowed
    Exhausted --> ThreadWaiting: New request thread arrives
    ThreadWaiting --> InUse: Connection returned before timeout
    ThreadWaiting --> TimeoutException: connectionTimeout exceeded (Default 30s)
    
    InUse --> LeakLogged: Connection held longer than leakDetectionThreshold
```

#### The Connection Pool Sizing Myth

Many developers assume that larger connection pools increase throughput. In reality, oversized connection pools degrade performance due to disk I/O thrashing and CPU context-switching on the database server.

The PostgreSQL and HikariCP engineering teams established the definitive formula for optimal connection pool sizing:

$$\text{Pool Size} = (\text{CPU Cores} \times 2) + \text{Effective Spindle Count}$$

- **CPU Cores**: The number of physical CPU cores on the database server.
- **Effective Spindle Count**: The number of independent disk spindles (typically 1 for modern NVMe SSDs).

On an 8-core database server with fast SSD storage, the mathematically optimal connection pool size is:

$$(8 \times 2) + 1 = 17 \text{ connections}$$

A pool of 15 to 25 connections can easily handle thousands of requests per second if each transaction executes within 5 to 15 milliseconds.

#### Production HikariCP Configuration

The following `application.yml` provides a battle-tested HikariCP production configuration with active leak detection:

```yaml
spring:
  datasource:
    hikari:
      # Maximum number of actual physical connections in the pool
      maximum-pool-size: 20
      # Keep all connections open to avoid runtime allocation latency spikes
      minimum-idle: 20
      # How long a thread waits for a connection before throwing SQLException (ms)
      connection-timeout: 5000
      # Maximum time a connection may sit idle before being retired (ms)
      idle-timeout: 300000
      # Maximum lifetime of a connection; prevents stale connection leaks on firewalls (ms)
      max-lifetime: 1800000
      # Logs a warning stack trace if a thread holds a connection longer than this (ms)
      # Essential for detecting unclosed transactions or slow external calls inside @Transactional!
      leak-detection-threshold: 4000
      pool-name: ProductionHikariPool
```

#### Diagnosing Connection Leaks

A connection leak occurs when a thread obtains a connection from the pool but fails to return it, frequently caused by executing slow third-party REST calls inside a `@Transactional` method:

```java
// Anti-Pattern: Holds database connection open while waiting for external network call!
@Transactional
public void processOrder(Long orderId) {
    Order order = orderRepository.findById(orderId).orElseThrow();
    
    // BAD: If payment gateway takes 8 seconds, DB connection is held and unusable by other threads!
    paymentGatewayClient.chargeCreditCard(order.getAmount()); 
    
    order.setStatus("PAID");
    orderRepository.save(order);
}
```

When `leak-detection-threshold: 4000` is set, HikariCP outputs an explicit warning with the exact stack trace where the connection was checked out:

```text
WARN 12480 --- [HikariPool-1 housekeeper] com.zaxxer.hikari.pool.ProxyLeakTask : 
Connection leak detection triggered for connection org.postgresql.jdbc.PgConnection@6b3a0c, 
stack trace follows:
    at com.example.demo.service.OrderService.processOrder(OrderService.java:42)
    at com.example.demo.controller.OrderController.pay(OrderController.java:28)
```

---

### 7.3 Concurrency Evolution: Java 21 Virtual Threads (Project Loom)

For decades, the Java Virtual Machine mapped each `java.lang.Thread` directly 1:1 to an operating system kernel thread (Platform Thread). Because OS threads are expensive, modern servers could only support 200 to 500 concurrent threads before exhausting memory and crashing.

#### Platform Threads vs Virtual Threads

Java 21 introduced **Virtual Threads (Project Loom)**, revolutionizing concurrency by separating Java threads from underlying OS kernel threads:

The following diagram contrasts the thread scheduling models during a blocking database query:

```text
Platform Thread Model (1:1 with OS Kernel Thread):
[ Web Request 1 ] ---> [ OS Thread 1 (~1 MB Stack) ] ===> BLOCKED on Database Query (100ms)
                                                           (OS Thread sits idle, wasting RAM & CPU)

Virtual Thread Model (M:N User-Space Cooperative Scheduling):
[ Web Request 1 ] ---> [ Virtual Thread 1 ]
                              | (Mounted)
                       [ Carrier OS Thread A ] ===> Blocks on Database Query (100ms)
                              |
                       [ Virtual Thread 1 UNMOUNTS! ] (Preserves lightweight call stack in heap)
                              |
                       [ Carrier OS Thread A ] ===> Immediately runs Virtual Thread 2!
```

- **Platform Threads**:
  - Allocated directly in OS kernel memory (~1 MB stack per thread).
  - Context switching requires kernel transitions (expensive CPU cache invalidation).
  - An idle thread blocked on database I/O or REST calls holds its OS thread hostage.
- **Virtual Threads**:
  - Lightweight user-space objects managed directly by the JVM runtime (~few hundred bytes).
  - Millions of virtual threads can run simultaneously without memory exhaustion.
  - When a virtual thread encounters blocking I/O (e.g., `SocketInputStream.read()` or `Thread.sleep()`), it **unmounts** from its carrier platform thread. The carrier thread immediately executes other tasks. When the I/O completes, the virtual thread resumes on any available carrier thread.

#### Enabling Virtual Threads in Spring Boot 3.2+

Spring Boot 3.2+ provides first-class support for Virtual Threads via a single configuration flag in `application.yml`:

```yaml
spring:
  threads:
    virtual:
      enabled: true
```

When enabled, Spring Boot automatically configures:
1. **Embedded Tomcat**: Switches Tomcat's request processing executor to use a virtual thread per task (`Executors.newVirtualThreadPerTaskExecutor()`). Every incoming HTTP request executes on its own virtual thread.
2. **Spring Async**: Changes `@Async` execution to use virtual threads.
3. **Scheduled Tasks**: Executes `@Scheduled` methods using virtual threads.
4. **Message Listeners**: RabbitMQ and Kafka message listener containers spawn virtual threads for event processing.

#### Verifying Virtual Thread Execution in Code

The following controller demonstrates how to verify that incoming HTTP requests run on virtual threads:

```java
package com.example.demo.controller;

import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

import java.util.Map;

@RestController
@RequestMapping("/api/v1/threads")
public class ThreadInspectionController {

    private static final Logger log = LoggerFactory.getLogger(ThreadInspectionController.class);

    @GetMapping("/current")
    public Map<String, Object> getCurrentThreadInfo() {
        Thread current = Thread.currentThread();
        
        // Thread.isVirtual() is a Java 21 method returning true for virtual threads
        boolean isVirtual = current.isVirtual();
        String threadDetails = current.toString();

        log.info("Request serviced by: {} (isVirtual = {})", threadDetails, isVirtual);

        return Map.of(
            "threadName", current.getName(),
            "isVirtual", isVirtual,
            "threadDetails", threadDetails
        );
    }
}
```

When you make a request to this endpoint with `spring.threads.virtual.enabled: true`, the log outputs:

```text
Request serviced by: VirtualThread[#38,tomcat-handler-0]/runnable@ForkJoinPool-1-worker-1 (isVirtual = true)
```

Notice that the thread is named `VirtualThread` and is executing on top of carrier worker thread `ForkJoinPool-1-worker-1`.

#### Avoiding the Virtual Thread Pinning Trap

While Virtual Threads dramatically simplify concurrency, developers must avoid **thread pinning**. Pinning occurs when a virtual thread cannot unmount from its carrier thread during blocking operations, degrading performance back to platform thread levels.

Pinning happens primarily in two scenarios:
1. **Inside a `synchronized` block or method**: If a thread blocks on I/O inside a `synchronized` block, it pins the carrier thread.
2. **Executing native methods or Foreign Function Calls (JNI)**.

The following code illustrates refactoring `synchronized` code to `ReentrantLock` to prevent thread pinning:

```java
// BEFORE: Synchronized block PINS the virtual thread to its carrier thread during I/O!
public synchronized String fetchRemoteDataPinned() {
    return restClient.get().uri("https://api.example.com/data").retrieve().body(String.class);
}

// AFTER: ReentrantLock unmounts cleanly without pinning the carrier thread!
private final java.util.concurrent.locks.ReentrantLock lock = new java.util.concurrent.locks.ReentrantLock();

public String fetchRemoteDataClean() {
    lock.lock();
    try {
        return restClient.get().uri("https://api.example.com/data").retrieve().body(String.class);
    } finally {
        lock.unlock();
    }
}
```

To detect pinned threads during performance testing, run the JVM with the diagnostic flag:

```bash
java -Djdk.tracePinnedThreads=full -jar app.jar
```

---

### 7.4 JVM Profiling, Memory Leaks, and Garbage Collection Tuning

Even well-architected applications can experience degradation from memory leaks or excessive Garbage Collection (GC) pauses. Systematic profiling allows engineers to locate allocation hotspots and tune JVM flags.

#### JVM Memory Layout Overview

The Java Virtual Machine organizes memory into specialized regions:

```text
+---------------------------------------------------------------------------------+
|                                 JVM TOTAL MEMORY                                |
+-------------------------------------------------------+-------------------------+
|                       HEAP MEMORY                     |     NON-HEAP MEMORY     |
|  +------------------------+------------------------+  |  +-------------------+  |
|  |     YOUNG GENERATION   |     OLD GENERATION     |  |  |     METASPACE     |  |
|  |  +------+------+----+  |  (Tenured Long-Lived   |  |  | (Class Metadata,  |  |
|  |  | Eden |  S0  | S1 |  |       Objects)         |  |  | Method Bytecode)  |  |
|  |  +------+------+----+  |                        |  |  +-------------------+  |
|  +------------------------+------------------------+  |  |   THREAD STACKS   |  |
|                                                       |  |   CODE CACHE (JIT)|  |
+-------------------------------------------------------+-------------------------+
```

- **Eden Space**: Where new objects are initially allocated. Most objects die young here during minor GCs.
- **Survivor Spaces (S0 / S1)**: Objects that survive Eden collections are copied between survivor spaces.
- **Old (Tenured) Generation**: Objects that survive multiple collection cycles are promoted here. Major GCs (Full GC) clean this space, causing longer pause times.
- **Metaspace**: Stores loaded class structures, method bytecode, and runtime constant pools in native memory.

#### Identifying Common Spring Memory Leaks

A memory leak in Java occurs when unused objects remain reachable through an active root reference, preventing the Garbage Collector from reclaiming their memory:

- **Unbounded Static Collections**: Appending items to static maps or lists without size limits or eviction policies.
- **`ThreadLocal` Leaks**: Storing objects in `ThreadLocal` variables within pooled threads (like Tomcat worker threads) without calling `.remove()`. When the thread returns to the pool, the referenced object remains pinned in memory indefinitely.
- **Unclosed Resource Streams**: Failing to close database `ResultSet` streams, file handles, or network sockets.

#### Capturing Heap Dumps and Using Java Flight Recorder (JFR)

When an application experiences an `OutOfMemoryError` or growing memory consumption, capturing a heap dump or JFR recording isolates the offending classes:

The following JVM flags configure automated heap dumps and low-overhead profiling:

```bash
# Automatically dump the complete heap to disk when an OutOfMemoryError occurs
java -XX:+HeapDumpOnOutOfMemoryError \
     -XX:HeapDumpPath=/var/log/dumps/oom-dump.hprof \
     -XX:+UnlockCommercialFeatures \
     -XX:+FlightRecorder \
     -XX:StartFlightRecording=duration=120s,filename=profile.jfr,settings=profile \
     -jar app.jar
```

Alternatively, trigger an on-demand heap dump via Spring Boot Actuator:

```bash
curl -X POST http://localhost:8080/actuator/heapdump -o live-heapdump.hprof
```

Inspect the `.hprof` file using tools like **Eclipse Memory Analyzer (MAT)** or **VisualVM** to run the "Dominator Tree" analysis, which immediately pinpoints the classes retaining the largest percentage of memory.

#### Choosing Modern Garbage Collectors: G1GC vs ZGC

Spring Boot 3 running on Java 21 supports advanced low-latency collectors:

- **G1GC (Garbage-First GC)**: The default collector in modern JDKs. Balances throughput with pause-time goals (`-XX:MaxGCPauseMillis=200`). Ideal for standard microservices with heaps up to 16 GB.
- **Generational ZGC (Java 21+)**: An ultra-low latency collector designed for multi-gigabyte or terabyte heaps with sub-millisecond maximum pause times. Enable with:

```bash
java -XX:+UseZGC -XX:+ZGenerational -Xmx8g -jar app.jar
```

---

### 7.5 Production Observability: Prometheus & Grafana Performance Dashboards

Production monitoring requires collecting real-time operational telemetry and visualizing it on centralized dashboards.

#### Telemetry Pipeline Architecture

The standard cloud-native monitoring stack combines Spring Boot Actuator, Micrometer, Prometheus, and Grafana:

```mermaid
flowchart LR
    App["Spring Boot 3 Application"] -->|"Micrometer collects JVM & HTTP metrics"| Actuator["/actuator/prometheus Endpoint"]
    Prometheus["Prometheus Server"] -->|"Scrapes every 15s (HTTP Pull)"| Actuator
    Grafana["Grafana Dashboards"] -->|"Queries PromQL"| Prometheus
    Alertmanager["Alertmanager"] -->|"Triggers PagerDuty / Slack on SLA breach"| Prometheus
```

#### Production Docker Compose Stack

The following `docker-compose.yml` launches a local monitoring environment consisting of Prometheus and Grafana connected to your local Spring Boot application:

```yaml
version: '3.8'

services:
  prometheus:
    image: prom/prometheus:v2.48.0
    container_name: prometheus
    volumes:
      - ./prometheus.yml:/etc/prometheus/prometheus.yml
    ports:
      - "9090:9090"

  grafana:
    image: grafana/grafana:10.2.0
    container_name: grafana
    ports:
      - "3000:3000"
    environment:
      - GF_SECURITY_ADMIN_USER=admin
      - GF_SECURITY_ADMIN_PASSWORD=admin
```

The accompanying `prometheus.yml` instructs Prometheus to scrape your application:

```yaml
global:
  scrape_interval: 10s

scrape_configs:
  - job_name: 'spring-boot-app'
    metrics_path: '/actuator/prometheus'
    static_configs:
      - targets: ['host.docker.internal:8080']
```

#### Essential Production PromQL Queries

Once Prometheus scrapes metrics from `/actuator/prometheus`, monitor system health using these industry-standard PromQL queries:

- **HTTP Request Rate (Throughput in RPS)**:
  ```promql
  sum(rate(http_server_requests_seconds_count{status="200"}[1m]))
  ```
- **HTTP p95 Latency by Endpoint**:
  ```promql
  histogram_quantile(0.95, sum(rate(http_server_requests_seconds_bucket[1m])) by (le, uri))
  ```
- **HikariCP Connection Pool Saturation**:
  ```promql
  hikaricp_connections_active / hikaricp_connections_max
  ```
- **JVM Heap Memory Usage Percentage**:
  ```promql
  (jvm_memory_used_bytes{area="heap"} / jvm_memory_max_bytes{area="heap"}) * 100
  ```

---

### 7.6 Task Scheduling and Distributed Locking with ShedLock and Redis

Automated background processing is fundamental to enterprise backends: generating daily financial summaries, sending cart abandonment emails, purging expired user sessions, or warming up caches.

However, scheduling tasks in modern cloud architectures introduces a critical danger: **duplicate execution across multi-instance clusters**.

---

#### Part 1: Building a Task Scheduler in Spring Boot

##### Step 1: Enable Scheduling
In any `@Configuration` or `@SpringBootApplication` class, add the `@EnableScheduling` annotation:

```java
package com.example.demo.config;

import org.springframework.context.annotation.Configuration;
import org.springframework.scheduling.annotation.EnableScheduling;

@Configuration
@EnableScheduling
public class SchedulerConfig {}
```

##### Step 2: The 3 Flavors of `@Scheduled` Tasks

```mermaid
flowchart TD
    subgraph SchedFlavors ["The 3 Scheduling Flavors"]
        direction TB
        FR["1. fixedRate = 5000\nExecutes every 5000ms from START to START\n(Fixed interval regardless of execution time)"]
        FD["2. fixedDelay = 5000\nWaits 5000ms AFTER previous execution FINISHES\n(Prevents overlapping executions)"]
        CR["3. cron = '0 0 2 * * ?'\nExecutes at exact wall-clock calendar times\n(e.g., 2:00 AM every night)"]
    end

    style FR fill:#e1f5fe,stroke:#0288d1
    style FD fill:#e8f5e9,stroke:#2e7d32
    style CR fill:#fff9c4,stroke:#fbc02d
```

```
Timeline Comparison: fixedRate vs. fixedDelay (when task takes 3 seconds):

fixedRate = 5000ms:
0s [ Task 1 starts ] -------- 3s [ Ends ]
                      5s [ Task 2 starts ] -------- 8s [ Ends ]
                                            10s [ Task 3 starts ]

fixedDelay = 5000ms:
0s [ Task 1 starts ] -------- 3s [ Ends ] === (Waits 5s) ===> 8s [ Task 2 starts ]
```

##### Demystifying Cron Expressions:
Spring's `@Scheduled` uses a **6-field cron pattern**:

```
 ┌───────────── second (0 - 59)
 │ ┌───────────── minute (0 - 59)
 │ │ ┌───────────── hour (0 - 23)
 │ │ │ ┌───────────── day of the month (1 - 31)
 │ │ │ │ ┌───────────── month (1 - 12 or JAN - DEC)
 │ │ │ │ │ ┌───────────── day of the week (0 - 7 or SUN - SAT)
 │ │ │ │ │ │
 * * * * * *
```

- `"0 0 2 * * ?"` $\rightarrow$ Run at 2:00:00 AM every night.
- `"0 */15 * * * ?"` $\rightarrow$ Run every 15 minutes.
- `"0 0 9-17 * * MON-FRI"` $\rightarrow$ Run at the top of every hour during business hours on weekdays.

##### Production Task Scheduler Service:

```java
package com.example.demo.scheduler;

import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.scheduling.annotation.Scheduled;
import org.springframework.stereotype.Service;

import java.time.LocalDateTime;

@Service
public class ReportSchedulerService {

    private static final Logger log = LoggerFactory.getLogger(ReportSchedulerService.class);

    // 1. Fixed Rate: Fires every 10 seconds (10,000ms) with a 5s initial startup delay
    @Scheduled(initialDelay = 5000, fixedRate = 10000)
    public void synchronizeInventory() {
        log.info("Synchronizing inventory with external supplier at: {}", LocalDateTime.now());
    }

    // 2. Fixed Delay: Waits 30 seconds AFTER previous audit run completes
    @Scheduled(fixedDelay = 30000)
    public void cleanupExpiredSessions() {
        log.info("Purging expired user sessions from cache...");
    }

    // 3. Cron Expression: Runs at 00:00 (Midnight) every Sunday
    @Scheduled(cron = "0 0 0 ? * SUN")
    public void generateWeeklyFinancialSummary() {
        log.info("Generating weekly financial PDF report...");
    }
}
```

##### Critical Beginner Trap: The Single-Threaded Default!
By default, Spring Boot runs all scheduled tasks on a **single worker thread**!
If `synchronizeInventory()` takes 15 minutes, `cleanupExpiredSessions()` is **blocked and cannot run** until the first task finishes!

**The Fix: Configure a Dedicated `ThreadPoolTaskScheduler`**:

```java
package com.example.demo.config;

import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.scheduling.concurrent.ThreadPoolTaskScheduler;

@Configuration
public class SchedulingPoolConfig {

    @Bean
    public ThreadPoolTaskScheduler taskScheduler() {
        ThreadPoolTaskScheduler scheduler = new ThreadPoolTaskScheduler();
        scheduler.setPoolSize(5); // Allows up to 5 scheduled tasks to run concurrently in parallel
        scheduler.setThreadNamePrefix("scheduled-task-");
        scheduler.setErrorHandler(throwable -> {
            System.err.println("Scheduled task threw unhandled exception: " + throwable.getMessage());
        });
        scheduler.initialize();
        return scheduler;
    }
}
```

---

#### Part 2: The Multi-Instance Scheduling Disaster

In production Kubernetes or cloud environments, applications run across multiple pods/instances (e.g. `App-Pod-1`, `App-Pod-2`, `App-Pod-3`) behind a load balancer.

```mermaid
flowchart TD
    subgraph Disaster ["The Multi-Instance Scheduling Disaster"]
        Cron["Midnight 00:00 AM Cron Trigger Fires!"]
        Cron --> P1["App Pod 1: Runs Cron -> Charges Customer Credit Card ($50)"]
        Cron --> P2["App Pod 2: Runs Cron -> Charges Customer Credit Card ($50)"]
        Cron --> P3["App Pod 3: Runs Cron -> Charges Customer Credit Card ($50)"]
    end

    style Disaster fill:#ffebee,stroke:#c62828,stroke-width:2px,color:#000
```

> [!CAUTION]
> **Duplicate Execution Alert**:
> Spring Boot's built-in `@Scheduled` annotation is **instance-local**. It has zero awareness of other application instances!
> If you deploy 3 pods of your application, every single pod will execute the midnight batch job, sending 3 duplicate emails and charging customers 3 times!

---

#### Part 3: Distributed Locking with ShedLock

To ensure that a scheduled task executes on **exactly one node at a time**, we use **Distributed Locking**.

**ShedLock** is the industry-standard lightweight library designed specifically for Spring's `@Scheduled`. It coordinates locks using an external shared datastore (PostgreSQL, MySQL, or Redis).

```mermaid
sequenceDiagram
    autonumber
    participant P1 as App Pod 1
    participant P2 as App Pod 2
    participant P3 as App Pod 3
    participant DB as Shared Store (PostgreSQL / Redis)

    Note over P1,P3: 00:00:00 - Midnight Cron triggers on all 3 pods simultaneously
    P1->>DB: INSERT / UPDATE lock WHERE name = 'nightlyReport' (Attempt to acquire)
    P2->>DB: INSERT / UPDATE lock WHERE name = 'nightlyReport' (Attempt to acquire)
    P3->>DB: INSERT / UPDATE lock WHERE name = 'nightlyReport' (Attempt to acquire)

    DB-->>P1: Lock ACQUIRED! (Pod 1 holds lock until 00:15:00)
    DB-->>P2: Lock DENIED! (Already held by Pod 1)
    DB-->>P3: Lock DENIED! (Already held by Pod 1)

    Note over P2: Pod 2 skips execution immediately!
    Note over P3: Pod 3 skips execution immediately!

    P1->>P1: Executes generateWeeklyFinancialSummary()
    P1->>DB: Task finished! Updates lock_until
```

---

#### Understanding `lockAtMostFor` and `lockAtLeastFor`

ShedLock introduces two critical parameters to protect against failure:

1. **`lockAtMostFor` (Safety Against Node Death)**:
   - If Pod 1 acquires the lock and immediately suffers a hardware failure, kernel panic, or out-of-memory kill, the lock would remain stuck forever without this setting!
   - `lockAtMostFor = "15m"` guarantees that even if Pod 1 dies without releasing the lock, the lock automatically expires after 15 minutes.
2. **`lockAtLeastFor` (Safety Against Fast Execution & Clock Drift)**:
   - If Pod 1 runs a task that completes in $50\text{ ms}$, and releases the lock, Pod 2's clock might be 200ms slower. Pod 2 would see the lock free and run the task a second time!
   - `lockAtLeastFor = "30s"` guarantees the lock stays held for at least 30 seconds, preventing other pods from running it during that interval.

---

#### Complete Implementation: ShedLock with PostgreSQL / MySQL

##### Step 1: Add ShedLock Dependencies in `pom.xml`:

```xml
<!-- Core ShedLock Spring Integration -->
<dependency>
    <groupId>net.javacrumbs.shedlock</groupId>
    <artifactId>shedlock-spring</artifactId>
    <version>5.13.0</version>
</dependency>

<!-- ShedLock JDBC Provider for Relational Databases (PostgreSQL / MySQL) -->
<dependency>
    <groupId>net.javacrumbs.shedlock</groupId>
    <artifactId>shedlock-provider-jdbc-template</artifactId>
    <version>5.13.0</version>
</dependency>
```

##### Step 2: Create the `shedlock` Database Table (SQL / Flyway):

```sql
-- PostgreSQL / MySQL Table Schema
CREATE TABLE shedlock (
    name VARCHAR(64) NOT NULL,
    lock_until TIMESTAMP NOT NULL,
    locked_at TIMESTAMP NOT NULL,
    locked_by VARCHAR(255) NOT NULL,
    PRIMARY KEY (name)
);
```

##### Step 3: Configure `LockProvider` in Spring:

```java
package com.example.demo.config;

import net.javacrumbs.shedlock.core.LockProvider;
import net.javacrumbs.shedlock.provider.jdbctemplate.JdbcTemplateLockProvider;
import net.javacrumbs.shedlock.spring.annotation.EnableSchedulerLock;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

import javax.sql.DataSource;

@Configuration
// defaultLockAtMostFor: Fallback safety if a task doesn't specify its own lockAtMostFor
@EnableSchedulerLock(defaultLockAtMostFor = "10m")
public class ShedLockConfiguration {

    @Bean
    public LockProvider lockProvider(DataSource dataSource) {
        return new JdbcTemplateLockProvider(
                JdbcTemplateLockProvider.Configuration.builder()
                        .withJdbcTemplate(new org.springframework.jdbc.core.JdbcTemplate(dataSource))
                        .usingDbTime() // Use database clock to avoid host clock drift issues!
                        .build()
        );
    }
}
```

##### Step 4: Annotate Scheduled Methods with `@SchedulerLock`:

```java
package com.example.demo.scheduler;

import net.javacrumbs.shedlock.spring.annotation.SchedulerLock;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.scheduling.annotation.Scheduled;
import org.springframework.stereotype.Service;

@Service
public class DistributedBillingScheduler {

    private static final Logger log = LoggerFactory.getLogger(DistributedBillingScheduler.class);

    /**
     * Executes at 2:00 AM every night.
     * ShedLock guarantees that across 10 Kubernetes pods, EXACTLY ONE POD runs this method!
     */
    @Scheduled(cron = "0 0 2 * * ?")
    @SchedulerLock(
            name = "generateCustomerInvoicesTask",
            lockAtMostFor = "30m",   // Release lock after 30 mins even if node crashes
            lockAtLeastFor = "1m"    // Keep lock held for at least 1 min to prevent duplicate runs
    )
    public void generateCustomerInvoices() {
        log.info("Lock acquired! Generating customer monthly invoices...");
        // Heavy billing calculation...
    }
}
```

---

#### Alternative: Distributed Locking with Redis (Redisson)

For high-speed, non-scheduled application locking (e.g., preventing two users from claiming the same promo code in a REST controller), use **Redisson Distributed Locks**:

```java
package com.example.demo.service;

import org.redisson.api.RLock;
import org.redisson.api.RedissonClient;
import org.springframework.stereotype.Service;

import java.util.concurrent.TimeUnit;

@Service
public class PromoCodeService {

    private final RedissonClient redissonClient;

    public PromoCodeService(RedissonClient redissonClient) {
        this.redissonClient = redissonClient;
    }

    public void redeemCoupon(String couponCode, String userId) {
        // Create a distributed lock key specific to this coupon
        RLock lock = redissonClient.getLock("lock:coupon:" + couponCode);

        try {
            // Wait up to 5 seconds to acquire lock, hold lock for at most 10 seconds (automatic watchdog)
            boolean isLocked = lock.tryLock(5, 10, TimeUnit.SECONDS);
            if (!isLocked) {
                throw new IllegalStateException("Coupon is currently being processed by another user. Try again.");
            }

            // Critical Section: Only one thread across all clusters can execute here!
            System.out.println("Processing coupon redemption for user: " + userId);

        } catch (InterruptedException e) {
            Thread.currentThread().interrupt();
        } finally {
            // Always unlock in a finally block!
            if (lock.isHeldByCurrentThread()) {
                lock.unlock();
            }
        }
    }
}
```

---

### Chapter 7 Exercises & Solutions

Test your knowledge of performance tuning, database optimization, and Virtual Threads.

#### Exercise 7.1: Fixing N+1 Queries with DTO Projections

**Task**: You have an `Order` entity with a lazy collection of `OrderItem` objects. You need an endpoint that returns order summaries (`id`, `orderNumber`, `totalItemCount`) for the 10 most recent orders without causing an N+1 query storm and without loading full entity objects into the persistence context. Write the Spring Data JPQL projection query.

The following solution uses a Java 17 record constructor expression to compute the aggregate count directly in SQL:

```java
package com.example.demo.dto;

public record OrderSummaryDto(Long id, String orderNumber, Long totalItemCount) {}
```

The repository query maps directly to the DTO constructor:

```java
package com.example.demo.repository;

import com.example.demo.dto.OrderSummaryDto;
import com.example.demo.domain.Order;
import org.springframework.data.domain.Pageable;
import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.data.jpa.repository.Query;
import org.springframework.stereotype.Repository;

import java.util.List;

@Repository
public interface OrderRepository extends JpaRepository<Order, Long> {

    // Emits exactly ONE query using SQL GROUP BY and aggregate COUNT
    @Query("""
        SELECT new com.example.demo.dto.OrderSummaryDto(o.id, o.orderNumber, COUNT(i.id))
        FROM Order o
        LEFT JOIN o.items i
        GROUP BY o.id, o.orderNumber
        ORDER BY o.id DESC
    """)
    List<OrderSummaryDto> findRecentOrderSummaries(Pageable pageable);
}
```

#### Exercise 7.2: Refactoring Thread Pinning Code

**Task**: The following service method executes an expensive external payment call inside a `synchronized` block. Under high concurrency with Java 21 Virtual Threads enabled, this method severely degrades throughput. Explain why and rewrite it using non-pinning concurrency primitives.

```java
// Problematic Code:
public synchronized PaymentResult processPayment(PaymentRequest req) {
    return restClient.post().uri("/charges").body(req).retrieve().body(PaymentResult.class);
}
```

**Explanation and Refactored Solution**:
The `synchronized` keyword causes the virtual thread to pin its underlying carrier thread while waiting for the blocking HTTP network call to complete. To eliminate pinning, replace the monitor lock with a `ReentrantLock`:

```java
package com.example.demo.service;

import org.springframework.stereotype.Service;
import org.springframework.web.client.RestClient;
import java.util.concurrent.locks.ReentrantLock;

@Service
public class OptimizedPaymentService {

    private final RestClient restClient;
    private final ReentrantLock lock = new ReentrantLock();

    public OptimizedPaymentService(RestClient.Builder builder) {
        this.restClient = builder.baseUrl("https://payment.example.com").build();
    }

    public PaymentResult processPayment(PaymentRequest req) {
        lock.lock();
        try {
            // ReentrantLock allows the virtual thread to unmount cleanly during blocking HTTP I/O
            return restClient.post()
                    .uri("/charges")
                    .body(req)
                    .retrieve()
                    .body(PaymentResult.class);
        } finally {
            lock.unlock();
        }
    }
}
```

---

## Chapter 8: Spring Reactive and Spring Cloud Stream

For systems requiring massive streaming concurrency, push notifications, or decoupled event-driven microservice messaging, Spring provides reactive programming models and asynchronous stream binders.

### 8.0 Reactive Streams Mental Model: Mono and Flux

Traditional Spring MVC applications follow a thread-per-request paradigm: an operating system thread is assigned to each incoming HTTP request for its entire lifespan. In contrast, reactive programming is based on non-blocking asynchronous event loops that handle massive concurrency with a small, fixed thread pool.

#### The Reactive Manifesto and Backpressure

The foundation of reactive programming in Java is the **Reactive Streams specification**, comprised of four fundamental interfaces:
1. `Publisher<T>`: Emits a potential infinite stream of sequenced data items.
2. `Subscriber<T>`: Listens for events emitted by a publisher.
3. `Subscription`: Connects a publisher and subscriber; allows the subscriber to demand data.
4. `Processor<T, R>`: Represents a processing stage that acts as both subscriber and publisher.

The defining characteristic of Reactive Streams is **non-blocking backpressure**:

```mermaid
sequenceDiagram
    autonumber
    participant Sub as Subscriber (Consumer)
    participant Pub as Publisher (Producer)

    Sub->>Pub: 1. subscribe(Subscriber)
    Pub-->>Sub: 2. onSubscribe(Subscription)
    
    Note over Sub,Pub: Backpressure in action: Consumer dictates demand!
    Sub->>Pub: 3. subscription.request(2) [Demands at most 2 items]
    Pub-->>Sub: 4. onNext(item 1)
    Pub-->>Sub: 5. onNext(item 2)
    
    Note over Sub,Pub: Publisher pauses! Waits for further consumer demand.
    Sub->>Pub: 6. subscription.request(1) [Demands 1 more item]
    Pub-->>Sub: 7. onNext(item 3)
    Pub-->>Sub: 8. onComplete() [Stream finished]
```

Without backpressure, a fast producer (e.g., reading 100,000 database rows) can overwhelm a slow consumer (e.g., streaming over a throttled mobile network), leading to buffer overflows and `OutOfMemoryError` crashes.

#### Project Reactor Primitives: `Mono<T>` vs `Flux<T>`

Spring WebFlux is built on **Project Reactor**, which implements the Reactive Streams specification through two primary publisher types:

```text
Mono<T> (Emits 0 or 1 item):
--[ item ]------------|--------->  (Completes successfully with 1 value)
----------------------|--------->  (Completes empty - like Optional.empty())
------------X------------------->  (Terminates with onError(ex))

Flux<T> (Emits 0 to N items):
--[ item 1 ]---[ item 2 ]---[ item 3 ]---|---------> (Completes with 3 values)
--[ event ]----[ event ]----[ event ]--------------> (Infinite real-time stream)
--[ item 1 ]---X-----------------------------------> (Emits 1 item then errors)
```

- **`Mono<T>`**: Emits at most one item, then terminates with `onComplete` or `onError`. Used for single-value operations (e.g., `findById`, `save`, `count`).
- **`Flux<T>`**: Emits an asynchronous stream of 0 to $N$ items. Used for collections, database queries returning multiple records, and real-time streaming feeds.

#### Imperative vs Reactive Programming Comparison

The following table highlights the conceptual transition from synchronous imperative constructs to reactive publishers:

| Concept | Traditional Imperative | Project Reactor Reactive |
| :--- | :--- | :--- |
| Single Value (Present) | `T` (e.g., `User`) | `Mono<T>` |
| Single Value (Optional) | `Optional<T>` | `Mono<T>` (empty indicates absence) |
| Multiple Values | `List<T>`, `Set<T>` | `Flux<T>` |
| Asynchronous Future | `CompletableFuture<T>` | `Mono<T>` |
| Real-Time Event Stream | WebSockets / Polling | `Flux<T>` (via Server-Sent Events) |
| Execution Trigger | Eager (executes immediately) | **Lazy (nothing happens until `.subscribe()`)** |

> [!IMPORTANT]
> **Nothing Happens Until You Subscribe!**
> In Project Reactor, defining a `Mono` or `Flux` merely builds an execution pipeline. The code inside does not execute until an active subscriber registers. In Spring WebFlux, the framework automatically subscribes to publishers returned by controller methods.

---

### 8.1 Building Reactive REST APIs with Spring WebFlux

Spring WebFlux provides a fully non-blocking reactive web runtime built on **Project Reactor** and **Netty**, capable of serving tens of thousands of concurrent connections with minimal memory overhead.

#### Project Dependencies for WebFlux

To build a WebFlux service, include the reactive web starter in your Maven `pom.xml`:

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-webflux</artifactId>
</dependency>
```

#### Step-by-Step Implementation: Reactive Controller

The following controller exposes non-blocking endpoints demonstrating single-value retrieval, data transformation, and real-time Server-Sent Events (SSE) streaming:

The controller definition with full reactive pipelines:

```java
package com.example.demo.reactive.controller;

import org.springframework.http.HttpStatus;
import org.springframework.http.MediaType;
import org.springframework.web.bind.annotation.*;
import org.springframework.web.server.ResponseStatusException;
import reactor.core.publisher.Flux;
import reactor.core.publisher.Mono;

import java.time.Duration;
import java.util.Map;
import java.util.concurrent.ConcurrentHashMap;

public record SensorReading(String sensorId, double temperatureCelsius, long timestamp) {}

@RestController
@RequestMapping("/api/v1/sensors")
public class ReactiveSensorController {

    private final Map<String, SensorReading> inMemoryStore = new ConcurrentHashMap<>();

    public ReactiveSensorController() {
        inMemoryStore.put("SN-101", new SensorReading("SN-101", 22.4, System.currentTimeMillis()));
        inMemoryStore.put("SN-102", new SensorReading("SN-102", 28.1, System.currentTimeMillis()));
    }

    // 1. Single non-blocking resource retrieval (Mono)
    @GetMapping("/{id}")
    public Mono<SensorReading> getSensorById(@PathVariable String id) {
        return Mono.justOrEmpty(inMemoryStore.get(id))
                // Non-blocking error handling if the sensor is missing
                .switchIfEmpty(Mono.error(new ResponseStatusException(HttpStatus.NOT_FOUND, "Sensor not found")));
    }

    // 2. Reactive mutation returning Created status (Mono)
    @PostMapping
    @ResponseStatus(HttpStatus.CREATED)
    public Mono<SensorReading> registerSensor(@RequestBody SensorReading reading) {
        return Mono.fromCallable(() -> {
            inMemoryStore.put(reading.sensorId(), reading);
            return reading;
        });
    }

    // 3. Server-Sent Events (SSE) streaming: Pushes telemetry readings every 1 second
    @GetMapping(value = "/stream", produces = MediaType.TEXT_EVENT_STREAM_VALUE)
    public Flux<SensorReading> streamLiveTelemetry() {
        return Flux.interval(Duration.ofSeconds(1)) // Emits an incrementing Long tick every second
                .map(sequence -> new SensorReading(
                        "LIVE-STREAM",
                        20.0 + (Math.random() * 10.0), // Generates random temperature reading
                        System.currentTimeMillis()
                ))
                // Cleanly limits the stream or runs indefinitely until the client disconnects
                .log(); // Logs reactive signals (onSubscribe, request, onNext) for debugging
    }
}
```

#### Consuming Remote Endpoints with Reactive `WebClient`

The legacy `RestTemplate` is fundamentally blocking and should not be used in modern Spring Boot 3 applications. **`WebClient`** is Spring's modern, fully non-blocking HTTP client supporting both reactive and synchronous programming models:

The following service demonstrates fetching external data asynchronously using `WebClient`:

```java
package com.example.demo.reactive.client;

import com.example.demo.reactive.controller.SensorReading;
import org.springframework.stereotype.Service;
import org.springframework.web.reactive.function.client.WebClient;
import reactor.core.publisher.Flux;
import reactor.core.publisher.Mono;
import reactor.util.retry.Retry;

import java.time.Duration;

@Service
public class ExternalWeatherClient {

    private final WebClient webClient;

    public ExternalWeatherClient(WebClient.Builder builder) {
        this.webClient = builder
                .baseUrl("https://api.weather-provider.com")
                .build();
    }

    public Mono<SensorReading> fetchRemoteWeather(String cityId) {
        return webClient.get()
                .uri("/v1/forecast/{id}", cityId)
                .retrieve()
                .bodyToMono(SensorReading.class)
                // Timeout if upstream service fails to respond within 2 seconds
                .timeout(Duration.ofSeconds(2))
                // Non-blocking retry with exponential backoff on transient network failures
                .retryWhen(Retry.backoff(3, Duration.ofMillis(200)))
                // Fallback value if upstream is completely unavailable
                .onErrorResume(ex -> Mono.just(new SensorReading(cityId, 0.0, System.currentTimeMillis())));
    }
}
```

---

### 8.2 Non-Blocking Relational Persistence with Spring Data R2DBC

Traditional JDBC (and Hibernate) is fundamentally blocking: a thread must wait idle while the database parses the query, reads disk blocks, and returns result sets. **R2DBC (Reactive Relational Database Connectivity)** provides a vendor-neutral, fully reactive driver specification for SQL databases including PostgreSQL, MySQL, and SQL Server.

#### Architectural Contrast: JDBC / JPA vs R2DBC

Understanding the differences between JPA and R2DBC is essential before designing reactive database applications:

```text
Traditional Spring Data JPA (Blocking):
[ Thread 1 ] ---> [ Hibernate ORM (Lazy Proxies, Dirty Checking) ] ---> [ JDBC Driver (Blocks Thread) ]

Spring Data R2DBC (Non-Blocking Reactive):
[ Event Loop ] -> [ ReactiveCrudRepository (Explicit SQL Mapping) ] -> [ R2DBC Driver (Async Socket Streams) ]
```

- **No Lazy Loading**: R2DBC does not support transparent lazy-loading proxies because calling a getter cannot trigger a blocking database query in a reactive architecture.
- **No Dirty Checking / First-Level Cache**: All database queries and updates must be explicitly invoked via repositories or `DatabaseClient`.
- **Lightweight Table Mapping**: Uses simple `@Table` and `@Id` annotations directly without complex entity relationship hierarchies (`@ManyToMany`, `@JoinColumn`).

#### R2DBC Maven Dependencies

Add Spring Data R2DBC and the PostgreSQL R2DBC driver to your `pom.xml`:

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-r2dbc</artifactId>
</dependency>
<dependency>
    <groupId>org.postgresql</groupId>
    <artifactId>r2dbc-postgresql</artifactId>
    <scope>runtime</scope>
</dependency>
```

#### Complete R2DBC Implementation

The following complete example implements a reactive PostgreSQL entity, repository, and service with declarative transactions:

The entity maps directly to a relational table:

```java
package com.example.demo.r2dbc.domain;

import org.springframework.data.annotation.Id;
import org.springframework.data.relational.core.mapping.Table;

@Table("customer_accounts")
public class CustomerAccount {

    @Id
    private Long id;
    private String accountNumber;
    private double balance;

    public CustomerAccount() {}

    public CustomerAccount(Long id, String accountNumber, double balance) {
        this.id = id;
        this.accountNumber = accountNumber;
        this.balance = balance;
    }

    public Long getId() { return id; }
    public String getAccountNumber() { return accountNumber; }
    public double getBalance() { return balance; }
    public void setBalance(double balance) { this.balance = balance; }
}
```

The reactive repository interface extends `ReactiveCrudRepository`:

```java
package com.example.demo.r2dbc.repository;

import com.example.demo.r2dbc.domain.CustomerAccount;
import org.springframework.data.r2dbc.repository.Query;
import org.springframework.data.repository.reactive.ReactiveCrudRepository;
import org.springframework.stereotype.Repository;
import reactor.core.publisher.Flux;
import reactor.core.publisher.Mono;

@Repository
public interface CustomerAccountRepository extends ReactiveCrudRepository<CustomerAccount, Long> {

    // Returns a non-blocking Mono emitting the found account or completing empty
    Mono<CustomerAccount> findByAccountNumber(String accountNumber);

    // Custom SQL query returning a non-blocking Flux stream
    @Query("SELECT * FROM customer_accounts WHERE balance >= :minBalance ORDER BY balance DESC")
    Flux<CustomerAccount> findWealthyAccounts(double minBalance);
}
```

The service layer handles reactive transactions using `@Transactional`:

```java
package com.example.demo.r2dbc.service;

import com.example.demo.r2dbc.domain.CustomerAccount;
import com.example.demo.r2dbc.repository.CustomerAccountRepository;
import org.springframework.stereotype.Service;
import org.springframework.transaction.annotation.Transactional;
import reactor.core.publisher.Mono;

@Service
public class AccountTransferService {

    private final CustomerAccountRepository repository;

    public AccountTransferService(CustomerAccountRepository repository) {
        this.repository = repository;
    }

    // In R2DBC, @Transactional manages reactive transactions across the returned Publisher!
    @Transactional
    public Mono<Void> transferFunds(String fromAccount, String toAccount, double amount) {
        return repository.findByAccountNumber(fromAccount)
                .switchIfEmpty(Mono.error(new IllegalArgumentException("Source account not found")))
                .flatMap(source -> {
                    if (source.getBalance() < amount) {
                        return Mono.error(new IllegalStateException("Insufficient balance"));
                    }
                    source.setBalance(source.getBalance() - amount);
                    return repository.save(source);
                })
                .then(repository.findByAccountNumber(toAccount))
                .switchIfEmpty(Mono.error(new IllegalArgumentException("Destination account not found")))
                .flatMap(dest -> {
                    dest.setBalance(dest.getBalance() + amount);
                    return repository.save(dest);
                })
                .then(); // Completes with Mono<Void> when the transaction successfully commits
    }
}
```

---

### 8.3 Event-Driven Messaging with Spring Cloud Stream and RabbitMQ

In distributed enterprise architectures, microservices communicate asynchronously by publishing domain events to message brokers like RabbitMQ or Apache Kafka. **Spring Cloud Stream** abstracts the underlying broker mechanics into a unified, functional programming model.

#### Spring Cloud Stream Core Concepts

Spring Cloud Stream eliminates boilerplate messaging code by introducing three core architectural components:

```mermaid
flowchart LR
    subgraph ServiceA["Order Service (Publisher)"]
        Supplier["Supplier<OrderEvent><br/>or StreamBridge"]
    end
    
    subgraph Broker["RabbitMQ Message Broker"]
        Exchange["Exchange: orders-topic"]
        Queue1["Queue: inventory-orders"]
        Queue2["Queue: notification-orders"]
        Exchange --> Queue1
        Exchange --> Queue2
    end
    
    subgraph ServiceB["Inventory Service"]
        Consumer1["Consumer<OrderEvent>"]
    end
    
    subgraph ServiceC["Notification Service"]
        Consumer2["Consumer<OrderEvent>"]
    end

    Supplier -->|"Binding: orderSupplier-out-0"| Exchange
    Queue1 -->|"Binding: orderConsumer-in-0"| Consumer1
    Queue2 -->|"Binding: notificationConsumer-in-0"| Consumer2
```

- **Destination Binders**: Components responsible for integrating with external messaging systems (e.g., RabbitMQ, Apache Kafka, Amazon Kinesis).
- **Bindings**: Declarative configurations in `application.yml` that bridge external broker destinations (exchanges/topics) to application code.
- **Consumer Groups**: Ensures that multiple instances of the same microservice share work in a round-robin competing consumer pattern, rather than each receiving a duplicate copy of every message.
- **Dead Letter Queue (DLQ)**: A dedicated quarantine queue where unprocessable or poisoned messages are automatically routed after retry attempts are exhausted.

#### Maven Dependencies for Spring Cloud Stream RabbitMQ

Add the Spring Cloud Stream RabbitMQ starter to your `pom.xml`:

```xml
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-stream-rabbit</artifactId>
</dependency>
```

#### The Functional Programming Model

Spring Boot 3 and Spring Cloud Stream 4 leverage standard Java functional interfaces (`Supplier`, `Function`, `Consumer`) to define message handlers:

The following configuration defines event processors and consumers:

```java
package com.example.demo.stream;

import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

import java.util.function.Consumer;
import java.util.function.Function;

public record OrderEvent(String orderId, String customerId, double amount, String status) {}

@Configuration
public class OrderStreamConfiguration {

    private static final Logger log = LoggerFactory.getLogger(OrderStreamConfiguration.class);

    // 1. Processor (Function<Input, Output>): Enriches and transforms incoming events
    @Bean
    public Function<OrderEvent, OrderEvent> processOrder() {
        return incomingOrder -> {
            log.info("Processing order event: {}", incomingOrder.orderId());
            // Transforms order status to APPROVED
            return new OrderEvent(
                    incomingOrder.orderId(),
                    incomingOrder.customerId(),
                    incomingOrder.amount(),
                    "APPROVED"
            );
        };
    }

    // 2. Sink / Consumer (Consumer<Input>): Final message destination (logs or persists)
    @Bean
    public Consumer<OrderEvent> auditOrder() {
        return event -> {
            log.info("AUDIT LOG: Order {} finalized with status {}", event.orderId(), event.status());
        };
    }
}
```

#### Publishing Events on Demand with `StreamBridge`

While `Supplier` is suitable for scheduled or polling producers, interactive web applications need to send messages immediately upon user actions. **`StreamBridge`** provides on-demand publishing:

The following REST controller publishes domain events to RabbitMQ when an order is created:

```java
package com.example.demo.stream.controller;

import com.example.demo.stream.OrderEvent;
import org.springframework.cloud.stream.function.StreamBridge;
import org.springframework.http.HttpStatus;
import org.springframework.web.bind.annotation.*;

@RestController
@RequestMapping("/api/v1/orders")
public class OrderEventPublishingController {

    private final StreamBridge streamBridge;

    public OrderEventPublishingController(StreamBridge streamBridge) {
        this.streamBridge = streamBridge;
    }

    @PostMapping
    @ResponseStatus(HttpStatus.ACCEPTED)
    public void submitOrder(@RequestBody OrderEvent order) {
        // Publishes directly to the binding named "orderOutput-out-0"
        streamBridge.send("orderOutput-out-0", order);
    }
}
```

#### Enterprise Production Configuration with Consumer Groups and DLQ

The following `application.yml` demonstrates production-ready configuration connecting the functional beans to RabbitMQ exchanges, consumer groups, and dead-letter queues:

```yaml
spring:
  cloud:
    stream:
      bindings:
        # StreamBridge output binding
        orderOutput-out-0:
          destination: orders.exchange
        # processOrder function input binding
        processOrder-in-0:
          destination: orders.exchange
          group: order-processing-group # Consumer group for load balancing across instances
        # processOrder function output binding
        processOrder-out-0:
          destination: approved-orders.exchange
        # auditOrder consumer input binding
        auditOrder-in-0:
          destination: approved-orders.exchange
          group: audit-logging-group
      rabbit:
        bindings:
          processOrder-in-0:
            consumer:
              # Automatically route failed messages to a Dead Letter Queue (DLQ)
              auto-bind-dlq: true
              max-attempts: 3
              requeue-rejected: false
              dlq-name: orders.dlq
```

---

### 8.4 Pub/Sub and Event Streaming with Apache Kafka & Reactive Spring

While traditional message brokers (like RabbitMQ) excel at routing discrete messages to point-to-point queues and deleting them once acknowledged, **Apache Kafka** is a distributed, horizontally partitioned, replicated **event streaming platform**.

---

#### Pub/Sub vs. Point-to-Point Queue: Mental Model

```mermaid
flowchart TD
    subgraph PTP ["Point-to-Point Queue (RabbitMQ / AWS SQS)"]
        direction TB
        PProducer["Publisher"] --> PQueue["Queue: orders"]
        PQueue -->|Worker 1 consumes| C1["Worker 1 (Message DELETED!)"]
        PQueue -.->|Worker 2 gets nothing| C2["Worker 2"]
    end

    subgraph PubSub ["Pub/Sub Distributed Commit Log (Apache Kafka)"]
        direction TB
        KProducer["Publisher"] --> KTopic["Topic: orders-topic (Immutable Append-Only Log)\n[Msg 0 | Msg 1 | Msg 2 | Msg 3 | Msg 4]"]
        KTopic -->|"Consumer Group A (Offset: 4)"| G1["Inventory Service\n(Reads from beginning to end)"]
        KTopic -->|"Consumer Group B (Offset: 2)"| G2["Analytics Service\n(Reads at its own slower speed)"]
        KTopic -->|"Consumer Group C (Offset: 0)"| G3["Audit Service\n(Replays all history from Msg 0)"]
    end

    style PTP fill:#fbe9e7,stroke:#d84315,color:#000
    style PubSub fill:#e8f5e9,stroke:#2e7d32,color:#000
```

- **Point-to-Point (Queues)**: A message is delivered to exactly one worker and destroyed once processed.
- **Pub/Sub (Kafka Commit Log)**: Messages are appended to an immutable disk log and retained for days or months. Multiple independent subscriber groups read the same stream at their own pace, tracking their progress using **Offsets**.

---

#### Core Kafka Architecture: Topics, Partitions, and Offsets

```
Topic: 'orders-topic' (3 Partitions across Kafka cluster)

Partition 0: [ 0 | 1 | 2 | 3 | 4 | 5 ]  ---> Read by Consumer Instance 1
Partition 1: [ 0 | 1 | 2 | 3 ]          ---> Read by Consumer Instance 2
Partition 2: [ 0 | 1 | 2 | 3 | 4 ]      ---> Read by Consumer Instance 3
```

- **Topic**: A logical category where records are published.
- **Partition**: Topics are sliced into partitions across multiple servers for horizontal scaling.
- **Partition Key**: Kafka hashes the message key (`e.g., orderId`). **Messages with the exact same key are guaranteed to land on the same partition, preserving strict chronological ordering!**
- **Consumer Group**: Multiple instances of the same service join a group to share partitions. If you have 3 partitions and 3 service pods, each pod reads from exactly 1 partition.

---

#### Standard Spring for Apache Kafka (`spring-kafka`)

##### Step 1: Add Dependency to `pom.xml`

```xml
<dependency>
    <groupId>org.springframework.kafka</groupId>
    <artifactId>spring-kafka</artifactId>
</dependency>
```

##### Step 2: Configuration in `application.yml`

```yaml
spring:
  kafka:
    bootstrap-servers: localhost:9092
    producer:
      key-serializer: org.apache.kafka.common.serialization.StringSerializer
      value-serializer: org.springframework.kafka.support.serializer.JsonSerializer
      acks: all # Wait for all in-sync replicas to confirm write (zero data loss)
      retries: 3
    consumer:
      group-id: order-fulfillment-group
      auto-offset-reset: earliest # Read from beginning if no committed offset exists
      key-deserializer: org.apache.kafka.common.serialization.StringDeserializer
      value-deserializer: org.springframework.kafka.support.serializer.JsonDeserializer
      enable-auto-commit: false # CRITICAL: Disable auto-commit to prevent message loss!
      properties:
        spring.json.trusted.packages: "com.example.demo.kafka.dto"
    listener:
      ack-mode: MANUAL_IMMEDIATE # Application manually acknowledges offsets after processing
```

##### Step 3: High-Reliability Kafka Producer with `KafkaTemplate`

```java
package com.example.demo.kafka.producer;

import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.kafka.core.KafkaTemplate;
import org.springframework.kafka.support.SendResult;
import org.springframework.stereotype.Service;

import java.time.Instant;
import java.util.concurrent.CompletableFuture;

public record OrderPlacedEvent(String orderId, String customerId, double amount, Instant createdAt) {}

@Service
public class OrderEventProducer {

    private static final Logger log = LoggerFactory.getLogger(OrderEventProducer.class);
    private static final String TOPIC = "orders-topic";

    private final KafkaTemplate<String, OrderPlacedEvent> kafkaTemplate;

    public OrderEventProducer(KafkaTemplate<String, OrderPlacedEvent> kafkaTemplate) {
        this.kafkaTemplate = kafkaTemplate;
    }

    public void publishOrder(OrderPlacedEvent event) {
        // We use orderId as the PARTITION KEY to guarantee order sequence for the same order!
        CompletableFuture<SendResult<String, OrderPlacedEvent>> future = 
                kafkaTemplate.send(TOPIC, event.orderId(), event);

        // Handle async callback
        future.whenComplete((result, ex) -> {
            if (ex == null) {
                log.info("Event published to topic {} partition {} with offset {}",
                        result.getRecordMetadata().topic(),
                        result.getRecordMetadata().partition(),
                        result.getRecordMetadata().offset());
            } else {
                log.error("Failed to publish event for order: {}", event.orderId(), ex);
            }
        });
    }
}
```

##### Step 4: Resilient Kafka Consumer with Manual Offset Acknowledgment and Dead Letter Topic (DLT)

```java
package com.example.demo.kafka.consumer;

import com.example.demo.kafka.producer.OrderPlacedEvent;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.kafka.annotation.DltHandler;
import org.springframework.kafka.annotation.KafkaListener;
import org.springframework.kafka.annotation.RetryableTopic;
import org.springframework.kafka.support.Acknowledgment;
import org.springframework.kafka.support.KafkaHeaders;
import org.springframework.messaging.handler.annotation.Header;
import org.springframework.messaging.handler.annotation.Payload;
import org.springframework.retry.annotation.Backoff;
import org.springframework.stereotype.Service;

@Service
public class OrderEventConsumer {

    private static final Logger log = LoggerFactory.getLogger(OrderEventConsumer.class);

    /**
     * @RetryableTopic: If an exception occurs, automatically retries 3 times with exponential backoff
     * before routing the poisoned message to a Dead Letter Topic (orders-topic-dlt).
     */
    @RetryableTopic(
            attempts = "3",
            backoff = @Backoff(delay = 1000, multiplier = 2.0),
            autoCreateTopics = "true"
    )
    @KafkaListener(topics = "orders-topic", groupId = "order-fulfillment-group")
    public void consumeOrder(
            @Payload OrderPlacedEvent event,
            @Header(KafkaHeaders.RECEIVED_PARTITION) int partition,
            @Header(KafkaHeaders.OFFSET) long offset,
            Acknowledgment acknowledgment // Manual commit handle
    ) {
        log.info("Processing order {} from partition {} at offset {}", event.orderId(), partition, offset);

        if (event.amount() < 0) {
            throw new IllegalArgumentException("Invalid negative order amount! Poison pill message.");
        }

        // Business logic: Reserve stock, charge payment...

        // CRITICAL: Acknowledge offset ONLY after processing succeeds!
        // If the pod crashes before this line, Kafka will redeliver the message to another pod!
        acknowledgment.acknowledge();
    }

    /**
     * DLT Handler: Catches poisoned messages after all retries are exhausted.
     */
    @DltHandler
    public void handleDlt(OrderPlacedEvent event, @Header(KafkaHeaders.EXCEPTION_MESSAGE) String error) {
        log.error("POISONED MESSAGE MOVED TO DLT: Order {} failed permanently. Error: {}", event.orderId(), error);
        // Alert on-call engineers via Slack/PagerDuty or save to quarantine database table
    }
}
```

---

#### Reactive Kafka with Project Reactor (`reactor-kafka`) & Backpressure

In high-throughput microservices, a standard imperative listener can be overwhelmed when incoming traffic spikes. If the broker pushes 50,000 events/second, but your database can only persist 1,000 events/second, **memory buffers fill up and trigger `OutOfMemoryError` crashes!**

#### What is Reactive Backpressure?

**Backpressure** is a flow-control mechanism defined in the Reactive Streams specification where the **Consumer tells the Producer exactly how many records it is ready to receive (`request(N)`)**.

```mermaid
sequenceDiagram
    autonumber
    participant Broker as Kafka Broker (Topic: telemetry)
    participant Receiver as Reactive KafkaReceiver (Reactor Kafka)
    participant Consumer as Downstream DB / Processing Pipeline

    Note over Receiver,Consumer: Consumer requests only what it has capacity to process
    Consumer->>Receiver: request(100) (Send me 100 records)
    Receiver->>Broker: Fetch up to 100 records
    Broker-->>Receiver: Delivers 100 records
    Receiver-->>Consumer: onNext(record 1..100)

    Note over Consumer: Consumer is busy saving 100 records to DB...<br/>Zero new records are delivered! Broker buffers data safely on disk!

    Consumer->>Receiver: DB insert done! request(100) (Send me the next 100!)
    Receiver->>Broker: Fetch next 100 records
```

##### Step 1: Add Reactor Kafka Dependency

```xml
<dependency>
    <groupId>io.projectreactor.kafka</groupId>
    <artifactId>reactor-kafka</artifactId>
    <version>1.3.23</version>
</dependency>
```

##### Step 2: The Non-Blocking Reactive Kafka Consumer with Backpressure Control

```java
package com.example.demo.reactive.kafka;

import org.apache.kafka.clients.consumer.ConsumerConfig;
import org.apache.kafka.common.serialization.StringDeserializer;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.boot.CommandLineRunner;
import org.springframework.stereotype.Component;
import reactor.core.publisher.Flux;
import reactor.core.scheduler.Schedulers;
import reactor.kafka.receiver.KafkaReceiver;
import reactor.kafka.receiver.ReceiverOptions;
import reactor.kafka.receiver.ReceiverRecord;

import java.time.Duration;
import java.util.Collections;
import java.util.HashMap;
import java.util.Map;

@Component
public class ReactiveKafkaConsumerRunner implements CommandLineRunner {

    private static final Logger log = LoggerFactory.getLogger(ReactiveKafkaConsumerRunner.class);
    private static final String TOPIC = "sensor-telemetry-topic";

    @Override
    public void run(String... args) {
        startReactiveConsumer();
    }

    public void startReactiveConsumer() {
        Map<String, Object> props = new HashMap<>();
        props.put(ConsumerConfig.BOOTSTRAP_SERVERS_CONFIG, "localhost:9092");
        props.put(ConsumerConfig.GROUP_ID_CONFIG, "reactive-telemetry-group");
        props.put(ConsumerConfig.KEY_DESERIALIZER_CLASS_CONFIG, StringDeserializer.class);
        props.put(ConsumerConfig.VALUE_DESERIALIZER_CLASS_CONFIG, StringDeserializer.class);
        props.put(ConsumerConfig.AUTO_OFFSET_RESET_CONFIG, "earliest");

        ReceiverOptions<String, String> receiverOptions = ReceiverOptions.<String, String>create(props)
                .subscription(Collections.singleton(TOPIC))
                .commitInterval(Duration.ofSeconds(1)); // Commit batch offsets periodically

        KafkaReceiver<String, String> receiver = KafkaReceiver.create(receiverOptions);

        Flux<ReceiverRecord<String, String>> inboundFlux = receiver.receive();

        inboundFlux
                // 1. BACKPRESSURE CONTROL: limitRate bounds in-flight items requested from Kafka
                .limitRate(50)
                // 2. Offload heavy non-blocking processing to dedicated thread pool
                .publishOn(Schedulers.boundedElastic())
                .flatMap(record -> {
                    return processTelemetryRecord(record)
                            // 3. Acknowledge offset asynchronously upon completion
                            .doOnSuccess(v -> record.receiverOffset().acknowledge())
                            .doOnError(e -> log.error("Error processing record key {}", record.key(), e));
                }, 10) // Concurrency factor: process up to 10 records in parallel
                .subscribe();
    }

    private reactor.core.publisher.Mono<Void> processTelemetryRecord(ReceiverRecord<String, String> record) {
        return reactor.core.publisher.Mono.fromRunnable(() -> {
            log.info("Processing sensor telemetry: Key={}, Value={}, Partition={}, Offset={}",
                    record.key(), record.value(), record.partition(), record.offset());
        });
    }
}
```

---

#### 4 Golden Rules for Production Apache Kafka

1. **Always Set a Meaningful Partition Key**: If ordering matters (e.g. sequence of status changes for an order or user account), use the entity's ID as the key. Null keys are assigned round-robin across partitions, destroying ordering guarantees!
2. **Never Enable Auto-Commit (`enable-auto-commit: false`)**: Auto-commit advances the consumer offset on a background timer, regardless of whether your business logic succeeded or threw an exception. Always acknowledge manually!
3. **Partition Sizing Rule**: You cannot have more active consumers in a consumer group than partitions on the topic. If a topic has 6 partitions, running 10 consumer pods means 4 pods will sit 100% idle!
4. **Use Dead Letter Topics (DLT)**: Never retry a poisoned payload (like corrupted JSON) in an infinite loop. Set max retries with exponential backoff, then route to a DLT for post-mortem analysis.

---

### Chapter 8 Exercises & Solutions

Test your comprehension of reactive pipelines, R2DBC transactions, and event streaming.

#### Exercise 8.1: Combining Multiple Reactive Sources with `zipWith`

**Task**: You have two reactive services: `UserService.fetchUser(id)` returning `Mono<User>` and `RatingService.fetchCreditRating(userId)` returning `Mono<CreditRating>`. Write a reactive pipeline that queries both services concurrently and combines them into an `EnrichedProfile` object.

The following solution uses `Mono.zip` to execute both calls in parallel:

```java
package com.example.demo.reactive.service;

import reactor.core.publisher.Mono;

public record User(String id, String name) {}
public record CreditRating(String userId, int score) {}
public record EnrichedProfile(String userId, String name, int creditScore) {}

public class ProfileEnrichmentService {

    public Mono<EnrichedProfile> getEnrichedProfile(String userId, UserService userService, RatingService ratingService) {
        Mono<User> userMono = userService.fetchUser(userId);
        Mono<CreditRating> ratingMono = ratingService.fetchCreditRating(userId);

        // Mono.zip executes both non-blocking publishers in parallel and merges results
        return Mono.zip(userMono, ratingMono)
                .map(tuple -> {
                    User user = tuple.getT1();
                    CreditRating rating = tuple.getT2();
                    return new EnrichedProfile(user.id(), user.name(), rating.score());
                });
    }
}
```

#### Exercise 8.2: Handling Stream Errors and Fallback

**Task**: In Spring WebFlux, write a controller endpoint `/api/v1/telemetry/safe` that calls an external sensor service returning a `Flux<Double>`. If the upstream sensor stream fails with any exception, switch to an in-memory fallback stream emitting `[0.0, 0.0, 0.0]` without throwing an HTTP 500 error to the client.

The following controller uses `.onErrorResume` to intercept failures:

```java
package com.example.demo.reactive.controller;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;
import reactor.core.publisher.Flux;

@RestController
@RequestMapping("/api/v1/telemetry")
public class SafeTelemetryController {

    private final ExternalSensorService sensorService;

    public SafeTelemetryController(ExternalSensorService sensorService) {
        this.sensorService = sensorService;
    }

    @GetMapping("/safe")
    public Flux<Double> getSafeTelemetry() {
        return sensorService.readLiveTelemetryStream()
                // Gracefully intercepts stream error and supplies fallback Flux
                .onErrorResume(ex -> Flux.just(0.0, 0.0, 0.0));
    }
}
```

---

# Part 4: Upgrading to Spring Boot 3 from Previous Versions

Migrating existing applications across major framework versions requires a structured approach. Understanding breaking changes in enterprise namespaces, security configurations, and application properties ensures smooth migrations without production regressions.

---

## Chapter 9: Upgrading from Spring Boot 2.x to Spring Boot 3.0

Upgrading an enterprise codebase across major architectural milestones is one of the most critical engineering responsibilities. Spring Boot 3.0 (and its minor releases 3.1, 3.2, 3.3, and 3.4) represents the most significant paradigm shift in the Java ecosystem in a decade.

This chapter provides an exhaustive, battle-tested roadmap for migrating legacy Spring Boot 2.x applications to modern Spring Boot 3.x cleanly, safely, and without production regressions.

---

### 9.0 The Major Milestones of Spring Boot 3

Spring Boot 3.0 is not merely an incremental release; it establishes a brand-new technical foundation for the next decade of enterprise Java:

```mermaid
graph TD
    Boot3["Spring Boot 3.0 Core Foundations"]
    Boot3 --> J17["Java 17 LTS / Java 21 Baseline\n(Records, Sealed Types, Pattern Matching, Virtual Threads)"]
    Boot3 --> Jak["Jakarta EE 10 Baseline\n(Namespace shift: javax.* -> jakarta.*)"]
    Boot3 --> Native["GraalVM Native Image Support\n(Ahead-of-Time compilation, instant startup, low memory)"]
    Boot3 --> Sec6["Spring Security 6.0\n(Component-based SecurityFilterChain, purely functional Lambda DSL)"]
    Boot3 --> Obs["Micrometer Observation API\n(Unified metrics, distributed tracing, and logging)"]
    Boot3 --> Hib6["Hibernate 6 ORM\n(New SQM Query Engine, strict type checking, higher SQL efficiency)"]
```

#### Prerequisite Concepts & Terminologies

Before touching legacy codebases, master these core concepts:

- **Jakarta EE 10 Migration**: In 2017, Oracle transferred Java EE to the Eclipse Foundation. Because Oracle retained ownership of the `javax.*` trademark, all enterprise specifications (`javax.servlet`, `javax.persistence`, `javax.validation`, `javax.annotation`) were legally renamed to `jakarta.*`. Spring Boot 3.0 marks the final break: **`javax.*` enterprise packages do not exist in Spring Boot 3**.
- **Java 17 LTS Baseline**: Spring Boot 3 requires Java 17 as its absolute minimum version. It also seamlessly leverages Java 21 LTS features (including Virtual Threads and Record Patterns). Any application running on Java 8 or Java 11 **must first be upgraded to Java 17** before upgrading to Spring Boot 3.
- **GraalVM Native Image (AOT Compilation)**: Spring Boot 3 features first-class Ahead-of-Time (AOT) compilation. Using GraalVM, bytecode is analyzed at build time, dead code is pruned, and a standalone machine executable is produced that starts in 10 to 50 milliseconds and uses one-fifth the RAM of a JVM.
- **Micrometer Tracing**: Spring Cloud Sleuth was completely retired in Spring Boot 3. All distributed tracing is now handled natively by Micrometer Tracing.
- **OpenRewrite**: An automated source-code refactoring engine that parses Java Abstract Syntax Trees (ASTs) and executes recipes to update imports, dependencies, and deprecated methods automatically.

---

### 9.1 The Java 17 Baseline & Java EE to Jakarta EE Namespace Migration

The most pervasive change in Spring Boot 3 is the migration from `javax.*` to `jakarta.*`. Every Java file utilizing servlets, JPA, or validation must be updated.

#### Comprehensive Namespace Conversion Table

| Specification | Spring Boot 2.x (Legacy Java EE) | Spring Boot 3.x (Modern Jakarta EE 10) |
| :--- | :--- | :--- |
| **Servlet API** | `javax.servlet.http.HttpServletRequest`<br>`javax.servlet.Filter` | `jakarta.servlet.http.HttpServletRequest`<br>`jakarta.servlet.Filter` |
| **JPA / ORM** | `javax.persistence.Entity`<br>`javax.persistence.Table`<br>`javax.persistence.Id`<br>`javax.persistence.OneToMany` | `jakarta.persistence.Entity`<br>`jakarta.persistence.Table`<br>`jakarta.persistence.Id`<br>`jakarta.persistence.OneToMany` |
| **Bean Validation** | `javax.validation.constraints.NotNull`<br>`javax.validation.constraints.NotBlank`<br>`javax.validation.Valid` | `jakarta.validation.constraints.NotNull`<br>`jakarta.validation.constraints.NotBlank`<br>`jakarta.validation.Valid` |
| **Common Annotations** | `javax.annotation.PostConstruct`<br>`javax.annotation.PreDestroy` | `jakarta.annotation.PostConstruct`<br>`jakarta.annotation.PreDestroy` |
| **Transactions** | `javax.transaction.Transactional` | `jakarta.transaction.Transactional` |
| **JavaMail** | `javax.mail.internet.MimeMessage` | `jakarta.mail.internet.MimeMessage` |
| **WebSockets** | `javax.websocket.OnMessage` | `jakarta.websocket.OnMessage` |

> [!WARNING]
> **Do NOT Replace JDK Core `javax.*` Packages!**
> Only enterprise packages were migrated to `jakarta.*`. Standard JDK packages such as `javax.crypto.*`, `javax.net.ssl.*`, and `javax.sql.DataSource` remain part of the Java standard library and must **NOT** be changed to `jakarta.*`!

#### The Third-Party Library Graveyard

One of the most common causes of migration failure is outdated third-party libraries that still depend on `javax.*`:

1. **Springfox Swagger 2 (`springfox-boot-starter`)**:
   - **Status**: Completely abandoned and incompatible with Spring Boot 3.
   - **Fix**: Replace immediately with **SpringDoc OpenAPI v2**:
     ```xml
     <dependency>
         <groupId>org.springdoc</groupId>
         <artifactId>springdoc-openapi-starter-webmvc-ui</artifactId>
         <version>2.5.0</version>
     </dependency>
     ```
2. **Legacy Jackson JAXB Modules**:
   - Replace `jackson-module-jaxb-annotations` with `jakarta.xml.bind-api` compatible versions.
3. **Embedded Databases**:
   - Upgrade H2 to version 2.1+ (H2 v1.x databases will fail to parse modern SQL).

---

### 9.2 Modern Security Configuration Updates (Spring Security 6)

In Spring Boot 2.x, security was declared by extending `WebSecurityConfigurerAdapter` and overriding `configure(HttpSecurity http)`. In Spring Boot 3.0 / Spring Security 6, this class was **completely deleted**.

Furthermore, Spring Security 6 made the **Lambda DSL mandatory**, deprecating the old chained `.and()` syntax.

#### The Complete Security Refactoring Comparison:

```java
// ==============================================================================
// BEFORE: Spring Boot 2.x (Legacy WebSecurityConfigurerAdapter - DELETED IN BOOT 3)
// ==============================================================================
@Configuration
public class LegacySecurityConfig extends WebSecurityConfigurerAdapter {

    @Override
    protected void configure(HttpSecurity http) throws Exception {
        http
            .csrf().disable() // Chained syntax with .and()
            .authorizeRequests()
                .antMatchers("/public/**").permitAll() // antMatchers() DELETED
                .antMatchers(HttpMethod.POST, "/admin/**").hasRole("ADMIN")
                .anyRequest().authenticated()
            .and()
            .httpBasic()
            .and()
            .sessionManagement()
                .sessionCreationPolicy(SessionCreationPolicy.STATELESS);
    }
}

// ==============================================================================
// AFTER: Spring Boot 3.x (Modern Component-Based Lambda DSL)
// ==============================================================================
@Configuration
@EnableWebSecurity
@EnableMethodSecurity // Replaces @EnableGlobalMethodSecurity
public class ModernSecurityConfig {

    @Bean
    public SecurityFilterChain securityFilterChain(HttpSecurity http) throws Exception {
        return http
            // 1. Functional lambda DSL (No .and() chains!)
            .csrf(AbstractHttpConfigurer::disable)
            
            // 2. Stateless session policy via lambda
            .sessionManagement(session -> 
                session.sessionCreationPolicy(SessionCreationPolicy.STATELESS))
            
            // 3. authorizeHttpRequests replaces authorizeRequests
            .authorizeHttpRequests(auth -> auth
                // requestMatchers() replaces antMatchers() and mvcMatchers()
                .requestMatchers("/public/**").permitAll()
                .requestMatchers(HttpMethod.POST, "/admin/**").hasRole("ADMIN")
                .anyRequest().authenticated()
            )
            
            // 4. httpBasic using Customizer
            .httpBasic(Customizer.withDefaults())
            
            .build();
    }
}
```

#### Summary of Security Breaking Changes:

| Spring Boot 2.x / Security 5.x | Spring Boot 3.x / Security 6.x | Reason for Change |
| :--- | :--- | :--- |
| `extends WebSecurityConfigurerAdapter` | `@Bean SecurityFilterChain` | Favors composition over inheritance. |
| `.authorizeRequests()` | `.authorizeHttpRequests()` | Enhanced performance and simplified authorization rules. |
| `.antMatchers()`, `.mvcMatchers()` | `.requestMatchers()` | Unified matching eliminates security bypasses from URL pattern differences. |
| Chained `.and()` methods | Lambda DSL `auth -> auth...` | Prevents ambiguous chaining and improves IDE code completion. |
| `@EnableGlobalMethodSecurity` | `@EnableMethodSecurity` | Modernized method-level security with faster SpEL evaluation. |

---

### 9.3 Hibernate 6 & Spring Data 3 Breaking Changes

Spring Boot 3 upgrades Hibernate from 5.6 to **Hibernate 6.x**, which introduces an entirely rewritten **Semantic Query Model (SQM)**:

1. **Strict JPQL Type Checking**:
   In Hibernate 5, arithmetic operations and functions were loosely typed. In Hibernate 6, types are strictly validated. For example:
   ```java
   // In Hibernate 5: This might return an Integer or BigInteger
   // In Hibernate 6: COUNT() strictly returns a java.lang.Long!
   Long userCount = entityManager.createQuery("SELECT COUNT(u) FROM User u", Long.class).getSingleResult();
   ```
2. **Automatic Batch Fetching**:
   Hibernate 6 includes a brand-new query execution plan cache that reduces SQL generation overhead by over 40%.
3. **Sequence Generators**:
   The default table and sequence naming convention changed. If you relied on Hibernate 5's automatic sequence names (`hibernate_sequence`), add this property to maintain backward compatibility:
   ```yaml
   spring:
     jpa:
       properties:
         hibernate:
           id:
             db_structure_naming_strategy: legacy
   ```
4. **Spring Data `findById` Semantics**:
   `CrudRepository.findById()` returns `Optional<T>`. Calling `.get()` directly without checking `.isPresent()` will throw `NoSuchElementException`. Always use `.orElseThrow(() -> new ResourceNotFoundException(...))`.

---

### 9.4 Migrating Distributed Tracing: The Sleuth to Micrometer Transition

One of the biggest architectural removals in Spring Boot 3 is **Spring Cloud Sleuth**. 

> [!CAUTION]
> **Spring Cloud Sleuth is Deprecated and Dead**:
> `spring-cloud-starter-sleuth` does **NOT** exist in Spring Boot 3 and will fail to resolve in Maven!

#### How to Migrate to Micrometer Tracing:

1. **Remove Old Dependency**:
   Remove `spring-cloud-starter-sleuth` from `pom.xml`.
2. **Add Modern Micrometer Tracing Starters**:
   ```xml
   <!-- Micrometer Tracing Facade -->
   <dependency>
       <groupId>io.micrometer</groupId>
       <artifactId>micrometer-tracing-bridge-brave</artifactId> <!-- Or micrometer-tracing-bridge-otel -->
   </dependency>
   
   <!-- Reporter for Zipkin -->
   <dependency>
       <groupId>io.zipkin.reporter2</groupId>
       <artifactId>zipkin-reporter-brave</artifactId>
   </dependency>
   ```
3. **Update Application Properties**:
   Replace legacy Sleuth property keys:
   ```yaml
   # OLD (Spring Boot 2.x Sleuth):
   # spring.sleuth.sampler.probability: 1.0
   # spring.zipkin.base-url: http://localhost:9411

   # NEW (Spring Boot 3.x Micrometer):
   management:
     tracing:
       sampling:
         probability: 1.0 # 100% of requests sampled
     zipkin:
       tracing:
         endpoint: http://localhost:9411/api/v2/spans
   ```

---

### 9.5 The Spring Boot 3.x Feature Roadmap (3.1, 3.2, 3.3, 3.4)

When upgrading to Spring Boot 3, do not stop at 3.0! Take advantage of the game-changing features introduced across minor releases:

```mermaid
timeline
    title Spring Boot 3 Innovation Timeline
    Spring Boot 3.0 (Nov 2022) : Java 17 Baseline : Jakarta EE 10 : GraalVM AOT Compilation : ProblemDetail RFC 7807
    Spring Boot 3.1 (May 2023) : Docker Compose Auto-Lifecycle : Testcontainers @ServiceConnection : ConnectionDetails Abstraction
    Spring Boot 3.2 (Nov 2023) : RestClient Fluent HTTP Client : Java 21 Virtual Threads Support : Declarative @HttpExchange Improvements
    Spring Boot 3.3 & 3.4 (2024+) : Class Data Sharing (CDS) Support : Structured JSON Logging : Extended GraalVM Native Hints
```

#### Highlights of the 3.x Line:

- **Spring Boot 3.1: `@ServiceConnection`**: Eliminates `@DynamicPropertySource` in Testcontainers integration tests.
- **Spring Boot 3.1: `spring-boot-docker-compose`**: Automatically detects `compose.yaml` and starts local databases on application boot.
- **Spring Boot 3.2: `RestClient`**: Modern synchronous HTTP client replacing verbose `RestTemplate`.
- **Spring Boot 3.2: Virtual Threads**: Enabling `spring.threads.virtual.enabled=true` automatically switches embedded Tomcat and `@Async` executors to lightweight Java 21 Virtual Threads, boosting I/O throughput by 300%.

---

### 9.6 Automated Migration with OpenRewrite

Manually editing hundreds of imports, changing POM dependencies, and rewriting security configs across thousands of files is error-prone. **OpenRewrite** automates this entire process using deterministic Abstract Syntax Tree (AST) recipes.

#### Step 1: Add OpenRewrite to Your Legacy `pom.xml`

```xml
<plugin>
    <groupId>org.openrewrite.maven</groupId>
    <artifactId>rewrite-maven-plugin</artifactId>
    <version>5.38.0</version>
    <configuration>
        <activeRecipes>
            <recipe>org.openrewrite.java.spring.boot3.UpgradeSpringBoot_3_0</recipe>
        </activeRecipes>
    </configuration>
    <dependencies>
        <dependency>
            <groupId>org.openrewrite.recipe</groupId>
            <artifactId>rewrite-spring</artifactId>
            <version>5.10.0</version>
        </dependency>
    </dependencies>
</plugin>
```

#### Step 2: Preview the Changes with `dryRun`

Run the dry-run goal to generate a Git-style patch without modifying your files:

```bash
mvn rewrite:dryRun
```

Inspect the generated `target/rewrite/patch.diff` to review all proposed transformations.

#### Step 3: Execute the Automated Upgrade

Apply the transformations directly to your source files:

```bash
mvn rewrite:run
```

##### What OpenRewrite Performs Automatically in Seconds:
1. Rewrites all `javax.servlet.*`, `javax.persistence.*`, `javax.validation.*`, and `javax.annotation.*` imports to `jakarta.*`.
2. Updates Maven POM parent version to `3.0.x` and sets `java.version` to `17`.
3. Replaces `WebSecurityConfigurerAdapter` with `@Bean SecurityFilterChain`.
4. Replaces `.antMatchers()` with `.requestMatchers()`.
5. Renames removed configuration properties in `application.yml`.

---

### 9.7 The 10-Step Production Upgrade Playbook (Checklist)

Follow this battle-tested checklist when migrating production microservices:

```text
[ ] Step 1: Upgrade to the latest Spring Boot 2.7.x release first!
            (Ensure zero deprecation warnings on Boot 2.7 before leaping to 3.0).
[ ] Step 2: Upgrade JDK to Java 17 LTS (or Java 21 LTS) and ensure tests pass on Boot 2.7.
[ ] Step 3: Run the temporary Properties Migrator to flag deprecated keys:
            (Add spring-boot-properties-migrator to pom.xml).
[ ] Step 4: Audit third-party libraries for Jakarta EE 10 compatibility
            (Replace Springfox Swagger with SpringDoc OpenAPI v2).
[ ] Step 5: Execute OpenRewrite to automate namespace and security migrations:
            (mvn rewrite:run).
[ ] Step 6: Migrate Spring Cloud Sleuth to Micrometer Tracing.
[ ] Step 7: Refactor Spring Security to use the Lambda DSL and requestMatchers.
[ ] Step 8: Update Hibernate 6 JPQL queries to verify strict type handling.
[ ] Step 9: Remove the spring-boot-properties-migrator dependency.
[ ] Step 10: Run the full integration test suite with Testcontainers to verify runtime behavior!
```

---

### Chapter 9 Exercises & Solutions

Test your comprehension of Spring Boot 3 upgrade requirements.

#### Exercise 9.1: Identifying Namespace Equivalents

**Task**: What is the Jakarta EE replacement for `javax.servlet.Filter` and `javax.validation.constraints.NotNull`?

**Explanation**:
- `javax.servlet.Filter` $\rightarrow$ `jakarta.servlet.Filter` (packaged in `jakarta.servlet:jakarta.servlet-api`).
- `javax.validation.constraints.NotNull` $\rightarrow$ `jakarta.validation.constraints.NotNull` (packaged in `jakarta.validation:jakarta.validation-api`).

#### Exercise 9.2: Refactoring antMatchers & Lambda DSL

**Task**: Refactor the following legacy security snippet to valid Spring Boot 3 syntax:
```java
http.csrf().disable()
    .authorizeRequests()
    .antMatchers(HttpMethod.GET, "/api/**").hasRole("USER")
    .anyRequest().authenticated();
```

**Solution**:
```java
http
    .csrf(AbstractHttpConfigurer::disable)
    .authorizeHttpRequests(auth -> auth
        .requestMatchers(HttpMethod.GET, "/api/**").hasRole("USER")
        .anyRequest().authenticated()
    );
```

#### Exercise 9.3: Sleuth Replacement

**Task**: A developer complains that their microservice fails to compile after upgrading to Spring Boot 3 because Maven cannot find `spring-cloud-starter-sleuth`. What is the resolution?

**Explanation**:
Spring Cloud Sleuth was retired in Spring Boot 3. The developer must remove `spring-cloud-starter-sleuth` and replace it with `io.micrometer:micrometer-tracing-bridge-brave` (or `micrometer-tracing-bridge-otel`) and configure `management.tracing.sampling.probability` in `application.yml`.

---

# Chapter 10: Massive Exercises Section (Concept Checks, Debugging & Capstones)

This chapter provides an extensive collection of conceptual review questions, code debugging challenges, and multi-layered capstone coding projects designed to test and reinforce your mastery of modern enterprise Spring Boot 3 engineering. Complete answers and production-grade solutions are provided for every problem.

---

## 10.1 Conceptual & Architectural Review Questions

The following questions evaluate your architectural understanding of core Spring principles, web frameworks, security mechanics, database optimizations, and distributed systems.

### Question 1: Inversion of Control vs Dependency Injection

What is the fundamental distinction between Inversion of Control (IoC) and Dependency Injection (DI)?

<details>
<summary>Click to view answer and explanation</summary>

**Answer**:
- **Inversion of Control (IoC)** is a broad architectural design principle where the control flow of a program is inverted: instead of custom application code controlling the execution and instantiation of objects, an external framework (the container) manages program execution and object lifecycles.
- **Dependency Injection (DI)** is a specific design pattern used to *implement* Inversion of Control. Under DI, an object does not construct its dependencies internally (e.g., using `new ServiceImpl()`); instead, dependencies are supplied ("injected") into the object at runtime by the IoC container via constructors, setters, or fields.
- In summary: IoC is the architectural philosophy ("Don't call us, we'll call you"); Dependency Injection is the mechanism used to provide objects with their collaborators.
</details>

---

### Question 2: Constructor Injection vs Field Injection

Why does the Spring team officially discourage `@Autowired` on private fields in favor of constructor injection?

<details>
<summary>Click to view answer and explanation</summary>

**Answer**:
Constructor injection is preferred for three major architectural reasons:
1. **Immutability and Thread Safety**: Dependencies can be declared as `final`, ensuring that beans are immutable once constructed and preventing race conditions.
2. **Ease of Unit Testing**: A class with constructor injection can be instantiated cleanly in plain JUnit tests using `new MyService(mockRepo)` without booting up a Spring `ApplicationContext` or resorting to reflection.
3. **Explicit Contract & Circular Dependency Detection**: With constructor injection, all required dependencies must be provided at instantiation time. If a class requires too many dependencies (e.g. > 5), it immediately signals a violation of the Single Responsibility Principle. Furthermore, circular dependencies fail fast during container initialization.
</details>

---

### Question 3: Spring Bean Scopes: Singleton vs Prototype

How does the default `singleton` bean scope behave in Spring, and what happens when a `singleton` bean injects a `prototype` bean?

<details>
<summary>Click to view answer and explanation</summary>

**Answer**:
- In Spring, the default scope is **Singleton**, meaning the Spring IoC container creates exactly *one* shared instance of that bean per `ApplicationContext`. All concurrent threads share this same instance, requiring singleton beans to be strictly stateless and thread-safe.
- A **Prototype** bean creates a *new* instance every time it is requested from the container.
- **The Injection Trap**: When a `singleton` bean injects a `prototype` bean via standard constructor or field injection, the prototype is resolved and injected *only once* during the singleton's initialization. Consequently, the singleton holds onto that single prototype instance forever, effectively nullifying the prototype behavior! To obtain a fresh prototype instance on every method invocation, the singleton must use a `Provider<MyPrototypeBean>`, `ObjectProvider<MyPrototypeBean>`, or `@Lookup` method injection.
</details>

---

### Question 4: Idempotent vs Safe HTTP Methods

In REST API design, what is the exact semantic difference between a "Safe" HTTP method and an "Idempotent" HTTP method?

<details>
<summary>Click to view answer and explanation</summary>

**Answer**:
- **Safe Methods**: HTTP methods that do not alter the state of the target resource on the server. `GET`, `HEAD`, and `OPTIONS` are safe. They are strictly read-only and can be pre-fetched or cached by CDNs and browsers without side effects.
- **Idempotent Methods**: HTTP methods where the side-effect of making $N > 0$ identical requests is identical to making a single request. `GET`, `HEAD`, `PUT`, `DELETE`, and `OPTIONS` are idempotent. For example, deleting a resource with `DELETE /api/v1/items/42` multiple times leaves the system in the exact same state (the item does not exist).
- Note: `POST` is neither safe nor idempotent (calling `POST /api/v1/orders` twice creates two separate orders). `PUT` is idempotent but NOT safe (it modifies server state, but repeated calls yield the same state).
</details>

---

### Question 5: Spring Security Filter Chain vs Interceptors

Why does Spring Security enforce authentication and authorization within a Servlet Filter chain rather than using Spring MVC `HandlerInterceptors`?

<details>
<summary>Click to view answer and explanation</summary>

**Answer**:
- **Execution Order**: Servlet Filters execute *before* the request reaches Spring MVC's `DispatcherServlet`. `HandlerInterceptors`, on the other hand, execute *inside* `DispatcherServlet` after the handler mapping has already been resolved.
- **Security Isolation**: By blocking unauthorized requests at the Servlet Filter level, malicious requests are rejected before Spring MVC spends CPU cycles parsing request parameters, resolving content negotiation, or executing custom controller converters.
- **Universal Protection**: Filters protect all web resources uniformly—including static resources, custom servlets, WebSockets, and Actuator endpoints—not just `@RestController` handlers mapped within Spring MVC.
</details>

---

### Question 6: CSRF Protection in Stateless REST APIs

Why is it standard practice to disable Cross-Site Request Forgery (`csrf.disable()`) in stateless REST APIs that use JWT Bearer tokens?

<details>
<summary>Click to view answer and explanation</summary>

**Answer**:
- CSRF attacks rely on browsers automatically attaching authenticated session cookies (`JSESSIONID`) to cross-origin HTTP requests. An attacker tricks an authenticated user into clicking a link that submits a form to `bank.com/transfer`, and the browser automatically sends the user's session cookie.
- Stateless REST APIs do not use HTTP session cookies for authentication. Instead, clients authenticate by explicitly attaching an `Authorization: Bearer <JWT>` header to requests.
- Browsers *never* automatically attach custom `Authorization` headers to cross-origin requests. Because malicious websites cannot forge the `Authorization` header, stateless JWT-based REST APIs are inherently immune to classic CSRF attacks. Disabling CSRF eliminates unnecessary token validation overhead.
</details>

---

### Question 7: The JPA N+1 Query Problem

Explain what causes the JPA N+1 query problem, why it is dangerous in production, and how to fix it using JPQL.

<details>
<summary>Click to view answer and explanation</summary>

**Answer**:
- **Cause**: When an entity has a lazy-loaded association (e.g., an `Author` with a `@OneToMany List<Book> books`), executing `authorRepository.findAll()` sends 1 initial SQL query to fetch all $N$ authors. When the application subsequently accesses `author.getBooks()` in a loop or during JSON serialization, Hibernate issues an individual SQL query for *each* author to load their books.
- **Impact**: Fetching 100 authors executes $1 + 100 = 101$ separate database network round-trips, causing extreme latency, connection pool saturation, and database CPU spikes.
- **Solution**: Use JPQL with `JOIN FETCH` (or `@EntityGraph`) to load both the parent entities and their associated collections in a single SQL query:
  ```java
  @Query("SELECT DISTINCT a FROM Author a LEFT JOIN FETCH a.books")
  List<Author> findAllWithBooks();
  ```
</details>

---

### Question 8: `@Transactional` Rollback Mechanics

If an unhandled checked exception (e.g., `IOException` or `SQLException`) is thrown inside a `@Transactional` method, does Spring roll back the transaction by default?

<details>
<summary>Click to view answer and explanation</summary>

**Answer**:
- **No, it does NOT roll back by default.**
- By default, Spring's declarative transaction management rolls back transactions only on *unchecked* exceptions (instances of `RuntimeException` and `Error`).
- Checked exceptions (subclasses of `java.lang.Exception` that are not `RuntimeException`) are considered anticipated domain outcomes, so Spring commits the transaction unless configured otherwise.
- **The Fix**: To ensure that checked exceptions trigger an automatic database rollback, explicitly specify `rollbackFor`:
  ```java
  @Transactional(rollbackFor = Exception.class)
  public void processTransaction() throws CustomCheckedException { ... }
  ```
</details>

---

### Question 9: Sizing HikariCP Connection Pools

Why is setting a database connection pool size to a very large number (e.g. 200) often detrimental to application performance, and what formula does HikariCP recommend?

<details>
<summary>Click to view answer and explanation</summary>

**Answer**:
- Each active database connection consumes server memory and requires OS context switching between CPU threads. When hundreds of threads compete for database disk I/O simultaneously, the database engine spends more time context-switching and thrashing disk spindles than executing queries.
- PostgreSQL and MySQL run faster with a small pool of active connections matching the physical hardware capabilities.
- The standard formula recommended by the HikariCP engineering team is:
  $$\text{Pool Size} = (\text{CPU Cores} \times 2) + \text{Effective Spindle Count}$$
- On a standard multi-core server with SSD storage, a connection pool of **10 to 20 connections** can easily support thousands of concurrent HTTP requests!
</details>

---

### Question 10: Cache Stampede & Mitigation Strategies

What is a "Cache Stampede" (also known as the "Thundering Herd" problem) and how can it be mitigated in high-traffic applications?

<details>
<summary>Click to view answer and explanation</summary>

**Answer**:
- **Problem**: When a frequently accessed cache key (e.g., the home page banner or top 10 products) expires, hundreds or thousands of concurrent user requests simultaneously experience a *cache miss*. Every request immediately queries the underlying database to compute the missing data, overwhelming database connection pools and causing cascading system downtime.
- **Mitigation Strategies**:
  1. **Distributed Mutex Locking (Single-Flight)**: When a cache miss occurs, the first thread acquires a short-lived distributed lock (e.g., via Redis `SETNX`) to query the database and update the cache. All other threads wait briefly or return slightly stale data until the cache is refreshed.
  2. **Jittered Expirations**: Add random variance (jitter) to cache TTLs so multiple keys do not expire at the exact same millisecond.
  3. **Background Pre-Warming**: Asynchronously refresh the cache before the TTL expires using a scheduled worker.
</details>

---

## 10.2 Code Pitfall & Debugging Challenges

Review the following buggy code examples. Identify why each snippet fails or behaves unexpectedly in production, and review the corrected implementation.

### Challenge 1: The Invisible Validation Failure

The developer declared validation rules on a record DTO, but the endpoint fails to reject malformed input:

The following code illustrates a controller handler missing the mandatory validation trigger:

```java
@RestController
@RequestMapping("/api/v1/orders")
public class BuggyOrderController {

    private final OrderService orderService;

    public BuggyOrderController(OrderService orderService) {
        this.orderService = orderService;
    }

    // BUG: Missing @Valid annotation! Spring binds JSON but skips validation execution!
    @PostMapping
    public ResponseEntity<OrderDto> placeOrder(@RequestBody CreateOrderRequest request) {
        OrderDto order = orderService.createOrder(request);
        return ResponseEntity.ok(order);
    }
}

public record CreateOrderRequest(
    @NotBlank(message = "Customer email is required")
    @Email(message = "Must be a valid email")
    String customerEmail,

    @Positive(message = "Quantity must be positive")
    int quantity
) {}
```

#### Diagnosis & Explanation

The developer declared validation annotations (`@NotBlank`, `@Positive`) on the `CreateOrderRequest` record, but omitted `@Valid` before `@RequestBody` in the controller method signature. Without `@Valid`, Spring MVC's `HandlerAdapter` binds incoming JSON payload into the record but completely skips bean validation execution! As a result, blank emails and negative quantities pass silently into the business layer.

#### Corrected Code

The following corrected method adds `@Valid` directly before `@RequestBody` to enforce validation:

```java
@PostMapping
public ResponseEntity<OrderDto> placeOrder(@Valid @RequestBody CreateOrderRequest request) {
    // Now Spring rejects invalid requests with HTTP 400 before this line ever runs!
    OrderDto order = orderService.createOrder(request);
    return ResponseEntity.ok(order);
}
```

---

### Challenge 2: The Self-Invocation Transaction Trap

The following service attempts to execute database operations inside a transaction, but rollbacks never occur when an exception is thrown:

The following code illustrates the self-invocation anti-pattern that bypasses Spring AOP proxies:

```java
@Service
public class UserService {

    private final UserRepository userRepository;

    public UserService(UserRepository userRepository) {
        this.userRepository = userRepository;
    }

    // Public method lacks @Transactional
    public void registerUser(UserRegistrationDto dto) {
        validateDto(dto);
        // BUG: Calling this.saveUserWithAudit() bypasses Spring's dynamic AOP proxy!
        saveUserWithAudit(dto);
    }

    @Transactional(rollbackFor = Exception.class)
    public void saveUserWithAudit(UserRegistrationDto dto) {
        userRepository.save(new User(dto.username(), dto.email()));
        if (dto.role().equals("BLOCKED")) {
            throw new IllegalStateException("Blocked users cannot be registered");
        }
    }
}
```

#### Diagnosis & Explanation

When `registerUser` calls `this.saveUserWithAudit(dto)`, it invokes the method directly on the internal Java instance (`this`), completely bypassing Spring's dynamic AOP proxy! Because Spring's `@Transactional` mechanism relies on proxy interception to begin and commit database transactions, the `@Transactional` annotation on `saveUserWithAudit` is completely ignored. When the `IllegalStateException` is thrown, the user is already permanently written to the database without rollback.

#### Corrected Code

The following corrected service places `@Transactional` on the public entry point intercepted by Spring's proxy:

```java
@Service
public class UserService {

    private final UserRepository userRepository;

    public UserService(UserRepository userRepository) {
        this.userRepository = userRepository;
    }

    // Place @Transactional on the public method intercepted by Spring's AOP proxy!
    @Transactional(rollbackFor = Exception.class)
    public void registerUser(UserRegistrationDto dto) {
        validateDto(dto);
        userRepository.save(new User(dto.username(), dto.email()));
        if (dto.role().equals("BLOCKED")) {
            throw new IllegalStateException("Blocked users cannot be registered");
        }
    }
}
```

---

### Challenge 3: The Dangerous EAGER Fetch Association

The following entity configuration causes severe database performance degradation:

The following code demonstrates the query amplification flaw of eager collection associations:

```java
@Entity
@Table(name = "customers")
public class Customer {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;

    // BUG: EAGER fetching on collections forces automatic joins and query explosions!
    @OneToMany(mappedBy = "customer", fetch = FetchType.EAGER)
    private List<Order> orders = new ArrayList<>();
}
```

#### Diagnosis & Explanation

Configuring `FetchType.EAGER` on collections (`@OneToMany` or `@ManyToMany`) is one of the most severe performance anti-patterns in JPA. Whenever a single `Customer` is loaded—even for a simple login check or profile display—Hibernate automatically forces an expensive SQL `JOIN` or executes subsequent select queries to pull every single associated `Order` into memory. When querying `customerRepository.findAll()`, Hibernate generates an avalanche of queries that saturates JVM heap space and destroys database throughput.

#### Corrected Code

The following corrected entity uses `FetchType.LAZY` for collection associations:

```java
@Entity
@Table(name = "customers")
public class Customer {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;

    // Correct: Always use LAZY fetching for collections!
    @OneToMany(mappedBy = "customer", fetch = FetchType.LAZY, cascade = CascadeType.ALL, orphanRemoval = true)
    private List<Order> orders = new ArrayList<>();
}
```

---

### Challenge 4: The Stateless API CSRF Blocker

The following security configuration causes all HTTP POST requests from external clients to fail:

The following configuration demonstrates a common Spring Security 6 misconfiguration in stateless APIs:

```java
@Configuration
@EnableWebSecurity
public class SecurityConfig {

    @Bean
    public SecurityFilterChain securityFilterChain(HttpSecurity http) throws Exception {
        return http
                // BUG: In Spring Security 6, CSRF is enabled by default!
                // Stateless REST APIs with Bearer tokens reject all POST requests with 403 Forbidden!
                .sessionManagement(s -> s.sessionCreationPolicy(SessionCreationPolicy.STATELESS))
                .authorizeHttpRequests(auth -> auth
                        .requestMatchers(HttpMethod.POST, "/api/v1/orders").hasRole("USER")
                        .anyRequest().authenticated()
                )
                .oauth2ResourceServer(oauth2 -> oauth2.jwt(Customizer.withDefaults()))
                .build();
    }
}
```

#### Diagnosis & Explanation

In Spring Security 6, CSRF protection is **enabled by default**. When mobile apps or frontend SPAs send an authenticated HTTP `POST` request to `/api/v1/orders` with a valid JWT Bearer token, Spring Security rejects the request with HTTP `403 Forbidden` because the incoming request lacks a CSRF token (`_csrf`). Since this API is completely stateless and does not rely on session cookies, CSRF must be explicitly disabled.

#### Corrected Code

The following corrected configuration explicitly disables CSRF for stateless APIs:

```java
@Bean
public SecurityFilterChain securityFilterChain(HttpSecurity http) throws Exception {
    return http
            // Explicitly disable CSRF for stateless REST APIs using Bearer tokens
            .csrf(AbstractHttpConfigurer::disable)
            .sessionManagement(s -> s.sessionCreationPolicy(SessionCreationPolicy.STATELESS))
            .authorizeHttpRequests(auth -> auth
                    .requestMatchers(HttpMethod.POST, "/api/v1/orders").hasRole("USER")
                    .anyRequest().authenticated()
            )
            .oauth2ResourceServer(oauth2 -> oauth2.jwt(Customizer.withDefaults()))
            .build();
}
```

---

## 10.3 Comprehensive Cumulative Capstone Projects

The following capstone projects integrate multiple enterprise concepts—combining Spring Web, Security, Spring Data JPA, Redis caching, microservice gateways, and reactive streams.

### Capstone 1: Secure Order Processing Microservice

This capstone builds a complete, production-grade order processing REST API using Spring Boot 3, Spring Data JPA, Bean Validation, RFC 7807 global exception handling, and Spring Security 6 with JWT authentication.

The following architectural diagram illustrates the components of the order processing microservice:

```mermaid
flowchart TD
    Client["HTTP Client (Authenticated)"] --> Auth["Spring Security 6 (JWT Bearer)"]
    Auth --> Ctrl["OrderController (@RestController)"]
    Ctrl --> Val["Bean Validation (@Valid)"]
    Val --> Svc["OrderService (@Transactional)"]
    Svc --> Repo["OrderRepository (Spring Data JPA)"]
    Repo --> DB[("PostgreSQL 16")]
    Ctrl -.->|"Invalid Input / Error"| Advice["GlobalExceptionHandler (RFC 7807)"]
```

#### Complete Implementation: Order Microservice

The following code provides the complete, self-contained project implementation:

```java
package com.example.demo.capstone1;

import jakarta.persistence.*;
import jakarta.validation.Valid;
import jakarta.validation.constraints.Min;
import jakarta.validation.constraints.NotBlank;
import jakarta.validation.constraints.Positive;
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.data.jpa.repository.Query;
import org.springframework.data.repository.query.Param;
import org.springframework.http.HttpStatus;
import org.springframework.http.ProblemDetail;
import org.springframework.http.ResponseEntity;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.config.annotation.web.configurers.AbstractHttpConfigurer;
import org.springframework.security.config.http.SessionCreationPolicy;
import org.springframework.security.web.SecurityFilterChain;
import org.springframework.stereotype.Repository;
import org.springframework.stereotype.Service;
import org.springframework.transaction.annotation.Transactional;
import org.springframework.validation.FieldError;
import org.springframework.web.bind.MethodArgumentNotValidException;
import org.springframework.web.bind.annotation.*;
import org.springframework.web.servlet.support.ServletUriComponentsBuilder;

import java.net.URI;
import java.time.Instant;
import java.util.*;

// 1. Entities
@Entity
@Table(name = "customer_orders")
class CustomerOrder {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @Column(nullable = false, unique = true)
    private String orderNumber;

    @Column(nullable = false)
    private Instant createdAt = Instant.now();

    @OneToMany(mappedBy = "customerOrder", cascade = CascadeType.ALL, orphanRemoval = true, fetch = FetchType.LAZY)
    private List<CustomerOrderItem> items = new ArrayList<>();

    protected CustomerOrder() {}
    public CustomerOrder(String orderNumber) { this.orderNumber = orderNumber; }

    public void addItem(String itemSku, int quantity, double price) {
        items.add(new CustomerOrderItem(itemSku, quantity, price, this));
    }

    public Long getId() { return id; }
    public String getOrderNumber() { return orderNumber; }
    public List<CustomerOrderItem> getItems() { return items; }
}

@Entity
@Table(name = "customer_order_items")
class CustomerOrderItem {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @Column(nullable = false)
    private String itemSku;

    @Column(nullable = false)
    private int quantity;

    @Column(nullable = false)
    private double price;

    @ManyToOne(fetch = FetchType.LAZY)
    @JoinColumn(name = "order_id", nullable = false)
    private CustomerOrder customerOrder;

    protected CustomerOrderItem() {}
    public CustomerOrderItem(String itemSku, int quantity, double price, CustomerOrder customerOrder) {
        this.itemSku = itemSku;
        this.quantity = quantity;
        this.price = price;
        this.customerOrder = customerOrder;
    }

    public String getItemSku() { return itemSku; }
    public int getQuantity() { return quantity; }
    public double getPrice() { return price; }
}

// 2. DTOs
record OrderItemRequest(
    @NotBlank(message = "Item SKU cannot be blank") String itemSku,
    @Min(value = 1, message = "Quantity must be at least 1") int quantity,
    @Positive(message = "Price must be strictly positive") double price
) {}

record CreateOrderRequest(
    @NotBlank(message = "Order number is required") String orderNumber,
    @Valid List<OrderItemRequest> items
) {}

record OrderResponseDto(Long id, String orderNumber, int itemCount, double totalAmount) {}

// 3. Repository
@Repository
interface CustomerOrderRepository extends JpaRepository<CustomerOrder, Long> {
    @Query("SELECT o FROM CustomerOrder o LEFT JOIN FETCH o.items WHERE o.id = :id")
    Optional<CustomerOrder> findByIdWithItems(@Param("id") Long id);
}

// 4. Service
@Service
class CustomerOrderService {
    private final CustomerOrderRepository repository;

    public CustomerOrderService(CustomerOrderRepository repository) {
        this.repository = repository;
    }

    @Transactional(rollbackFor = Exception.class)
    public OrderResponseDto createOrder(CreateOrderRequest req) {
        CustomerOrder order = new CustomerOrder(req.orderNumber());
        for (OrderItemRequest item : req.items()) {
            order.addItem(item.itemSku(), item.quantity(), item.price());
        }
        CustomerOrder saved = repository.save(order);
        double total = req.items().stream().mapToDouble(i -> i.price() * i.quantity()).sum();
        return new OrderResponseDto(saved.getId(), saved.getOrderNumber(), saved.getItems().size(), total);
    }
}

// 5. Controller
@RestController
@RequestMapping("/api/v1/orders")
class CustomerOrderController {
    private final CustomerOrderService service;

    public CustomerOrderController(CustomerOrderService service) {
        this.service = service;
    }

    @PostMapping
    public ResponseEntity<OrderResponseDto> createOrder(@Valid @RequestBody CreateOrderRequest req) {
        OrderResponseDto dto = service.createOrder(req);
        URI location = ServletUriComponentsBuilder.fromCurrentRequest().path("/{id}").buildAndExpand(dto.id()).toUri();
        return ResponseEntity.created(location).body(dto);
    }
}

// 6. RFC 7807 Global Exception Handler
@RestControllerAdvice
class GlobalOrderExceptionHandler {
    @ExceptionHandler(MethodArgumentNotValidException.class)
    public ProblemDetail handleValidation(MethodArgumentNotValidException ex) {
        ProblemDetail problem = ProblemDetail.forStatusAndDetail(HttpStatus.BAD_REQUEST, "Validation failed on payload");
        problem.setTitle("Invalid Request Format");
        Map<String, String> errors = new HashMap<>();
        for (FieldError fe : ex.getBindingResult().getFieldErrors()) {
            errors.put(fe.getField(), fe.getDefaultMessage());
        }
        problem.setProperty("invalidParams", errors);
        return problem;
    }
}

// 7. Security Configuration
@Configuration
class CapstoneSecurityConfig {
    @Bean
    public SecurityFilterChain filterChain(HttpSecurity http) throws Exception {
        return http
                .csrf(AbstractHttpConfigurer::disable)
                .sessionManagement(s -> s.sessionCreationPolicy(SessionCreationPolicy.STATELESS))
                .authorizeHttpRequests(auth -> auth.anyRequest().permitAll()) // Permit all for capstone demo
                .build();
    }
}
```

---

### Capstone 2: Distributed High-Throughput Product Catalog with Redis

This capstone implements a high-performance product catalog service utilizing the Cache-Aside pattern with Redis to ensure sub-millisecond read access, automated cache eviction, and protection against cache stampedes.

#### Complete Implementation: Redis Cache-Aside Service

The following service demonstrates cache-aside fetching, declarative cache eviction, and mutex-locked protection against cache stampedes:

```java
package com.example.demo.capstone2;

import org.springframework.cache.annotation.CacheEvict;
import org.springframework.cache.annotation.CachePut;
import org.springframework.cache.annotation.Cacheable;
import org.springframework.data.redis.core.RedisTemplate;
import org.springframework.stereotype.Service;

import java.io.Serializable;
import java.time.Duration;

// Domain Record
public record ProductRecord(
    Long id,
    String name,
    double price,
    int stockQuantity
) implements Serializable {}

@Service
public class CachedCatalogService {

    private final RedisTemplate<String, Object> redisTemplate;

    public CachedCatalogService(RedisTemplate<String, Object> redisTemplate) {
        this.redisTemplate = redisTemplate;
    }

    // 1. Declarative Caching with @Cacheable
    @Cacheable(value = "products", key = "#id", unless = "#result == null")
    public ProductRecord getProductById(Long id) {
        simulateDatabaseDelay();
        return new ProductRecord(id, "Mechanical Keyboard Pro", 149.99, 50);
    }

    // 2. Cache Invalidation on Update
    @CachePut(value = "products", key = "#product.id")
    public ProductRecord updateProduct(ProductRecord product) {
        return product;
    }

    // 3. Complete Cache Eviction
    @CacheEvict(value = "products", allEntries = true)
    public void evictAllProductCache() {
        System.out.println("Purged all products from cache.");
    }

    // 4. Mutex-Locked Fetch to Mitigate Cache Stampede
    public ProductRecord getProductWithStampedeProtection(Long id) {
        String cacheKey = "product:" + id;
        ProductRecord cached = (ProductRecord) redisTemplate.opsForValue().get(cacheKey);
        if (cached != null) {
            return cached;
        }

        String lockKey = "lock:" + cacheKey;
        Boolean lockAcquired = redisTemplate.opsForValue().setIfAbsent(lockKey, "LOCKED", Duration.ofSeconds(5));

        if (Boolean.TRUE.equals(lockAcquired)) {
            try {
                simulateDatabaseDelay();
                ProductRecord freshData = new ProductRecord(id, "Mechanical Keyboard Pro", 149.99, 50);
                redisTemplate.opsForValue().set(cacheKey, freshData, Duration.ofMinutes(15));
                return freshData;
            } finally {
                redisTemplate.delete(lockKey);
            }
        } else {
            try { Thread.sleep(60); } catch (InterruptedException ignored) {}
            return (ProductRecord) redisTemplate.opsForValue().get(cacheKey);
        }
    }

    private void simulateDatabaseDelay() {
        try { Thread.sleep(250); } catch (InterruptedException ignored) {}
    }
}
```

---

### Capstone 3: Resilient Microservice Gateway and Client with Circuit Breaker

This capstone configures an outbound payment client using modern `RestClient` protected by a Resilience4j `@CircuitBreaker`, complete with automated WireMock integration testing.

#### Complete Implementation: Resilient Payment Client & WireMock Test

The following implementation demonstrates an outbound client protected by Resilience4j with automated WireMock integration testing:

```java
package com.example.demo.capstone3;

import io.github.resilience4j.circuitbreaker.annotation.CircuitBreaker;
import org.springframework.stereotype.Service;
import org.springframework.web.client.RestClient;

public record PaymentAuthResponse(String transactionId, String status) {}

@Service
public class ResilientPaymentClient {

    private final RestClient restClient;

    public ResilientPaymentClient(RestClient.Builder builder) {
        this.restClient = builder.baseUrl("http://localhost:8089").build();
    }

    @CircuitBreaker(name = "paymentGateway", fallbackMethod = "fallbackPaymentAuth")
    public PaymentAuthResponse authorizePayment(String accountId, double amount) {
        return restClient.post()
                .uri("/api/v1/payments/authorize")
                .body(new PaymentAuthRequest(accountId, amount))
                .retrieve()
                .body(PaymentAuthResponse.class);
    }

    // Fallback gracefully degrades without throwing 500 errors to callers
    public PaymentAuthResponse fallbackPaymentAuth(String accountId, double amount, Throwable t) {
        return new PaymentAuthResponse("PENDING-REVIEW", "QUEUED_DUE_TO_GATEWAY_OUTAGE");
    }

    record PaymentAuthRequest(String accountId, double amount) {}
}
```

The accompanying test verifies healthy execution and fallback triggering using WireMock:

```java
package com.example.demo.capstone3;

import com.github.tomakehurst.wiremock.junit5.WireMockTest;
import org.junit.jupiter.api.DisplayName;
import org.junit.jupiter.api.Test;
import org.springframework.web.client.RestClient;

import static com.github.tomakehurst.wiremock.client.WireMock.*;
import static org.junit.jupiter.api.Assertions.*;

@WireMockTest(httpPort = 8089)
class ResilientPaymentClientTest {

    @Test
    @DisplayName("Returns authorization response when downstream gateway is healthy")
    void shouldAuthorizePaymentWhenServiceIsUp() {
        stubFor(post(urlEqualTo("/api/v1/payments/authorize"))
                .willReturn(aResponse()
                        .withHeader("Content-Type", "application/json")
                        .withStatus(200)
                        .withBody("""
                                {
                                  "transactionId": "TXN-98765",
                                  "status": "APPROVED"
                                }
                                """)));

        ResilientPaymentClient client = new ResilientPaymentClient(RestClient.builder());
        PaymentAuthResponse res = client.authorizePayment("ACC-123", 99.95);

        assertNotNull(res);
        assertEquals("TXN-98765", res.transactionId());
        assertEquals("APPROVED", res.status());
    }

    @Test
    @DisplayName("Triggers circuit breaker fallback when downstream gateway returns HTTP 500")
    void shouldInvokeFallbackOnServerError() {
        stubFor(post(urlEqualTo("/api/v1/payments/authorize"))
                .willReturn(aResponse().withStatus(500)));

        ResilientPaymentClient client = new ResilientPaymentClient(RestClient.builder());
        PaymentAuthResponse res = client.authorizePayment("ACC-123", 99.95);

        assertNotNull(res);
        assertEquals("PENDING-REVIEW", res.transactionId());
        assertEquals("QUEUED_DUE_TO_GATEWAY_OUTAGE", res.status());
    }
}
```

---

### Capstone 4: High-Performance Real-Time Telemetry Pipeline with WebFlux

This capstone constructs a reactive non-blocking Server-Sent Events (SSE) streaming endpoint using Spring WebFlux and Project Reactor to publish real-time IoT device telemetry to connected clients.

#### Complete Implementation: WebFlux SSE Stream

The following reactive controller implementation streams simulated IoT device telemetry to clients using Server-Sent Events:

```java
package com.example.demo.capstone4;

import org.springframework.http.MediaType;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;
import reactor.core.publisher.Flux;

import java.time.Duration;
import java.time.Instant;
import java.util.concurrent.ThreadLocalRandom;

public record DeviceTelemetry(String deviceId, double voltage, double temperature, Instant timestamp) {}

@RestController
@RequestMapping("/api/v1/telemetry")
public class DeviceTelemetryStreamController {

    // Streams telemetry events over persistent HTTP connection as Server-Sent Events (SSE)
    @GetMapping(value = "/stream/{deviceId}", produces = MediaType.TEXT_EVENT_STREAM_VALUE)
    public Flux<DeviceTelemetry> streamTelemetry(@PathVariable String deviceId) {
        return Flux.interval(Duration.ofSeconds(1))
                .map(sequence -> new DeviceTelemetry(
                        deviceId,
                        12.0 + (ThreadLocalRandom.current().nextDouble() * 0.4 - 0.2),
                        45.0 + (ThreadLocalRandom.current().nextDouble() * 2.0 - 1.0),
                        Instant.now()
                ))
                .onBackpressureDrop(); // Drop readings if slow client network buffer fills up
    }
}
```
