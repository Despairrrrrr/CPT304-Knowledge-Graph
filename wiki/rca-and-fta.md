---
tags:
  - cpt304
  - quality
  - rca
  - fta
source: lecture-6
---
# RCA & Fault Tree Analysis

## Overview

Root Cause Analysis (RCA) is a **reactive** detective tool used to investigate failures after they occur. Fault Tree Analysis (FTA) is an advanced RCA technique that uses a top-down, deductive approach to identify the causes of a specific system failure.

---

## Root Cause Analysis (RCA)

### The "5 Whys" Method

A simple but powerful technique: repeatedly ask "why" to drill down from symptoms to root causes.

### Bridging RCA with FMEA

Turning a reactive lesson into a proactive defense: take RCA findings and insert them into the [[wiki/fmea|FMEA]] table to prevent future occurrences.

---

## Fault Tree Analysis (FTA)

FTA is a top-down approach that starts with a specific system failure (the "top event") and decomposes it into contributing causes using logic gates.

### Logic Gates

| Gate | Behavior | Probability Formula | Example |
|------|----------|-------------------|---------|
| **OR Gate** | At least one cause occurs | P = 1 - (1 - P₁) × (1 - P₂) | Network OR Payment failure |
| **AND Gate** | Both inputs must occur | P = P₁ × P₂ | High load AND No scaling |

### Dynamic vs. Static Probabilities

| Type | Unit | Used For | Example |
|------|------|----------|---------|
| **Dynamic** | Per hour (failure rate) | Random events over time (hardware) | 0.02/hour network failure |
| **Static** | Dimensionless chance | Constant conditions or design flaws | 0.15 chance of "no scaling" |

---

## Tutorial Examples

### Example 1: E-Commerce Order Processing

**Top Event**: Order processing fails

**Tree Structure**:
- Top: OR (Network, Server Overload, Payment Failure, DB Lock)
  - **Server Overload** (AND): High Load (0.05/hr) × No Scaling (0.15) = 0.0075/hr
  - **DB Lock** (AND): Concurrency Bug (0.01/hr) × No Lock Timeout (0.2) = 0.002/hr
  - **Network**: 0.02/hr
  - **Payment**: 0.03/hr

**Calculation**:
- Top OR: P = 1 - (1 - 0.02) × (1 - 0.0075) × (1 - 0.03) × (1 - 0.002)
- P = 1 - 0.98 × 0.9925 × 0.97 × 0.998 = **0.058/hr (5.8%)**
- **MTTF** = 1 / 0.058 = **17.24 hours**

### Example 2: Cloud Backup System

**Top Event**: Backup fails to complete

**Tree Structure**:
- Top: OR (Network Issue, Storage Failure, Software Bug)
  - **Network Issue** (OR): Packet Loss (0.04/hr) OR Slow Bandwidth (0.03/hr) = 0.0688/hr
  - **Storage Failure** (AND): Disk Full (0.02/hr) × No Auto-expansion (0.25) = 0.005/hr
  - **Software Bug** (OR):
    - Compression Error (0.015/hr) OR
    - (File Lock (0.01/hr) AND No Retry (0.3)) = 0.003/hr
    - Total = 1 - (1 - 0.015) × (1 - 0.003) = 0.01796/hr

**Calculation**:
- Top OR: P = 1 - (1 - 0.0688) × (1 - 0.005) × (1 - 0.01796)
- P = 1 - 0.9312 × 0.995 × 0.98205 = **0.090/hr (9.0%)**

---

## Related Pages

- [[wiki/fmea|FMEA]] — Proactive counterpart to RCA
- [[wiki/critical-analysis|Critical Analysis Overview]] — Context and importance
- [[wiki/software-testing|Software Testing Overview]] — Complementary quality approach

## Sources

- [[Clippings/lecture 6]]
