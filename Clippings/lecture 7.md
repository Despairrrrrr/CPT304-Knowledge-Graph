---
title: lecture
source: https://gemini.google.com/app/0485a051a55b8a67
author:
published:
created: 2026-05-16
description: Gemini conversation with 2 messages
tags:
  - clippings
---
**You**

我上传了CPT304课程的一节课课件以及课后对应的练习，请你将知识点和习题整理成markdown的形式，方便我录入给Claude code整理笔记。要求内容为英文，尽量保持课件中原有的表达方式

---

**Gemini**

Here is the comprehensive Markdown summary of your CPT304 lecture slides and exercises, structured specifically for ingestion into your code-notetaking tools.

## Part 1: Introduction to CBSE

- Component-Based Software Engineering (CBSE) is a software engineering practice that develops software mainly based on reusable software components.
- The three core principles of CBSE are Components, Interfaces, and Composition.
- **Benefits:** It reduces development time and costs through reusability, enhances maintainability via modularity, and makes isolating and testing components easier.
- **Challenges:** Developers must manage dependency and version conflicts, handle overhead from inter-component communication, and design components that are both specific and reusable.
- **Component Characteristics:**
	- **Self-contained:** Each component encapsulates its own logic and data.
		- **Reusable:** Components are designed to be used across different systems or contexts.
		- **Replaceable:** They can be swapped with another component providing the same interface.
		- **Interface-driven:** Components interact solely through defined interfaces, promoting loose coupling and high cohesion.
- **Interfaces:** They define the contract that components must follow, specifying provided and required services without exposing internal workings.
- **Composition:** This involves assembling components into a complete system by connecting them through their interfaces.
- **Component Models & Middleware:** Component models (like Spring) provide conventions, interaction mechanisms, and lifecycle management, while middleware (like Spring Data or Spring Cloud) handles communication, data management, and infrastructure services.

## Part 2: Components in Spring Boot Foundations

- Spring Boot streamlines development by providing auto-configuration, embedded servers (like Tomcat), and opinionated defaults.
- **Core Annotations:**
	- `@Component`: General Spring-managed bean.
		- `@Service`: Encapsulates business logic.
		- `@Repository`: Data access component.
		- `@Controller` / `@RestController`: Handles HTTP requests.
- **Inversion of Control (IoC) Container:** The framework takes control of instantiating beans, configuring them via dependency injection, managing their lifecycle, and storing them in the application context.
- **Dependency Injection (DI):** Dependencies are provided by the framework to enhance modularity and testability.
	- **Constructor Injection:** Recommended for mandatory dependencies.
		- **Setter Injection:** Suitable for optional or runtime-changeable dependencies.
		- **Field Injection:** Direct field injection, which is less preferred due to testability concerns.

## Part 3: Component Interfaces, Composition, and Lifecycle

- Interfaces enable polymorphism, loose coupling, and testability by defining interactions through abstractions rather than concrete implementations.
- If multiple beans implement the same interface, developers can resolve the ambiguity using the `@Primary` or `@Qualifier` annotations.
- **Component Lifecycle:**
	- **Creation:** The IoC container creates the instance and injects dependencies.
		- **Initialization:** Spring invokes initialization logic, which can be hooked using `@PostConstruct`.
		- **Usage:** The bean is ready for other components to use.
		- **Destruction:** Spring invokes cleanup logic before the context closes, utilizing `@PreDestroy`.

## Part 4: Advanced Component Features

- **Component Scopes:**
	- **Singleton:** One instance per ApplicationContext, which is the default.
		- **Prototype:** A new instance is created per request.
		- **Web Scopes:** `Request` (per HTTP request), `Session` (per user session), and `Application` (per ServletContext).
- **Dynamic Dependency Resolution:** `ObjectProvider` can be used for dynamic or conditional runtime dependency selection.
- **Circular Dependencies:** When two beans depend on each other tightly, it causes a crash during context initialization. This is resolved using the `@Lazy` annotation, which tells Spring to inject a proxy object instead of the actual target bean during startup.
- **Programmatic Bean Definition:**
	- `@Configuration` and `@Bean` allow developers to explicitly create and configure beans, which is especially useful for third-party libraries without Spring annotations.
		- `@Conditional` (e.g., `@ConditionalOnProperty`) creates beans dynamically based on runtime environments or properties.

## Part 5: Component-Based Architecture (DDD & Hexagonal)

### Domain-Driven Design (DDD)

- DDD aligns software structure with business domains.
- **Entities:** Objects in the domain model with a distinct identity and a lifecycle, tracked by a unique identifier.
- **Aggregates:** A cluster of related entities and value objects treated as a single unit for data consistency, managed through an aggregate root.
- **Bounded Contexts:** Specific boundaries defining a domain model, ubiquitous language, and rules. They prevent the domain model from becoming a monolithic mess by splitting it into focused subdomains like `ProductCatalog` and `OrderManagement`.

### Hexagonal Architecture (Ports and Adapters)

- This architectural style decouples an application's core business logic from external systems like databases and UIs.
- **Ports:** Abstract interfaces defining what the core provides (Inbound Ports) or requires (Outbound Ports).
- **Adapters:** Concrete classes that implement these ports to bridge the core to external systems, such as REST controllers or JPA repositories.

---

## Part 6: Building a User Management System (Spring Security)

- **Project Setup:** Standard dependencies include Spring Web, Spring Data JPA, and H2 Database.
- **Data Transfer Objects (DTOs):** Simplified objects that transfer data between the frontend and backend. In Java 14+, the `record` keyword is used to create immutable data carriers. Records automatically generate private final fields, a public constructor, getter methods, `equals()`, `hashCode()`, and `toString()`. Records cannot have setters, extend other classes, or modify their final fields.
- **Repository Component:** Uses Spring Data JPA conventions where method names define the query logic, such as `findByUsername(String username)`. Spring automatically derives queries, generates proxy classes, and delegates execution.
- **Spring Security Implementation:**
	- Spring Security protects endpoints by intercepting HTTP requests to enforce authentication.
		- The `User` entity must implement the `UserDetails` interface.
		- A component must implement `UserDetailsService` and its `loadUserByUsername` method to fetch user details during login.
		- **SecurityConfig:** A `@Configuration` class is created to define a `SecurityFilterChain` bean. Configuration includes disabling CSRF, defining `.authorizeHttpRequests`, and setting `httpBasic`.
		- Passwords must be encoded before saving using a `PasswordEncoder` bean (like `BCryptPasswordEncoder`).

---

## Hands-On Exercise: Building an E-Commerce API

- **Objective:** Develop an e-commerce API managing products and orders to reinforce modularity and composition.
- **Requirements:** Endpoints to retrieve products (`GET /products`) and add products (`POST /products`).
- **Component Structure:**
	- **Product Model:** Data structure with `id`, `name`, `price`, and `stock`.
		- **ProductRepository:** An interface annotated with `@Repository` for data access.
		- **ProductService:** Annotated with `@Service` to encapsulate business logic, utilizing constructor injection for the repository.
		- **ProductController:** Annotated with `@RestController` to expose the REST endpoints.
- **Testing:** Verify the API functionality using Postman to send requests to `http://localhost:8080/products`.