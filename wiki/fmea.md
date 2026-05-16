---
tags:
  - cpt304
  - quality
  - fmea
source: lecture-6
---
# FMEA (Failure Modes and Effects Analysis)

## Overview

FMEA is a **proactive** planning tool used to identify and prioritize potential failures in a system before they occur. It involves listing all possible failure modes, rating them, and prioritizing fixes.

---

## Key Metrics (1-10 Scale)

| Metric | Description | 1 (Low) | 10 (High) |
|--------|-------------|---------|-----------|
| **Severity (S)** | How bad the impact is | Minor | Catastrophic |
| **Occurrence (O)** | How often failure happens | Rare | Frequent |
| **Detection (D)** | How likely to catch before reaching user | Always detected | Undetectable |

## Risk Priority Number (RPN)

**Formula**: RPN = Severity × Occurrence × Detection

### Rules
- **High RPN items** require immediate attention
- **Critical Rule**: Any item with Severity 9 or 10 **must** be addressed regardless of total RPN (due to risk to human life or system integrity)

---

## Quantitative FMEA (Advanced)

Uses probabilistic models instead of subjective 1-10 scales.

**Formula**: RPN = S × O × (1 - D%), where D% is detection probability.

**Mitigation Prioritization (Cost-Benefit Model)**:
- **Cost** = Development effort (hours) + Tooling cost
- **Benefit** = Risk reduction (ΔRPN × Impact)

---

## Tutorial Examples

### Example 1: User Login System

| Failure Mode | Effect | S | O | D | RPN |
|-------------|--------|---|---|---|-----|
| Incorrect password check | User cannot login | 7 | 3 | 4 | 84 |
| Server timeout | Login hang | 5 | 4 | 3 | 60 |

### Example 2: File Upload Feature

| Failure Mode | Effect | S | O | D | RPN |
|-------------|--------|---|---|---|-----|
| File corruption | User loses data | 9 | 3 | 4 | 108 |
| Upload timeout | Upload failed, user retries | 6 | 5 | 3 | 90 |

### Example 3: Real-Time Video Streaming (Quantitative)

Data: 10,000 streams/hour during peak. Failure rates calculated from historical logs.

| Failure Mode | Effect | S | O | D | RPN |
|-------------|--------|---|---|---|-----|
| Stream interruption | 10% user dropout | 10 | 5 | 2 | 100 |
| Buffering delays | 5% user dropout | 6 | 3 | 3 | 54 |
| Decode errors | 8% user dropout | 8 | 2 | 4 | 64 |
| Crashes | 15% dropout + complaints | 10 | 1 | 6 | 60 |

---

## Related Pages

- [[wiki/critical-analysis|Critical Analysis Overview]] — Context and importance
- [[wiki/rca-and-fta|RCA & Fault Tree Analysis]] — Reactive counterpart to FMEA
- [[wiki/software-testing|Software Testing Overview]] — Complementary QA approach

## Sources

- [[Clippings/lecture 6]]
