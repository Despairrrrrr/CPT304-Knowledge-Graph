---
title: lecture
source: https://gemini.google.com/app/ff74b757961f7eda
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

Here is the organized Markdown compilation of the lecture concepts and tutorial exercises, formatted specifically for easy ingestion by Claude Code.

---

## 1\. Introduction to Software Reuse

- Software reuse is the practice of using existing software components (code, designs, etc.) to build new system.
- **Benefits of Software Reuse:**
	- Cost savings: Reuse reduces development and maintenance cost.
		- Faster delivery: Get products to market quicker.
		- Higher quality: Tested components mean fewer bugs.
		- Specialist knowledge: Leverage experts’ work without reinventing the wheel.
- **Challenges of Software Reuse:**
	- Maintenance costs: Reuse code may become outdated or incompatible.
		- Tool support: Some tools don’t integrate well with reuse components.
		- Not-invented-here syndrome: Developers may resist using others’ code.
		- Finding and Adapting components: It can be hard to locate and modify the right components.

## 2\. Core Reuse Techniques

### 2.1 Application Frameworks

- **Definition:** A generic structure (e.g. a set of classes) that you extend to create specific applications.
- **How they work:** Provide common features (e.g., security, database support) that you customize.
- **Extension Methods:**
	- Inheritance: Create subclasses from framework classes.
		- Callbacks: Register functions to be called at specific times or events.
		- Hooks: Insert custom code at predefined points.
- **Challenges:**
	- Learning Curve: Steep initial effort to understand and adapt the framework.
		- Overhead: May include unused features, bloating the app.

**Application Framework vs. Software Library**

- **Application Framework:** Broad scope, often covering an entire application domain. Uses an inversion of control (IoC) model—the framework controls the flow. Your application depends heavily on the framework; it’s the backbone of the system.
- **Software Library:** Narrower scope, focusing on specific tasks or features. The developer retains control—you call the library when you need its functionality. Dependency is lighter—you can swap out or remove a library with less impact.

### 2.2 Software Product Lines (SPL)

- **Definition:** A set of related software products sharing a common core but specialized for different needs.
- **Benefits:** Reuse across multiple products, enabling faster development for new variants.

**Types of SPL Specialization:**

- **Platform Specialization:** This focuses on adapting the software to run across different hardware architectures, operating systems, or computing infrastructures while maintaining the same core logic. Example: Cross-Platform Gaming Engines.
- **Functional Specialization:** This involves tailoring the feature set or capabilities of the software to suit different user roles, industry niches, or service tiers. Example: Banking Software specialized into Retail Banking and Investment Banking.
- **Environment Specialization:** This centers on the external conditions, constraints, or peripheral systems where the software must operate, such as regulatory zones or network conditions. Example: Automotive Infotainment Systems specialized for different Regional Markets.
- **Process Specialization:** This focuses on the workflow, methodology, or operational constraints under which the software is deployed or maintained. Example: E-Learning Platforms specialized for Academic Use versus Corporate Training.
- **Challenges:**
	- Upfront Investment: High cost and time to design a reusable core.
		- Complexity: Managing variants can get messy as the family grows.

### 2.3 Commercial Off-The-Shelf (COTS)

- **Definition:** Pre-built software that you can buy and adapt without changing the source code.
- **Tailoring Methods:** Configure settings, Plugins, API calls.
- **Benefits:** Fast deployment, lower development risk, vendor support.
- **Testing Focus:** Testing of COTS focus on integration. Key focus is to test how the COTS software interacts with your operational processes.
- **Challenges:** \* Limited Customization: Configuration-only approach restricts flexibility.
	- Vendor Dependency: Reliant on vendor updates or support.

**SPL vs. COTS Differences**

- SPL is a family of software focused on a specific domain of industry, whereas COTS is a single, more generic software.
- COTS is a software readily available in the market for immediate use. In this aspect, SPL may not be as readily usable as COTS.
- COTS is rather limited in term of customization as compared to SPL. SPL provide greater degree of customization.

---

## 3\. Tutorial Questions & Concepts

**Q: Suggest why the savings in cost from reusing existing software are not simply proportional to the size of the components that are reused.**

- **Answer:** The larger part of the software is being reused, the more work has to be done to understand and test the code, more change may be required to accommodate the reuse software.

**Q: Testing process for COTS-solution system should focus on the interactions between the operational processes and the system configuration. Justify.**

- **Answer:** The COTS systems are production-ready systems. Unit tests are completed long before it is available in the market for sales, and hence the user do not need to worry about the technical aspect of the software. A COTS system is useful only if its processes is compatible to the user’s operations, and it if doesn’t it should be able to be reconfigured.

**Q: Dive into the roles of callbacks and hooks: how do they work in a web framework, and what sets them apart in bringing your app to life?**

- **Answer:** \* Callbacks are functions you write and pass to the framework to be executed at specific moments, usually triggered by user actions or external events. They run when you say (e.g., on a click).
	- Hooks, on the other hand, are special functions provided by the framework that let you “hook into” its lifecycle or state system, giving you control at predefined points without taking over the flow. They run when the framework decides (e.g., on state change).

---

## 4\. Scenario-Based Exercises

**Scenario 1: Fitness Tracking App**

- **Context:** A software development team is tasked with creating a fitness tracking application that supports multiple user roles, includes workout planning features, and integrates with external wearable devices. The client demands delivery within five months and prioritizes scalability and maintainability.
- **Technique:** Application Frameworks.
- **Justification:** \* Frameworks support scalability by offering extensible architectures, allowing the app to handle increasing users as wearable adoption grows.
	- Projects develop with framework are more maintainable because developers extend the framework mainly by inheritance, callbacks, and hooks.
		- Application Frameworks provide pre-built modules for user management and device integration, enabling the team to deliver the fitness tracking app within the five-month timeline.

**Scenario 2: Suite of Mobile Apps for Small Businesses**

- **Context:** Developing a new set of mobile apps including a POS app, appointment scheduling app, and inventory management app. All apps need to run on both iOS and Android, and they must share common features like user authentication, payment processing, and data analytics.
- **Technique:** Software Product Lines (SPL).
- **Justification:**
	- SPLs allow the company to create a single core system with shared features that can be reused across all three apps, reducing redundant development effort and ensuring consistency.
		- The specialization capability of SPLs aligns perfectly with the need for distinct yet related apps, enabling efficient customization for each business type.
		- SPLs support cross-platform deployment through platform specialization, ensuring the apps work seamlessly on both operating systems.
- **Challenges:** High initial investment in designing the common core and defining reusable components. Maintaining consistency across variants as the apps evolve.

**Scenario 3: Travel Booking Platform**

- **Context:** Supports multiple user roles, includes trip planning features, integrates with external APIs. Client requires delivery within six months and prioritizes ease of updates to adapt to new travel regulations.
- **Technique:** Application Frameworks.
- **Justification:** Provide pre-built modules for user management and API integration, enabling the team to meet the six-month deadline. Frameworks support ease of updates through extensible designs, allowing quick adaptations.

**Scenario 4: Event Management System**

- **Context:** Supports multiple user roles, includes ticketing, integrates with external payment gateways. Client insists on delivery within three months and prioritizes rapid deployment.
- **Technique:** COTS (Commercial Off-The-Shelf).
- **Justification:** COTS provides a pre-built event management solution, enabling rapid deployment within three months to meet the tight deadline. It includes tested ticketing and payment integration features, ensuring the system is ready without extensive custom development.

**Scenario 5: Smart Home Applications Suite**

- **Context:** Supporting multiple user roles, features for device control, integrating with external IoT systems. Client demands delivery within eight months and prioritizes consistency across the suite for branding.
- **Technique:** Software Product Lines (SPL).
- **Justification:** SPL allows the team to build a reusable core for device control and integration, speeding up development. SPL ensures consistency across all apps by sharing a common architecture, meeting the client’s branding priority.