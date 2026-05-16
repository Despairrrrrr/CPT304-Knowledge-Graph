---
tags:
  - cpt304
  - cbse
  - spring-boot
  - architecture
source: lecture-7
---
# Component-Based Software Engineering & Spring Boot

## Overview

Component-Based Software Engineering (CBSE) develops software primarily from reusable software components. It is built on three core principles: **Components**, **Interfaces**, and **Composition**.

---

## CBSE Fundamentals

### Benefits
- Reduced development time and cost through reusability
- Enhanced maintainability via modularity
- Easier isolation and testing of components

### Challenges
- Managing dependency and version conflicts
- Overhead from inter-component communication
- Designing components that are both specific and reusable

### Component Characteristics

| Characteristic | Description |
|---------------|-------------|
| **Self-contained** | Each component encapsulates its own logic and data |
| **Reusable** | Designed for use across different systems |
| **Replaceable** | Swappable with another component providing the same interface |
| **Interface-driven** | Interaction solely through defined interfaces |

### Component Models & Middleware

Component models (like Spring) provide conventions, interaction mechanisms, and lifecycle management. Middleware (like Spring Data, Spring Cloud) handles communication, data management, and infrastructure services.

---

## Components in Spring Boot

Spring Boot streamlines development with auto-configuration, embedded servers (Tomcat), and opinionated defaults.

### Core Annotations

| Annotation | Role |
|-----------|------|
| `@Component` | General Spring-managed bean |
| `@Service` | Business logic encapsulation |
| `@Repository` | Data access component |
| `@Controller` / `@RestController` | HTTP request handling |

### Inversion of Control (IoC) Container

The framework takes control of:
- Instantiating beans
- Configuring via [[wiki/concepts/dependency-injection|Dependency Injection]]
- Managing lifecycle
- Storing in application context

### Dependency Injection (DI) Types

| Type | When to Use |
|------|-------------|
| **Constructor Injection** | Recommended for mandatory dependencies |
| **Setter Injection** | Suitable for optional or runtime-changeable dependencies |
| **Field Injection** | Less preferred due to testability concerns |

---

## Component Interfaces, Composition & Lifecycle

### Interface Benefits

Interfaces enable polymorphism, loose coupling, and testability by defining interactions through abstractions. Multiple bean implementations can be resolved using `@Primary` or `@Qualifier`.

### Component Lifecycle

1. **Creation**: IoC creates instance and injects dependencies
2. **Initialization**: Spring invokes init logic (`@PostConstruct`)
3. **Usage**: Bean is ready for other components
4. **Destruction**: Cleanup before context closes (`@PreDestroy`)

### Advanced Features

| Feature | Description |
|---------|-------------|
| **Scopes** | Singleton (default), Prototype, Request, Session, Application |
| **Dynamic Resolution** | `ObjectProvider` for runtime dependency selection |
| **Circular Dependencies** | Resolved with `@Lazy` (injects a proxy instead of actual bean) |
| **Programmatic Beans** | `@Configuration` + `@Bean` for explicit creation; `@Conditional` for dynamic creation |

---

## Architecture Patterns

### Domain-Driven Design (DDD)

Aligns software structure with business domains.

| Concept | Description |
|---------|-------------|
| **Entities** | Objects with distinct identity and lifecycle, tracked by unique ID |
| **Aggregates** | Cluster of entities/value objects treated as unit for consistency |
| **Bounded Contexts** | Boundaries defining domain model and ubiquitous language |

### Hexagonal Architecture (Ports and Adapters)

Decouples core business logic from external systems.

- **Ports**: Abstract interfaces defining what the core provides (Inbound) or requires (Outbound)
- **Adapters**: Concrete classes (REST controllers, JPA repositories) bridging core to external systems

---

## Hands-On: E-Commerce API with Spring Boot

### Component Structure

```
Product Model (data) → ProductRepository (@Repository) → ProductService (@Service) → ProductController (@RestController)
```

**Key Points**:
- Endpoints: `GET /products`, `POST /products`
- Constructor injection for repository in service
- Test via Postman at `localhost:8080/products`

---

## Related Pages

- [[wiki/software-reuse|Software Reuse]] — Broader reuse context including CBSE
- [[wiki/concepts/dependency-injection|Dependency Injection & IoC]] — Core DI concepts
- [[wiki/concepts/cohesion-and-coupling|Cohesion & Coupling]] — Design quality metrics
- [[wiki/solid-principles|SOLID Principles]] — Design principles for component design
- [[wiki/structural-patterns|Structural Patterns]] — Adapter pattern for hexagonal architecture

## Sources

- [[Clippings/lecture 7]]
