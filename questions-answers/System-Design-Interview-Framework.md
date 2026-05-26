# How To Explain System Design

A structured framework for answering System Design interviews.

Goal:

- Cover requirements clearly
- Show scaling thinking
- Explain tradeoffs
- Justify design decisions
- Demonstrate production knowledge

---

## 1. Requirements Gathering [5 Minutes]

Understand the problem before designing.

Discuss:

1. Use Cases
2. Out Of Scope Scenarios
3. Users Of The System
4. Expected User Scale
5. Usage Patterns

Examples:

```text
Who uses the system?

How frequently?

Read Heavy?
Write Heavy?

Real Time Requirement?
```

---

## 2. Estimations [5 Minutes]

Estimate scale before architecture.

Discuss:

1. Throughput

```text
Read QPS
Write QPS
```

2. Latency Requirement

```text
Read Latency
Write Latency
```

3. Read Write Ratio

Example:

```text
Read : Write
100 : 1
```

4. Traffic Estimation

```text
Write QPS
Read QPS
Daily Traffic
```

5. Storage Estimation

6. Memory Estimation

Questions:

```text
Cache Required?

What Data Goes Into Cache?

How Much RAM Needed?

SSD Requirement?
```

---

## 3. Design Goals [5 Minutes]

Define system priorities.

Discuss:

1. Latency Requirement
2. Throughput Requirement
3. Consistency Requirement
4. Availability Requirement
5. Reliability Requirement

Examples:

Weak Consistency:

```text
Temporary Data Loss Acceptable

Example:
Video Call
```

Strong Consistency:

```text
Latest Data Required

Example:
Banking System
```

Eventual Consistency:

```text
Small Delay Acceptable

Example:
Instagram Feed
```

---

## 4. High Level Design [5 To 10 Minutes]

Discuss:

1. API Design
2. Database Schema
3. Core Algorithm
4. Read Flow
5. Write Flow
6. High Level Architecture

Example:

```text
Client
 ↓
Load Balancer
 ↓
Application Layer
 ↓
Cache
 ↓
Database
```

---

## 5. Deep Dive [15 To 20 Minutes]

### Scaling Strategy

Discuss:

- Availability
- Consistency
- Scalability
- Failure Handling

### Infrastructure Components

DNS

CDN

```text
Push CDN
Pull CDN
```

Load Balancer

```text
Active Active
Active Passive
Layer 4
Layer 7
```

Reverse Proxy

API Gateway

Application Layer

```text
Microservices
Service Discovery
```

Database Layer

SQL:

```text
Primary Replica
Sharding
Denormalization
Indexing
SQL Tuning
```

NoSQL:

```text
Key Value
Document
Wide Column
Graph
```

Cache Layer

```text
Client Cache
CDN Cache
Application Cache
Database Cache
```

Cache Patterns:

```text
Cache Aside
Write Through
Write Behind
Refresh Ahead
```

Asynchronous Components

```text
Message Queue
Task Queue
Back Pressure
Retry Strategy
```

Communication Layer

```text
REST
RPC
TCP
UDP
WebSocket
```

Reliability Layer

```text
Rate Limiter
Circuit Breaker
Distributed Lock
Idempotency
```

Observability

```text
Logging
Metrics
Tracing
Alerting
```

---

## 6. Justify Design [5 Minutes]

Explain decisions.

Discuss:

1. Throughput Per Layer
2. Latency Per Layer
3. Bottlenecks
4. Failure Handling
5. Tradeoffs
6. Scaling Approach

Interviewers often ask:

```text
Why This Design?

How Will It Scale?

What Breaks First?

Tradeoffs?
```

---

## 7. Scalability And Reliability

Discuss:

### Scaling

- Vertical Scaling
- Horizontal Scaling
- Replication
- Sharding
- Consistent Hashing

### Reliability

- Retry Strategy
- Circuit Breaker
- Distributed Lock
- Idempotency
- Rate Limiter

### Failure Handling

Questions:

```text
What Breaks First?

Single Point Of Failure?

How Will System Recover?
```

---

## Interview Questions

### Q1. CAP Theorem?

Partition tolerance is mandatory.

Real tradeoff:

```text
CP vs AP
```

---

### Q2. Latency vs Throughput?

```text
Latency
→ Time Per Request

Throughput
→ Requests Processed
```

---

### Q3. SQL vs NoSQL?

```text
SQL
→ Transactions

NoSQL
→ Scale
```

---

### Q4. Why Kafka?

```text
Async Processing
Event Streaming
```

---
---

## Interview Shortcut

Remember:

```text
Requirements
↓
Estimations
↓
Design Goals
↓
High Level Design
↓
Deep Dive
↓
Tradeoffs
↓
Justification
```

---

## Quick Revision

- Clarify requirements first
- Estimate scale before design
- Explain tradeoffs clearly
- Discuss bottlenecks
- Cover scaling approach
- Cover reliability approach
- Justify architecture decisions
- System Design interviews reward structured thinking
- Distributed Lock → Concurrency control
- Rate Limiter → Traffic protection
- Observability → Logs + Metrics + Tracing
- CAP → CP vs AP