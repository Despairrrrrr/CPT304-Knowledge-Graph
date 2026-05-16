---
title: lecture
source: https://gemini.google.com/app/08db330adf83cad6
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

Here is the Markdown summary of the CPT304 lecture slides and tutorial exercises, formatted specifically for ingestion into your note-taking tool.

## 1\. Overview of Software Testing

- **Definition**: Software testing is the process of evaluating and verifying that a software application or system meets its requirements and functions as expected.
- **Limitation**: Testing can never establish the correctness of computer software; it can only find defects, not prove that there are none.
- **Purpose**: To discover more problems, ensure quality, and check whether the product matches the requirements.
- **Testing Activities**:
	1. Identify Test conditions ("What").
		2. Design (How the "what" can be tested).
		3. Build test cases (scripts, data).
		4. Execute (Run the system).
		5. Compare test case outcome with expected outcome.
		6. Determine Test result.
- **Test Stopping Criteria**: Meeting a deadline or exhausting budget, achieving desired coverage, or achieving a desired level of failure intensity.

---

## 2\. Black-box / Functional Testing

- **Definition**: A software testing methodology where the system under test is evaluated based on its external behavior, without knowledge of its internal code, structure, or implementation details.
- **Focus**: Testers focus on input and output ($I/O$) behavior. If for any given input, the output can be predicted, the module passes the test.
- **Advantages**: Test cases are independent of how the software is developed, and their development can occur in parallel with implementation.
- **Disadvantages**: Significant redundancies may exist among test cases, and there is a possibility of gaps of untested software.
- **Goal**: Reduce the number of test cases by dividing input conditions into equivalence classes and choosing representative test cases for each.

---

## 3\. Boundary Value Testing (BVT)

Boundary value analysis selects input variable values based on the rationale that errors tend to occur near the extreme values of an input variable. It works well for physical variables (e.g., temperature, pressure) but not for logical variables (e.g., PINs).

For a function with $n$ variables, BVT defines test cases based on standard variable values: Minimum (`min`), Just above minimum (`min+`), Nominal (`nom`), Just below maximum (`max-`), and Maximum (`max`).

### Types of BVT

- **Normal BVT**: Relies on the single fault assumption (failures rarely occur from simultaneous faults). Variables are held at nominal values while one variable assumes extreme values. Yields $4n+1$ unique test cases.
- **Robust BVT**: Adds values slightly greater than the maximum (`max+`) and slightly less than the minimum (`min-`) to force attention on exception handling. Yields $6n+1$ unique test cases.
- **Worst-case BVT**: Rejects the single fault assumption and tests what happens when more than one variable has an extreme value. Uses the Cartesian product of the five normal boundary values, yielding $5^n$ test cases.
- **Robust Worst-case BVT**: Applies the Cartesian product to the seven-element sets used in robustness testing, yielding $7^n$ test cases.

---

## 4\. Equivalence Class Testing

Equivalence classes form a partition of a set (mutually disjoint subsets whose union is the entire set). This technique identifies test cases by using one element from each equivalence class, providing completeness and assuring non-redundancy.

### Types of Equivalence Class Testing

- **Weak Normal Equivalence Class Testing**: Aims to cover all the equivalence classes at least once without covering all possible combinations. The minimum number of test cases equals the number of classes in the partition with the largest number of subsets.
- **Strong Normal Equivalence Class Testing**: Based on the Cartesian product of the partition subsets, generating more test cases to test for any interaction between representative values.
- **Weak Robust Equivalence Class Testing**: Similar to Weak Normal, but adds one test case to cover out-of-range (invalid) values for each variable.
- **Strong Robust Equivalence Class Testing**: Derives test cases from the Cartesian product of all equivalence classes, including the additional out-of-range classes.
- **Output Equivalence Class**: Partitioning is applied to the output domain of the software to represent different responses or behaviors the software may exhibit based on input.

---

## 5\. Decision Table Based Testing

Decision tables are a precise and compact way to model complicated logic, associating independent conditions with several actions. They are most appropriate for programs with prominent if-then-else logic, complex computation logic (high cyclomatic complexity), and important logical relationships among input variables.

### Structure

- **Condition Stubs**: Lists the variables, relations, or predicates.
- **Condition Entries**: Lists the possible values for conditions (True, False, or Don't Care).
- **Action Stubs**: Lists the procedures or operations to perform.
- **Action Entries**: Specifies whether the action is to be performed.

### Methodology

1. Determine conditions and values.
2. Determine maximum number of rules.
3. Determine actions.
4. Encode possible rules and their appropriate actions.
5. Verify the policy and simplify the rules (reduce the number of columns whenever possible).

---

## 6\. Tutorial Week 11 Exercises

### Question 1: Car Loan Application BVT

**Scenario**: Calculate monthly payments based on Cost of the car ($1,000 to $200,000), Loan period (1 to 10 years), and Interest rate (0.01 to 0.2).

- **Boundary Values**:
	- Cost: 1000 (min), 1001 (min+), 100000 (nom), 199999 (max-), 200000 (max).
		- Period: 1 (min), 2 (min+), 5 (nom), 9 (max-), 10 (max).
		- Interest: 0.01 (min), 0.02 (min+), 0.1 (nom), 0.19 (max-), 0.2 (max).
- **Invalid Values**:
	- Cost: 999, 200001.
		- Period: 0, 11.
		- Interest: 0, 0.21.
- **Test Case Yields**:
	- **Normal BVT**: $4(3) + 1 = 13$ test cases.
		- **Robust BVT**: $6(3) + 1 = 19$ test cases.
		- **Worst-case BVT**: $5^3 = 125$ test cases.
		- **Robust Worst-case BVT**: $7^3 = 343$ test cases.

### Question 2: Equivalence Class Testing

**Scenario**: Function $f(x_1, x_2)$ defined by $1000 \le x_1 \le 10000$ and $10 \le x_2 \le 50$. Classes are V1 \[1000-5000\], V2 \[5001-10000\], V3 \[10-19\], V4 \[20-29\], V5 \[30-50\].

- **Strong vs. Weak Normal**: Strong normal equivalence class testing generates more test cases because it is based on the Cartesian product of the partition subsets (testing all combinations), whereas weak normal only aims to cover each equivalence class at least once.

### Question 3: Decision Table for E-commerce Shipping

**Scenario**: Calculate shipping based on Item Type (Fragile/Non-Fragile), Shipping Method (Standard, Express, Overnight), and Order Price (<$50, $50-$100, >$100).

- **Rules**:
	- Standard: Non-Fragile ($5), Fragile ($10).
		- Express: Non-Fragile ($10), Fragile ($15).
		- Overnight: Non-Fragile ($20), Fragile ($25).
		- <$50: Additional $5 handling fee.
		- $50-$100: No additional fees.
		- \>$100: Free shipping entirely.

**Decision Table (Test Cases)**:

| Case | Item Type | Shipping Method | Order Price | Shipping Fee | Handling Fee | Total |
| --- | --- | --- | --- | --- | --- | --- |
| **1** | Fragile | Standard | <$50 | $10 | $5 | $15 |
| **2** | Fragile | Express | <$50 | $15 | $5 | $20 |
| **3** | Fragile | Overnight | <$50 | $25 | $5 | $30 |
| **4** | Non-Fragile | Standard | <$50 | $5 | $5 | $10 |
| **5** | Non-Fragile | Express | <$50 | $10 | $5 | $15 |
| **6** | Non-Fragile | Overnight | <$50 | $20 | $5 | $25 |
| **7** | \- | \- | \>$100 | $0 | $0 | $0 |
| **8** | Fragile | Standard | $50-100 | $10 | $0 | $10 |
| **9** | Fragile | Express | $50-100 | $15 | $0 | $15 |
| **10** | Fragile | Overnight | $50-100 | $25 | $0 | $25 |
| **11** | Non-Fragile | Standard | $50-100 | $5 | $0 | $5 |
| **12** | Non-Fragile | Express | $50-100 | $10 | $0 | $10 |
| **13** | Non-Fragile | Overnight | $50-100 | $20 | $0 | $20 |