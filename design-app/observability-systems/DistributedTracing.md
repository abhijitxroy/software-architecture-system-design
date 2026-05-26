

# Distributed Tracing System Design

## Problem Statement

Design a distributed tracing system to track requests across microservices and identify latency bottlenecks, failures and service dependencies.

Used in:

- Microservices
- API Platforms
- Kubernetes
- Cloud Native Systems
- Event Driven Systems

Examples:

- OpenTelemetry
- Jaeger
- Zipkin
- Datadog Tracing

System should support:

- End To End Request Tracking
- Trace Collection
- Span Collection
- Service Dependency Mapping
- Latency Analysis
- Error Analysis
- Distributed Search

---

## Functional Requirements

### Core Features

- Generate Trace ID
- Generate Span ID
- Collect traces
- Search traces
- Service dependency view
- Latency visualization
- Error debugging
- Sampling support

---

## Non Functional Requirements

### Scalability

- Millions of traces/day
- Thousands of services

### Availability

- 99.99% uptime

### Reliability

- Minimal trace loss

### Latency

- Trace ingestion under seconds

---

## Why Distributed Tracing Needed

Problem:

```text
User Request
↓
API Gateway
↓
Order Service
↓
Payment Service
↓
Inventory Service
↓
Notification Service
```

Payment becomes slow.

Question:

```text
Which service caused latency?
```

Distributed tracing answers this.

---

## Core Concepts

### Trace

Definition:

```text
Entire request journey
```

Example:

```text
TraceID=abc123

Gateway
→ Order
→ Payment
→ Notification
```

---

### Span

Definition:

```text
Single operation inside trace
```

Example:

```text
Span1 → API Gateway
Span2 → Payment Service
Span3 → Database Query
```

Span Data:

- Span ID
- Start Time
- End Time
- Service Name
- Error Status

---

### Trace ID

Purpose:

```text
Connect services under same request
```

Example:

```text
TraceID=xyz999
```

Flows across all services.

---

## High Level Design

```text
Application
 |
OpenTelemetry SDK
 |
Collector
 |
Kafka
 |
Trace Processor
 |
Distributed Storage
 |
Query Service
 |
Visualization Layer
```

---

## Request Flow

```text
User Request
↓
Generate Trace ID
↓
Create Span
↓
Pass Context
↓
Collect Trace
↓
Store Trace
↓
Visualization
```

---

## OpenTelemetry

Purpose:

Unified observability framework.

Provides:

- Trace collection
- Metrics collection
- Log collection

Flow:

```text
Application
↓
Instrumentation
↓
OpenTelemetry Collector
↓
Backend Storage
```

---

## Sampling

Problem:

Store every trace becomes expensive.

Solution:

### Head Sampling

Sample request early.

### Tail Sampling

Sample after request completion.

Benefits:

- Lower storage
- Lower compute

---

## Storage Strategy

Store:

- Trace ID
- Span ID
- Metadata
- Service name
- Latency

Storage Backend:

- Cassandra
- Elasticsearch
- ClickHouse

---

## Bottleneck Detection

Example:

```text
Gateway → 20ms
Order → 50ms
Payment → 1200ms
Inventory → 30ms
```

Root Cause:

```text
Payment Service
```

---

## Scaling Strategy

### Kafka

Responsibilities:

- Trace buffering
- Async processing

### Partitioning

Partition by:

```text
TraceID
```

### Retention

Strategies:

- TTL
- Compression

---

## Reliability

Strategies:

- Replication
- Retry mechanism
- Collector buffering
- Distributed storage

---

## Tradeoffs

| Choice | Benefit | Drawback |
|----------|----------|-----------|
| Full tracing | Better debugging | Higher cost |
| Sampling | Lower storage | Partial visibility |
| Long retention | Better debugging | Higher storage |

---

## Interview Questions

1. Trace vs Span?
2. Why Trace ID needed?
3. Why sampling required?
4. How bottleneck identified?
5. Why OpenTelemetry useful?
6. Why partition by Trace ID?

---

## Quick Revision

- Trace tracks request journey
- Span tracks operation
- Trace ID connects services
- Sampling reduces cost
- Kafka buffers traces
- OpenTelemetry standardizes observability