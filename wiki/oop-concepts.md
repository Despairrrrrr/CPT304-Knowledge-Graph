---
tags:
  - cpt304
  - oop
  - object-oriented
source: lecture-2
---
# Four Pillars of OOP

## Overview

Object-Oriented Programming (OOP) is a programming paradigm based on the concept of "objects" containing data and behavior. The four pillars of OOP — Abstraction, Encapsulation, Inheritance, and Polymorphism — form the foundation of modern software design.

---

## The Four Pillars

### 1. Abstraction

A model of a real-world object or phenomenon, limited to a specific context, representing all details relevant to this context with high accuracy and omitting the rest.

**Purpose**: Allows developers to interact with a system at a higher level without needing to understand the intricate details of its implementation.

### 2. Encapsulation

The ability of an object to hide parts of its state and behaviors from other objects, exposing only a limited interface to the rest of the program.

**Key Points**:
- The interface mechanism defines contracts of interaction between objects
- Classes that bind to a contract must implement the methods defined in it
- Enables [[wiki/concepts/cohesion-and-coupling|loose coupling]] by hiding implementation details

### 3. Inheritance

The ability to build new classes on top of existing ones, achieving code reuse.

**Mechanism**: Extending an existing class (superclass) and putting extra functionality into the resulting subclass, which inherits fields and methods of the superclass.

### 4. Polymorphism

Allows a class to take different forms. Objects of different types can be accessed through the same interface.

**Mechanism**: A parent class reference is used to refer to a child class object.

---

## What is Good Design?

A good design:
- Hides **inherent complexity** via abstraction, encapsulation, inheritance
- Eliminates **accidental complexity** via simplification, reusability, design patterns
- Minimizes the cost of change

This is achieved through [[wiki/concepts/cohesion-and-coupling|high cohesion and low coupling]]:
- **High Cohesion**: Each class has a single, well-defined purpose; changes are localized
- **Low Coupling**: Classes depend on interfaces, not concrete implementations; minimal "ripple effect"

### Problems with Low Cohesion

- Hard to reuse, test, debug, and navigate
- Leads to duplication and code clutter
- Changes become risky; hard to find specific code

---

## Composition vs Inheritance

| Aspect | Inheritance | Composition |
|--------|-------------|-------------|
| Relationship | "is-a" | "has-a" |
| Flexibility | Static (compile-time) | Dynamic (runtime) |
| When to use | B should be usable anywhere A is used | B should use an object of A |
| Combinatorial explosion | Yes (requires new class per combination) | No (compose behaviors dynamically) |

### The Combinatorial Explosion Problem

With pure inheritance, adding one new movement type (e.g., Fly, Swim) × combat type (Laser, Rifle) forces creating a class for every combination. Composition solves this by defining behavior interfaces and "plugging in" implementations at runtime.

---

## Related Pages

- [[wiki/solid-principles|SOLID Principles]] — Design principles built on OOP foundations
- [[wiki/concepts/cohesion-and-coupling|Cohesion & Coupling]] — Key quality metrics for OOP design
- [[wiki/concepts/dependency-injection|Dependency Injection & IoC]] — Decoupling through DI
- [[wiki/design-patterns|Design Patterns Overview]] — Patterns that leverage OOP principles
- [[wiki/software-crisis|Software Crisis & No Silver Bullet]] — Brooks' view on OOP

## Sources

- [[Clippings/lecture 2]]
