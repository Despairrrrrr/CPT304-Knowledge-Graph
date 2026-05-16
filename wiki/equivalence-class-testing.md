---
tags:
  - cpt304
  - testing
  - equivalence-class
source: lecture-9
---
# Equivalence Class Testing

## Overview

Equivalence classes form a **partition** of a set — mutually disjoint subsets whose union equals the entire set. This technique identifies test cases by using one element from each equivalence class, providing completeness and assuring non-redundancy.

---

## Types of Equivalence Class Testing

### Weak Normal

Aims to cover all equivalence classes at least once without covering all possible combinations.

- Minimum test cases = number of classes in the partition with the largest number of subsets
- Single fault assumption

### Strong Normal

Based on the **Cartesian product** of the partition subsets, generating more test cases to test for interactions between representative values.

- Tests all combinations of equivalence class representatives
- Rejects single fault assumption

### Weak Robust

Similar to Weak Normal, but adds one test case to cover **out-of-range (invalid) values** for each variable.

### Strong Robust

Derives test cases from the Cartesian product of **all** equivalence classes, including the additional out-of-range classes.

---

## Comparison Summary

| Type | Single Fault? | Covers Invalid? | Test Count |
|------|:---:|:---:|------------|
| Weak Normal | Yes | No | Fewest cases |
| Strong Normal | No | No | More (Cartesian product) |
| Weak Robust | Yes | Yes | Weak Normal + invalid cases |
| Strong Robust | No | Yes | Most (full Cartesian + invalid) |

### Output Equivalence Class

Partitioning can also be applied to the **output domain** of the software to represent different responses or behaviors the software may exhibit.

---

## Tutorial Example

**Function**: f(x₁, x₂) where 1000 ≤ x₁ ≤ 10000 and 10 ≤ x₂ ≤ 50

**Classes**:
- V₁: [1000, 5000], V₂: [5001, 10000]
- V₃: [10, 19], V₄: [20, 29], V₅: [30, 50]

**Key Insight**: Strong Normal generates more test cases than Weak Normal because it tests all combinations (Cartesian product) rather than only covering each class at least once.

---

## Related Pages

- [[wiki/software-testing|Software Testing Overview]] — Context and fundamentals
- [[wiki/boundary-value-testing|Boundary Value Testing]] — Complementary extreme-value testing
- [[wiki/decision-table-testing|Decision Table Testing]] — Logic-based testing

## Sources

- [[Clippings/lecture 9]]
