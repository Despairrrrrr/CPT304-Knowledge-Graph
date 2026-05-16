---
tags:
  - cpt304
  - software-reuse
  - architecture
source: lecture-5
---
# Software Reuse

## Overview

Software reuse is the practice of using existing software components (code, designs, etc.) to build new systems. It is a key strategy for improving productivity, quality, and time-to-market.

---

## Benefits & Challenges

### Benefits
- **Cost savings**: Reduced development and maintenance costs
- **Faster delivery**: Quicker time-to-market
- **Higher quality**: Tested components mean fewer bugs
- **Specialist knowledge**: Leverage experts' work without reinventing the wheel

### Challenges
- **Maintenance costs**: Reused code may become outdated or incompatible
- **Tool support**: Some tools don't integrate well with reusable components
- **Not-invented-here syndrome**: Developer resistance to using others' code
- **Finding & adapting**: Difficulty locating and modifying the right components

---

## Core Reuse Techniques

### 1. Application Frameworks

**Definition**: A generic structure (e.g., a set of classes) that you extend to create specific applications.

**How they work**: Provide common features (security, database support) that you customize.

**Extension Methods**:
- **Inheritance**: Create subclasses from framework classes
- **Callbacks**: Register functions to be called at specific events
- **Hooks**: Insert custom code at predefined points

**Challenges**: Steep learning curve; may include unused features (bloat).

#### Application Framework vs Software Library

| Aspect | Application Framework | Software Library |
|--------|---------------------|------------------|
| **Scope** | Broad (entire application domain) | Narrow (specific tasks) |
| **Control** | Inversion of Control (IoC) — framework controls flow | Developer retains control |
| **Dependency** | High — the backbone of the system | Lighter — can be swapped out |

#### Scenario: Fitness Tracking App
An app with multiple user roles, workout planning, and wearable integration needed within 5 months. **Frameworks** provide pre-built modules for user management and device integration, supporting scalability and maintainability through extensible architectures.

---

### 2. Software Product Lines (SPL)

**Definition**: A set of related software products sharing a common core but specialized for different needs.

#### Types of Specialization

| Type | Focus | Example |
|------|-------|---------|
| **Platform** | Hardware/OS adaptation | Cross-platform gaming engines |
| **Functional** | Feature sets for user roles/niches | Retail vs. Investment Banking |
| **Environment** | External conditions/regulations | Regional automotive infotainment |
| **Process** | Workflow/operational constraints | Academic vs. Corporate e-learning |

**Benefits**: Reuse across multiple products; faster development for new variants.
**Challenges**: High upfront investment; managing variant complexity.

#### Scenario: Mobile Apps for Small Businesses
POS, appointment scheduling, and inventory management apps sharing user auth, payment, and analytics. **SPL** creates a single core with shared features, specialized for each business type across iOS and Android.

---

### 3. Commercial Off-The-Shelf (COTS)

**Definition**: Pre-built software that you can buy and adapt without changing the source code.

**Tailoring Methods**: Configuration settings, Plugins, API calls.

**Testing Focus**: Integration testing — how COTS interacts with operational processes.

**Benefits**: Fast deployment, lower development risk, vendor support.
**Challenges**: Limited customization; vendor dependency.

#### SPL vs COTS

| Aspect | SPL | COTS |
|--------|-----|------|
| Scope | Family focused on a domain | Single, more generic software |
| Availability | May not be readily usable | Immediately available |
| Customization | High degree | Limited (configuration only) |

#### Scenario: Event Management System
Ticketing system with payment integration needed within 3 months. **COTS** provides pre-built, tested features for rapid deployment.

---

## Key Insight

> "The savings in cost from reusing existing software are not simply proportional to the size of the components that are reused. The larger the reused part, the more work is needed to understand, test, and accommodate changes."

---

## Related Pages

- [[wiki/component-based-engineering|CBSE & Spring Boot]] — Component-based reuse with frameworks
- [[wiki/open-source-software|Open Source Software]] — Community-driven software reuse
- [[wiki/design-patterns|Design Patterns Overview]] — Design-level reuse
- [[wiki/concepts/dependency-injection|Dependency Injection & IoC]] — Framework control mechanisms
- [[wiki/software-crisis|Software Crisis & No Silver Bullet]] — Buy vs. Build as attack on essential complexity

## Sources

- [[Clippings/lecture 5]]
