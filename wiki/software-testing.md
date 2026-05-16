---
tags:
  - cpt304
  - testing
  - quality
source: lecture-9
---
# Software Testing Overview

## Overview

Software testing is the process of evaluating and verifying that a software application meets its requirements and functions as expected. Testing can never establish correctness — it can only find defects, not prove their absence.

### Testing Activities

1. Identify test conditions ("What")
2. Design test approach ("How")
3. Build test cases (scripts, data)
4. Execute (run the system)
5. Compare outcome with expected outcome
6. Determine test result

### Test Stopping Criteria

- Meeting a deadline or exhausting budget
- Achieving desired coverage
- Achieving a desired level of failure intensity

---

## Black-Box (Functional) Testing

A methodology where the system is evaluated based on external behavior — input and output — without knowledge of its internal code or structure.

**Focus**: I/O behavior. If for any given input the output can be predicted, the module passes.

**Goal**: Reduce the number of test cases by dividing input conditions into equivalence classes and choosing representative test cases for each.

### Advantages
- Test cases independent of implementation
- Can be developed in parallel with implementation

### Disadvantages
- Potential redundancies among test cases
- Possible gaps in test coverage

---

## Key Testing Techniques

| Technique | Focus | Best For |
|-----------|-------|----------|
| [[wiki/boundary-value-testing|Boundary Value Testing]] | Extreme values of input variables | Physical variables (temperature, pressure) |
| [[wiki/equivalence-class-testing|Equivalence Class Testing]] | Partitioning inputs into classes | Reducing test cases while maintaining coverage |
| [[wiki/decision-table-testing|Decision Table Testing]] | Logical relationships among inputs | Complex business logic, if-then-else |

---

## Related Pages

- [[wiki/boundary-value-testing|Boundary Value Testing]]
- [[wiki/equivalence-class-testing|Equivalence Class Testing]]
- [[wiki/decision-table-testing|Decision Table Testing]]
- [[wiki/critical-analysis|Critical Analysis Overview]] — Complementary quality approaches
- [[wiki/fmea|FMEA]] — Proactive quality analysis

## Sources

- [[Clippings/lecture 9]]
