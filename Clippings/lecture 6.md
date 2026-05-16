---
title: lecture
source: https://gemini.google.com/app/b607eb17986fa6b4
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

Here is the organized Markdown documentation combining the knowledge points from the presentation and the tutorial exercises, keeping the original English phrasing from your materials. You can easily copy and paste this into Claude Code to compile your notes.

## Part 1: Knowledge Points

### What is Critical Analysis

- **Definition**: A systematic evaluation process to assess the strengths, weaknesses, and validity of software artifacts.
- **Purpose in Software Engineering**:
	- Identify defects early.
		- Improve system reliability.
		- Optimize development processes.
- **Why it Matters**:
	- 60% of software defects originate in the requirements phase (General industry consensus).
		- Fixing a bug in production is 100x more expensive than in design.
		- Real-world impact example: Therac-25 incident (1985-1987) where software flaws led to fatal radiation overdoses.
		- It is often a legal requirement in contexts like medical software (ISO 14971) and automotive software (ISO 26262).
- **Critical Thinking vs. Critical Analysis**:
	- Critical Thinking is general problem-solving and reasoning.
		- Critical Analysis is the focused, structured evaluation of specific artifacts, utilizing domain-specific tools and methods.

### Failure Modes and Effects Analysis (FMEA)

- FMEA is a proactive planning tool used to stop trouble before it starts.
- It involves listing all possible failures (failure modes) across a system, rating them, and prioritizing fixes.
- **Key Metrics (1-10 Scale)**:
	- **Severity (S)**: How bad the impact of the failure is on the system, user, or business (1 = minor, 10 = catastrophic).
		- **Occurrence (O)**: How often the failure happens (1 = rare, 10 = frequent).
		- **Detection (D)**: How likely we are to catch the failure before it reaches the user (1 = always detected, 10 = undetectable).
- **Risk Priority Number (RPN)**: Calculated as RPN = Severity × Occurrence × Detection.
	- High RPN items require immediate attention.
		- *Critical Rule*: Any item with a Severity of 9 or 10 must be addressed regardless of the total RPN, due to the high risk to human life or system integrity.

### Quantitative FMEA (Advanced)

- Instead of subjective 1-10 scales, this utilizes probabilistic models like failure rates or Mean Time To Failure (MTTF).
- **Formula**: RPN = S × O × (1 - D%), where D% is detection probability.
- **Mitigation Prioritization (Cost-Benefit Model)**:
	- Cost = Development effort (hours) + Tooling cost.
		- Benefit = Risk reduction (ΔRPN × Impact).

### Root Cause Analysis (RCA) and Fault Tree Analysis (FTA)

- **RCA** is a reactive, detective tool used to fix trouble after it happens. A common method is the "5 Whys".
- **Fault Tree Analysis (FTA)** is an advanced RCA technique. It is a top-down, deductive approach to identify and analyze the causes of a specific system failure (the "top event").
- **FTA Logic Gates**:
	- **OR Gate**: Represents that at least one of its causes occurs. Formula: P = 1 - (1 - P1) × (1 - P2).
		- **AND Gate**: Requires both inputs to occur. Formula: P = P1 × P2.
- **Dynamic vs. Static Probabilities**:
	- **Dynamic Nature**: Probabilities specified as "per hour" (failure rates), used for events that happen randomly over time (e.g., hardware failures). Tied to Mean Time To Failure (MTTF).
		- **Static Nature**: Single, dimensionless chances without a time unit. Used for constant conditions or design flaws (e.g., a 10% chance the system lacks a timeout mechanism).
- **Bridging RCA with FMEA**: This is the process of turning a reactive lesson into a proactive defense by taking RCA findings and manually inserting them into the FMEA table.

---

## Part 2: Tutorial Questions & Answers

### Question 1: User Login System FMEA

**Scenario**: You’re a quality engineer analyzing a simple user login system for a web application. The system authenticates users via a username and password. You need to perform an FMEA to identify potential failures and prioritize risks.

**Answer**:

| Failure Mode | Effect | Cause | Severity | Occurrence | Detection | RPN |
| --- | --- | --- | --- | --- | --- | --- |
| Incorrect password check | User cannot login | Logical error in code | 7 | 3 | 4 | 84 |
| Server timeout | Login hang | Network overload | 5 | 4 | 3 | 60 |
|  |  |  |  |  |  |  |

### Question 2: File Upload Feature FMEA

**Scenario**: You’re assessing a file upload feature in a cloud storage app. Users upload files via a web interface, and the system saves them to a server.

**Answer**:

| Failure Mode | Effect | Cause | Severity | Occurrence | Detection | RPN |
| --- | --- | --- | --- | --- | --- | --- |
| File corruption | User loss data | Transfer interrupt | 9 | 3 | 4 | 108 |
| Upload timeout | Upload failed, user retries | Slow server response | 6 | 5 | 3 | 90 |
|  |  |  |  |  |  |  |

### Question 3: Real-Time Video Streaming Service FMEA

**Scenario**: You’re a quality engineer for a real-time video streaming service. The critical function is “Stream video to user device”. The system processes 10,000 streams/hour during peak events.

**Data**:

- Historical Logs: 50 stream interruptions in 1,000 hours (0.05/hour/stream); 20 buffering delays in 1,000 hours (0.02/hour/stream); 10 decode errors in 1,000 hours (0.01/hour/stream); 5 crashes in 1,000 hours (0.005/hour/stream).
- Detection Metrics: Monitoring catches 90% of interruptions, 80% of delays, 70% of decode errors, 50% of crashes.
- Impact Assessment: Interruption: 10% dropout; Delay: 5% dropout; Decode error: 8% dropout; Crash: 15% dropout + complaints.

**Answer**:

| Failure Mode | Effect | Cause | S | O | D | RPN |
| --- | --- | --- | --- | --- | --- | --- |
| stream interruptions | 10% user dropout | Network package loss | 10 | 5 | 2 | 100 |
| buffering delays | 5% user dropout | Insufficient bandwidth | 6 | 3 | 3 | 54 |
| decode errors | 8% user dropout | Codec error/incompatible | 8 | 2 | 4 | 64 |
| crashes | 15% user dropout + complaints | Memory overflow | 10 | 1 | 6 | 60 |
|  |  |  |  |  |  |  |

### Question 4: E-Commerce Order Processing Failure RCA

**Scenario**: You’re a reliability engineer performing an RCA for an e-commerce platform where “Order processing fails”. The system handles order validation, payment, and inventory updates. Any one of these—network issue, server overload, payment failure, or DB lock—can halt order processing (top-level OR gate).

**Data**:

- Network disconnect: 0.02/hour.
- Server overload (caused by both): “High load” (0.05/hour) and “No scaling” (0.15).
- Payment gateway failure: 0.03/hour.
- Database lock (caused by both): “Concurrency bug” (0.01/hour) and “No lock timeout” (0.2).

**Answer**:

- **Server Overload** (AND): P = 0.05 × 0.15 = 0.0075/hour.
- **DB Lock** (AND): P = 0.01 × 0.2 = 0.002/hour.
- **Network**: 0.02/hour (direct).
- **Payment**: 0.03/hour (direct).
- **Top Event** (OR): P = 1 - (1 - 0.02) × (1 - 0.0075) × (1 - 0.03) × (1 - 0.002) = 1 - 0.98 × 0.9925 × 0.97 × 0.998 = 0.0580562 ≈ 0.058/hour (5.8% chance/hour).
- **MTTF**: 1/0.058 = 17.24 hours.

### Question 5: Cloud Backup System Failure RCA

**Scenario**: You’re investigating a failure where “Backup fails to complete”. Any one of Network, Storage, or Software failure causes the backup to fail (Top-Level Logic).

**Data**:

- Network Issue (caused by either): “Packet loss” (0.04/hour) or “Slow bandwidth” (0.03/hour).
- Storage Failure (caused by both): “Disk full” (0.02/hour) and “No auto-expansion” (0.25).
- Software Bug (caused by either): “Compression error” (0.015/hour) or (“File lock” (0.01/hour) AND “No retry” (0.3)).

**Answer**:

- **Network Issue** (OR): P = 1 - (1 - 0.04) × (1 - 0.03) = 1 - 0.96 × 0.97 = 0.0688/hour.
- **Storage Failure** (AND): P = 0.02 × 0.25 = 0.005/hour.
- **Software Bug**:
	- Lock Issue (AND): P = 0.01 × 0.3 = 0.003/hour.
		- Total (OR): P = 1 - (1 - 0.015) × (1 - 0.003) = 1 - 0.985 × 0.997 = 0.017955/hour.
- **Top Event** (OR): P = 1 - (1 - 0.0688) × (1 - 0.005) × (1 - 0.017955) = 1 - 0.9312 × 0.995 × 0.982045 = 0.090302 ≈ 0.090/hour (9.0% chance/hour).