---
tags:
  - cpt304
  - oop
  - solid
  - design-principles
source: lecture-2
---
# SOLID Principles

## Overview

SOLID is a mnemonic for five design principles intended to make software designs more understandable, flexible, and maintainable. They are foundational to [[wiki/oop-concepts|object-oriented design]] and are closely related to [[wiki/concepts/cohesion-and-coupling|high cohesion and low coupling]].

> **Note**: Striving for these principles is good, but always be pragmatic — over-application can lead to unnecessary complexity.

---

## S — Single Responsibility Principle (SRP)

**A class should have one, and only one, reason to change.**

Every class should have single responsibility, entirely encapsulated by the class. The main goal is **reducing complexity**.

**Example**: A class handling user authentication should NOT also be responsible for sending email notifications. These responsibilities belong in separate classes.

---

## O — Open/Closed Principle (OCP)

**Software entities should be open for extension, but closed for modification.**

Use interfaces instead of superclasses to allow different implementations without changing the code that uses them. This keeps existing code from breaking when implementing new features.

**Example**: Using abstract classes or interfaces to define general behavior that can be extended by concrete implementations without modifying existing code.

---

## L — Liskov Substitution Principle (LSP)

**Objects of a superclass should be replaceable with objects of a subclass without affecting program correctness.**

Inheritance should be used only for substitutability. The user of a base class should be able to use a derived class instance without knowing the difference.

### Rules of LSP

| Rule | Description |
|------|-------------|
| 1 | Parameter types in subclass should match or be more abstract than superclass |
| 2 | Return types in subclass should match or be subtypes of superclass |
| 3 | Exception types must match or be subtypes |
| 4 | Subclass must not strengthen pre-conditions |
| 5 | Subclass must not weaken post-conditions |
| 6 | Superclass invariants must be preserved |
| 7 | Subclass must not change private/protected state values of superclass |

**Violation Example**: A subclass override returns a `long` while the superclass returns an `int`. Clients expecting a smaller range may fail.

---

## I — Interface Segregation Principle (ISP)

**Clients should not be forced to depend upon interfaces they do not use.**

Make interfaces narrow enough that clients don't need to implement behaviors they don't need. This promotes modularity and reusability through smaller, more focused interfaces.

---

## D — Dependency Inversion Principle (DIP)

**High-level modules should not depend on low-level modules. Both should depend on abstractions.**

Abstractions should not depend on details; details should depend on abstractions.

**Example**: Depending on an abstract `Database` interface rather than a specific `MySQLDatabase` implementation allows swapping databases without modifying high-level code.

---

## Related Pages

- [[wiki/oop-concepts|Four Pillars of OOP]] — Foundational OOP concepts
- [[wiki/concepts/cohesion-and-coupling|Cohesion & Coupling]] — Quality metrics SOLID aims to optimize
- [[wiki/concepts/dependency-injection|Dependency Injection & IoC]] — DIP in practice with DI containers
- [[wiki/design-patterns|Design Patterns Overview]] — Patterns that implement SOLID principles
- [[wiki/behavioral-patterns|Behavioral Patterns]] — Strategy pattern as OCP implementation

## Sources

- [[Clippings/lecture 2]]
