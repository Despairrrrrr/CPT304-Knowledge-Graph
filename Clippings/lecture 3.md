---
title: lecture
source: https://gemini.google.com/app/dda3ca3308f786b6
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

Here is the consolidated Markdown compilation of the lecture notes and tutorial exercises, formatted cleanly so you can feed it into Claude Code.

## Part 1: Lecture Notes - Design Patterns Theory

### Introduction to Design Patterns

- Design patterns are typical solutions to commonly occurring problems in software design.
- They are like pre-made blueprints that you can customize to solve a recurring design problem in your code.
- The pattern is not a specific piece of code that you can copy and paste, but a general concept for solving a particular problem.
- **Benefits:**
	- **Reusability:** Provides solutions that can be reused in multiple projects, reducing development time.
		- **Best Practices:** Reflects the experience and insights of software development professionals.
		- **Understandability and Maintainability:** Applies a consistent, well-documented approach making code easier to understand.
		- **Communication:** Improves communication within the team by providing a common vocabulary.
- **Drawbacks:**
	- **Overuse:** Using a design pattern where it's not needed can lead to unnecessary complexity.
		- **Initial Overhead:** Understanding and implementing them can initially slow down development.
		- **Dependence:** Over-reliance could limit a developer's ability to innovate outside the box.

### Classification of Design Patterns

All patterns can be categorized by their intent or purpose:

- **Creational patterns:** Provide object creation mechanisms that increase flexibility and reuse of existing code.
- **Structural patterns:** Explain how to assemble objects and classes into larger structures, while keeping the structures flexible and efficient.
- **Behavioral patterns:** Take care of effective communication and the assignment of responsibilities between objects.

---

### Creational Patterns

Creational design patterns deal with object creation, aiming to create objects in a manner suitable to the situation. They abstract the instantiation process and hide the implementation details of the objects being created.

**1\. Factory Pattern**

- **Definition:** Defines an interface for creating an object, but lets subclasses decide which class to instantiate.
- **Usage:** Useful when a class cannot anticipate the class of objects it needs to create.
- **Problem Solved:** Addresses violations of the Dependency Inversion Principle, where a high-level module shouldn't depend on a concrete implementation.
- **Solution:** Instead of the High-Level class instantiating the object itself (using the `new` keyword), it calls a "Factory" to handle the dirty work of object creation.

**2\. Builder Pattern**

- **Definition:** An alternative way to construct complex objects step by step.
- **Problem Solved:** Used to get rid of a constructor with many optional parameters.
- **Implementation:** Extracts the object construction code out of its own class and moves it to a separate object called Builder.
- **Enhancement:** Can introduce an optional `Director` class to manage the order of construction steps and hide details from the client code.

---

### Structural Patterns

Structural patterns guide developers in composing objects to form larger structures while keeping these structures flexible and efficient.

**1\. Decorator Pattern**

- **Definition:** Allows dynamically adding functionality and behavior to an object without affecting the behavior of other existing objects in the same class.
- **Implementation:** Also known as a "Wrapper." It uses abstract classes or interfaces with composition to wrap the original class.
- **Usage:** Used when you need to assign extra behaviors at runtime, or when extending an object's behavior using inheritance (e.g., classes with the `final` keyword) is awkward or impossible.
- **Industry Example:** The standard library for Input/Output (I/O) stream operations in Java or C# is built using the Decorator Pattern (e.g., wrapping `FileInputStream` inside `BufferedInputStream`).

**2\. Adapter Pattern**

- **Definition:** Makes two incompatible interfaces compatible without changing their existing code.
- **Implementation:** Also known as a "Wrapper." The adapter implements the interface of one object and wraps the other.
- **Usage:** The adapter receives calls from the client via the adapter interface and translates them into calls to the wrapped service object in a format it expects. Ideal for integrating 3rd-party or legacy code.

---

## Part 2: Tutorial Theory Questions & Answers

**Question 1: Logging System**

- **Scenario:** You need an application to write logs (info, debug, error) to a single log file. All parts of the application must write to the same file, but only one part can write at a time to avoid concurrency issues.
- **Pattern:** **Singleton Pattern**
- **Reasoning:** Every part of the application can access the globally accessible logging class. Having only one instance prevents multiple parts from writing to the file simultaneously.

**Question 2: Video Streaming Service**

- **Scenario:** You are developing a streaming service. Streaming directly for every request causes latency and server overload. You want to initially hold a reference to the video, and only stream/buffer it when the user clicks.
- **Pattern:** **Proxy Pattern**
- **Reasoning:** You create a `VideoProxy` holding the original reference. The proxy only executes the heavy stream from the original location when the user actually clicks to watch.

**Question 3: Vehicle Rental Service**

- **Scenario:** A service rents out cars, trucks, and motorcycles. The system must create specific vehicle objects based on customer choices, without repetitive and error-prone inline creation code.
- **Pattern:** **Factory Pattern**
- **Reasoning:** You create a `VehicleFactory` featuring a `createVehicle(String type)` method that handles the instantiation logic.

**Question 4: Data Analytics Integration**

- **Scenario:** A tool requires data from multiple sources (SQL, NoSQL, CSV, JSON APIs), each with completely different query syntaxes and return formats.
- **Pattern:** **Adapter Pattern**
- **Reasoning:** For each data source, you create an adapter that translates the specific source delivery method into a common interface your system understands.

**Question 5: File System Hierarchy**

- **Scenario:** A file system contains `File` (a leaf node with content and size) and `Directory` (a node containing multiple files or directories, deriving its size from its contents).
- **Pattern:** **Composite Pattern**
- **Reasoning:** It allows clients to treat individual `File` objects and compositions of `File` and `Directory` objects uniformly.

**Question 6: Text Editor Formatting**

- **Scenario:** A text editor allows users to apply formats (bold, italic, underline, strikethrough) independently or in combined combinations to plain text.
- **Pattern:** **Decorator Pattern**
- **Reasoning:** Formatting classes (`BoldText`, `ItalicText`, etc.) act as decorators wrapping the original `PlainText` component, easily allowing combined chains of formatting.

---

## Part 3: Practical Implementation Exercises

- **Exercise 1 (Factory Pattern):** Base on the full factory example in the lecture notes, extend the code following Factory Pattern to accept the ordering of Chicken Burger.
- **Exercise 2 (Factory Pattern):** A document management system features diverse formats (Word, PDF, Excel). Documents need to be created, opened, edited, and saved. Write a factory design pattern to encapsulate the objects initialization process, keeping in mind future document types.
- **Exercise 3 (Decorator Pattern):** A new type of Robot is invented. It is smarter because it can apply deep learning to cook better. Any Robot can be a rational robot and a smart robot at the same time. Enhance the base example by implementing a `SmartRobotDecorator`.
- **Exercise 4 (Decorator Pattern):** In a cafe scenario, customers start with basic coffee and dynamically add extra features (milk, sugar, flavors, whipped cream) that affect the final cost. Decorator classes wrap the base object to form a chain where each adds its own behavior and cost.
- **Exercise 5 (Adapter Pattern):** In an e-commerce scenario, users can pay via PayPal, CreditCards, and cryptocurrencies. Each has a different API. Directly integrating these APIs into the core system creates code clutter. Implement the Adapter Pattern to streamline payment processing based on user choice.