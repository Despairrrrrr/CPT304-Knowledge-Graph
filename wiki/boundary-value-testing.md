---
tags:
  - cpt304
  - testing
  - bvt
source: lecture-9
---
# Boundary Value Testing (BVT)

## Overview

Boundary Value Analysis selects input variable values based on the rationale that **errors tend to occur near the extreme values** of input variables. It works well for physical variables (temperature, pressure) but not for logical variables (PINs).

For a function with **n** variables, BVT defines test cases based on these standard values:

| Value | Meaning |
|-------|---------|
| **min** | Minimum valid value |
| **min+** | Just above minimum |
| **nom** | Nominal (typical) value |
| **max-** | Just below maximum |
| **max** | Maximum valid value |

---

## Types of BVT

| Type | Values Used | Assumption | Formula |
|------|------------|------------|---------|
| **Normal BVT** | min, min+, nom, max-, max | Single fault assumption (failures rarely involve multiple simultaneous faults) | 4n + 1 |
| **Robust BVT** | Adds max+, min- (beyond bounds) | Tests exception handling; still single fault | 6n + 1 |
| **Worst-case BVT** | min, min+, nom, max-, max | Rejects single fault; tests extreme value combinations | 5ⁿ |
| **Robust Worst-case BVT** | All 7 values (min-, min, min+, nom, max-, max, max+) | Combines robustness with worst-case combinations | 7ⁿ |

---

## Tutorial Example: Car Loan Application

**Variables**:
- Cost of car: $1,000 to $200,000
- Loan period: 1 to 10 years
- Interest rate: 0.01 to 0.2

### Boundary Values

| Variable | min | min+ | nom | max- | max |
|----------|-----|------|-----|------|-----|
| Cost | 1000 | 1001 | 100000 | 199999 | 200000 |
| Period | 1 | 2 | 5 | 9 | 10 |
| Interest | 0.01 | 0.02 | 0.1 | 0.19 | 0.2 |

### Invalid (Robust) Values

| Variable | min- | max+ |
|----------|------|------|
| Cost | 999 | 200001 |
| Period | 0 | 11 |
| Interest | 0 | 0.21 |

### Test Case Counts

| Type | Formula | Count |
|------|---------|-------|
| Normal BVT | 4(3) + 1 | **13** |
| Robust BVT | 6(3) + 1 | **19** |
| Worst-case BVT | 5³ | **125** |
| Robust Worst-case BVT | 7³ | **343** |

---

## Related Pages

- [[wiki/software-testing|Software Testing Overview]] — Context and fundamentals
- [[wiki/equivalence-class-testing|Equivalence Class Testing]] — Complementary partitioning technique
- [[wiki/decision-table-testing|Decision Table Testing]] — Logic-based testing for complex conditions

## Sources

- [[Clippings/lecture 9]]
