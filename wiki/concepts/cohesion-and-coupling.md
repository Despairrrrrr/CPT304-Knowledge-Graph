---
tags:
  - cpt304
  - design
  - quality
  - cross-cutting
source: lecture-2
---
# Cohesion & Coupling

## Overview

**Cohesion** and **Coupling** are two of the most important metrics for evaluating software design quality. The goal of good design is **high cohesion** and **low coupling** — this minimizes the cost of change and maximizes modularity.

---

## Cohesion (Focus)

**Definition**: How focused a module or class is on a single purpose.

### High Cohesion
- A class has a single, well-defined purpose
- When requirements change, changes are localized to predictable places
- Easier to maintain, test, and understand

### Low Cohesion (Problems)
- Hard to reuse
- Leads to duplication
- Difficult to understand and navigate
- Changes become risky (one feature change may break unrelated features)
- Hard to test (too many possibilities)
- Difficult to debug

---

## Coupling (Dependency)

**Definition**: How much one class knows about or relies on another.

### Tight Coupling
- Class A depends on the internal details of Class B
- Any change to B forces a change in A
- Creates a "ripple effect" where one change causes cascading edits

### Loose Coupling
- Class A only knows "what" Class B can do, not "how"
- Achieved through interfaces instead of concrete implementations
- Minimizes the ripple effect

---

## Practical Implications

| Design Quality | Cohesion | Coupling | Change Impact |
|---------------|:--------:|:--------:|:-------------:|
| Good | High | Low | Minimal, localized |
| Poor | Low | High | Cascading, widespread |

### Achieving Good Design

- **[[wiki/solid-principles|SOLID Principles]]** — Especially SRP (cohesion) and DIP (coupling)
- **[[wiki/design-patterns|Design Patterns]]** — Many patterns (Strategy, Adapter, etc.) promote loose coupling
- **[[wiki/concepts/dependency-injection|Dependency Injection]]** — Reduces coupling by letting the framework wire dependencies
- **[[wiki/oop-concepts|Composition over Inheritance]]** — Composition provides looser coupling than inheritance

---

## Related Pages

- [[wiki/solid-principles|SOLID Principles]] — SRP for high cohesion, DIP for low coupling
- [[wiki/oop-concepts|Four Pillars of OOP]] — Encapsulation reduces coupling
- [[wiki/concepts/dependency-injection|Dependency Injection & IoC]] — DI as coupling reduction technique
- [[wiki/design-patterns|Design Patterns Overview]] — Patterns that manage coupling
- [[wiki/structural-patterns|Structural Patterns]] — Adapter, Decorator for loose coupling
- [[wiki/behavioral-patterns|Behavioral Patterns]] — Chain of Responsibility, Strategy for decoupled communication

## Sources

- [[Clippings/lecture 2]]
