---
tags:
  - cpt304
  - design-patterns
  - creational
source: lecture-3
---
# Creational Design Patterns

## Overview

Creational design patterns deal with object creation, aiming to create objects in a manner suitable to the situation. They abstract the instantiation process and hide implementation details of the objects being created.

---

## Factory Pattern

### Definition

Defines an interface for creating an object, but lets subclasses decide which class to instantiate.

### Problem Solved

Addresses violations of the [[wiki/solid-principles|Dependency Inversion Principle (DIP)]] — a high-level module shouldn't depend on a concrete implementation. Instead of using the `new` keyword directly, the high-level class calls a "Factory" to handle object creation.

### When to Use

- A class cannot anticipate the class of objects it needs to create
- Object creation logic should be centralized

### Tutorial Example

**Vehicle Rental Service**: A `VehicleFactory` with a `createVehicle(String type)` method handles instantiation for cars, trucks, and motorcycles based on customer choice.

---

## Builder Pattern

### Definition

An alternative way to construct complex objects step by step.

### Problem Solved

Eliminates constructors with many optional parameters (the "telescoping constructor" anti-pattern).

### Implementation

- Extracts object construction code out of its own class into a separate `Builder` object
- Can optionally introduce a `Director` class to manage the order of construction steps and hide details from client code

---

## Singleton Pattern

### Definition

Ensures a class has only one instance and provides a global point of access to it.

### When to Use

When exactly one instance is needed to coordinate actions across the system.

### Tutorial Example

**Logging System**: An application needs to write logs (info, debug, error) to a single file. Only one part can write at a time to avoid concurrency issues. A globally accessible singleton logging class prevents multiple parts from writing simultaneously.

---

## Related Pages

- [[wiki/design-patterns|Design Patterns Overview]] — Classification and benefits
- [[wiki/structural-patterns|Structural Patterns]] — Patterns for composing objects
- [[wiki/behavioral-patterns|Behavioral Patterns]] — Patterns for object communication
- [[wiki/solid-principles|SOLID Principles]] — Factory as DIP solution
- [[wiki/concepts/dependency-injection|Dependency Injection & IoC]] — Factory alternatives in DI frameworks

## Sources

- [[Clippings/lecture 3]]
