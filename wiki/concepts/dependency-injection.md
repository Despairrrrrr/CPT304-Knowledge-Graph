---
tags:
  - cpt304
  - design
  - dependency-injection
  - ioc
  - cross-cutting
source: lecture-7
---
# Dependency Injection & Inversion of Control

## Overview

**Inversion of Control (IoC)** and **Dependency Injection (DI)** are fundamental design principles that reverse the traditional flow of control in software. Instead of the application controlling the flow, the **framework** takes control — a key characteristic of [[wiki/software-reuse|application frameworks]].

---

## Inversion of Control (IoC)

### Traditional vs IoC

| Aspect | Traditional | IoC (Framework) |
|--------|------------|-----------------|
| **Control** | Application calls libraries | Framework calls your code |
| **Flow** | Developer controls execution | Framework controls the lifecycle |
| **Dependency** | You manage instantiation | Framework wires dependencies |

### IoC in Practice (Spring)

The IoC container:
1. Instantiates beans
2. Configures them via DI
3. Manages their lifecycle
4. Stores them in the application context

---

## Dependency Injection (DI)

**Definition**: Dependencies are "injected" into a class by an external entity (the framework) rather than the class creating them itself.

### DI Types

| Type | Description | Best For |
|------|-------------|----------|
| **Constructor Injection** | Dependencies provided via constructor parameters | Mandatory dependencies |
| **Setter Injection** | Dependencies provided via setter methods | Optional or runtime-changeable dependencies |
| **Field Injection** | Direct field injection (using `@Autowired`) | Quick prototyping (less testable) |

### Benefits
- **Modularity**: Components are loosely coupled
- **Testability**: Dependencies can be mocked easily
- **Flexibility**: Implementations can be swapped without changing consumers

### Resolution

When multiple beans implement the same interface:
- `@Primary`: Marks a bean as the default
- `@Qualifier`: Selects a specific bean by name

---

## Relationship to Other Concepts

### DI and [[wiki/concepts/cohesion-and-coupling|Coupling]]

DI is a primary tool for achieving **loose coupling**. By depending on abstractions (interfaces) rather than concrete classes, components can be swapped without ripple effects.

### DI and [[wiki/solid-principles|SOLID]]

DI directly supports the **Dependency Inversion Principle (DIP)**: high-level modules should not depend on low-level modules — both should depend on abstractions.

### DI and [[wiki/structural-patterns|Design Patterns]]

The **Adapter Pattern** uses similar principles: dependency on interfaces that translate between incompatible systems.

---

## Related Pages

- [[wiki/component-based-engineering|CBSE & Spring Boot]] — DI in practice with Spring
- [[wiki/concepts/cohesion-and-coupling|Cohesion & Coupling]] — How DI reduces coupling
- [[wiki/solid-principles|SOLID Principles]] — DIP and DI
- [[wiki/software-reuse|Software Reuse]] — Frameworks and IoC
- [[wiki/structural-patterns|Structural Patterns]] — Adapter pattern for interface compatibility

## Sources

- [[Clippings/lecture 7]]
