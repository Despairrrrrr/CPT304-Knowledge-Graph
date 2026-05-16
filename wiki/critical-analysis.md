---
tags:
  - cpt304
  - quality
  - critical-analysis
source: lecture-6
---
# Critical Analysis Overview

## Overview

Critical analysis is a systematic evaluation process used to assess the strengths, weaknesses, and validity of software artifacts. It is essential for identifying defects early, improving system reliability, and optimizing development processes.

### Why It Matters

- ~60% of software defects originate in the requirements phase
- Fixing a bug in production is **100x more expensive** than in design
- Real-world impact: Therac-25 incident (1985-1987) — software flaws led to fatal radiation overdoses
- Legal requirement in many domains: medical (ISO 14971), automotive (ISO 26262)

### Critical Thinking vs. Critical Analysis

| Aspect | Critical Thinking | Critical Analysis |
|--------|------------------|-------------------|
| Scope | General problem-solving and reasoning | Focused, structured evaluation of specific artifacts |
| Methods | Generic | Domain-specific tools and methods (FMEA, RCA, FTA) |

---

## Key Techniques

| Technique | Type | Purpose |
|-----------|------|---------|
| [[wiki/fmea|FMEA]] | Proactive | Prevent trouble before it starts |
| [[wiki/rca-and-fta|RCA & FTA]] | Reactive | Fix trouble after it happens |

### FMEA (Failure Modes and Effects Analysis)

A proactive planning tool that involves listing all possible failures across a system, rating them, and prioritizing fixes using the **Risk Priority Number (RPN)**.

**Key Metrics**: Severity (S), Occurrence (O), Detection (D) on 1-10 scales.
**RPN Formula**: RPN = S × O × D

→ See full details: [[wiki/fmea|FMEA page]]

### RCA (Root Cause Analysis) & FTA (Fault Tree Analysis)

RCA is a reactive detective tool (e.g., "5 Whys"). FTA is an advanced top-down, deductive approach using logic gates (AND/OR) to analyze failure causes.

→ See full details: [[wiki/rca-and-fta|RCA & FTA page]]

---

## Related Pages

- [[wiki/fmea|FMEA — Failure Modes and Effects Analysis]]
- [[wiki/rca-and-fta|RCA & Fault Tree Analysis]]
- [[wiki/software-testing|Software Testing Overview]] — Complementary quality assurance approach

## Sources

- [[Clippings/lecture 6]]
