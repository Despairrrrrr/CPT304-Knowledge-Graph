---
title: lecture
source: https://gemini.google.com/app/ee9a886d7ee6a7a6
author:
published:
created: 2026-05-16
description: Gemini conversation with 4 messages
tags:
  - clippings
---
**You**

我上传了CPT304课程的一节课课件以及课后对应的练习，请你将知识点和习题整理成markdown的形式，方便我录入给Claude code整理笔记。要求内容为英文，尽量保持课件中原有的表达方式

---

**Gemini**

CPT304 – Object-oriented Concepts

1\. Four Pillars of OOP

- **Abstraction:** Abstraction is a model of a real-world object or phenomenon, limited to a specific context, which represents all details relevant to this context with high accuracy and omits all the rest. It allows developers to interact with a system at a higher level without needing to understand the intricate details of its implementation.
- **Encapsulation:** This is the ability of an object to hide parts of its state and behaviors from other objects, exposing only a limited interface to the rest of the program. The interface mechanism lets you define contracts of interaction between objects. The class that binds to the contract must implement the methods defined in the contract.
- **Inheritance:** The ability to build new classes on top of existing ones. The main benefit of inheritance is code reuse. This is achieved by extending the existing class and putting the extra functionality into a resulting subclass, which inherits fields and methods of the superclass.
- **Polymorphism:** Allows a class to take different forms. It is the concept that you can access objects of different types through the same interface. A parent class reference is used to refer to a child class object.

---

2\. What is a Good Design?

A good design hides inherent complexity (via abstraction, encapsulation, inheritance) and eliminates accidental complexity (via simplification, reusability, design patterns). Ultimately, a software has a good design if the cost of changing it is minimized.

How Cohesion and Coupling contribute to this goal:

- **Cohesion (Focus):** High cohesion means a module or class has a single, well-defined purpose. When requirements change, a highly cohesive system is easier to maintain because the changes are localized to specific, predictable places. If a class is "low cohesion" (doing too many unrelated things), changing one feature might accidentally break an unrelated one.
- **Coupling (Dependency):** Coupling refers to how much one class knows about or relies on another.
	- *Tight Coupling:* If Class A depends on the internal details of Class B, any change to B forces a change in A.
		- *Loose Coupling:* By using interfaces instead of concrete implementations, we decouple the classes. Class A only knows "what" Class B can do, not "how" it does it. This minimizes the "ripple effect" where a single change necessitates a cascade of edits across the codebase.
- **Conclusion:** A design with High Cohesion and Low Coupling ensures that the system is modular, making it cheaper and safer to evolve over time.

Problems with Low Cohesion (Long Methods / Multiple Responsibilities):

- Hard to reuse.
- Lead to duplication.
- Difficult to understand.
- Making changes to the code becomes riskier.
- Often clutter with codes.
- Hard to test. Too many possibilities.
- Difficult to navigate and hard to find a specific code.
- Involve in the modification frequently.
- Difficult to debug.

---

3\. SOLID Principles

SOLID is a mnemonic for five design principles intended to make software designs more understandable, flexible and maintainable. Striving for these principles is good, but always try to be pragmatic.

S – Single Responsibility Principle (SRP)

A class should have one, and only one, reason to change. Make every class have single responsibility, and make that responsibility entirely encapsulated by the class. The main goal of this principle is reducing complexity.

- Application Example : A class that handles user authentication should not also be responsible for sending email notifications. These responsibilities should be separated into distinct classes to adhere to SRP.

O – Open/Closed Principle (OCP)

Software entities (classes, modules, functions, etc.) should be open for extension, but closed for modification. The main idea of this principle is to keep existing code from breaking when you implement new features. Use interfaces instead of superclasses to allow different implementations without changing the code that uses them.

- Contribution to Maintainability & Example : By adhering to OCP, developers can create software components that can be extended without modifying their source code. For example, using abstract classes or interfaces to define general behavior that can be extended by concrete implementations without modifying the existing code showcases OCP in action.

L – Liskov Substitution Principle (LSP)

Inheritance should be used only for substitutability. The user of a base class should be able to use an instance of a derived class without knowing the difference. Objects of a superclass should be replaceable with objects of a subclass without affecting the correctness of the program.

- Significance : This principle ensures that subtypes should be substitutable for their base types without altering the desirable properties of the program. Code that adheres to LSP is flexible and promotes high reusability.
- **Rules of LSP:**
	1. Parameter types in a subclass method should match or be more abstract than the superclass.
		2. Return type in a subclass method should match or be a subtype of the superclass.
		3. Types of exceptions thrown shouldn't be new types (must match or be subtypes).
		4. A subclass shouldn't strengthen pre-conditions.
		5. A subclass shouldn't weaken post-conditions.
		6. Invariants of a superclass must be preserved.
		7. A subclass shouldn't change values of private/protected states of the superclass.
- Violation Example: When a subclass override returns a `long` data type while the superclass returns an `int`. There exists an unexpected error in the client software when the subclass is replacing its superclass. The client is expecting a smaller range of values. The subclass returns a larger range of values which the client may not be able to accommodate.

I – Interface Segregation Principle (ISP)

Clients should not be forced to depend upon interfaces that they do not use. Make your interface narrow enough that clients don't need to implement behaviors they don't need.

- Role in Software Design : By creating specific interfaces for specific client requirements, ISPs promote modularity and reusability by allowing for smaller, more focused interfaces that cater to the specific needs of each client class.

D – Dependency Inversion Principle (DIP)

High-level modules should not depend on low-level modules. Both should depend on abstractions. Abstractions should not depend on details. Details should depend on abstractions.

- Decoupling Modules : DIP helps to decouple software modules and enhance flexibility by relying on abstractions rather than concrete implementations. For example, depending on an abstract database interface rather than a specific database implementation allows for different database implementations to be used without modifying the high-level module.

---

4\. Loosening Coupling using Composition

Composition represents a "has a" relationship (Class B has a Class A), while Inheritance represents an "is a" relationship (Class B is a Class A). You can always replace an inheritance relationship by a composition relationship.

**When to use Inheritance vs Composition?**

- **Inheritance:** If an object of B should be used anywhere an object of A is used, then use inheritance.
- **Composition:** If an object of B should use an object of A, then use composition. Use composition as an alternative to multiple inheritance.

**Benefits of Composition:**

- **Dynamic Flexibility:** Makes dynamic changes possible at runtime (often through polymorphism), allowing an object to change its behavior by swapping out its composed parts.
- **Avoids Combinatorial Explosion:** Allows you to combine behaviors dynamically without creating a new class for every possible combination of traits.

The Combinatorial Explosion Problem:

- *Scenario:* Designing a "Machine" hierarchy with movements (Fly, Swim) and combat capabilities (Laser, Rifle).
- *Problem with pure inheritance:* The number of required classes grows exponentially. You are forced to create a class for every possible combination (e.g., `FlyLaserMachine`, `SwimRifleMachine`). If you add just one more movement type, you must manually create even more subclasses, resulting in a bloated, rigid hierarchy with duplicated code.
- *Solution using Composition:* Use a "has-a" relationship. Define interfaces for behaviors (e.g., `IMoveBehavior` and `IWeaponBehavior`). The `Machine` class is composed of references to these interfaces. At runtime, you can "plug in" different implementations into a generic `Machine` object. You only need one `Machine` class and a few behavior classes, creating combinations dynamically without writing new class definitions.

---

**You**

我补充了辅助学习的代码文件，据此完善你整理的笔记

---

**Gemini**

首先，您需要连接至 Google Workspace，以打开该扩展。