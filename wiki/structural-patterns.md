---
tags:
  - cpt304
  - design-patterns
  - structural
source: lecture-3
---
# Structural Design Patterns

## Overview

Structural patterns guide developers in composing objects to form larger structures while keeping these structures flexible and efficient.

---

## Decorator Pattern

### Definition

Allows dynamically adding functionality and behavior to an object without affecting the behavior of other existing objects in the same class.

### Implementation

Also known as a "Wrapper." Uses abstract classes or interfaces with [[wiki/oop-concepts|composition]] to wrap the original class.

### When to Use

- Need to assign extra behaviors at runtime
- Extending behavior using inheritance is awkward or impossible (e.g., `final` classes)

### Industry Example

The standard library for I/O stream operations in Java/C# (e.g., wrapping `FileInputStream` inside `BufferedInputStream`).

### Tutorial Examples

- **Text Editor Formatting**: `BoldText`, `ItalicText` classes act as decorators wrapping `PlainText`, easily creating combined formatting chains
- **SmartRobotDecorator**: Any Robot can be a rational robot and a smart robot simultaneously via decorators
- **Cafe Ordering**: Base coffee dynamically gets extras (milk, sugar, flavors) affecting cost through a decorator chain

---

## Adapter Pattern

### Definition

Makes two incompatible interfaces compatible without changing their existing code.

### Implementation

Also known as a "Wrapper." The adapter implements the interface of one object and wraps the other. It receives calls from the client via the adapter interface and translates them into calls the wrapped service object expects.

### When to Use

- Integrating 3rd-party or legacy code
- Making existing classes work with others without modifying their source

### Tutorial Examples

- **Data Analytics Integration**: Create adapters for each data source (SQL, NoSQL, CSV, JSON APIs) that translate to a common interface
- **Payment Processing**: Different payment APIs (PayPal, CreditCards, Crypto) with different interfaces unified through adapters

---

## Proxy Pattern

### Definition

Provides a surrogate or placeholder for another object to control access to it.

### Tutorial Example

**Video Streaming Service**: A `VideoProxy` holds a reference to the original video but only executes the heavy stream operation when the user actually clicks to watch, reducing latency and server load.

---

## Composite Pattern

### Definition

Composes objects into tree structures to represent part-whole hierarchies. Clients can treat individual objects and compositions uniformly.

### Tutorial Example

**File System Hierarchy**: `File` (leaf node with content and size) and `Directory` (node containing multiple files/directories, deriving size from contents). Clients treat both uniformly.

---

## Related Pages

- [[wiki/design-patterns|Design Patterns Overview]] — Classification and benefits
- [[wiki/creational-patterns|Creational Patterns]] — Object creation patterns
- [[wiki/behavioral-patterns|Behavioral Patterns]] — Object communication patterns
- [[wiki/oop-concepts|Four Pillars of OOP]] — Composition vs Inheritance

## Sources

- [[Clippings/lecture 3]]
