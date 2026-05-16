---
tags:
  - cpt304
  - design-patterns
  - behavioral
source: lecture-4
---
# Behavioral Design Patterns

## Overview

Behavioral patterns are concerned with the assignment of responsibilities between objects and encapsulating behavior in objects. They focus on how objects are interconnected — allowing objects to communicate while remaining [[wiki/concepts/cohesion-and-coupling|loosely coupled]].

---

## Chain of Responsibility Pattern

### Concept

Passes a request from a client to a chain of objects. Each object in the chain decides whether to process the request and whether to pass it to the next object.

### Key Components

| Component | Role |
|-----------|------|
| **Handler** | Defines interface for handling requests and setting the next handler |
| **BaseHandler** | Optional abstract class with boilerplate code for concrete handlers |
| **Concrete Handlers** | Actual processing logic, chained in sequential order |
| **Client** | Originator that composes the chain and accesses the handler |

### Benefits

- **Reduced Coupling**: Object doesn't need to know which other object handles the request
- **Dynamic Flexibility**: Handlers can be added, removed, or reordered at runtime
- **Clear Sequential Process**: Explicit control over operation sequence
- **Separation of Concerns**: Each handler is independent of others

### Tutorial Example

**Web Server Request Processing**: HTTP requests go through authentication, logging, and data validation before handling the final request — each as a separate handler in the chain.

---

## Strategy Pattern

### Concept

Deals with changes in class behavior at runtime. Each type of algorithm is placed into its own class to achieve the [[wiki/solid-principles|Single Responsibility Principle]], making them easily interchangeable.

> The [[wiki/solid-principles|Open/Closed Principle (OCP)]] is mostly implemented through the Strategy Pattern in the software industry.

### Key Components

| Component | Role |
|-----------|------|
| **Context** | Maintains reference to a concrete strategy; communicates via the strategy interface |
| **Strategy Interface** | Common interface to different algorithms |
| **Concrete Strategies** | Individual implementations of the strategy interface |
| **Client** | Creates specific strategy objects and passes them to the context |

### Benefits

- **Runtime Flexibility**: Behavior can be altered by swapping strategy objects
- **Encapsulation & Reusability**: Complex behavior grouped into decoupled classes
- **Isolated Testing**: Each strategy can be tested independently

### Tutorial Examples

- **E-Commerce Payment**: Adding "Apple Pay" requires only a new `ApplePayStrategy` class (Open for Extension). The core `PaymentProcessor` context doesn't need recompilation (Closed for Modification).
- **E-Commerce Delivery**: Each delivery type (Express, Standard, Drone, In-Store) in its own strategy class.

---

## State Pattern

### Concept

Allows an object to alter its behavior when its internal state changes, making the object appear to change its class. Both the context and concrete states can set the next state and perform state transitions.

### Key Components

| Component | Role |
|-----------|------|
| **Context** | Stores reference to current concrete state; delegates state-specific work |
| **State Interface** | Common interface for all concrete states |
| **Concrete States** | Type-specific implementations of behavior |

### Benefits

- **Organized Control Flow**: Improves complex state switching
- **Localized State Behavior**: Groups specific behaviors into corresponding state classes
- **Explicit Transitions**: Predictable, readable state changes
- **Extensibility**: New states added easily; eliminates large conditionals

### Tutorial Examples

- **Vending Machine**: States like "NoSelection", "HasSelection", "InsertedMoney", "Dispensed" — each with varying event behaviors. The State pattern localizes operations into state classes.
- **Video Player**: A `PlayerContext` holds states like `StopState` or `PlayState`; `Play()` and `Stop()` delegate to these state classes.

---

## Related Pages

- [[wiki/design-patterns|Design Patterns Overview]] — Classification and benefits
- [[wiki/structural-patterns|Structural Patterns]] — Object composition patterns
- [[wiki/creational-patterns|Creational Patterns]] — Object creation patterns
- [[wiki/solid-principles|SOLID Principles]] — Strategy as OCP implementation
- [[wiki/concepts/cohesion-and-coupling|Cohesion & Coupling]] — Loose coupling via behavioral patterns

## Sources

- [[Clippings/lecture 4]]
