

# Circuit Breaker System Design

## Problem Statement

Design a circuit breaker mechanism that prevents cascading failures in distributed systems when downstream services become slow or unavailable.

Used in:

- Microservices
- API Platforms
- Cloud Native Systems
- Kubernetes Platforms
- Payment Systems
- AI Platforms

Examples:

- Hystrix
- Resilience4j
- Envoy
- Istio

System should support:

- Failure Detection
- Fast Failure Response
- Retry Protection
- Fallback Response
- Service Recovery
- Traffic Control

---

## Functional Requirements

### Core Features

- Detect failures
- Stop unhealthy traffic
- Retry support
- Fallback mechanism
- Health monitoring
- Recovery validation

---

## Non Functional Requirements

### Scalability

- Millions of requests/minute

### Availability

- 99.99% uptime

### Reliability

- Prevent cascading failures

### Latency

- Circuit evaluation under milliseconds

---

## Why Circuit Breaker Needed

Without protection:

```text
Order Service
↓
Payment Service Slow
↓
Request Queue Build Up
↓
Thread Exhaustion
↓
System Failure
```

Goal:

```text
Detect Failure
↓
Stop Traffic
↓
Recover Safely
```

---

## Circuit Breaker States

### Closed State

Normal operation.

Flow:

```text
Request
↓
Backend Service
↓
Response
```

Behavior:

- Requests allowed
- Failure metrics tracked

---

### Open State

Backend unhealthy.

Flow:

```text
Request
↓
Circuit Breaker
↓
Fail Fast
```

Behavior:

- Block traffic
- Return fallback

---

### Half Open State

Recovery validation.

Flow:

```text
Limited Traffic
↓
Backend Service
↓
Healthy ?
```

Healthy:

```text
Move Closed
```

Failure:

```text
Move Open
```

---

## Failure Detection

Signals:

- Error rate
- Timeout
- High latency
- Connection failure

Example:

```text
Failure Rate > 50%
10 Seconds
↓
Open Circuit
```

---

## High Level Design

```text
Client
 |
API Gateway
 |
Circuit Breaker Layer
 |
Retry Layer
 |
Backend Service
```

---

## Request Flow

```text
Client Request
↓
Check Circuit State
↓
Backend Service
↓
Failure Metrics
↓
Circuit Decision
```

---

## Fallback Strategy

Examples:

```text
Cached Data
Default Response
Graceful Degradation
```

Example:

```text
Payment Down
↓
Show Retry Message
```

---

## Scaling Strategy

### Distributed Metrics

Track:

- Failure count
- Latency
- Timeout

### Redis

Optional:

- Shared breaker state

---

## Reliability

Strategies:

- Timeout configuration
- Retry limits
- Bulkhead isolation
- Health check

---

## Tradeoffs

| Choice | Benefit | Drawback |
|----------|----------|-----------|
| Aggressive opening | Faster protection | False positive |
| Retry logic | Better recovery | More load |
| Shared state | Consistency | Complexity |

---

## Interview Questions

1. Why circuit breaker needed?
2. Open vs Closed vs Half Open?
3. Retry vs Circuit Breaker?
4. Why cascading failures happen?
5. Why fallback needed?
6. Why timeout important?

---

## Quick Revision

- Circuit breaker prevents cascading failure
- Open blocks traffic
- Closed allows traffic
- Half Open validates recovery
- Timeout prevents resource exhaustion
- Fallback improves resilience