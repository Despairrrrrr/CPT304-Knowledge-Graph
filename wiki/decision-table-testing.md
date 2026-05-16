---
tags:
  - cpt304
  - testing
  - decision-table
source: lecture-9
---
# Decision Table Testing

## Overview

Decision tables are a precise and compact way to model complicated logic, associating independent conditions with several actions. They are most appropriate for programs with:

- Prominent if-then-else logic
- High cyclomatic complexity (complex computation logic)
- Important logical relationships among input variables

---

## Table Structure

| Component | Description |
|-----------|-------------|
| **Condition Stubs** | Lists the variables, relations, or predicates |
| **Condition Entries** | Lists possible values for conditions (True, False, or Don't Care) |
| **Action Stubs** | Lists the procedures or operations to perform |
| **Action Entries** | Specifies whether the action is to be performed |

## Methodology

1. Determine conditions and their possible values
2. Determine maximum number of rules (2ⁿ for binary conditions)
3. Determine actions
4. Encode possible rules and their appropriate actions
5. Verify the policy and simplify rules (reduce columns where possible)

---

## Tutorial Example: E-Commerce Shipping Calculation

### Conditions
- **Item Type**: Fragile / Non-Fragile
- **Shipping Method**: Standard, Express, Overnight
- **Order Price**: <$50, $50-$100, >$100

### Rules

- **Standard**: Non-Fragile ($5), Fragile ($10)
- **Express**: Non-Fragile ($10), Fragile ($15)
- **Overnight**: Non-Fragile ($20), Fragile ($25)
- **<$50**: Additional $5 handling fee
- **$50-$100**: No additional fees
- **>$100**: Free shipping entirely

### Decision Table

| Case | Item Type | Shipping Method | Order Price | Shipping Fee | Handling Fee | Total |
|:----:|:---------:|:---------------:|:-----------:|:------------:|:------------:|:-----:|
| 1 | Fragile | Standard | <$50 | $10 | $5 | $15 |
| 2 | Fragile | Express | <$50 | $15 | $5 | $20 |
| 3 | Fragile | Overnight | <$50 | $25 | $5 | $30 |
| 4 | Non-Fragile | Standard | <$50 | $5 | $5 | $10 |
| 5 | Non-Fragile | Express | <$50 | $10 | $5 | $15 |
| 6 | Non-Fragile | Overnight | <$50 | $20 | $5 | $25 |
| 7 | — | — | >$100 | $0 | $0 | $0 |
| 8 | Fragile | Standard | $50-100 | $10 | $0 | $10 |
| 9 | Fragile | Express | $50-100 | $15 | $0 | $15 |
| 10 | Fragile | Overnight | $50-100 | $25 | $0 | $25 |
| 11 | Non-Fragile | Standard | $50-100 | $5 | $0 | $5 |
| 12 | Non-Fragile | Express | $50-100 | $10 | $0 | $10 |
| 13 | Non-Fragile | Overnight | $50-100 | $20 | $0 | $20 |

---

## Related Pages

- [[wiki/software-testing|Software Testing Overview]] — Context and fundamentals
- [[wiki/boundary-value-testing|Boundary Value Testing]] — Extreme-value testing
- [[wiki/equivalence-class-testing|Equivalence Class Testing]] — Partition-based testing

## Sources

- [[Clippings/lecture 9]]
